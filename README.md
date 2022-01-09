## Welcome to my first attempt at scraping raw data from the web using selenium!

### Current Progress:

#### IMDb Scrape
The current code for scraping IMDb definitely isn't as elegant as I'd like it to be. It still contains some relics from the "working out the kinks" phase, and it probably could be optimized a bit better as well.  That being said, it does currently work as intended, and anyone who has chromedriver.exe somewhere in their path can pull it, run the program, and get movie data for all movies related to the entered plot keyword.  Note that the data definitely isn't clean yet, the dollar amounts are strings and some have '(estimated)' text at the end... nothing that can't be handled if you for whatever reason wanted to use it in the current state, but annoying nonethless.

** NOTE ** When entering keywords, the program only works if you enter a keyword that IMDb recognizes.  It's probably best to first search for the keyword you want to use on IMDb to confirm that it actually gives results.

#### NUFORC Scrape
I'm a bit torn on how to handle the current state of the NUFORC scraping code.  The data that it exports does contain some bad rows, so there's some bug exploration needed, but I'm also thinking it might be better to just re-do the project using selenium. At the same time, I'm proud of what I was able to do without using it, and it feels wrong to just get rid of the code I sweated over for an entire day.  If you're interested, go and take a look!

#### Analysis
I haven't gotten very far with the analysis portion yet, mainly because I only just finished collecting the data and haven't had a chance to clean it yet.  I do have a gameplan as far as the stats that will help me answer the questions I'm asking, and I'm confident I should be able to upload some interesting visualizations and results soon enough.

### The Story:

Over the last few months, I've been downloading datasets from Kaggle.com and using them to practice my data science skills (analysis, visualization, etc.)

I was browsing the web for interesting data sets to analyze when I happened upon NUFORC.org, a website housing all reports made to the National UFO Reporting Center. Unfortunately, the website does not come with a "download" feature, and to make matters worse, the data is separated across various pages by state, year, shape of craft, etc., rather than being housed all-in-one.  I was effectively stuck with the toolset I had at the time. After doing a little searching, I found the BeautifulSoup Python package, which I was able to use to parse the source HTML from each page.  This was done in the jupyter notebook Scrape_NUFORC.ipynb.

After taking a look through the data, I figured it might be fun to look into the frequency of reports as it relates to some other variable. I decided to answer the question:

### Does the frequency of UFO reports across the U.S. increase following the release of popular Alien-related movies?

To answer this question, I needed to find, of course, some data about movies relating to Aliens. I figured my best option was to go to IMDb.com and do the same thing I did with the NUFORC data: parse the source HTML using BeautifulSoup.  IMDb, however, loads all of their pages dynamically, so I wasn't going to be able to do this with just BeautifulSoup alone.  Enter Selenium! Using Selenium, I was able to automate an instance of Chrome to visit IMDb, search for movies by a specified keyword, load and grab the necessary info from each movie's page, and bundle it all into a DataFrame which could be easily exported into a .csv using the Pandas library.  This was done in the jupyter notebook Scrape_IMDb.ipynb
