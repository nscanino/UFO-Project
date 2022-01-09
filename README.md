## Welcome to my first attempt at scraping raw data from the web using selenium!

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
 
#### Scrape_NUFORC.ipynb
  1. This one is more straightforward. You simply need to have pandas and BeautifulSoup.  Run all cells in order and you should be left with a semi-usable .csv containing info on all reports made to NUFORC in the last ~100 years.

#### Analysis.ipynb
  1. I don't recommend doing anything with this yet. All I've done so far here is organized the necessary data, haven't actually started analyzing it yet.

### Current Progress:

#### IMDb Scrape
The current code for scraping IMDb definitely isn't as elegant as I'd like it to be. It still contains some relics from the "working out the kinks" phase, and it probably could be optimized a bit better as well.  That being said, it does currently work as intended, and anyone who has chromedriver.exe somewhere in their path can pull it, run the program, and get movie data for all movies related to the entered plot keyword.  Note that the data definitely isn't clean yet, the dollar amounts are strings and some have '(estimated)' text at the end... nothing that can't be handled if you for whatever reason wanted to use it in the current state, but annoying nonethless.

#### NUFORC Scrape
I'm a bit torn on how to handle the current state of the NUFORC scraping code.  The data that it exports does contain some bad rows, so there's some bug exploration needed, but I'm also thinking it might be better to just re-do the project using selenium. At the same time, I'm proud of what I was able to do without using it, and it feels wrong to just get rid of the code I sweated over for an entire day.  If you're interested, go and take a look!

#### Analysis
I haven't gotten very far with the analysis portion yet, mainly because I only just finished collecting the data and haven't had a chance to clean it yet.  I do have a gameplan as far as the stats that will help me answer the questions I'm asking, and I'm confident I should be able to upload some interesting visualizations and results soon enough.

### The Story:

Over the last few months, I've been downloading datasets from Kaggle.com and using them to practice my data science skills (analysis, visualization, etc.).

I was browsing the web for more interesting data sets outside of Kaggle, when I happened upon NUFORC.org, a website housing all reports made to the National UFO Reporting Center. Unfortunately, the website does not come with a "download" feature, and to make matters worse, the data is separated across various pages by state, year, shape of craft, etc., rather than being housed all-in-one.  I was effectively stuck with the toolset I had at the time. After doing a little searching, I found the BeautifulSoup Python package, which I was able to use to parse the source HTML from each page.  This was done in the jupyter notebook Scrape_NUFORC.ipynb.

After taking a look through the data, I figured it might be fun to look into the frequency of reports as it relates to some other variable. I decided to answer the question:

## Does the frequency of UFO reports across the U.S. increase following the release of popular Alien-related movies?

To answer this question, I needed to find, of course, some data about movies relating to Aliens. I figured my best option was to go to IMDb.com and do the same thing I did with the NUFORC data: parse the source HTML using BeautifulSoup.  IMDb, however, loads all of their pages dynamically, so I wasn't going to be able to do this with just BeautifulSoup alone.  Enter Selenium! Using Selenium, I was able to automate an instance of Chrome to visit IMDb, search for movies by a specified keyword, load and grab the necessary info from each movie's page, and bundle it all into a DataFrame which could be easily exported into a .csv using the Pandas library.  This was done in the jupyter notebook Scrape_IMDb.ipynb

Once I've completed the analysis, I'll update this section to include some of the more interesting findings. Thanks for checking this out!
