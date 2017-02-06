# Data Visualization for Peer Graded Systems

## Bubble Charts
A bubble chart can be used to represent 4 dimensions, x-axis, y-axis, color of the bubble and the size of the bubble. In this visualization, the student ids are represented along the y-axis, the criteria along the x-axis, the color denotes the Mean of the scores and the size of the bubbles represent the Standard Deviation/variance. 
## Libraries Used
* dimple.js
* d3.js

## JSON Structure

### Bubble Chart for Student v/s Criteria with means and variance
 '''
 {
    "x_labels" : [
                        {"label_name" : "", "url" : ""}
                  ],
     "y_labels" : [
                        {"label_name" : "", "url" : ""}  
                  ],
     "configuration":
              {
                    "is_mean_user_provided" : true,
                    "color_scheme": ["#a50026","#d73027","#f46d43","#fdae61","#fee08b","#ffffbf","#d9ef8b","#a6d96a","#66bd63","#1a9850","#006837"],
                    "svg-height" : "",
                    "svg-width" : "",
                    "bubble" : {
                        "min_radius" : "0", 
                        "max_radius" : "60"
                    },
                    "font_family" : "sans-serif",
                    "font_size" : "18px"
                },

   "content" :[
                  [ 
                      {
                        "weighted_mean_score" : 0,
                        "variance" : 100, 
                        "scores" :[
                                    {
                                      "score": 10, 
                                      "comment" : "", 
                                      "reviewer_name" : "Student2" 
                                     }
                          ]
                       }
                 ]
      ]
  }
 
 
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
  
  * <b><em>content</em></b>
    This denotes all the content to be visualized.
    It is a 3 dimensional array structure.
    The outer most dimension represents the students across all the criteria.
    The intermediate dimension represents the criteria. 
    And finally, the inner most dimension denotes the scores awarded by the reviewers to the given student. The input can either be the mean score & variance, ( i.e. if "is_mean_user_provided" is set to true), in which case, "weighted_mean_score" denotes the weighted mean for all scores and the "variance". On the other hand, if "is_mean_user_provided" is set to false, then an array of "scores" need to be provided, each element of the scores array, has the score value, the reviewer Id who has awarded the score and the comments, if any.
    
    
 
    
    
    
  
### References 
* https://d3js.org/
* https://github.com/PMSI-AlignAlytics/dimple/wiki
