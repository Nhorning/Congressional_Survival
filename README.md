# Capstone Project 2: Congressional Survival

## Problem
Based on their voting history, what type of congress member is most likely to survive in what political environment? 
Election results are highly dependent on voter enthusiasm, partisanlean, and the national political environment.  However, when voting on legislation, members of congress in swing districts must do a cost benefit analysis of meeting the partisan preferences of their district or the expectations of their own base. What type of strategy most successfully predicts survival?

## Client / Stakeholder case:
This information could be useful for any number of congressional members for determining their voting choices, or for National level party organs such as the Democratic National Committee to inform voting strategies. It could also be of interest to any number of political blogs.

## Data Sets
The primary dataset is congressional voting records going back to 1981 available from the House and Senate clerk offices via the [ProPublica Congress API](https://projects.propublica.org/api-docs/congress-api/).

Other datasets, available from fivethirtyeight:
- Partisan lean of districts and states
- Predictions of Partisan votes based on district lean.

### Prospective datasets: 
  The [voteview dataset](https://voteview.com/data) stores congressional voting records and ideological scores going back to the first congress in 1781.

## Data Wrangling and Cleaning:

As the dataset is being fetched via API, wrangling and cleaning focused mostly on constructing the data into a useful format. The Pro Publica Congress API makes metadata for votes available for a given month chamber and year, and each members position on a given vote available for individual roll call votes for a given congress number, chamber, sesson, and roll call number.

Steps: 
1. Created a function to request the ProPublica API with a given API key for a given end point, and return the response as a dictionary.
2. Created a function to construct an endpoint and request meta data by month and return a data frame.
3. Created a function which uses the above to request metadata for all months for a given chamber and year, and return a dataframe indexed by congress, chamber, session, and roll call for each vote.
4. Created a function which takes the index of the metadata for a given year and uses it to request each members position for each vote in that year returning a dataframe with the same index.
5. Created a series of functions that will take a given year and chamber, and return a corosponding dataframe of all the metadata and a seperate dataframe of positions. These functions will check if a there is an existing CSV file for those dataframes in the Data directory, and if so load it. If not, they will construct new dataframes using the API and save the CSV to the Data directory.

## Exploritory Data Analysis





