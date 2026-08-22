# Prediction Market Edge Case Matrix

| Scenario | Expected Behavior | Priority |
|---|---|---|
| Valid market | Create successfully | High |
| Zero stake | Reject or handle according to rules | High |
| YES bet | Increase YES pool | High |
| NO bet | Increase NO pool | High |
| Late bet | Reject | High |
| Resolved market | Reject new bets | High |
| Invalid oracle response | Do not settle | High |
| Missing JSON field | Do not settle | High |
| HTTP failure | Retry | High |
| Repeated callback | Ignore/reject | High |
| Successful resolution | Set result | High |
| Invalid market | Refund | High |
| Winning claim | Pay reward | High |
| Duplicate claim | Reject | High |
| Unauthorized operation | Reject | High |
| Empty winning pool | Handle safely | High |
| Multiple participants | Correct payout | Medium |
| Multiple markets | Keep state isolated | Medium |
| Very small stake | Preserve accounting | Medium |
| Large stake | Preserve accounting | Medium |
| Resolution near deadline | Handle correctly | Medium |
| Repeated resolution attempt | Do not change result | High |
| Oracle data changes | Use configured resolution | Medium |
| Unexpected response format | Reject safely | High |
| Scheduler retry | Continue when allowed | High |

## Testing Order

I would test the high-priority financial cases first.

The most important ones are:

1. Betting
2. Deadline
3. Resolution
4. Invalid resolution
5. Claim
6. Duplicate claim

After those are stable, I would move to executor and oracle edge cases.

## Why This Matrix Helps

I found that writing the cases down was easier than trying to remember all
of them while reading the contract.

It also makes it easier to see which cases involve user funds and which ones
are mainly infrastructure failures.
