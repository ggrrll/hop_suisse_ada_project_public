# Parsing 

In this folder we present the 2 notebooks dedicated to the scraping and preprocessing of the [Datasport](www.datasport.com) site.

* [`parsing_datasport.ipynb`](parsing_datasport.ipynb) For each link gathered in the [global_parsing](https://github.com/ggrrll/hop_suisse_ada_project_public/tree/master/2-global_parsing)
we parsed the corresponding race in the [datasport.com](www.datasport.com) site. Example: [here](https://services.datasport.com/2013/lauf/lamara/) is the
starting page. We went inside each of the links _classements par ordre alphabetique_ to parse the corresponding table ([here](https://services.datasport.com/2013/lauf/lamara/alfas.htm) 
is an example of a parsed table). The parsing proved to be hard since the tables are not formatted as a standard HTML page. We parsed each row of
the dataset as a full string trying to retrieve the correct fields from it.

* [`preprocessing_dataset.ipynb`](preprocessing_dataset.ipynb) We got the raw dataset obtained from [parsing_datasport.ipynb](parsing_datasport.ipynb)
and we preprocessed it to make it usable.

The main preprocessing steps were the following:
- **Automatically extract the sex of the runners**. We divided the runners per category and we determined the sex of the category by using
a name database. We combined these results with a parsing of the name of the category to determine the sex.
- Elimination of clearly bad formatted entries. 
- Determination of the **correct distance run**. Since no reliable infos on the distance were available we computed it by dividing the total time and the pace.
We applied a **clustering algorithm** to avoid floating point errors in the division.  
- Solving **duplication issue**. Runners with same name and birth year.

## Desctiption of the dataframe

The dataframe is available
[here](https://drive.google.com/file/d/0BypxDaHZHjhfNG9qbHA0NGJpbU0/view?usp=sharing).
We used the Pandas library with the Python 3.5 language.

The main features are the following:

### Race
> *dtype* object
>
> Name of the Race
>
> _not null_

### Date
> *dtype* object
>
> Date of the Race as String
>
> _not null_

### RaceYear
> *dtype* int64
>
> Year of the Race as int
>
> _not null_

### RaceMonth
> *dtype* int64
>
> Month of the Race as int
>
> _not null_

### Category
> *dtype* object
>
> Categoty of the Race - directly parsed from the Datasport website
>
> _not null_

### Distance
> *dtype* float64
>
> Distance run by the runner. Obtained as Time/Pace
>
> _not null_

### Name
> *dtype* object
>
> Name of the runner
>
> _not null_

### Sex
> *dtype* object
>
> Sex of the runner
> M or F
>
> _not null_

### Year
> *dtype* float64
>
> Year of birth of the runner
>
> _can be null_

### LivingPlace
> *dtype* object
>
> Living place of the runner
>
> _not null_

### Rank
> *dtype* int64
>
> Placement of the runner in the race
>
> _not null_

### Time
> *dtype* timedelta64
>
> Time taken by the runner. datetime.timedelta format
>
> _not null_

### Pace
> *dtype* timedelta64
>
> Pace of the runner. datetime.timedelta format.
>
> _not null_

### Place
> *dtype* object
>
> Place where the race is set.
>
> _not null_

### MinTemp
> *dtype* float64
>
> Minimum temperature the day of the race
>
> _can be null_

### MaxTemp
> *dtype* float64
>
> Maximum temperature the day of the race
>
> _can be null_

### Weather
> *dtype* object
>
> Description of the weather the day of the race
>
> _can be null_

### RaceID
> *dtype* object
>
> Unique identifier for the race. It is the link to the datasport race page.
>
> _not null_

### UserID
> *dtype* object
>
> Unique identifier for the User. Name + Year
> Not always correct. There can be 2 users with the same ID.
>
> _not null_


