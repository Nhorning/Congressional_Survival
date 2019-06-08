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


|                       | bill                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         | date       | democratic                                                                     | description                                                                                                                                                                                                                                                                                         |   document_number | document_title                                                                                                                                                                                                                                                                                      | independent                                        | question                            | question_text                            | republican                                                                      | result                                    | source                                                                               |   tie_breaker |   tie_breaker_vote | time     | total                                                | url                                                                                                             | vote_type   | vote_uri                                                                  |
|-----------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|--------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------------------------------|-------------------------------------|------------------------------------------|---------------------------------------------------------------------------------|-------------------------------------------|--------------------------------------------------------------------------------------|---------------|--------------------|----------|------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|-------------|---------------------------------------------------------------------------|
| (116, 'Senate', 1, 1) | {'bill_id': 's1-116', 'number': 'S.1', 'sponsor_id': 'R000595', 'api_uri': 'https://api.propublica.org/congress/v1/116/bills/s1.json', 'title': 'A bill to make improvements to certain defense and security assistance provisions and to authorize the appropriation of funds to Israel, to reauthorize the United States-Jordan Defense Cooperation Act of 2015, and to halt the wholesale slaughter of the Syrian people, and for other purposes.', 'latest_action': 'Held at the desk.'} | 2019-01-08 | {'yes': 4, 'no': 41, 'present': 0, 'not_voting': 0, 'majority_position': 'No'} | A bill to make improvements to certain defense and security assistance provisions and to authorize the appropriation of funds to Israel, to reauthorize the United States-Jordan Defense Cooperation Act of 2015, and to halt the wholesale slaughter of the Syrian people, and for other purposes. |                 1 | A bill to make improvements to certain defense and security assistance provisions and to authorize the appropriation of funds to Israel, to reauthorize the United States-Jordan Defense Cooperation Act of 2015, and to halt the wholesale slaughter of the Syrian people, and for other purposes. | {'yes': 0, 'no': 2, 'present': 0, 'not_voting': 0} | On Cloture on the Motion to Proceed | On Cloture on the Motion to Proceed S. 1 | {'yes': 52, 'no': 1, 'present': 0, 'not_voting': 0, 'majority_position': 'Yes'} | Cloture on the Motion to Proceed Rejected | https://www.senate.gov/legislative/LIS/roll_call_votes/vote1161/vote_116_1_00001.xml |           nan |                nan | 17:39:00 | {'yes': 56, 'no': 44, 'present': 0, 'not_voting': 0} | https://www.senate.gov/legislative/LIS/roll_call_lists/roll_call_vote_cfm.cfm?congress=116&session=1&vote=00001 | 3/5         | https://api.propublica.org/congress/v1/116/senate/sessions/1/votes/1.json |


## Exploritory Data Analysis

![Visualization: legend](images/visualize_session_legend.png)

![Visualization: Senate 2019](images/visualize_session_senate_2019.png)

![Visualization: House 2018](images/visualize_session_house_2018.png)

![Visualization: house 2019](images/visualize_session_house_2019.png)
