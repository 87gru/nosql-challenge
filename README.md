# nosql-challenge
## Background
### Per BootCampSpot page:
> The UK Food Standards Agency evaluates various establishments across the United Kingdom, and gives them a food hygiene rating. 
> You've been contracted by the editors of a food magazine, Eat Safe, Love, to evaluate some of the ratings data in order to help their journalists and food critics decide where to focus future articles.

## Assignment Breakdown
### Part 1 - Database and Jupyter Notebook Set Up (`NoSQL_setup_starter.ipynb`)
- Data is imported from the establishments.json file. `!mongoimport` is included in markdown cell and as actual code.
- Using PyMongo, an instance of Mongo Client is created.
- Confirmation that databases was successfully loaded by listing the databases and collections.
- Use `find_one` and `pprint` to display one document.

### Part 2 - Update the Database (`NoSQL_setup_starter.ipynb`)
- Added "Penang Flavours" restaurant to `establishments` collection using the provided dictionary.
- Find the BusinessTypeID for BusinessType "Restaurant/Cafe/Canteen," return only `BusinessTypeID` and `BusinessType` fields.
- Update Penang Flavours' `BusinessTypeID`
- Removed all documents with Dover in the `LocalAuthorityName`. Used `find_one` before and after deletion to confirm success.
- Used `update_many` to cast `latitude` and `longitude` fields to decimal/double; also converted `RatingValue` to integer.
- Using provided code, changed any non numerical value in `RatingValue` to `None`.
- To confirm that `latitude`, `longitude`, and `RatingValue` fields are numbers, I used aggregate pipeline to display fieldTypes. I made sure that the only values in these fields are `double` and `int` (`null` values in `RatingValue` are fine).

### Part 3 - Exploratory Analysis (`NoSQL_analysis_starter.ipynb`)
- Answered the following questions:
    - Which establishments have a hygiene score equal to 20?
        - There are 41 establishments with a hygiene score equal to 20. The first result in the list is The Chase Rest Home.
    - Which establishments have a `RatingValue` greater than or equal to 4?
        - There are 33 establishments with a `RatingValue` greater than or equal to 4.
    - What are the top 5 establishments with a `RatingValue` of 5, sorted by lowest hygiene score, nearest to the newly added restaurant "Penang Flavours" (nearest = 0.01 degree on either side of lat/lon to Penang).
        - Establishments are detailed in the Jupyter Notebook file.
    - How many establishments in each Local Authority area have a hygiene score of 0? To answer this question, I used the Aggregation Pipleine method. The results were then converted into a DataFrame.
        - Thanet, Greenwich, Maidstone, Newham and Swale have the highest number of establishments with hygiene scores of 0.

## Repository Breakdown
- README.md
- .gitignore
- `NoSQL_setup_starter.ipynb`
- `NoSQL_analysis_starter.ipynb`
- Resources directory
    - `establishments.json`