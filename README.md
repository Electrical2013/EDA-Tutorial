Word to Markdown
Results of converting Readme.md.docx
Markdown
## **Title**: **EDA Using Univariate,** **Bivariate or Multivariate**

# Introduction: The preliminary analysis of data to discover relationships between measures in the data and to gain an insight on the trends, patterns, and relationships among various entities present in the data set with the help of statistics and visualization tools is called Exploratory Data Analysis (EDA). Exploratory data analysis is cross-classified in two different ways where each method is either graphical or non-graphical. And then, each method is either univariate, bivariate or multivariate.

\## **Structure**:

├── README.md # Details of topic  
├── EDA Using Univariate Analysis.py # Python script

├── EDA Using Bivariate & Multivariate Analysis.py # Python script

\## **Steps**:

For EDA, First, we need to identify the types of Data: -

1. Numerical Data means Numbers like Height, Age, Prices etc.
2. Categorical Data, examples – Nationality, Gender, States etc.

After that will apply different type of Visualization of establish relationship or the story of data.

\## **Univariate Analysis**: - Uni means one and variate means variable, so in univariate analysis, there is only one dependable variable. The objective of the univariate analysis is to derive the data, define and summarize it, and analyse the pattern present in it. In a dataset, it explores each variable separately. It is possible for two kinds of variables- Categorical and Numerical.

For Example, will consider Titanic Dataset,

\`\`\` python code

import seaborn as sns

titanic = sns.load_dataset('titanic')

print(titanic)

Column Details-

| Survived | Survival (0 = No, 1 = Yes) |
| --- | --- |
| Pclass | Passenger class (1 = 1st, 2 = 2nd, 3 = 3rd) |
| Sex | Gender (male, female) |
| Age | Age in years |
| Sibsp | Number of siblings/spouses aboard |
| Parch | Number of parents/children aboard |
| Fare | Passenger fare |
| Embarked | Port of Embarkation (C = Cherbourg, Q = Queenstown, S = Southampton) |
| Class | Passenger class (First, Second, Third) |
| Who | Gender (Man, Women) |
| adult_male | Adult Male(True, False) |
| Deck | Deck nos. |
| embark_town | Port of Embarkation |
| Alive | Survival (no and Yes) |
| Alone | Alone(False & True) |

Here there are some duplicate columns, ‘survived’=’alive’, ‘pclass’= ’class’, ‘sex’ = ‘who’, ‘embarked’= ‘embark_town’), which we don’t require.

\`\`\` python code

titanic.drop(\['alive', 'class', 'who', 'embark_town'\], axis=1, inplace=True)

print(titanic)

Some of column not require for further process – ‘adult_male’, ‘deck’, ‘alone’

\`\`\` python code

titanic.drop(\['adult_male', 'deck', 'alone'\], axis=1, inplace=True)

print(titanic)

Data Type of Each Column: -

Survived - Categorical data, pclass - Categorical Data, sex - Categorical Data, age - Numerical Data, sibsp - Categorical Data, parch - Categorical Data, fare - Numerical Data, embarked - Categorical Data

## **Analysis on Categorical Data**\-

**count Plot**

On **Survived** Data – 1<sup>st</sup> question would be how many people survived and how many not, for that will apply count Plot

\`\`\` python code

import seaborn as sns

import matplotlib.pyplot as plt

sns.countplot(x='survived', data=titanic)

plt.title("Survival Count")

plt.show()

As per the graph in ipynp file, it shows out of 891 people, more than 500 people died and less than people survived.

Or,

\`\`\` python code

titanic\['survived'\].value_counts().plot(kind='bar')

On pclass column – Question in which class most people were travelling-

\`\`\` python code

sns.countplot(x='pclass', data=titanic)

As per the graph in ipynp file, it shows most people are travelling at 3<sup>rd</sup> class.

On sex column – Gender distribution

\`\`\` python code

sns.countplot(x='sex', data=titanic)

As per the graph in ipynp file, it shows male category people are higher than female.

**Pie Chart**

On Survived Data-

\`\`\` python code

titanic\['survived'\].value_counts().plot(kind='pie', autopct='%1.1f%%')

It shows, total of people how % people survived and how many % are not

Same way for pclass column shows how % people travelled in different classes-

\`\`\` python code

titanic\['pclass'\].value_counts().plot(kind='pie', autopct='%1.1f%%')

plt.title('class Distribution')

## **Analysis on Numerical Data**\-

**Histogram**

Here we can create range or bins,

\`\`\` python code

import matplotlib.pyplot as plt

plt.hist(titanic\['age'\])

As per graph, it shows age between 0 to 18 people are less, 18 to 40 age group people are more and again older age after 40 people are less in titanic.

**Kdeplot**

\`\`\` python code

sns.kdeplot(titanic\['age'\])

Here, x-axis represent age, y-axis represent Density. So it shows at any age in x axis, y represent probability of people present in titanic. Example, people of age 60 were 5% present in titanic of total people.

**Boxplot**

\`\`\` python code

sns.boxplot(titanic\['fare'\])

This is the box plot for fare column. It shows more fares are between medium & maximum values are less as the box is in below side. 1 no. outlier shows above 500-dollar way more than other passengers.

\## **Bivariate & Multivariate Analysis**: - It examines relationships between two or more variables, uncovering patterns and insights in the data.

For Example, will consider Titanic, tips, flights, and iris Dataset

\`\`\` python code

import seaborn as sns

import pandas as pd

titanic = sns.load_dataset('titanic')

titanic.drop(\['alive', 'class', 'who', 'embark_town', 'adult_male', 'deck', 'alone'\], axis=1, inplace=True)(#as explained earlier)

print(titanic) (#Column details explained earlier)

tips=sns.load_dataset('tips')

print(tips)

Column Details-

| total_bill | Total ill amount, numerical Column |
| --- | --- |
| tip | Tip given by customer, numerical Column |
| Sex | Gender(Male or female) |
| Smoker | Customer smoker (Yes or not) |
| Day | Day of dinning |
| Time | Time of dinning |
| Size | Size of group customers |

\`\`\` python code

flights=sns.load_dataset('flights')

print(flights)

Column Details-

| Year | Year of flying |
| --- | --- |
| Month | Month of flying |
| Passengers | Total passengers number in the flight |

\`\`\` python code

iris=sns.load_dataset('iris')

print(iris)

Column Details-

| sepal_length | Length of the sepal in centimeters |
| --- | --- |
| sepal_width | Width of the sepal in centimeters |
| petal_length | Length of the petal in centimeters |
| petal_width | Width of the petal in centimeters |
| species | Type of Iris flower (e.g., _setosa_, _versicolor_, _virginica_) |

**Scatterplot (Numeric – Numeric)**

In tips data, total_bill and tip column are numerical. To establish relationship between those two columns, will use scatterplot.

\`\`\` python code

import matplotlib.pyplot as plt

sns.scatterplot(x=tips\['total_bill'\], y=tips\['tip'\])

plt.show()

As per graph, each dot represents one customer. It looks like linear type relationship, as the total bill increased tip also increased. This is bivariate analysis. To establish multivariate analysis, we can add sex column on that.

\`\`\` python code

sns.scatterplot(x=tips\['total_bill'\], y=tips\['tip'\],hue=tips\['sex'\])

plt.show()

Now in this same graph, we can identify blue dot customers are Male and orange dot customers are Female. Now add smoker column on the same graph as style-

\`\`\` python code

sns.scatterplot(x=tips\['total_bill'\], y=tips\['tip'\],hue=tips\['sex'\],style=tips\['smoker'\])

plt.show()

Now in this same graph, we can identify round dot customers are smoker and cross dot customers are non-smoker.

Similarly we can add size column to identify how many peoples are there with each customer.

\`\`\` python code

sns.scatterplot(x=tips\['total_bill'\], y=tips\['tip'\],hue=tips\['sex'\],style=tips\['smoker'\],size=tips\['size'\])

plt.show()

**Bar plot (Numeric – Categorical)**

In titanic data, pclass is Categorical data and age is Numerical data. We can analyse the average age of traveller’s age as per pclass.

\`\`\` python code

sns.barplot(x=titanic\['pclass'\],y=titanic\['age'\])

plt.show()

It shows, pclass 1 travellers’ ages are higher (upto 38) and pclass travellers’ age range upto 25 approx. Now replace fare with age as it is numeric column.

\`\`\` python code

sns.barplot(x=titanic\['pclass'\],y=titanic\['fare'\])

plt.show()

It shows, pclass 1 travellers’ fare is higher than pclass 2 & 3. Now if we need to know fare according to gender of pclass, can add as hue-

\`\`\` python code

sns.barplot(x=titanic\['pclass'\],y=titanic\['fare'\],hue=titanic\['sex'\])

plt.show()

It shows, female passengers paid higher average fare.

**Box plot (Numeric – Categorical)**

\`\`\` python code

sns.boxplot(x=titanic\['sex'\],y=titanic\['age'\])

plt.show()

It shows, category wise (male & female) age group and male travellers’ have some outliers.

\`\`\` python code

sns.boxplot(x=titanic\['sex'\],y=titanic\['age'\], hue=titanic\['survived'\])

plt.show()

It shows, in male, young people are more survived and in female, older people are more survived.

**Kdeplot (Numeric – Categorical)**

\# Drop missing ages, as kdeplot does not support missing value.

\`\`\` python code

titanic_clean = titanic.dropna(subset=\['age'\])

KDE plots for survivors and non-survivors

\`\`\` python code

sns.kdeplot(data=titanic_clean\[titanic_clean\['survived'\] == 0\], x='age', label='Did not survive', fill=True)

sns.kdeplot(data=titanic_clean\[titanic_clean\['survived'\] == 1\], x='age', label='Survived', fill=True)

plt.title('Age Distribution by Survival Status')

plt.xlabel('Age')

plt.ylabel('Density')

plt.legend()

plt.show()

Blue curve represents the curve for age group of non-survivors, pink curve represent the curve for age group of survivors.

If the age is less, the probability of dying is less means surviving probability is more.

For age group from 15 to 30, the probability of dying is higher means surviving probability is less. For age above 60 people, survival probability is less.

**HeatMap (Categorical – Categorical)**

\`\`\` python code

pd.crosstab(titanic\['pclass'\],titanic\['survived'\])

Crosstab show, in every pclass, how many people survived and how many people not survived. This is relationship between two categorical column. The graph for the same-

\`\`\` python code

sns.heatmap(pd.crosstab(titanic\['pclass'\],titanic\['survived'\]))

plt.show()

It shows lighter shade people are pclass 3 are higher quantity and not survived. To get the % wise the surviving people quantity per pclass, we can write-

\`\`\` python code

(titanic.groupby('pclass')\['survived'\].mean()\*100).plot(kind='bar')

To get % wise people survived as per Embarked-

\`\`\` python code

titanic.groupby('embarked')\['survived'\].mean()\*100

It show 55% people are from c(Cherbourg).

**HeatMap (Categorical – Categorical)**

\`\`\` python code

pd.crosstab(titanic\['parch'\],titanic\['survived'\])

It shows relationship between parent-child and survived people.

\`\`\` python code

sns.clustermap(pd.crosstab(titanic\['parch'\],titanic\['survived'\]))

plt.show()

The dendrograms shows, cluster 1 & 2s probability of surviving and not surviving chances are almost similar. Someway for 3,4,5,6 cluster groups surviving probabilities are same.

**Pairplot (For multiple Numerical Columns)**

In iris dataset 4 columns are numerical. Will apply pairplot to establish relationship.

\`\`\` python code

sns.pairplot(iris, hue='species')

Each row and column in the grid represents one feature (e.g., sepal_length, sepal_width, petal_length, petal_width). The diagonal typically shows histograms or KDE plots for individual features. The off-diagonal plots show scatter plots of one feature vs another. The hue='species' argument colors the points based on their class label (setosa, versicolor, virginica), helping you see how separable the species are based on feature pairs. Example, setosa is very clearly separable from the other two species, especially when using petal_length and petal_width.

**Lineplot (Numerical-Numerical)**

Lineplot mainly used for time variant. As example, the flights dataset has years and month column. To get yearwise passenger travelled in flight, python code is-

\`\`\` python code

new=flights.groupby('year')\['passengers'\].sum().reset_index()

print(new)

sns.lineplot(x=new\['year'\],y=new\['passengers'\])

Above graph shows year wise passenger also increased simultaneously.

\`\`\` python code

flights.pivot_table(values='passengers', index='month',columns='year')

Above code table creates a pivot table showing the number of passengers for each month across different years. Now will apply heatmap on this result-

\`\`\` python code

sns.heatmap(flights.pivot_table(values='passengers', index='month',columns='year'))

The heatmap shows as years are increased, heatmap colours get lighter that means passengers quantity increased. If we consider month, July-August means summer months have more passengers.

Now instead of heatmap, if clustermap apply, then we get the similar months behaviours.

\`\`\` python code

sns.clustermap(flights.pivot_table(values='passengers', index='month',columns='year'))

Example July-August both months are in same cluster. 1959 & 1960 are in same cluster.
