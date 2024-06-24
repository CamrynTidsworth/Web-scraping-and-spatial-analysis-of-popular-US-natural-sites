# Web-scraping-and-spatial-analysis-of-popular-US-natural-sites
A data adventure wherin I use python and QGIS to scrape and analyze spatial data on popular natural sites accross the United States.

<img width="682" alt="Screenshot 2024-06-18 at 11 09 05 AM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/341c1f0d-81bc-4829-8cfb-6de2045bc509">




By: Camryn Tidsworth

Last Updated: June 18, 2024

For this project, I decided to scrape map coordinates off the internet to analyze natural sites, including National Parks and State Forests, in the US. While there are so many things I would love to do with this data, and so many additional data sources I’m tempted to bring in, I wanted to focus this analysis around a central question. So, imagine you are going on a trip and you want to find an area that has as many natural sites nearby as possible, as well as close proximity to an airport. Where should you go? We can answer this question with a few key steps. First, I’ll use Python to scrape the web and find a list of popular natural sites with coordinates. Then, I’ll upload this information to QGIS and do some spatial analysis to narrow in on the areas that fit our criteria. Finally, I'll explain my findings and make a data-driven reccomendation for your next outdoor vacation spot. 

### Section Links
1. [Web Scraping](https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/blob/main/README.md#1-web-scraping)
2. [QGIS Analysis](https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/blob/main/README.md#2-qgis-analysis)
3. [Conclusion](https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/blob/main/README.md#conclusion)

## 1. Web Scraping
The first step was to do a quick google search and find a website with the information I needed. I settled on [this site](https://www.latlong.net/category/national-parks-236-42.html) that includes a list of popular natural areas in the US with their longitude and latitude coordinates. I wrote the code using Python in Jupyter Notebook. You can view the code [here](https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/blob/main/natural_sites_web_scraping.ipynb) or check out the screenshots below. Once I had my information in a Pandas dataframe, I downloaded it to my computer as a .csv file. 

<img width="1212" alt="Screenshot 2024-06-18 at 12 16 39 PM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/04d3b424-1dc0-42bc-88fe-2a2611cf7605">
<img width="1213" alt="Screenshot 2024-06-18 at 12 16 54 PM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/02cbc453-7660-4cd2-9ace-daca6528b7af">
<img width="1212" alt="Screenshot 2024-06-18 at 12 17 10 PM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/e479a7d7-b337-431e-8d76-13a4a14f70be">


## 2. QGIS Analysis
From here, it was time to bring the data into QGIS. I uploaded my natural sites data as a point layer and visually compared the points to google maps to confirm accuracy. Fortunately, all the points were where they should be. I then imported data on airport locations and population centers from [Natural Earth](https://www.naturalearthdata.com/)’s open data repository. And of course, a Natural Earth base map for aesthetics and clarity. 

Now, the data was finally ready for some vector analysis. I used QGIS’s “distance to nearest hub” feature from the processing toolbox to link each natural site to the nearest airport and population center. The map looks like this: 

<img width="682" alt="Screenshot 2024-06-18 at 11 09 05 AM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/919883c5-7c44-4aa6-b521-d05fe44655ea">
<img width="288" alt="Screenshot 2024-06-18 at 11 16 02 AM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/135a496d-3e1b-46fb-b489-a5233cb78856">



By looking at the map, I could easily visually identify the airports and population centers with the most nearby natural sites. Simply put, the airports and cities with the most hub connections (visualized as lines to nearby natural sites) are the most favorable for this analysis. I also exported the attribute tables, which contained the distance between each hub and natural feature, as Excel files to enable closer inspection of the data and additional numerical analysis. 

## Conclusion
So, if you’re looking to see as many natural sites as possible while still remaining close to an airport and city, where should you go? With 8 natural site hub connections from the airport and 4 natural site connections from the city, Denver Colorado is your best bet. 

<img width="364" alt="Screenshot 2024-06-18 at 11 06 27 AM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/74915577-757b-4112-b29b-b3b388276b85">


|Denver, CO |   |
|---|---|
|**Airport** |  |
| | Denver International|
|**Nearest Natural Sites** | |
| | Mesa Verde National Park|
| | Bandelier National Monument|
| | Rocky Mountain National Park|
| | Golden Gate Canyon State Park|
| | William F Hayden Green Mountain Park|
| | Garden of the Gods|
| | Cherry Creek State Park|
| | Bear Butte State Park|

Coming up strong as number 2, Salt Lake City, Utah has 7 airport connections and 4 natural sites close to the city. 

<img width="300" alt="Screenshot 2024-06-18 at 11 06 15 AM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/0db8ed70-dff1-4b21-a298-d2d4d457b16a">

|Salt Lake City, UT |   |
|---|---|
|**Airport** |  |
| | Salt Lake City International|
|**Nearest Natural Sites** | |
| | Manti-La Sal National Forest|
| | Capitol Reef National Park|
| | Jackson Hole|
| | Grand Teton National Park|
| | Yellowstone National Park|
| | Arches National Park|
| | Bryce Canyon National Park|


Finally, what if you decide that you’d rather go somewhere as remote as possible? In that case, you should go to the Pacific Remote Islands Marine National Monument, Hawaii which is 822 miles from the nearest airport (Honolulu International) and 825 miles from the nearest city (Honolulu). 

<img width="976" alt="Screenshot 2024-06-18 at 11 07 41 AM" src="https://github.com/CamrynTidsworth/web-scraping-and-spatial-analysis-of-popular-US-natural-sites/assets/167467192/ede064af-5e47-4169-9408-07a1d0b94ae5">



It was a pleasure to explore one of the many ways that geographic data can be used to shape practical decision making. Thank you for taking the time to check out this project, and as always, constructive feedback is more than welcome. 
