# Home Sales Spark Big Data Project

<p align="center">
  <img src="https://www.adiyprojects.com/wp-content/uploads/2021/08/Selling-Your-Home1-768x432.jpg" alt="Home for Sale (Image Taken from adiyprojects.com)">
</p>

-----

## Project Description

The goal of this project was to use Spark SQL queries to ascertain information from a database of information about home sales. The data contained the following fields:
- An id for each house for sale
- The date the house was listed
- The year the house was built
- The final selling price of the house
- The number of bedrooms, bathrooms, and floors
- The square footage of living space, and the square footage of the lot
- Whether the house was on a waterfront
- How many times the house had been viewed

Spark SQL queries were written to collect the requested information, and these were practiced further after caching the data and partioning the data using parquet.

-----

## Queries

#### Average Price by Build Year of Four Bedroom Houses

A SQL query was written to find the average price of four bedroom houses sold for each build year within the dataset. The results are plotted on the graph below:

<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/Home_Sales_Spark/main/Output%20Images/Price%20by%20Year%20for%204%20Bedroom%20Houses.png" alt="Average Price by Build Year of Four Bedroom Houses">
</p>

It can be seen from the above graph that, while there are slight variations, the build years in the dataset all had approximately similar average prices of around $300,000. This is likely due to the fact that all build years are relatively recent, and there is only a narrow range within the dataset.

#### Average Price by Build Year of Three Bed/Three Bath Houses

A query was then written to find the average price of 3 Bedroom/3 Bathroom houses sold for each build year within the dataset. The results are plotted on the graph below:

<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/Home_Sales_Spark/main/Output%20Images/Average%20Price%20by%20Build%20Year%20of%20Three%20Bed_Three%20Bath%20Houses.png" alt="Average Price by Build Year of Three Bedroom/Three Bathroom Houses">
</p>

Again, the build year does not appear to have a significant impact on the average price likely for the same reasons as stated above. The average price is slightly below $300,000 in all years, and slightly below the average price for 4 bedroom houses. This is to be expected since we are filtering for fewer bedrooms, but including the requirement of 3 bathrooms, which probably removes some of the cheaper, less be-bathroomed houses from the pool.

#### Average Price by Build Year of Three Bed/Three Bath more than 2,000 sqft Houses with two floors

A similar query was then written to find the average price of 3 Bedroom/3 Bathroom houses sold for each build year within the dataset, but with the specific inclusions of requiring two floors and a minimum living size (not lot size) of 2,000 sqft. The results are plotted on the graph below:

<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/Home_Sales_Spark/main/Output%20Images/Average%20Price%20by%20Build%20Year%20of%20Three%20Bed_Three%20Bath%20more%20than%202%2C000%20sqft%20Houses%20with%20two%20floors.png" alt="Average Price by Build Year of Three Bedroom/Three Bathroom Houses with other considerations">
</p>

In this case, we see slightly more variability in the house price. Slightly unexpectedly, houses more recently built (2016, 2017) actually sold for less (at around %275,000) whereas a house built in 2013 had an average price of just above $300,000. This is still not an enormous amount of variability though. It must also be remembered that we are including a wide range of houses in each of these averages, in spite of the specific filter criteria applied.

#### Viewed Times by Average Price of homes that are $350,000 or higher

Finally, a query was written to find out the average price of a house based on how many times it had been viewed. This was filtered to only show houses with sale prices of at least $350,000.

The results can be seen in the graph below:

<p align="center">
  <img src="https://raw.githubusercontent.com/jonnybrammah/Home_Sales_Spark/main/Output%20Images/View%20Times%20vs%20Average%20Price%20for%20homes%20greater%20than%20%24350%2C000.png" alt="View times vs Average Price">
</p>

This yielded some pretty interesting results. There are essentially three clusters in the dataset:
- Houses of around $400,000 tend to be viewed from anywhere from 0 to about 50 times. This makes sense because this price range probably includes a wide variety of types of house, attracting a range of people with differing needs.
- Houses around $700,000 and $800,000 are viewed roughly between 50 and 75 times.
- The most expensive houses (just under $1M to about $1.15M are viewed between 75 and 100 times.

This query ran in 0.68 seconds, since the dataset is relatively small.
Caching the dataset reduced this time to 0.45 seconds, and partitioning it using Parquet before running actually increased the time 0.79 seconds. This is likely because on the whole the dataset could be considered relatively small (33,000 rows) and partioning, while slowest here, would almost certainly end up being the fastest method if this dataset was expanded.

-----

### Next Steps

Now that the central questions of this project have been answered using a small dataset, the major next step is to repeat this process using a much larger dataset.
I would also aim to investigate more specific questions and break down analyses to also include factors in the analysis.

### Acknowledgements

In order to learn to cache data using PySpark, information was taken from [spark.apache.org](https://spark.apache.org/docs/latest/sql-ref-syntax-aux-cache-cache-table.html) (https://spark.apache.org/docs/latest/sql-ref-syntax-aux-cache-cache-table.html)
