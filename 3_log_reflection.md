# Log and Reflection

## Interpretation Audit

I checked the AI's interpretation against the numbers in the CSV. I marked
verified statements as accepted, and I used amber when the explanation went
beyond what the data actually showed.

| Sentence / claim | Check | Verdict |
|---|---|---|
| Staple A mean is 111.39 and median is 112.50. | Recomputed from 22 valid Staple A prices. | Accepted |
| Oil B mean is 325.13 and median is 324.00. | Recomputed from 23 valid Oil B prices after excluding label-collision rows. | Accepted |
| Pulse C mean is 205.91 and median is 206.00. | Recomputed from 23 valid Pulse C prices. | Accepted |
| Sweetener D mean is 167.15 and median is 167.50. | Recomputed from 23 valid Sweetener D prices. | Accepted |
| Staple A increased 12.98% from first to last date. | City means 101.50 to 114.50. | Accepted |
| Oil B increased 15.28% from first to last date. | City means 301.00 to 347.00. | Accepted |
| Pulse C increased 5.25% from first to last date. | City means 200.00 to 210.50. | Accepted |
| Sweetener D increased 19.41% from first to last date. | City means 152.00 to 181.50. | Accepted |
| Staple A mean changes from 160.89 to 111.39 when 1250.0 is excluded. | Recomputed with and without the one review value. | Accepted |
| Sweetener D mean changes from 576.81 to 167.15 when 9999.0 is excluded. | Recomputed with and without the one review value. | Accepted |
| The extreme values may be data-entry or unit-recording errors. | No root cause is recorded, so this is only a plausible explanation. | Amber |
| Ms. Noor should exclude missing and review-flagged observations. | Supported by quality flags and sensitivity analysis. | Accepted |

## Conversation with a Confused Classmate

**Me:** “I thought the mean was supposed to tell us the typical
Staple A price. Why shouldn't I just use 160.89?”

**Classmate:** Because 160.89 includes the one review value of 1250.0, and that
value pulls the average upward. The cleaner mean is 111.39. The median is
112.50, so it tells a fairly similar story to the mean after the unusual value
is removed.

**Me:** “Okay, but does the 9999.0 price prove someone made a mistake?”

**Classmate:** It doesn't prove anything by itself. The data mark that observation
for review and it is much larger than the rest of Sweetener D. That makes an
entry or unit error plausible, but we have no evidence of the actual cause.
For that reason, I would say only that it is anomalous and needs checking,
not that it is definitely wrong.

**Me:** “Why did you exclude label-collision rows?”

**Classmate:** The flag tells us that those labels may not be suitable for
unambiguous aggregation. I chose to exclude them so that the results group
prices under one clear normalized item name. This does not mean I know what
the collision represents; it only means it is safer not to mix those rows into
the cleaned summary.

**Me:** “Why calculate both a mean and a median?”

**Classmate:** They answer slightly different questions. The mean uses every
included observation, while the median identifies the middle observation.
Looking at both makes it easier to notice when one unusual price has too much
influence on the result.

## Reflection

When I first saw the data, the large Staple A and Sweetener D values were
immediately noticeable. It was tempting to start by calling them errors,
but I eventually slowed down and checked what the data could and could not
support. The flags did justify further review, while the CSV did not provide
enough information to identify a specific cause.

I also learned that a small cleaning decision can have a large effect on the
result. For Staple A, removing the flagged 1250.0 value lowers the mean from
160.89 to 111.39. For Sweetener D, removing 9999.0 lowers the mean from
576.81 to 167.15. The medians barely move in comparison. That difference
made the sensitivity analysis more important than simply presenting one
cleaned table.

If I were writing the note again, I would begin with the exact cleaning rule:
missing prices, review values, and label collisions are excluded. I would then
show the cleaned statistics and the with-and-without comparison for the two
obvious anomalies. I would also keep the possible explanations cautious.
Calling them “possible entry or unit issues” is reasonable; claiming that they
are caused by entry or unit problems is not.
