# Workshop Learning Log

## Starting Point

I came into this workshop mainly wanting to understand what makes a Ritual
prediction market different from a normal prediction market.

At first glance, the contract looked familiar.

There are markets, users, YES and NO positions, resolution and rewards.

The part I did not understand well was how the contract could resolve itself
without somebody manually calling it.

## First Question

My first question was simple:

Who actually calls the contract when the market is ready to resolve?

I initially assumed there would be an off-chain bot running somewhere.

After reading the project again, I realized that the Scheduler is part of the
Ritual infrastructure used for this purpose.

## Second Question

The next thing that confused me was the TEE executor.

I originally thought the executor itself decided the market result.

That turned out to be the wrong mental model.

The executor is involved in performing the external operation, while the
contract still contains the rules that determine the final result.

## Understanding the Oracle

The oracle part became easier once I separated it into two steps.

First, the system retrieves an HTTP response.

Second, the required value is extracted from that response.

The jq precompile is useful because the response can contain many fields.

## Resolution Parameters

The market stores the information required for later resolution.

This includes the URL and the JSON path.

That means the market does not need somebody to manually tell it which value
to use later.

## Failure Cases

This was the part I spent the most time thinking about.

External requests can fail.

A failed request is not the same as a prediction being false.

This seems obvious after understanding the architecture, but I did not think
about it that way initially.

## Claims

The claim system also caught my attention.

Instead of paying everybody during resolution, users claim their own rewards.

This keeps the settlement process smaller.

## What I Would Improve

If I were continuing the workshop, I would probably build a small frontend
first.

I would want to see:

- market status
- YES pool
- NO pool
- resolution block
- oracle status
- claimable amount

That would make the lifecycle much easier to understand.

## Current Understanding

My current mental model is:

market rules
    ↓
Scheduler
    ↓
executor
    ↓
HTTP data
    ↓
JSON extraction
    ↓
contract comparison
    ↓
market result
    ↓
claim

Writing this sequence down helped more than reading the contract repeatedly.

## Next Steps

I want to spend more time on the failure paths and edge cases.

Those seem more interesting than simply testing a successful market.
