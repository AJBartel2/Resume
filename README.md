# AJ Bartel - Data Analyst
Longmont Colorado // 720-256-4196 // aiden.j.bartel@gmail.com

### Background
I am a Graduate of both Mathematics and Economics who is on a mission to interogate data. As someone who struggled early on with Math and later found the beauty/significance it plays in the world today, I strive to help others understand quantitative logic in a way that is not overwhelming. In my time at Western Colorado University I loved the pure math classes I took including Analysis, Non-Euclidean Geometry, and Abstract Algebra. These classes well portrayed the elegance of Mathematics, along with some of the higher level functionality of math that we use unkowingly every day. My Economics classes, along with stats, introduced me to the functionality of Data and the power it has. Data tells a story, and it is up to the interperator to pull everything they possibly can out of it. I look at data analytics and statistics like a treasure hunt; put in the work and ask the hard questions and eventually you will find the hidden treasure. 

# Education

**Western Colorado Univeristy - Gunnison, CO**
- B.S. Mathematics - 2021
- B.A. Economics - 2021

# Work Experience

- Data Analyst - Intrado // Sep 2021 ~ Present
- Club Baseball President - Western Colorado University // May 2019 ~ May 2021
- College Financial Representative - Northwestern Mutual // May 2020 ~ Dec 2020
- Crew Member - Timeless Landscape // Aug 2019 ~ May 2019
- Irrigation Technition - Turf Paradise // June 2016 ~ Aug 2019

# Code

- **R-Studio**

Most of my coding experience comes within R Studio, but I have experience in Python, Mathematica, SPSS, Matlab, and some exposure to SQL. Because R is my strong suite, I've included a small project where I take data from a webpage, format it for my use, and plot a simple graph of two variables. If that summary was enough for you, go ahead and scroll down to read one last thing I have to add. If you want to keep reading, here's the project!


I first started by scraping a webpage for the data I wanted to use, and then saved the data as a .csv so I could access it later. If you'd like to run this code for yourself, the .csv is included in this repository and linked right [here](https://github.com/AJBartel2/Resume/blob/gh-pages/plate_discipline_2021.csv). 

``` 
### A couble of these packages we use futher down in the code for plotting

install.packages("rvest")
install.packages("dplyr")
install.packages("ggplot2")
install.packages("ggrepel")


library(rvest)
library(dplyr)
library(ggplot2)
library(ggrepel)



link = "https://baseballsavant.mlb.com/league?view=statcast&nav=pitching&season=2021"
page = read_html(link)

plate.dicp.html = html_nodes(page, '#playeDiscipline')
plate.discp = html_table(plate.dicp.html)

### With the way that the html_table() function works, we need to decalare which object in our group of 4 is actually our data in the form we want it. In this case it was the first one, denoted by the double brackets [[]].

View(plate.discp[[1]])

write_csv(plate.discp[[1]], "plate_discipline_2021.csv")
```
Once the data was saved, I opened the csv with the readr package and took a quick look at the data to see if there was anything I wanted to explore more, or anything that would make a pretty graph for my Git-Resume. I noticed the last rows is a totals row, so I elimated that first and then looked at a summary of the data.  

```
library(readr)
plate_discipline_2021 <- read_csv("plate_discipline_2021.csv")
View(plate_discipline_2021)

### Trimming the bottom row off with the following line:

plate_discipline_2021 <- slice(plate_discipline_2021, 1:(n()-1))

summary(plate_discipline_2021)
```
This summary can provide insight of obvious red flags in the data, such as an outlier with a wrong decimal point along with other variations of data entry errors that may have squeaked by during the initial cleaning process. 

Next, let's put together a graph! I would like to look at Percent Of Pitches In The Zone plotted to Percent of Contact Made On Pitches In The Zone. This graph is interesting to me because it shows an interperitation "quality swings". 

```
Plot1 <- ggplot(plate_discipline_2021, aes(x= `Zone %`, y= `Zone Contact %`, color= `Team`, label=Team)) + 
  
  geom_point(size = 2,alpha = 0.6) +
  
  theme_bw()+
  
  ### geom_text_repel is a really clever tool for plotting I learned in school. It makes the labels on the points find somewhere to be withput overlapping the other labels
  
  geom_text_repel(aes(label=`Team`))

Plot1.Final <- Plot1 + ggtitle("Percent of Pitches Seen In Zone by Contact Made On These Pitches")
Plot1.Final

```

![Here is the final result!](Scraping.pdf) This Plot is simple, just to showcase some plotting with a simple data set in R. As I am just now starting to upload more projects here, I will open up more repositories showing more vigorous analysis. 

# Relevant School Work

**Linear Algebra Presentation** // December 2021
I delivered a presentation to the Math Department faculty and students at Western Colorado University on Linear Algebra. Using Markov Analysis, I attempted to simulate the game of baseball with the goal of predicting probability of runs scored in a given 9-inning game. The model used team data to predict the probabilities of events happening within a game, and then converted that data to predict the number of runs scored in a game. The code from this project is under my SampleCode repository, check it out!

**Economics Capstone Project** // May 2021
For my capstone project in Economics, I presented on Income Distribution and Inequality as it relates to the income structure of Major League Baseball. While this topic has more profound impacts outside of professional sports, it was fascinating to dive into the economic structure of the game. I employed critical analysis of the policies and changes in baseball from an economic standpoint. Additionally, I sourced, modified, and worked with all of the data for this project using RStudio.



# If you've made it this far...

Thank you for reading! Now that I have talked about my background, I'd like to add two things about why I enjoy data and how it is important to me from a career standpoint. This is a bit unconventinal to the typical resume, however I think it is important to add considering I have just graduated college. Presented in list form, here it is:

- **Keep Learning**:
    The most enjoyable part of writing code and exploring the realm of Data Analytics is that I learn so much every day. There is more than one way to solve a Rubix Cube, and the small things I pick up from others in Data Analytics encourage me to try new things in my own work. 
    
- **Challenge Data**:
    Data is never the same. It is found in prestine condition (rarely), and sometimes you find it balled up in the bottom of a dumpster fire being used as a home for a family of mice. Enjoying the ability to work with data of all forms and get answers from it is something that I love, and truely is at the heart of my pursuit for a career in Data. 
    



