# Data Visualization for Peer Graded Systems

## Bubble Charts

## Libraries Used
* dimple.js
* d3.js

## JSON Structure

1. Bubble Chart for Student v/s Criteria with means and variance
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
  '''
  
  * <em>x_label</em> denotes the entity represented on the x-axis, its label being specified by 'label_name' and the URL is given by 'url'. Upon clicking this URL link the user is redirected to another visualization of, say, Scores received on that particular criterion by different students for each stage of submission of an assignment. 
  
  
  * <em>y_label</em> denotes the entity represented on the x-axis, its label being specified by 'label_name' and the URL is given by 'url'.
  
  * <em>configuration</em> denotes all the kinds of settings that the user is allowed to configure. This includes the 
  ** <em>color_scheme</em>, the color code used to display variation from good to bad.
  ** <em>svg-height</em> denotes the height of the page, in pixels, take up by the visualization.
  ** <em>svg-width</em> denotes the width of the page, in pixels, take up by the visualization.
  ** <em>font-family</em> denotes the font family used to display the labels and text in the visualization.
  ** <em>font-size</em> denotes the size of the font used to display the labels and text in the visualization.
  ** <em>bubble</em> has the display configuration for bubble in the bubble chart, w.r.t. its minimum and maximum radius.
  ** <em>is_mean_user_provided</em> it is a flag to specify if the input given to the visualization are individual scores ( whose mean and variance are calculated programtically), or if the user provides mean scores and variance. Note that, here the mean can be a weighted means, calculated as per some algorithm.
  
  * <em>content</em>
    This denotes all the content to be visualized.
    It is a 3 dimensional array structure.
    The outer most dimension represents the students across all the criteria.
    The intermediate dimension represents the criteria. 
    And finally, the inner most dimension denotes the scores awarded by the reviewers to the given student. The input can either be the mean score & variance, ( i.e. if "is_mean_user_provided" is set to true), in which case, "weighted_mean_score" denotes the weighted mean for all scores and the "variance". On the other hand, if "is_mean_user_provided" is set to false, then an array of "scores" need to be provided, each element of the scores array, has the score value, the reviewer Id who has awarded the score and the comments, if any.
    
    
 --- The bubble chart can be used to represent 4 dimensions, x-axis, y-axis, color of the bubble and the size of the bubble.
    
    
    
  
### References 
* https://d3js.org/
* https://github.com/PMSI-AlignAlytics/dimple/wiki
