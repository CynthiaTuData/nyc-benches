# Mapping NYC's CityBench data
 This is a project mapping benches across NYC and finding public seating deserts.
 
*Read the story here: [Please Be Seated](https://xinyitu.github.io/benches-accessibility/)*
## Goal
Something that I've discovered since moving to NYC is the lack of streetside benches on New York's streets. With this project, I hope to assess the city's assessibility through public seating.

## Data Collection
- I used bench data published by NYC Department of Transportation's [CityBench Program](https://data.cityofnewyork.us/Transportation/Seating-Locations/esmy-s8q5) downloaded from NYC Open Data. Each row in this dataset is one Citybench installed in NYC, including its seating type, date of installation, and coordinate. Check out notebook `bench-data-cleaning&analysis.ipynb` for how I cleaned this data.
- NYC census tract geo data is retrived from [NHGIS's 2020 census geo data](https://www.nhgis.org/). 
- Walking distance calculation data is collected through [Google Maps Distance Matrix API](https://developers.google.com/maps/documentation/distance-matrix/overview).

## Methodlogy & Analysis
#### What's the data?
This project analyzed streetside benches in NYC, which does not include public seatings in parks/plaza/open street resturants/etc. NYC's CityBench program started installing these benches in 2016. Data was last updated in 2022, with latest installation date in 2020.

#### Steps taken to create the map
*Visualization/method inspo: CNN story, [Visualizing the inequality of abortion access in a post-Roe America](https://www.cnn.com/interactive/2022/us/abortion-laws-access-by-state/index.html)*.

1. `bench-data-cleaning&analysis.ipynb` import and clean bench data
2. `tract-to-nearest-bench-calculation.ipynb` import census tract centroid data
3. Using the coordinates of benches, loop through all census tract centroids to find the nearest bench that matches each tract
4. With each census tract's centroid coordinate as the starting point, and nearest bench location as the destination, use Google Maps Distance API to calculate the walking distance and time
5. Merge the dataframes, create a database of all census tracts: each row is a census tract, its nearest bench location, walking distance & time, census tract geo data, bench details
6. `pre-mapping.ipynb` Export for visualization in QGIS and Adobe Illustrator


#### Important Notes
- When calculating tract to nearest bench, bench type "leaning bar" was excluded as the project intends to focus on accessiblr seatings.
- Walking distance is used in this analysis as the users of public benches are mostly pedestrians. 
- Centroids refers to the point located in the geographic center of the polygon of each census tract.


## Findings
- The city's DOT installed more than 2,000 benches from 2016 to 2020. As the maps shows, a few "bench deserts" are present in NYC, meaning that some parts of the city do not have any streetside benches.
- Most benches in NYC are backed and backless.
- However, installation of leaning bars had increased over the years, while the other two had decrease.
- Queens and Staten Islands are the most bench deficient boroughs in NYC.

Bench location map:
<img width="669" alt="Screen Shot 2023-02-28 at 4 13 24 AM" src="https://user-images.githubusercontent.com/116761432/221807164-1551269d-2637-43db-bc0a-3a6da6f655f8.png">


Distance to bench by census tract map:
<img width="835" alt="Screen Shot 2023-02-28 at 4 13 37 AM" src="https://user-images.githubusercontent.com/116761432/221807067-a1b69111-615a-428d-bd9f-741c031dec63.png">

## New Skills&Growth
New tools I've learned to use to creat this project
- QGIS (first time!)
- ai2html (first time, created multiple versions of map for better viewing experience on mobile and desktop)
- Adobe Illustrator (my second attempt at Ai)
- Time management: this project was created in a week's time from pitching to the final product

## Challenges and possible improvement
- Bench data only include streetside benches, which might not provide a full picture of all accessible seating options in NYC.
- I focused solely on mapping this time, but the project could benefit from more data points & visualizations. e.g. a breakdown of types of benches and number of benches by borough.
- The piece would benefit from more reporting on this subject for further journalistic inquiries.

## Contact
I can be reached at xt2274@columbia.edu or on Twitter @CynthiaTu2. My inbox is open for any comments, suggestions, angry email telling me what I did wrong in this project... 

