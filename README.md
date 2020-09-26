# SP-500-TweetIDs
The repository contains an ongoing collection of tweets IDs of S&amp;P 500 companies and their tweets' comments, which commenced on January 1, 2020.
We used the Twitter's usertimeline API to gather the S&P 500 companies' history tweets, which contains 2400 tweets back from Janary 1, 2020. And also used Twitter's search API to get their tweets from the preceding 7 days. 

About the comments. Based on the companies' tweets we collected, we hydrated the tweet ID and then use Twitter's search API to get the comments for the tweets from the preceding 7 days, leading to the first Tweets in our dataset dating back to January 1,2020.

To comply with Twitter’s Terms of Service, we are only publicly releasing the Tweet IDs of the collected Tweets. The data is released for non-commercial research use.

# Data Organization
The Tweet-IDs are organized as follows:

•	Tweet-ID files are stored in folders that indicate the year and month of the collection (YEAR-MONTH).

•	Individual Tweet-ID files contain a collection of Tweet IDs, and the file names all follow the same structure, with a prefix “SP500-tweet-id-” followed by the YEAR-MONTH-DATE-HOUR.

•	Note that Twitter returns Tweets in UTC, and thus all Tweet ID folders and file names are all in UTC as well.

# Notes About the Data
•	I will be continuously maintaining this database for the foreseeable future, and I will be uploading new data on a weekly basis.

•	here may be a few hours of missing data due to technical difficulties. We have done our best to recover as many Tweets from those time frames by using Twitter’s search API.

•	We will keep a running summary of basic statistics as we upload data in each new release.

•	The file accounts.txt contains the SP companies’ accounts that we tracked in our data collection. 

•	Consider using tools such as the Hydrator and Twarc to rehydrate the Tweet IDs. Instructions for both are in the next section.

•	Hydrating may take a while, and Tweets may have been deleted since our initial collection. If that is the case, unfortunately you will not be able to get the deleted Tweets from querying Twitter's API. 

# How to Hydrate
# Hydrating using Hydrator (GUI)

Navigate to the Hydrator github repository and follow the instructions for installation in their README. As there are a lot of separate Tweet ID files in this repository, it might be advisable to first merge files from timeframes of interest into a larger file before hydrating the Tweets through the GUI. 

# Hydrating using Twarc (CLI)

Many thanks to Ed Summers (edsu) for writing this script that uses Twarc to hydrate all Tweet-IDs stored in their corresponding folders.
First install Twarc and tqdm

pip3 install twarc
pip3 install tqdm

Configure Twarc with your Twitter API tokens (note you must apply for a Twitter developer account first in order to obtain the needed tokens). You can also configure the API tokens in the script, if unable to configure through CLI.
twarc configure

Run the script. The hydrated Tweets will be stored in the same folder as the Tweet-ID file, and is saved as a compressed jsonl file

python3 hydrate.py

