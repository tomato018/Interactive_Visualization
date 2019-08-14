# Interactive_Visualization

Interactive visualization is becoming a more prominent feature of reporting. Business analytics packages tend to stress the ease eith which data can be played with by non-experts. Allowing students to explore aspects of complex data rather than simply telling them what you see can be a powerful tool for learning as explored in the readings. Within the RStudio universe this functionality is accomplished through the Shiny ecosystem. A web-app designing interface that allows web-apps to be built from within R with limited knowledge of javascript or html.

In this project, I built a basic Shiny App to show students' skill mastery based on their midterm score on each quiz category. You can find out the interactive visualization [here](https://meijuanzjenny.shinyapps.io/interactive-visualization/).

## Datasets

### quiz-categories.csv

This dataset contains skills required to answer each question:
* wrangling - Question required data manipulations skills  
* coding - Question required coding skills  
* d.trees - Question invoilved decision trees  
* sna - Question involved social network analysis  
* nlp - Question involved natural language processing  
* viz - Question involved visualization of data  
* n.nets - Question involved neural nets  
* googleable - Question could be answered by searching the internet  
* non-googleable - Question could not be answered through simple searching of the internet  
* jitl - Question involved learning somethimg new (just in time learning)  
* substantive - Question involved wrestling with a complex idea that does not have a definitive answer

### midterm-results.csv

This dataset contains each student's grade, time completion, and number of clicks on each question.

## Packages Required
```
install.packages("shiny")
```

## Procedures

1. Use rsconnect::setAccountInfo to gain access to building an indiviudal Shiny App.
2. Data wrangling:
   * Calculate percentage of number of correct answers and round the value to integers in miderm dataset.
   * Select the columns containing each skill from quiz dataset.
   * Group by student id, gather all 30 questions and score into 2 columns, and full join the midterm data wtih quiz data
   * Filter the score which is not equal to 0.
   * Group by student id and sum up all the scores in the skill columns (except googelable and non.googleable)
   * Mutate each skill column to calculate the percentage of score 
   * Get the student id, skill columns and percentage scores
   * Gather all the skill and percentage columns into two columns: "Skill", "Percent"
   * Spread with student id and percent, so that we can get students' percentage score for each skill category 
3. Generate a visualization by creating a UI, server, and shiny App.
   * In the UI interface, I put "Skill Mastery" as title panel, used sidebar layout for student id input, and used gghist for main panel graph.
   * In the server, I used render plot to show reactive data for each student's skill mastery
   
## Author
[Meijuan Zeng](https://github.com/tomato018), MS student in Learning Analytics, Columbia University
