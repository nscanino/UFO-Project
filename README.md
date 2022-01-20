## Welcome to my first attempt at scraping data from the web using selenium!

### Instructions:
#### Scrape_IMDB.ipynb
  1. In order to run this code, you will need to have chromedriver.exe someowhere in your PATH environment. You will also need the selenium, pandas, and BeautifulSoup libraries installed (pip install x).
  2. Currently the program only exists as a jupyter notebook, so you will need to open it as such.
  3. Run all cells in order. 
  4. When you run the last cell, you will be prompted to enter the keyword(s) you wish to search by.
  5. *important* The program only works if you enter a keyword that IMDb recognizes.  It's probably best to first search for the keyword you want on IMDb to confirm that it actually will give results.
  6. You can filter by multiple keywords by separating them with a /.
  7. You can queue multiple scrapes by entering 'n' into the second prompt and repeating steps 4-6. When you are finished queuing scrapes, enter 'y'.
  8. Now go do something that takes a while, and when you come back the data you wanted should be in a .csv in the same folder you ran the code from!
Known bugs: movie description is currently not being grabbed in all cases.
 
#### Scrape_NUFORC_V2.ipynb
  1. Same initial requirements as above.
  2. Run all cells.
  3. Once program is done you should have a .csv with ~135k rows of UFO reports in the same file you ran the notebook from.

#### Analysis.ipynb
  1. At the moment you can see my set up, i.e. data manipulation and how I'm deciding if an increase was seen following each movie release.  The data/results are inaccurate because currently the program is only analyzing reports surrounding movie release dates after 2009. Once that is fixed I think the program I currently have written will still work and will give me the results I desire.

### Current Progress:

#### IMDb Scrape
The current code for scraping IMDb definitely isn't as elegant as I'd like it to be. It still contains some relics from the "working out the kinks" phase, and it probably could be optimized a bit better as well.  That being said, it does currently work as intended, and anyone who has chromedriver.exe somewhere in their path can pull it, run the program, and get movie data for all movies related to the entered plot keyword.  Note that the data definitely isn't clean yet, the dollar amounts are strings and some have '(estimated)' text at the end... nothing that can't be handled if you for whatever reason wanted to use it in the current state, but annoying nonethless.

#### NUFORC Scrape
I've scrapped the initial method of scraping the NUFORC data (by state) and have instead created "Scrape_NUFORC_bymonth.ipynb". This file is much more elegant because it makes more intelligent use of beautifulsoup than my first attempt (namely, I'm not just brute-force processing the raw html...).  This update not only alleviated most of the bad data I was seeing previously, but also expanded the search to include more reports. Additionally, each row now has a 'Year' column, to help differentiate between, for instance, 1/1/2012 and 1/1/1912 (NUFORC date format is m/d/yy).

#### Analysis
The analysis portion is currently in progress. You can check out the file to see the latest findings, although be warned that it will be a little messy for the moment. I'm thinking of taking the analysis a few steps further than asking "how does reporting frequency relate to movie releases?"; I think it would be interesting to zoom in on a few hand-picked movies, selected based on how influential I feel they are/were in the perception of alien life, and see what there is to see.
