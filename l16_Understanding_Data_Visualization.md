# Understanding Data Visualization
## A plot tells a thousand words
3 Ways of getting insights
- Calculating summary statistics mean, median, standard deviation
- Running models linear and logistic regression
- Drawing plots scatter, bar, histogram

Continuous and Categorical variables
- Continuous: usually numbers
  - heights, temp, revenues
- Categorical: usually text
  - eye colors, countries, industry
- Can be either
  - age is continuous, but age group is categorical
  - time is continuous, month of year is categorical

### Histograms
When should you use histogram?
1. If you have a single continuous variable
2. You want to ask questions about the shape of its distribution

Skewness: Is it symmetric?
A left-skewed distribution has outliers, that is the extreme values on the left. A right-skewed distribution has outlier on the right.
![Image](https://drive.google.com/uc?id=18El085q1-q-iqttqZm11_z29SfjM290q)

### Box plots
When should you use Box plots?
1. When you have a continuous variable, split by a categorical variable.
2. When you want to compare the distributions of the continuous variable for each category.
![Image](https://drive.google.com/uc?id=154wZCStZ5iVK9Uw4-jM4UgyBjRcLiR-X)

### Scatter plots
When should you use scatter plot?
1. You have 2 continuous variables.
2. You want to answer questions about the relationship between the 2 variables.
![Image](https://drive.google.com/uc?id=1hDF2pGP6a91k9ZsQbF3LpQ8tZqUIAeLR)

### Line plots
A close relative to the scatter plot. 
\
When should you use Line plot?
1. You have 2 continuous variables.
2. You want to answer questions about the relationship.
3. Consecutive observations are connected somehow.
\
Usually, but not always, the x-axis is dates or times.
\
Can compare line plots to a trend line.

### Bar plots
When should you use bar plot?
- Most common cases:
1. You have a categorical variable.
2. You want counts or percentages for each category.
- Occasionnally:
1. You want another numeric score for each category, and need to include zero in the plot.

### Dot plots
When should you use Dot plot?
1. You have categorical variable.
2. You want to display numeric scores for each category on a log scale, or
3. You want to display multiple numeric scores for each category.

## The color and the shape
### Higher dimensions
x and y are not the only dimensions
\
Points also have these dimensions
1. color
![Image](https://drive.google.com/uc?id=14XF5F-T7yyB71up6jdlgrH_4TSkx-Smz)
2. size
![Image](https://drive.google.com/uc?id=10OCCs01-OhIS3K2T7h0C62L2lev1xMyv)
3. transparency
![Image](https://drive.google.com/uc?id=10iRcSR2fx51n02l0k22uAXzOhen2yOUY)
4. shape
![Image](https://drive.google.com/uc?id=1jHfjQTu1i1zVYczaisdwlndJGuLYnG5i)

One final option is to draw panels for diffenrent subsets of the dataset
![Image](https://drive.google.com/uc?id=18hcP6avnrHmzDfAjUFMCfCyuWR0UimtK)

### Using color
Choosing a plotting palette 
- Usually, each color should stand out as much as other colors. 
- The perceptual distance from one color in the plot to the next should be constant.

3 types of color scale
1. qualitative: Distinguish unordered categories
![Image](https://drive.google.com/uc?id=1jORa0-kjVv0zsmCubCXPxL7_4GceNmWd)
2. sequential: Show ordering
![Image](https://drive.google.com/uc?id=1dYlx1K4Ur5z8RF592Uw5WfHhkyd1L6dT)
3. diverging:	Show above or below a midpoint
![Image](https://drive.google.com/uc?id=16-E2a2vxDah4m9_5IPxc1bFpV2hiNznn)

### Plotting many variables at once
When should you use pair plot?
- You have up to 10 variables.
- You want to see the distribution for each variable. 
- You want to see the relationship between each pair of variables.