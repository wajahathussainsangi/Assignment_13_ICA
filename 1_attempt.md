# Referee's Note: Teaching Price Data

## Item Statistics

The following statistics use the normalized item name and exclude rows with
a missing price, a review flag, or a label-collision flag. The
first-to-last percentage change compares the mean of the two cities at the
first date with the mean of the two cities at the last date.

| Item | Mean | Median | First-to-last change |
|---|---:|---:|---:|
| Staple A | 111.39 | 112.50 | 12.98% |
| Oil B | 325.13 | 324.00 | 15.28% |
| Pulse C | 205.91 | 206.00 | 5.25% |
| Sweetener D | 167.15 | 167.50 | 19.41% |

### Staple A

- **Mean:** 111.39
- **Median:** 112.50
- **Effect of excluding the flagged 1250.0 value:** The mean is 160.89
  with the flagged value included and 111.39 with it excluded. The median
  is unchanged at 112.50.

### Sweetener D

- **Mean:** 167.15
- **Median:** 167.50
- **Effect of excluding the flagged 9999.0 value:** The mean is 576.81
  with the flagged value included and 167.15 with it excluded. The median
  changes only slightly, from 167.75 to 167.50.

## O (Observation)

Staple A contains a review-flagged value of 1250.0, and Sweetener D contains
a review-flagged value of 9999.0. Both are far outside the range of the
remaining observations for their respective items.

## E (Possible Explanation)

The extreme values may be data-entry or unit-recording errors rather than
genuine market movements. The flagging is therefore consistent with the
possibility of anomalous observations that should not drive publication
statistics.

## C (Causal Claim)

Ms. Noor should publish the summary estimates with missing and flagged
values excluded. The median is robust to the extreme observations, but the
mean becomes substantially misleading when they are included.
