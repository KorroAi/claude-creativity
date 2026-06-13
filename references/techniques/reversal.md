# Assumption Reversal

## When to Use
Debugging, dead ends, unsolvable problems. When you've tried everything and nothing works. When the bug makes no sense.

## The Method
1. List every assumption you're making about the problem.
2. One by one, reverse each assumption. "What if this is NOT true?"
3. For each reversal, ask: "If this were false, what would explain the observations?"
4. The reversal that makes everything suddenly make sense — that's your answer.

## Example
Bug: "The API returns 200 but the data is wrong."
Assumptions: The database has correct data. The ORM query is right. The serializer is mapping fields correctly. The cache isn't stale.
Reversal: "What if the database does NOT have correct data?"
Turns out: A background job was overwriting the field. Nobody checked because "the DB is the source of truth" was too sacred to question.

## Why It Works
The most dangerous assumptions are the ones you don't know you're making. Systematically reversing them surfaces blind spots that logical debugging misses.
