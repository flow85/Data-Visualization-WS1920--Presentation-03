# GEPRIS-Patents-Dashboard

## Short description: 
Our Goal was to visualize the Project Starts of the GEPRIS-Dataset per Bundesland in direct comparison with the outcoming Patents per 
Bundesland.

## Table of contents (TOC):
1. Project description
1.1 Design decisions using the “Four Nested Levels of Visualization Design” by Munzner
1.2 Validation of our design and lessons learned
1.3 Think aloud protocol
1.4 Installation
1.5 Manual
1.6 Contributors
1.7 Data copyright

## 1. Project description:

### 1.1 Design decisions using the “Four Nested Levels of Visualization Design” by Munzner:
#### a. Domain problem characterization: 
Our Main group of target users of the GEPRIS dataset consists of Students, Researchers and scientifically interested people.
Theiy would have questions about the proportionate course of the number of research projects per Bundesland and also of the subject area 
which they consist of. We enlarged this target group to Investors and people with a finacial background and business model interest by 
adding the patents data to the dashboard. This part of the target group might have questions such as "Which Bundesland produces the highest
number of patents in comparison to the number of research projects started?".

#### b. Data / task abstraction:

b1. We merged the GEPRIS-Data of the the following CSV-Files to be able to relate projects to their institutions and subject areas.
  * extracted_project_data.csv
  * institution_ids_and_names.csv
  * project_ids_to_subject_areas.csv
  
b2. We found out the Bundesland by Googleling of each Institution and therefore created a new column "Bundesland" containing the information.

b3. We downloaded the CSV-File "Patentsanmeldungen nach Bundesländern" from https://www.dpma.de/dpma/veroeffentlichungen/statistiken/csv-statistiken/index.html and joined it with our GEPRIS-Data.

b4. We filtered our entire CSV-File by year starting from the year 2000 to the year 2018 because the Patents data from the 
Trademark Registry only covered this timeframe.

b5. We transformed the resulting CSV-File to a JSON-File to be able to follow our Tutorial on Udemy which chose explaining the 
visualization process mainly with JSON-Files. We only kept the relevant Information in the file concerning Bundesländer, Projectstarts, Patents and the Year.

b6. TODO - Subject areas (We created a second TODO-File containing the number of subject areas per Bundesland that were included
in the Projectstarts)
  
#### c. Visual encoding / interaction design: Describe the visual encoding and why you decided for it. What interaction types did you use and why?
We decided to use a simple and clear structured All-in-One Dashboard-Design with multiple interlinked dataviews such as:
 * Dropdown menue containing the selected Bundesland. By selecting a Bundesland of interest with a left mouseclick the user can easily decide on a geographical category of interest, followed by the visualization in all interconnected Dataviews.
 area of interest and
 
 * Dropdown menue containing either the number of Projectstarts or the number of Patents of the selected Bundesland. By selecting either
 the Projectstarts or the number of Patents with a left mouseclick the user can decide if he or she either wants to display Projects or Patents in the Linechart view.
 
 * Timeslider containing our timeframe from the year 2000 to the year 2018. By trimming the timeslider with a holding left mouseclick followed by releasing the left mouse button the user can filter for a surtain timefrage of interest in the linechart view.
 
 * Time-Navigation-Bar containing an area chart of the Linechart view Data. This Dataview provides the possibility to navigate a previously filtered Timeframe of the Timeslider alongside of the X-Axis an therefore supporting the preffered Timefilter-Selection. The user can also draw a rectangle of an individual timeframe of interest to control the start and finishing point of the Timeslider functionality. With both Tools, the Timeslider and the Time-Navigation-Bar the user has a high amount of control to select individual timeframes of interest inspecting the Linechart data.
 
 * Donutchart of the Projects-Share in 2000-2018 containing the relative share of each Bundesland in the entire Timeframe of the year 2000 to the year 2018 considering the amount of Projectstarts. This gives the User a better understanding of the relevance of a Bundesland related to the number of Projectstarts. The Donutchart updates in interaction with each selection in the Bundesland Dropdown-Menue an supports the User by Coloring each Bundesland-Share in the same Color as each Linechart-Curve-Color, therefore reducing the number of different colors displayed on the entire Dashboard.
 
 * Donutchart of the Patents-Share in 2000-2018 containing the relative share of each Bundesland in the entire Timeframe of the year 2000 to the year 2018 considering the amount of Patents. This gives the User a better understanding of the relevance of a Bundesland related to the number of Patents registered. The Donutchart updates in interaction with each selection in the Bundesland Dropdown-Menue an supports the User by Coloring each Bundesland-Share in the same Color as each Linechart-Curve-Color, therefore reducing the number of different colors displayed on the entire Dashboard.
 
 * TODO (Area-Chart?!) containing the subject areas of each Bundesland related to the Number of Projectsstarts. This gives the User a better understanding of the type of Projectstarts considering strongly and weakly represented subject areas. Regrettably this data is only present related to the number of Projectstarts of each Bundesland since the Trademark Registry Statistics did not contain any information about subject areas.
 
#### d. Algorithm design: How did you make sure that the computational complexity of your solution is appropriate? What is the bottleneck with respect to performance?
* TODO - We tried to reduce the complexity of our solution starting with limited focus from the beginning only on a surtain aspect of the GEPRIS-Data, since we are only considering information about each Bundesland, the number of Projectstarts, the subject areas of the Projectstarts, the number of Patents and the Year concerning each Data Entry. Also the limited Timefrage from the Year 2000 to 2018 plays an advantage here.

* In the next phase we reduced the Dashboard-Complexity to only a surtain amount of Dataviews which we considered as necessary and benefiting for the User.

* The computational complexity is reduced by using only one main HTML-File for the visual representation and one main JavaScript-File to manipulate the biggest part to the represented data.

* For better Overview in computational design we used seperate JavaScript-Files for each Dataview-Type followed by their instanciation in the main JavaScript-File.


### 1.2 Validation of our design and lessons learned

* The Bottleneck in our Visualization consists of mainly two design aspects:

  * Since we are including all 16 Bundesländer in our Dashboard our Donutcharts contain all 16 Elements. This confronts the user with a high amount of differently colored Elements in Chart. In this case we explicitly decided to break the rule of the lecture of only coloring 5 to 6 Elements in a visualization differently because we wanted to stick to our overall design decision to visualize all 16 Bundesländer in our Dashboard-Design. Also the very tiny share slices of Bundesländer with a less amount of projects and or patents is a weakness in this visualization since the user can almost not see the selected donut slice. We also sticked to this design decision since we wanted to give an overall view of the dataset and present a generall picture of each Bundesland.

  * Also the (TODO - Area Chart View) shows an amount of differently colored elements in form of subject areas which can overwelm the user in its complexity. We also here sticked to this design decision because of our claim to show as much information as possible on as little screen space as possible. In an evaluation of this projects we would probably choose different chart types for the mentioned visualization weaknesses above.

* Overall we do not see our project weaknesses in the computational complexity since we have a limited focus but more in design decisions.

* Another general weakness in our argumentation chain in the fact that we are comparing the number of projectstarts to the number of registered Patents, which leads to the question if choosing projecstarts is suitable. We explicity decided to use this data because it was the most appealing information that we had contained in the GEPRIS-Dataset for our project objectives.

* Another general weakness is the fact that we are not able to show the subject areas of the number of Patents registered in each Bundesland. Regrettably the German Patents Statistic does not provide us with any information in this aspect. Also the general train of thought of comparing the number of Projectstarts to the number of Patents as a measure of efficiency and value is questionable. The Goal doing this was mainly on achieving more visualization experience during the process instead of delivering a waterproof argumentation of the represented data.

### 1.3 Think aloud protocol:

* TODO

### 1.4 Installation:

* TODO - install python Server

* TODO - install D3

* TODO - open Github-Link https://flow85.github.io/github.io/

### 1.5 Manual: A brief manual about how to use the software. For this it makes sense to use
screencasts or screenshots. TODO - create screencast and insert link

### 1.6 Contributors: Name your group members here and add links to their (Github) profiles.

* Adriana Printo, https://github.com/adrianapintod

* Florian Mercks, https://github.com/flow85

### 1.7 Data copyright: 

* “Data derived from original data provided by https://gepris.dfg.de (c) Deutsche Forschungsgemeinschaft”

* “Data derived from original data provided by https://www.dpma.de/dpma/veroeffentlichungen/statistiken/csv-statistiken/index.html (c) Deutsches Patent- und Markenamt”

* Code derived from original Code source provides by https://www.udemy.com/course/masteringd3js (c) "Udemy.com - Mastering data visualization in D3.js"
