# README to the "GEPRIS-Patents-Dashboard"

## Purpose of the visualization:
Our Goal was to visualize the Project Starts of the GEPRIS-Dataset per Bundesland in direct comparison with the outcoming Patents per 
Bundesland. By doing this we wanted to highlight Bundesländer with apparently high efficiency of scientific efforts resulting in a high 
number of registered Patents which can come into use by Industries. 

## Design decisions using the “Four Nested Levels of Visualization Design” by Munzner:
### a. Domain problem characterization: 
Our Main group of target users of the GEPRIS dataset consists of Students, Researchers and scientifically interested people.
Theiy would have questions about the proportionate course of the number of research projects per Bundesland and also of the subject area 
which they consist of. We enlarged this target group to Investors and people with a finacial background and business model interest by 
adding the patents data to the dashboard. This part of the target group might have questions such as "Which Bundesland produces the highest
number of patents in comparison to the number of research projects started?".

### b. Data / task abstraction:
b1. We merged the GEPRIS-Data of the the following CSV-Files to be able to relate projects to their institutions and subject areas.
  * extracted_project_data.csv
  * institution_ids_and_names.csv
  * project_ids_to_subject_areas.csv
b2. We found out the Bundesland by Googleling of each Institution and therefore created a new column "Bundesland" containing the information.
b3. We transformed the resulting CSV-File to a JSON-File to be able to follow our Tutorial on Udemy which chose explaining the 
visualization process mainly with JSON-Files.
b4. TODO - Subject areas  
  
### c. Visual encoding / interaction design: Describe the visual encoding and why you decided for it. What interaction types did you use and why?
### d. Algorithm design: How did you make sure that the computational complexity of your solution is appropriate? What is the bottleneck with respect to performance?
