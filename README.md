# hop_suisse_ada_project_public         

Repository for ADA project.
The goal of this project is data scraping, analysis and visualization from the
[Datasport](https://www.datasport.com) website, focusing on the "running" data.

A more detailed description of the steps followed can be found
[below](#working-steps).


## Team

NB : The project is run by a new team, obtained by merging two ADA teams 

- [Ondine Chanon](https://github.com/ochanon)
- [Maxime Peschard](https://github.com/maximepeschard)
- [Stefano Savarè](https://github.com/deatinor)
- [Gianrocco Lazzari](https://github.com/ggrrll)
- [Antonio Iubatti](https://github.com/antonioiubatti93)


## Working steps

In this section we describe our steps, (more or less) chronologically.

* [project proposal](1-project_proposal/project_proposal_hop_suisse.md) :

> Describes guideline, goals and objectives of the project.

* [global parsing](2-global_parsing/global_parsing.ipynb) :

> From datasport main page, make requests to extract all the names, dates and
> places of every running competition, and the url links where to find the
> results.
>
> Results :
> * [`links2runs.csv`](datasets/links2runs.csv)

* [ranking parsing](3-ranking_parsing/parsing_datasport.ipynb) : 

> From every url found in `links2runs.csv`, get all the information about every
> specific race, that is all the information about every runner : name, age,
> category, ranking, pace, etc. Note that given the way Datasport displays
> things, this is not an easy step :grin:
>
> Results :
> * [`pickle`](https://drive.google.com/file/d/0BypxDaHZHjhfYTBsMGM2WVlFdkU/view) (temporarily hosted on Google Drive)

* [weather](4-weather/weather_utils.py) :

> From `links2runs.csv` consider every date and place and (try to) find the corresponding
> weather and temperature in order to do performance analysis with respect to the
> weather/temperature. Due to the API used, such information for races older than
> July 2008 is not available.
> 
> Results :
> * [`races-information-weather.csv`](datasets/races-information-weather.csv)

* [gathering information](5-gathering_information/races_information.ipynb) :

> Extra steps to build, on top of `links2runs.csv`, a more complete table
> containing the scraped information plus the weather information and GPS
> coordinates for each location when available.
> 
> Results :
> * [`races-information.csv`](datasets/races-information.csv)

* [data analysis](6-data_analysis) :

> Data analysis, both on particular cases like Lausanne Marathon, and on the
> global dataset.

* [visualization](7-visualization) :

> Our goal is to display the gathered data and the analysis on a website, in a
> more "user-friendly" way than Datasport. The website pointed by [this
> link](https://hopsuisse.github.io) is the result, using GitHub
> Pages, Jekyll, D3.js, Leaflet, etc... :wink:

* [video](8-video):

> We have created a short video that can be found [here](https://www.youtube.com/watch?v=KzeR-H7_xlE) 
> in order to visualize the huge Datasport dataset in a concise way. Our 
> inspiration comes from the famous [Hans Rosling's video](https://www.youtube.com/watch?v=jbkSRLYSojo).

