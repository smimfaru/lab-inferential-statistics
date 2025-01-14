![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | Inferential statistics


### Instructions

1. It is assumed that the mean systolic blood pressure is `μ = 120 mm Hg`. In the Honolulu Heart Study, a sample of `n = 100` people had an average systolic blood pressure of 130.1 mm Hg with a standard deviation of 21.21 mm Hg. Is the group significantly different (with respect to systolic blood pressure!) from the regular population?

   - Set up the hypothesis test.
   - Write down all the steps followed for setting up the test.
   - Calculate the test statistic by hand and also code it in Python. It should be 4.76190. We will take a look at how to make decisions based on this calculated value.

2. If you finished the previous question, please go through the code for `principal_component_analysis_example` provided in the `files_for_lab` folder .




import scipy.stats as stats

# Given data
population_mean = 120  # μ = 120 mm Hg
sample_mean = 130.1    # Sample mean
sample_std = 21.21     # Sample standard deviation
sample_size = 100      # Sample size (n)

# Step 1: State the Hypotheses
# Null Hypothesis (H0): μ = 120 mm Hg (no difference)
# Alternative Hypothesis (H1): μ ≠ 120 mm Hg (there is a difference)

# Step 2: Calculate the Test Statistic (Z-score)
z_score = (sample_mean - population_mean) / (sample_std / (sample_size ** 0.5))
print(f"Calculated Z-score: {z_score:.5f}")

# Step 3: Decision Rule
# At a significance level of α = 0.05, the critical z-value for a two-tailed test is ±1.96
alpha = 0.05
critical_z = stats.norm.ppf(1 - alpha / 2)
print(f"Critical Z-value: ±{critical_z:.2f}")

# Step 4: Conclusion
if abs(z_score) > critical_z:
    print("Reject the null hypothesis: The group's systolic blood pressure is significantly different from the population mean.")
else:
    print("Fail to reject the null hypothesis: No significant difference in systolic blood pressure.")

# By hand calculation:
# Z = (130.1 - 120) / (21.21 / sqrt(100))
# Z = 10.1 / 2.121 = 4.76190
