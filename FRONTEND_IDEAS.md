# Frontend Ideas

## Goal

I would keep the frontend intentionally small.

The contract should remain the source of truth.

The frontend should mainly make the market state easier to understand.

## Market Card

Each market could show:

- question
- YES pool
- NO pool
- deadline
- resolution status
- winning side

## Betting

The user should be able to select:

YES

or

NO

and enter an amount.

Before sending the transaction, the interface should display the selected
side and amount.

## Resolution Status

A useful status display could contain:

- Waiting
- Resolving
- Resolved
- Invalid

This would make the Scheduler behavior easier for users to understand.

## Oracle Information

For debugging, an advanced view could show:

- oracle URL
- JSON path
- last resolution attempt
- resolution block

These values do not necessarily need to be shown to normal users.

## Claim

After resolution, the frontend should calculate whether the connected
address has a claimable amount.

The user should then have one obvious Claim button.

## Error Messages

The frontend should translate common contract errors into readable messages.

For example:

Instead of showing a raw transaction revert, display:

"You cannot place a bet after the market deadline."

## History

A later version could show:

- previous markets
- winners
- total volume
- number of participants

Events emitted by the contract could be used to build this history.

## Keep It Simple

I would avoid adding complicated frontend logic.

The important financial rules should stay in the smart contract.

The frontend should only display state and submit transactions.

## Future Version

A later version could add charts and market analytics.

For the workshop, however, a simple interface would be enough to understand
the complete lifecycle.
