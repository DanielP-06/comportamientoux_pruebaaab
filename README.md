# comportamientoux_pruebaaab
User behavior &amp; A/A/B test analysis for a food app. Funnel showed main screen to offers bottleneck. Font change A/B test found no significant impact on conversion. Recommend optimizing main screen transition; font decision based on design, not conversion.

# User Behavior Analysis and Typography A/A/B Test

## Project Overview

This project investigates user behavior within a food delivery application with two primary goals:
1. To map and analyze the user conversion funnel to identify bottlenecks.
2. To evaluate the impact of a typography change through an A/A/B test.

The analysis aims to provide data-driven insights to optimize the conversion rate and guide design decisions.

## Problem

The company needs to understand how users navigate the application towards making a purchase. Specifically:
- How many users reach the purchase stage?
- Where do users drop off in the funnel?
- What is the impact of a proposed application-wide font change on user behavior and conversion rates? Management is concerned the new font might be perceived as "intimidating."

An A/A/B test was conducted with three groups: two control groups using the old font and one test group using the new font. The A/A test between the two control groups serves to validate the experimental setup and establish a baseline for expected variation.

## Development

The analysis involved several steps:

1.  **Data Loading and Preparation**:
    - Loaded log data from `logs_exp_us.csv`.
    - Parsed a single combined column into separate columns (`event_name`, `device_id_hash`, `event_timestamp`, `exp_id`).
    - Converted `event_timestamp` to datetime objects and extracted a separate date column.
    - Checked for missing values and found none.

2.  **Data Study and Verification**:
    - Calculated the total number of events and unique users.
    - Determined the average number of events per user.
    - Identified the time period covered by the data.
    - Analyzed the distribution of events over time using a histogram, revealing incomplete data at the beginning of the log period.
    - Filtered the data to include only the period with complete data (starting from August 1, 2019).
    - Verified that filtering did not result in a significant loss of events or users.
    - Confirmed the presence of users from all three experimental groups in the filtered data with a relatively balanced distribution.

3.  **Event Funnel Analysis**:
    - Studied the frequency of each event type, identifying `MainScreenAppear` as the most frequent.
    - Analyzed the conversion funnel based on unique users reaching key stages (`MainScreenAppear` -> `OffersScreenAppear` -> `CartScreenAppear` -> `PaymentScreenSuccessful`).
    - Visualized the funnel to show user drop-off points.

4.  **A/A/B Test Analysis**:
    - Conducted an A/A test between the two control groups (246 and 247) using the Z-test for proportions to compare the percentage of users reaching each funnel stage.
    - Conducted A/B tests comparing the test group (248) with each control group individually (248 vs 246, 248 vs 247) and with the combined control groups (248 vs 246+247) for each event type using the Z-test for proportions.
    - Used a significance level ($\alpha$) of 0.05 for the statistical tests. Acknowledged the implication of multiple comparisons and the use of Bonferroni correction ($\alpha_{adjusted} = 0.0025$).
    - Visualized the proportion of users reaching each funnel stage by group to support the statistical findings.

## Solution

Based on the analysis:

1.  **Conversion Funnel**: The primary bottleneck in the user journey is the transition from the **Main Screen to the Offers Screen**. A significant number of users drop off at this stage. The subsequent stages (Offers to Cart, Cart to Payment Successful) show relatively higher completion rates for users who reach them.
2.  **A/A Test**: The A/A test confirmed **no statistically significant difference** between the two control groups (246 and 247) across all major funnel events. This validates the experimental setup and user distribution.
3.  **A/B Test**: The A/B test comparing the test group (248) with the control groups (246, 247, and combined) revealed **no statistically significant difference** in the proportion of users reaching any of the key funnel stages or the Tutorial event.

## Recommendations

1.  **Focus on Main Screen to Offers Transition**: The most impactful opportunity for improving overall conversion lies in optimizing the Main Screen experience and the user's journey towards exploring offers. Investigate potential reasons for the low transition rate, such as the visibility and clarity of calls-to-action, user interface design, or initial user engagement elements on the main screen.
2.  **Typography Change Decision**: Since the A/B test showed **no statistically significant impact** (neither positive nor negative) on key conversion metrics, the decision to implement the new typography can be based on **other factors** beyond conversion rate. These factors may include improved readability, aesthetic appeal, brand consistency, or technical ease of implementation. There is no statistical evidence from this experiment to suggest that the new font "intimidates" users or negatively affects conversion.

