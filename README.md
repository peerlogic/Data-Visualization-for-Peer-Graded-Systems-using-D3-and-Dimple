# Data Visualization for Peer Graded Systems

## Bubble Charts
A bubble chart can be used to represent 4 dimensions, x-axis, y-axis, color of the bubble and the size of the bubble.

## Libraries Used
* dimple.js
* d3.js
## Description of files

### JSON Structure

- The common properties for all the JSON files are described below:

 * <b><em>x_label</em></b> denotes the entity represented on the x-axis, its label being specified by 'label_name' and the URL is given by 'url'. Upon clicking this URL link the user is redirected to another visualization of, say, Scores received on that particular criterion by different students for each stage of submission of an assignment.   
  * <b><em>y_label</em></b> denotes the entity represented on the x-axis, its label being specified by 'label_name' and the URL is given by 'url'.
  * <b><em>configuration</em></b> denotes all the kinds of settings that the user is allowed to configure. This includes the 
  * <b><em>color_scheme</em></b>, the color code used to display variation from good to bad.
  * <b><em>svg-height</em></b> denotes the height of the page, in pixels, take up by the visualization.
  * <b><em>svg-width</em></b> denotes the width of the page, in pixels, take up by the visualization.
  * <b><em>font-family</em></b> denotes the font family used to display the labels and text in the visualization.
  * <b><em>font-size</em></b> denotes the size of the font used to display the labels and text in the visualization.
  * <b><em>bubble</em></b> has the display configuration for bubble in the bubble chart, w.r.t. its minimum and maximum radius.
  * <b><em>is_mean_user_provided</em></b> it is a flag to specify if the input given to the visualization are individual scores ( whose mean and variance are calculated programtically), or if the user provides mean scores and variance. Note that, here the mean can be a weighted means, calculated as per some algorithm.

- In addition, the "content" property differs across the files, and therefore described below

### student_criteria_bubble_with_means.html 
-  In this visualization, the student ids are represented along the y-axis, the criteria along the x-axis, the color denotes the Mean of the scores and the size of the bubbles represent the Standard Deviation/variance. 

#### Content Structure
 
  <b><em>content</em></b>
  - This denotes all the content to be visualized.
  - It is a 3 dimensional array structure.
  - The outer most dimension represents the students across all the criteria.
  - The intermediate dimension represents the criteria. 
  - And finally, the inner most dimension denotes the scores awarded by the reviewers to the given student. The input can either be the mean score & variance, ( i.e. if <b><em>"is_mean_user_provided"</em></b> is set to true), in which case, <em><b>"weighted_mean_score"</b></em> denotes the weighted mean for all scores and the "variance". On the other hand, if <b><em>"is_mean_user_provided"</em></b> is set to false, then an array of <b><em>"scores"</em></b> need to be provided, each element of the scores array, has the score value, the reviewer Id who has awarded the score and the comments, if any.
    

### reviewer_student.html
- This visualization opens when the user clicks on any of the links on the x-axis labels. In this visualization, the reviewers are represented on the x-axis and the students are represented on the y-axis. The size of the bubble denotes the value of the score and the color denotes the <b><em>submission</em></b>.

#### Content Structure
- The content is a 3 dimensional array, the outermost dimension represents <b><em>reviewers</em></b>, the intermediate represents the <b><em>submission number</em></b>,  while the innermost dimension represents the <b><em>student</em></b>. 

- For example,
'''javascript
      // scores by 0th reviewer for all submissions.
     reviewerData.content[0];
   
//      scores by 0th reviewer for the 2nd submission.
     reviewerData.content[0][2]; 
     
     // scores by 0th reviewer for the 2nd submission for the 4th student.
     reviewerData.content[0][1][4];
     '''
- In general, we can say...

    // Data for ith review
     '''reviewerData.content[i] ;'''
      
    // All the data(scores, comments) for ith review for the jth criteria.
     '''reviewerData.content[i][j] ;'''
       
    // The score for the ith review for the jth criteria
     '''reviewerData.content[i][j].score ; '''
       
    // Comment given by the ith reviewer for the jth criteria.
     '''reviewerData.content[i][j].comment ;'''

- Each score consists of the actual score value and the comments received, if any.


### criteria_reviewer.html
- This visualization opens when the user clicks on any of the links on the y-axis labels. In this visualization, the criteria are represented on the x-axis and the reviewer ids are represented on the y-axis. 

#### Content Structure
 - The content is a 2 dimensional array, the outer dimension represents <em>criteria</em> , while the inner dimension represents the <em>student</em>. The size of each bubble denotes the actual <em>score</em> values.
    
 - For example, we have..
 
       ''' // scores for 0th student across all criteria.'''
       ''' reviewerData.content[0];'''
       ''' // scores for 0th student for the 2nd criterion.'''
       ''' reviewerData.content[0][2];   '''
 
 - In General,

    ''' // Data for ith review '''
    ''' raw_reviewer_data[i];'''
    ''' // All the data(scores, comments) for ith review for the jth criteria'''
    ''' raw_reviewer_data[i][j];'''
       
    ''' // The score for the ith review for the jth criteria'''
    ''' raw_reviewer_data[i][j].score;
       
    ''' // Comment given by the ith reviewer for the jth criteria. '''
    ''' raw_reviewer_data[i][j].comment; '''
  
### References 
* https://d3js.org/
* https://github.com/PMSI-AlignAlytics/dimple/wiki
