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
 # Save the final candidate vote count to the text file.
 
    for candidate_name in candidate_votes:

        # Retrieve vote count and percentage
        
        votes = candidate_votes.get(candidate_name)
        vote_percentage = float(votes) / float(total_votes) * 100
        candidate_results = (
            f"{candidate_name}: {vote_percentage:.1f}% ({votes:,})\n")

        # Print each candidate's voter count and percentage to the terminal.
        
        print(candidate_results)
        
        #  Save the candidate results to our text file.
        
        txt_file.write(candidate_results)

        # Determine winning vote count, winning percentage, and candidate.
        
        if (votes > winning_count) and (vote_percentage > winning_percentage):
            winning_count = votes
            winning_candidate = candidate_name
            winning_percentage = vote_percentage

    # Print the winning candidate (to terminal)
    
    winning_candidate_summary = (
        f"-------------------------\n"
        f"Winner: {winning_candidate}\n"
        f"Winning Vote Count: {winning_count:,}\n"
        f"Winning Percentage: {winning_percentage:.1f}%\n"
        f"-------------------------\n")
    print(winning_candidate_summary)
```
##### This section of code loops through the data to finialize the vote count for each candidate. The code starts out by calculating the voter percentage, per candidate, and writes that to the text file. Then an if condition is considered to determine who won the election, based on the highest vote count and the highest percentage of the votes. After calculating this, the output is written to a text file for a final summary. 
---
#### Election-Audit Summary
---
##### This script can easily be used in any upcoming elections. One example of a change would be the actual data file used. The csv file, containing all of this election data, should be changed so that an error doesn't occur. Without changing the file, the results will be the same since the same data will be used. Another example of a change would be changing the directory of the output file, if need be. Another change to the code could be expanding the code to calculate the results per state, then show the overall winning candidate for the presidency. 
