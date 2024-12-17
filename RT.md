Calculates Statistical Measures Of Reaction Times For Truitbait Levels In Each PDA Category (High, Medium, Low Truthbait Levels) Which Is Compiled Into A pandas File





```python
df['pda'] = pd.Categorical(df['pda'], categories=['High', 'Medium', 'Low'], ordered=True)

# Function to calculate the standard error
def standard_error(x):
    return np.std(x, ddof=1) / np.sqrt(len(x))

# Function to calculate the 95% confidence interval
def confidence_interval(x):
    se = standard_error(x)
    mean = np.mean(x)
    ci_lower = mean - 1.96 * se
    ci_upper = mean + 1.96 * se
    return pd.Series([mean, se, ci_lower, ci_upper], index=['mean_rt', 'stnd_err', 'ci_lower', 'ci_upper'])

# Group by 'participant_id', 'truthbait', and 'pda' and apply the confidence_interval function
df_ci = df.groupby(['participant_id', 'truthbait', 'pda'], dropna=False, observed=False)['rt'].apply(confidence_interval).unstack()

df_ci```
