# Election_Analysis
---
## Performing analysis on election data and results to determine a winner.
---
### Election Analysis on Colorado Election Data based on County
---
#### Background of Election Analysis
---
##### This analysis was undertaken to help a Board of Elections employee, Tom, in an audit of the tabulated results of the congressional precinct election in Colorado. This analysis was to find the total number of votes cast, a complete candidate list, total number of votes per candidate, percentage of votes, and the winner of the election based on popular vote. Additionally, analysis was done on the voter turnout for each county, percentage of votes from each county, and the county with the highest turnout. 
---
#### Election-Audit Results
---
* ##### 369,711 votes were cast in this Colorado election. This was determined using the following code:
```
# Read the csv and convert it into a list of dictionaries
  with open(file_to_load) as election_data:
      reader = csv.reader(election_data)

      # Read the header
      header = next(reader)

      # For each row in the CSV file.
      for row in reader:

          # Add to the total vote count
          total_votes += 1 
```
##### This section of code takes the raw data from the election, located in a comma separated values file, and coverts it into a list of dictionaries. This list of dictionaries is then used to do the rest of the analysis. The program opens the file, reads the data while skipping the header row, then loops through all of the rows to count the total number of votes. 
---
* ##### In this congressional precinct election, Jefferson county had 10.5% of the votes, totaling 38,855 people who voted. Denver had 82.8% of the votes, totaling 306,055 people who voted. Araphahoe had 6.7% of the votes, totaling 24,801 people who voted. 
* ##### Denver had the largest voter turnout in this election, with a total of 82.8% of all votes taken in the election. This was determined using the following code:
```
 county_name = row[1]

        # Extract the county name from each row.
        if county_name not in county_list:
        
            #Add county name to the county list
            county_list.append(county_name)
            
            # And begin tracking that county's voter count
            county_votes[county_name] = 0
            
        #Add a vote to that county's count.
        county_votes[county_name] +=1
```
##### This section of code runs through all lines of code to look for unique county names, and adds them to a list. When the code finds all of the county names, it moves on to tracking that county's voter count and adds it accordingly. 
---
* ##### The candidates in this election were: Charles Casper Stockham, Diana DeGette, and Raymond Anthony Doane. Charles Casper Stockham received 23.0% of the votes, with a total of 85,213 people voting for them. Diana DeGette received 73.8% of the votes, with a total of 272,892 people voting for them. Raymon Anthony Doane received 3.1% of the votes, with a total of 11,606 people voting for them. This was determined using the following code:
```
# If the candidate does not match any existing candidate add it to
        # the candidate list
        candidate_name = row[2]

        if candidate_name not in candidate_options:

            # Add the candidate name to the candidate list.
            candidate_options.append(candidate_name)

            # And begin tracking that candidate's voter count.
            candidate_votes[candidate_name] = 0

        # Add a vote to that candidate's count
        candidate_votes[candidate_name] += 1
```
##### This section of code works exactly the same as the code used for counting county votes from above. The code loops through all the rows to look at the unique candidate names and adds them to a list. Then the code loops through all the rows to add votes to each candidates name. 
---
* ##### Diana DeGette won the election with a total of 73.8% of the votes. Diana DeGette's vote count was 272,892 people. 
```
enter code here
```
##### explain code here
---
#### Election-Audit Summary
---
##### Provide a summary of how this script can be used in the future, with modifications. Give at least 2 examples on how this can be changed for future elections
