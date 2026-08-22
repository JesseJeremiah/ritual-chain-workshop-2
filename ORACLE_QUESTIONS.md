# Oracle Questions

## Question 1

What happens if the endpoint is temporarily unavailable?

This should not become a YES or NO result.

## Question 2

What if the HTTP request succeeds but the JSON structure changes?

The configured JSON path may no longer point to the expected value.

## Question 3

What if the extracted value has an unexpected format?

The resolution process needs to reject data that cannot be interpreted
correctly.

## Question 4

Why store the JSON path when the market is created?

Because the resolution rule should not change after users have placed bets.

## Question 5

Why use multiple scheduled attempts?

Because external data sources are not guaranteed to respond successfully on
the first attempt.

## Question 6

What happens after a successful attempt?

There is no reason to keep executing the same resolution process once the
market has already been resolved.

## Question 7

What if every attempt fails?

The market should have a defined invalid/refund path instead of inventing an
outcome.

## Question 8

Could a callback be repeated?

The contract should protect an already resolved market from being settled
again.

## Question 9

Does an oracle decide the outcome?

No.

The oracle provides data.

The contract applies the configured comparison rule.

## Question 10

What is the most important security assumption?

The resolution process should not silently turn unavailable or malformed
external data into a valid prediction result.

## Notes

These questions helped me understand that the difficult part of a
self-resolving market is not simply fetching data.

The difficult part is defining what counts as valid data and what should
happen when the outside world behaves unexpectedly.
