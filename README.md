# dsc_project_1
Flatiron Phase 1 Project 1
by Evan Johnson, Ted Brandon and Jakub Rybicki

The goal of this repository is to present a  data analytical recommendation to a new movie studio on their first movie 
that will minimize their risk and increase their success at turning a profit.

Contents:

Phase1_Project.ipynb
- Jupyter notebook with detailed walkthrough, code used for data analysis and resulting plots. Includes findings and 
  recommendations for a new studios first movie
   - Python Packages used: matplotlib, Ipython
   - Imports used: pyplot, display, pandas, numpy, csv

data
- Data used for analyses in the Phase1_Project.ipynb Jupyter Notebook. Contains:
	- data_readme.md
	- idea1_main_genre.csv
	- idea1_main_genre_grouped.csv
	- idea1_only_aac.csv
	- idea1_only_aas.csv
	- idea1_only_bdh.csv
	- idea1_only_hmt.csv
	- the_oscar_award.csv
	- title.basics.csv
	- top_grossing_studios.csv

Appendix
- Contains supplementary files and information

.gitignore

README.md

# Summary:
Proof of Concept Goal - Show Studio Can Be Successful At Turning A Profit
Accomplishing this goal involves looking at types of movies that lend themselves to high profitability. In addition, 
partnering with another succesful studio that is experienced in making these types of movies will help to lay the framework 
for the new studio's success.

### The Bottom Line - Demonstrating profitability at the start will encourage studios, producers, filmcrew and actors to participate in future projects.

-Genre Profitability
-Profitability v Movie Budget
-Example of Movies Fitting This Model

Genre is the best way to breakdown types of movies as it can define the entire production process. For example, below are some of the top grossing movies for the Action/Adventure/Sci-Fi genre:
- Jurassic World : 2,301,125,489
- The Avengers : 2,141,215,444
- Black Panther : 2,048,317,790
- Avengers: Age of Ultron : 1,862,019,831
- Jurassic World: Fallen Kingdom : 1,723,492,559

Immediately what comes to mind are elaborate film sets, stunt teams and a star-studded cast. These requirements keep a production budget relatively high compared to other genres. In contrast, Compare this to top grossing movies from the Adventure/Animation/Comedy genre:
- Monsters University : 1,012,076,658
- Shrek Forever After : 994,981,460
- The Smurfs : 706,363,481
- Hotel Transylvania 3: Summer Vacation : 694,580,054
- Wreck-It Ralph : 685,924,198

Most animated films require no physical set and no stunt team. A lot of an animated film's budget will go into the animation and modeling of the movie versus the cast budget. On average the budget for an animated movie will be lower than that of an Action/Adventure/Sci-Fi movie.

Mean of Top Action/Adventure/Sci-fi Production Budgets: 191.88 million
Mean of Top Adventure/Animation/Comedy Production Budgets: 111.4 million

These defining differences between genres are not just between vastly different types like animation and action. They also exist within the genre subsets. For example, the adventure/animation/comedy genre has the highest average budget when compared to other genre amalgams that include animation.

It's important to note that these genre labels with multiple are not grouping together of the individual genres. Instead, each genre is being used as a descriptor to create a brand new, more specific genre.This leads to the importance of genre specificity.

### Genre Specificity:
Gone are the days of single genre movies. It is impossible to group movies by a single genre name (i.e Action, Animation, Comedy, Drama, Romance). There is a difference between The Notebook and 50 First Dates. One is a Romantic/Drama and the other is a Romantic/Comedy. These movies are created differently, marketed differently and viewed by different audiences.

<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>  <img src='https://www.kindpng.com/picc/m/10-103391_is-not-equal-to-mathematical-symbol-not-equal.png' style='width:50px;'/> <img src='https://upload.wikimedia.org/wikipedia/en/9/9d/50FirstDates.jpg', style='width:200px;'/>
</div>


### Viewing Production Budget as A Source of Risk:
#### "It takes money to make money." - Sol Luckman

The above saying carries a lot of weight. As seen in the results below, a higher production budget equates to a higher gross income. However, the business decision as defined at the start is not looking for highest gross income but highest profitability. In this case, production budget now serves as a source of risk. The higher the production budget the more money is being risked on the film.

The goal is proof of concept - can the studio make a profitable movie.

# Data Exploration
The primary data sources came from IMDB Datasets and Box Office Mojo by IMDB.

The data columns important to this business decision are:

Production Budget
Total Gross Income
Genre
Studio Name
Movie Title
Director Name
Oscar Award
Data Cleaning
For this decision there were some restrictions placed on the datasets to better represent the current film-making environment.

#### Only movies with:

Production Budget and Total Gross Income Data
A Recent Release Date (2000 or Later)
A Common Genre (Having 20 or More Movies Released Since 2000)

- Common Genres : Action/Adventure/Sci-Fi, Adventure/Animation/Comedy, Comedy/Romance
- Uncommon Genres : Crime/Drama/Musical, Comedy/Documentary/Horror
The data was also restricted to an IQR of 80% with respect to profitability which is defined in the Feature Exploration section. The cleaning process can be found in the appendix folder.

### Feature Engineering
Profitability is the key feature when looking at a business' financial health. Operating at a loss will ensure a swift end. For this study Profitability will be defined as Percent Gross Margin.

Profitability:
Define Profitability as Percent Gross Margin (GM%).

##### GM% = (I - B)/ I

Where:

I = Total Gross Income

B = Budget

### Profitability Explained:
In words, Profitability is what percent of every dollar made is above the cost. The max Profitability a movie can have is 100% (all profit and no costs). There is no limit on the lower end of Profitability. For Example, if a movie that cost 1,000,000 to make only makes 750,000 that would be a Profitability of -33% or a profit loss. The higher the production budget and the lower the gross income, the lower the Profitability.

#### Creating Profitability Feature:
The profitability feature was created using the total gross income and production budget numbers from the Box Office Mojo dataset and added as its own column in the genre dataset.

# Data Analysis
From the IMDB and Budget datasets, two final datasets were created:

 - The Genre Dataset : compares genre, profitability, budget and director - each row is a movie
 - The Studio Dataset : compares studio and total gross income - each row is a movie
 
#### Profitability and Production Budget By Genre

#####  Importing the Genre Dataset Grouped By Genre
Here we are looking for the top 5 entries in the Genre Dataset grouped by genre. We then sort by the mean profitability of each genre. 

# PUT IN MeanProfbyGenreTop5.png

<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

Below shows the mean profitabilities of each genre as a bar graph.

# PUT IN MeanProfbyGenre.png

<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

Not only is Horror/Mystery/Thriller at the top for profit, it also has by far the lowest budget costs compared to the other genres in the top 7 most profitable. Adventure/Animation/Comedy comes in second for profitability but is second highest for production budget.

### The Horror/Mystery/Thriller Genre has the Lowest Production Budget and Highest Profitability
The next two graphs shows Profitability v Production Budget by movie. The movies within the top two genres for profitability (as discovered above) are highlighted.

# PUT IN Scatter.png

<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

The left graph shows horror/mystery/thriller movies clustered to the top left. This indicates high profitability and some of the lowest movie budgets across all genres. The next most profitable genre is shown in the right graph. This shows a much larger spread on production budget.

##### Horror/Mystery/Thriller Genre Director Performance - For Chosing Director
The table below shows the top 4 grossing Horror/Mystery/Thriller movies with director information.

# PUT IN Top4GrossHorror.png

<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

James Wan has directed, produced or written half of the most successful horror/mystery/thriller movies of the last two decades. He was also the main director for the top grossing horror/mystery/thriller of all time - The Conjuring. He would be our top recommendation.

#### Top Performing Studio Data For Choosing Studio To Partner with
To choose a studio we want to look at the top performing studios that have been involved with horror movies. The below table shows the top 10 studios sorted by total gross income.

# PUT IN PNG FILE OF TABLE SHOWING TOP 10 STUDIOS BY TOTAL GROSS INCOME
<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

**BV** is the top grossing studio and supports Disney. The plot below shows a clear drop off in terms of total gross income after Warner Brothers.

# PUT IN PNG FILE OF TEDS CHART WITH THE STUDIOS AND AVERAGE TOTAL MEDIAN
<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

Both Paramount and Warner Bros work with Horror/mystery/thrillers. Paramount has released movies such as Paranormal Acitvity series while Warner Bros is responsible for The Conjuring universe. Either studio would be a good choice to partner with.

All studio average median is represented by the vertical dashed line
BV = Buena Vista (Disney)
Uni. = Universal Studios
Par. = Paramount Pictures
WB = Warner Bros. Studios
LGF = Lionsgate Entertainment Corp.
SPC = Sony Pictures Classics
IFC = Independent Film Channel (owned by AMC)
Magn. = Magnolia Pictures

## The Oscars
Looking at the IMDB title basics and the oscars awards dataframe
Combining the title basics and oscar awards dataframe
In order to relate the oscar winnings/nominations to a genre, we'll have to merge the dataframes. Upon analyzing the two, we can relate the data by movie title using the "primary_title" and "start_year" columns in the Titlebasics dataframe to the "film" and "year_film" columns in the oscars dataframe

#### Getting only the data we want
We'll be analyzing the oscar awards by genre going from 2010 onward. We will want to set up a new data frame that will only contain movies from the past 11 years and remove any NA values from the "genres" column.

##### Count up the genres and plot
Now we'll analyze how many total oscars nominations per genre there were since 2010 and plot them. Looking at the top 10 genres based on their Nominations over the past 10 years

Biography,Drama,History       85
Drama                         69
Drama,Romance                 51
Action,Adventure,Sci-Fi       39
Adventure,Animation,Comedy    36
Biography,Drama               32
Biography,Comedy,Drama        31
Drama,Thriller                30
Comedy,Drama                  29
Adventure,Drama,Fantasy       28

# PNG FILE OF OSCARS NOMINATIONS PLOT
<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>
##### Oscar Wins
We can also analyze the number of wins by genre since 2010.

Biography,Drama,History       17
Drama                         17
Action,Adventure,Sci-Fi       13
Adventure,Animation,Comedy    11
Drama,Romance                  9
Drama,Thriller                 9
Biography,Drama                9
Adventure,Drama,Fantasy        8
Drama,Sci-Fi,Thriller          7
Adventure,Drama,Family         6

# PNG FILE OF OSCARS Wins PLOT
<div class='center'>
<img src='https://m.media-amazon.com/images/M/MV5BMTk3OTM5Njg5M15BMl5BanBnXkFtZTYwMzA0ODI3._V1_.jpg' style='width:200px;'/>
</div>

# Conlusions
**Horror/Mystery/Thriller** genre should be the focus for the first movies from the new Microsoft Studio. These types of movies show the highest profitability and low required budget for success.
**James Wan** should be looked at as director of first movies as he has been apart of 50% of the top grossing horror/mystery/thriller movies of the past two decades.
**Paramount or Warner Bros.** would be the best studios to partner with as they both have experience in releasing successful horror/mystery/thrillers
Next Steps
##### Recommendations with regards to the Oscar Academy Awards
As a movie studio, you may decide to join the glorious pursuit of the ever covetted Oscar academy award. When you're ready to throw your hat into the ring, we highly recommend switching your main genre focus from Horror to Drama based on the wins and nominations since 2010.