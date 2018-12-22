Process Book
===

Russell Davis (rdavis@wpi.edu Github: russbdavis) contributed to visualization prototyping, implementation of visualization aesthetics, and screen-casting. 

Brittany Gradel (bgradel@wpi.edu Github: bgradel) contributed to the bulk of the visualization coding and the website. 

ML Tlachac (mltlachac@wpi.edu, Github: mltlachac) contribution to data acquisition, exploration, and manipulation. 

All team members contributed to visualization motivation, design development, and written deliverables. 

Goal Overview and Motivation
---

Measles is one of the leading causes of death among children according to the World Health Organization. Even in 2016, an all time low for measles incidents, measles was the cause of death for nearly 90,000 children globally (http://www.who.int/mediacentre/factsheets/fs286/en/). This is particularly tragic as the spread of the disease is preventable through vaccination. Unfortunately, instead of increasing vaccination rates, vaccines are becoming less popular in developed countries were the diseases are less prevalent.  According to a New York Times article appropriately titled Measles Cases in Europe Quadrupled in 2017, "the [measles] virus found its way into pockets of unvaccinated children all over the continent" (https://www.nytimes.com/2018/02/23/health/measles-europe.html?smid=fb-nytscience&amp;smtyp=cur&mtrref=undefined). 

An increasing number of parents hesitate to vaccinate their children out of fear. Stemming primarily from a misguided belief that vaccines have negative consequences such as autism, mercury poisoning, or chemical overloads, these fears are causing parents to either delay or refuse to have their children vaccinated.  Over ten percent of parents choose to delay or skip a standard vaccination (https://communitytable.parade.com/109306/sethmnookin/07-why-so-many-parents-are-delaying-vaccines/).  This not only puts their child at risk but also vulnerable members of the community such as infants, elderly, pregnant women, and those with preexisting health problems.  These people rely on herd immunity, which is when enough of the population are vaccinated to keep the disease from spreading  (http://www.pbs.org/wgbh/nova/body/herd-immunity.html).  As such, it is important for everyone to understand the importance of vaccinating, for themselves and their communities. 

Even after the autism myth was debunked and the 'mercury mom' trend faded, these concerns are kept alive by the media and the public (https://communitytable.parade.com/109306/sethmnookin/07-why-so-many-parents-are-delaying-vaccines/).  In addition, new concerns continue surface to plague the reputation of vaccines.  In fact, fear regarding chemical overload has led to alternative vaccine schedules that delay vaccine administration, such as Dr. Sear's vaccine solution (http://www.loving-attachment-parenting.com/alternative-vaccination-schedule-dr-sears.html).  "The Truth about Vaccines" documentary uses fear to propagate common myths about vaccines as well as stating other reasons vaccines are unsafe (https://vaccinesworkblog.wordpress.com/2017/04/16/the-truth-about-vaccines-episode-1-top-ten-lies-debunked/).  The lies and misrepresentation in this documentary are convincing previously pro-vaccine parents that vaccines are dangerous to their children.

Our goal is to demonstrate to the general public through visualization that vaccines are important for preventing diseases.  This is accomplished through enabling a direct comparison between disease incidence and vaccination rates for a given year.  By emphasizing the time-variant impact of vaccines with appropriate visual idioms, we hope to clearly illuminate their efficacy. In addition, comparison between diseases at different points in time can highlight the broad impact of vaccinations.  As the fear of vaccination is founded in misinterpretation of science, our visualization is designed to be accessible to our target audience by being simple, direct, and easy to interpret.  Our visualization attempts to hold the attention of our target audience by being interesting, interactive, and aesthetically pleasing.  Given these demands, we chose to proceed with a global map coded with color as our visualization. 

Related Work
---

![whodisandvacc](https://user-images.githubusercontent.com/26936744/36698099-fb122462-1b16-11e8-9f89-1683645fabd1.PNG)

This is the World Health Organization visualization of our primary two data sources (http://www.who.int/immunization/monitoring_surveillance/data/en/).  This visualization, while colorful, is boring to view and confusing to understand.  In particular, the channels are not used well.  Instead of a using hue in the color scale, saturation would have been more effective.  In addition, using both color and size for circle channels while overlaying a blank map is a poor visualization choice.  Not only is it difficult to compare the size of circles, it is difficult to pinpoint where they belong on the map.  Lastly, this visualization falls victim to falsely displaying disease incidence without considering the overall population of the country, making countries with larger populations seem disproportionately troubled. Our intent is to improve upon this visualization to provide an easier to understand visualization for the same data.

![reflectionwaterquality](https://user-images.githubusercontent.com/26936744/36360352-21c15ce4-14f1-11e8-91fd-d68199225163.PNG)

From the New York Times article "Here Are the Places That Struggle to Meet the Rules on Safe Drinking Water" (https://www.nytimes.com/2018/02/12/climate/drinking-water-safety.html), this visualization inspired the design choices for our visualization.

http://bl.ocks.org/micahstubbs/8e15870eb432a21f0bc4d3d527b2d14f

This map example was both a starting point for our code and also a huge inspiration for how we wanted our map to look and feel. 

Questions
---

Our initial intent was to focus on questions regarding the costs of failing to vaccinate, both human and financial.  This was intended as a direct and impactful way of presenting the repercussions of failing to vaccinate: "How much money is it likely to cost you? How likely is your child to die as a result of your decision?"  We hoped to obtain data dating back to the mid-20th century when vaccines were first developed in order to see the impact of their adoption and draw comparisons that way.

However, issues with data procurement and cleaning, discussed below, limited our ability to answer these questions and necessitated a different perspective.  The data about specific diseases is limited to incidence in individuals; however, we also
found data specifically about country population and vaccination rates, which enabled us to represent both incidence rates and vaccination rates.

This led to our primary question being: "What is the relationship between incidence and vaccination rates?"  

Because we had access to incidence rates across a period of 20 years and for a few different diseases, we were able to flesh this out into some more detailed questions: "How do vaccination rates affect incidence over time?" and "How do incidence rates of different diseases compare at the same point in time?"  This latter question is of less interest to those who are choosing whether or not to vaccinate, but allows for some exploratory analysis by more a research-minded audience.  

Our issues with data collection also led to a somewhat rhetorical question: "Why is the available data on disease and vaccination rates so limited?"   Our initial questions would likely have led to more powerful results by making the consequences of a failure to vaccinate extremely personal, but the data to support that question was simply unavailable.  As such, we hope that another use of this visualization is to highlight the difficulties imposed by this question.


Data
---

## Data Description and Source

This project mainly incorporates two different down-loadable datasets from WHO: one on vaccines and one on diseases (http://www.who.int/immunization/monitoring_surveillance/data/en/).  The Vaccine dataset contains 8 features and the Disease dataset contains 42 features. Both contain three location variables: name, region, and county. The Vaccine dataset also contains vaccine, year (2000-2016), target population, administered doses, and percent coverage.  There are 49,903 rows in this Vaccine dataset. The Disease dataset also contains the disease and the number of cases for each year between 1980 and 2000.  There are 194 rows for each of the 10 different diseases (though one disease is a subset of another disease).  Both datasets contain many missing values from countries where there is not vaccine rate or disease incidence data available.

We also have two supporting datasets.  The first is download-able country population data from the World Bank (https://data.worldbank.org/indicator/SP.POP.TOTL).  This dataset contains the country name and code, indicator name and code, and the population for every year between 1960 and 2016 for 264 countries.  Lastly, we also include data from Epidemiological Reviews found in a Nova article (http://www.pbs.org/wgbh/nova/body/herd-immunity.html).  This data required us to manually add it to a usable format, however it only contains 3 features and 7 rows of data.  The features include the disease, the basic reproduction number, and the herd immunity threshold.  

## Data Cleaning

There was a substantial amount of data cleaning.  First we wanted to decide what subset of the data we wished to use in our visualization.  In addition to the plentiful missing values in the dataset, there were also many zeros in the Disease dataset for less common diseases.  For instance, if we built a global map for polio instances, we would have only a dozen instances in a couple of countries, which would not have the impact we were intending.  As such, we identified four diseases with the most disease instances: measles, mumps, pertussis, and rubella.  However, only vaccines for measles, pertussis, and rubella were included in our datasets.  Thus, we have only included these three diseases in our final data visualization.  However, the visualization could be expanded to include other diseases with available data.

As mentioned, there were many missing values.  We chose to keep these values as missing data may have meaning within the domain and as such gave them all a value of negative one.  After building the visualization, we noticed that there was no country code for Greenland in our dataset.  

Then we tried to merge the Disease, Population, and Vaccine datasets.  In particular, it was vital to merge the Disease and Population datasets to achieve the percent of the population with the disease.  This was done because it eliminates the issue of misrepresentation of disease severity by scaling the number of infected by the population.  Also, disease percent makes more sense to compare to vaccine coverage which is also a percentage.  Merging the data highlighted some key concerns: each of three main datasets had a different number of country codes represented and the Vaccine dataset, in addition to have missing values, chose not to include certain rows of data.  While still possible to merge the Vaccine dataset, we realized it was not necessary given that we already had vaccine coverage as a percent of the target population.  Instead, we just created three vaccine datasets, one for each of the selected diseases.  Then we merged Disease and Population datasets for the three selected diseases and used the information to feature engineer disease percent.

After merging the datasets, we noticed that some of the disease percents were 100 percent as both the numerator (disease instances) and denominator (population) were missing values and both coded as -1. As such, we adjusted these percents to -1 to represent that the data was missing.  This means that all disease percents with missing data are negative numbers. 

The last data cleaning challenge we faced was the realization that vaccine coverage was over 100 percent for 595 rows of the portion of the Vaccine dataset we are using, which included 103 countries.  We pondered the correct way to handle this conundrum.  Given that this was not an issue isolated to a particular small subset of country, we acknowledged that there could be a logical reason for some of these values being over 100. Eventually, we decided that values slightly over 100 percent were acceptable but values more than slightly over 100 percent were probably errors.  We consulted the histogram of these questionable values below in making our determination of where that threshold belonged.  Any value over 115 was considered an error and coded the same as no data.

![vaccine coverage over 100](img/Vaccine100.PNG)

Exploratory Data Analysis
---

![whodisandvacc](https://user-images.githubusercontent.com/26936744/36698099-fb122462-1b16-11e8-9f89-1683645fabd1.PNG)

This is the World Health Organization visualization of our primary two data sources (http://www.who.int/immunization/monitoring_surveillance/data/en/).  From this, we were able to see the quantity of the data that was available within the Disease and Vaccine datasets.  Thus, we knew that the data was appropriate for a global map visualization.

Apart from the histogram of the vaccine coverage values over 100 percent, we used histograms of the data to determine how to best bin the data.  Due to the herd immunity threshold in the last dataset, we had an intuition about how we wished to bin the vaccine coverage percent.  We validated that these divisions made sense given the distribution of total 9071 vaccine coverage values using the below histogram.

![vaccines](img/Vaccine.PNG)

We had no intuition about the disease instances percent.  The minimum value for the disease instances percent was 0 and the maximum value for the disease instances percent was between 2-3 for all three of the Disease-Population datasets.  However, upon studying the data using the below histograms, we saw that the disease instances percent appeared to form a left skewed exponential distribution.  We adjusted our binning accordingly.

![measles](img/Measles.PNG)
![rubella](img/Rubella.PNG)
![pertussis](img/Pertussis.PNG)

Design Evolution
----

## Proposal Design

Initially, for our proposal we really wanted to make a map comparing disease and vaccine. We discussed a variety of options off of the map design when coming up with our proposal, but ultimately the map was the clearest way to display all the data we wanted.

![Whiteboard brainstorming](img/IMG_1830.JPG)

Our initial design attempted to use multiple visual channels to produce a single cohesive map which included all of the data.

![Proposal Drawing](img/MapDisAndHerd.jpg)

While we liked this design, our reasons for revising it were based around feedback we received. 

## Post Proposal Design Session 2/19

After our proposal, we received feedback that it was difficult for the user to remember data they had seen before, and that we should be adding functionality so that the user could directly compare aspects that were important rather than comparing between views. The proposal feedback has brought up the option of doing small multiples which was something that we explored at the time. In particular, we drew inspiration from this water quality map that featured one large map and several smaller maps:

![reflectionwaterquality](https://user-images.githubusercontent.com/26936744/36360352-21c15ce4-14f1-11e8-91fd-d68199225163.PNG)

After discussing and brainstorming, we came up with the 4 possibilities in the image below:

![Design Revisions](img/DesignRevisionsAfterProposal.JPG)

1. Keeping our original design choice but since our comparison point was disease vs. vaccine which were also both focused on the map. We decided ultimately that while the feedback that we got from the proposal (that people aren't good at comparing across diseases when they have to switch views) was not really what our focus was, it was fair to say that our vaccine vs. disease comparison might have been less obvious with our design which was why the incorrect conclusion was drawn by those reading the proposal.

2. Doing a collection of a bunch of tiny maps on an axis sorted by disease and time for comparison. We decided against this for two reasons. First of all, we had a lot of differences we were interested in showing to the user, and so doing a bunch of small maps would have either involved a ton of scrolling for the user, or would have made each map so small that they would have been difficult to read. We didn't think that either of these was an acceptable situation. We also debating making it so that the visualization would zoom in to each map as you moused over the map, but since the user would not be able to be moused over more than one map at once, that had the same issue as the original design with cognitive load increase for comparison maps. Thus this idea was rejected.

3.  We debated showing disease (possibly vs. vaccine usage) just over time. This allowed us to fit more maps on the screen and also made scrolling make more sense than in the second design. However, this still made it difficult to compare disease rates from years not next to each other, and made the visualization much larger and more confusing.

4. We finally settled on doing just two maps, one for disease incidents and one for vaccine percentage. This allowed us to focus the user intention on the particular thing that we wanted them to be comparing (vaccine prevalence vs.  disease incidents) and didn't distract them with too much information at once that might be hard to take in. It was also an improvement over our original design because it avoided having the users try to make comparisons between area for vaccine and color for disease which would have been difficult. Instead users have to compare the same visual channel (saturation) for a vaccine map and a disease map that are side by side.

## Initial Map 2/20

Initially our MVP was just to have a single map that showed disease prevalence so that we had something that could show how disease has gone away over time due to the increase of vaccines. We completed that in blue (bad color choice) as can be seen below.

![Initial Map](img/BaseMapWithSelectionMenus.PNG)

## Disease Vs. Vaccine Placeholder 2/21

The next day we were able to make a disease vs. vaccine map with a placeholder square for the vaccine map. In this iteration, the design was to have the vaccine map have it's own selector for disease and year. In this progress shot, the placeholder square changes colors to orange on disease change. 

![Map with Placeholder](img/PartialProgressTowards2Maps.png)

## Disease Vs. Disease 2/22

On February 22nd, the data for vaccine information was not yet available a "placeholder" map was made using just the disease information. When we actually looked at the disease maps though, there was some interesting insights that we thought that the user could pull out of looking at maps in that manner like comparing measles now to measles in 2001 and seeing how the disease prevalence has decreased due to vaccines. This caused us to revise our design to include a second mode.

![Disease Vs. Disease](img/DiseaseVsDisease.png)

## Disease Vs. Vaccine Multiple Modes 2/22

In this iteration, we added the second mode for vaccine. Since vaccine vs. disease was the primary comparison we wanted viewers to make, we made it the automatic mode. We also came to the design decision to always make the vaccine map match the disease map by removing the selector options for vaccine. This version still did not have sensible color buckets.

![Disease Vs. Vaccine](img/DiseaseVsVaccineWithSelector.png)

## Color Bin Decisions 2/26

We knew we wanted to bin our vaccine rates and disease instance rates as well as that we wanted to differentiate each bin by either brightness or saturation as rates are continuous numerical data.  We chose three bins, plus a bin for missing data, as 3-4 bins is the recommended number of bins according to Tamara Munzner (Visualization Analysis and Design, 2014).  

We chose to represent disease instance rate with a red scale as red is indicative of danger.  We chose to represent vaccine coverage with a green scale as green is indicative of life.  The specific colors used were identified from http://colorbrewer2.org/#type=sequential&scheme=Reds&n=4.

In order to decide where to make our bins, we decided to use the power of visualizations! Instead of making an instinctive decision on the best bins, we plotted the data on a histogram in order to see how our data was clustered and to pick bins that would best show our data. 

![Measles](img/Measles.PNG)

![Pertussis](img/Pertussis.PNG)

![Rubella](img/Rubella.PNG)

Unfortunately, when we took a closer look at the vaccine data, we found that there were multiple values that were over 100 percent. At first, we assumed that this was ok as the actual vaccine amounts were looking at a target group for vaccination and calculating a vaccination percentage based on doses administered vs. that target group. Some countries appeared to have vaccinated people who were not part of their target group. However, upon inspection, it appeared that some countries had reported very low target group numbers (a dozen people instead of thousands) in order to make their vaccination percentage higher. Since this data was suspect, we decided to exclude data that was over a certain value in order to protect the integrity of our visualization against data that we considered suspect. 

![Vaccine](img/Vaccine.PNG)

We binned the vaccine data based on the Herd Immunity Dataset.  The below image is the bins based on the herd immunity data.  Measles had a range for herd immunity with the lower and upper values corresponding with the herd immunity thresholds for rubella and pertussis.  We verified that binning based on these values made sense with the vaccine coverage distribution as seen in the vaccine histogram.

![herd immunity bins](img/herdBins.PNG) 

## Legend addition and minor improvements

After choosing colors, we were able to clean up our design and add legends to help the user. 

![Disease Vs. Vaccine](img/DiseaseVsVaccineFinal.png)

![Disease Vs. Disease Final](img/DiseaseVsDiseaseFinal.png)

Implementation
---

The first and primary application is to enable a direct comparison between disease incidence and vaccination rates for three different diseases for a given year.
Accordingly, there are selection menus for both year and disease to allow the user to explore and make comparisons as desired.
The selection menu for years gives a snapshot that allows for ready comparison between disease incidence and vaccination rates.  For
example, the screen-shot below allows a user to observe the data for measles in 2001, which shows that measles incidence is higher in
areas such as Africa that have lower vaccination rates.
![Date Selection](img/DateSelector.PNG)


The selection menu for disease allows the user to choose between measles, mumps, and rubella, based on their area of interest.
![Disease Selection](img/DiseaseSelector.PNG)



We also made it possible to toggle the view from Disease vs Vaccinations to Disease vs Disease.  In other words, a user can compare 
between different diseases at a given point in time, and can also compare the same disease at two different points in time. 
The screen-shot below shows a comparison between measles rates in 2001 and 2016, showing a clear reduction over time; we anticipate
that the user will use this to verify the effect of vaccinations.

![Measles in Different Years](img/MeaslesInTime.PNG)


The below screen-shot shows a comparison between measles and rubella incidence rates in 2016.  This view is likely to have the most
utility for exploratory analysis, enabling users to investigate whether or not diseases have outbreaks in similar years and
the rate at which they decrease in incidence over time, among other potential uses.

![Two Diseases](img/TwoDiseases.PNG)


While it is possible to compare different diseases at different points in time, we do not foresee an obvious use case for this.

Another feature of the visualization that persists in all views is the ability to hover over a country to obtain more information.  
For the disease incidence rate views, this information includes the name of the country, the country's total population, and the number of disease cases.  This allows discerning users to determine the true magnitude of an outbreak.

![Disease Tooltip](img/DiseaseTooltip.PNG)


For the vaccination rate views, hovering over the country shows its name and its vaccination percentage.


![Vaccination Tooltip](img/VaccinationTooltip.PNG)


Evaluation
---

## Our Impressions

There are some years where our visualization demonstrates that vaccines are important for preventing diseases. For instance, rubella disease instance rate is less over time and the vaccine rate is greater over time.  In addition, this trend of increasing vaccine rate and decrease disease instance rate can be in Africa for pertussis.

However, there are also some years and countries where this vaccine rate and disease instance rate is not so clearly related.  This is particularly true for measles. This indicates to us that the country level may be too high of a data granularity.  It also suggests that perhaps our concerns about the quality of the vaccine data, which is as good as there is publicly available, were well founded.

One of the most interesting parts of the visualization is the ability to easily see trends of disease instance rates and vaccine rates over time even this effect was not motivated.  For instance, measles diseases instance rates fluctuates over time, which makes sense given our background knowledge about measles vaccine adherence and outbreaks.  However, the vaccine rate for the measles vaccine does not change much over time.  

Detracting from this visualization is the large amount of missing data. Even developed countries that clearly would have kept disease incidence and vaccination rates records, such as the United States, Canada, and various European countries, have not contributed their data.  Thus, this visualization is a powerful tool to advocate for proper record-keeping and public dissemination of this information.  The uses of this visualization extend past the original motivation and target audience.

## Case Study

Our goals for the visualization was that it was simple, direct, easy to interpret, interesting, interactive, and aesthetically pleasing.  We created a case study to evaluate if our visualization achieved these goals.  We asked each participant three questions to judge the effectiveness of our visualization.

1. How easy is this visualization to understand?

2. Is the visualization interesting?

3.  What does the visualization tell you about the relationship between disease and vaccine coverage?

Our eight participants were gathered primarily through social media although one of the participants was a WPI student.  All are educated and most were at or under the age of 30.  This is not our target audience, however it gives us a starting point for how other people will interpret and interact with our visualization.  

The visualization was not as easy to understand as we desired.  While the majority of the participants thought the visualization was easy to understand, some did not.  The reasons were that the legends were not immediately visible, the relationship between the graphs was unclear, and the concept of herd immunity was not well understood.  

Every participant in our case study indicated that the visualization was interesting, regardless of their understanding of the visualization.  As such, we have accomplished our goal of making the visualization interesting enough to keep audience attention.  A few of our participants cited the interactive features as a primary reason our visualization was interesting and fun.

Six of our participants came to the conclusion that vaccine rate and disease instance rate were inversely correlated, however it was only phrased that way in one review.  This is encouraging as the majority of the participants were able to understand the intended point of the visualization.  However, their interpretation was likely biased by their previous knowledge about diseases and vaccines.  The two other participants both mentioned that the large amount of missing data was confusing. One participant seemed confused as to whether or not we were looking at vaccination rates of cows (because we mentioned herds), so a description of herd immunity was added to our website to help aid understanding. 

## Future Improvements

There were three main themes that multiple of our case study participants mentioned: too much missing data, too many data sets, and it would be better if the information was combined into a single graph.  We were already aware that the missing data detracted from the image.  As we have the most complete data currently available, this is not something that we could improve.  In the future, we could improve the visualization to provide the user with fewer options to view the data, which may keep the user from feeling overwhelming. However, this would detract somewhat from the versatility of the visualization usage.  Though just within the scope of our target audience reducing the options to make the point more clear makes sense.  Lastly, we debated extensively whether to display disease incidence rate and vaccine rate together or separately.  We chose to display them separately for ease of interpretation.  Finding a way to maintain this ease of interpretation while allowing for some type of data overlay, if possible, would be an improvement. 

Other comments involved making sure that herd immunity was more understandable and make the entire visualization was on one graph.  These comments are at direct odds with the current layout: by adding more information about herd immunity the user needs to scroll to view the legends and by having the entire visualization on one page the description needs to be minimized.  As such, finding a layout that supports both a more in depth description and the entire visualization on the visible screen would be an improvement.  

Lastly, while our objective was primarily to be able to make comparisons between two different maps, there is some merit for being able to view just one map larger.  Some countries are very difficult to see at the current size and there is information to be gleaned just from viewing a single map. Implementing the ability to zoom in on a map or an area of the visualization could be another way to improve the functionality of our visualization.

## Summary and Concluding Statements

Our goal was to create a visualization that could be used as part of a convincing argument for vaccinations, and while there is room for
improvement, we believe we have done accomplished our goal.  By highlighting the relationship between disease incidence and vaccination rates across two decades and multiple diseases, our visualization simply but powerfully demonstrates the value of vaccinations.  We have also created a visualization that reflects our difficulties in finding usable data about global vaccine rates, despite their
importance and the consequences of neglecting them.  We believe that this visualization has significant potential for exploratory
analysis of vaccine and disease rates, as well as serving as an effective means for explaining why vaccination is such an important
tool for reducing disease.

