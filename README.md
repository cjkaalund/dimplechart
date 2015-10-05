#Summary
In no more than 4 sentences, briefly introduce your data visualization and add any context that can help readers understand it.

This visualization is a scatterplot presenting flight delay data from http://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp. The average delay, which is the delay divided by the total number of flights for a given delay reason, is plotted against the total number of flights for that delay reason. Each point represents a different airport, with average delay additionally averaged over the 12 months of 2014 and the total number of flights summed over the same 12 months. An interactive legend enables different carriers to be selected or deselected, and different failure reasons can be chosen from a pull-down menu.
Design
Explain any design choices you made including changes to the visualization after collecting feedback.

Initially I produced a stacked barchart, but then realized that it was not explanatory (did not show a trend or relationship) as the project requires. I then chose to produce a scatterplot of the data, as it was the most appropriate chart for showing a relationship between the flight delay and flight count variables. This relationship was found after doing EDA in R. R was also used to pre-process the data to calculate an average delay (divide total delay by the number of flights for a particular airport and month) and reshape the data for plotting with dimplejs. This reshaped data is in a file called 2014_airline_delay_ct_reshaped.csv.

The average flight delay was plotted on the Y-axis, as it is the dependent variable. I aggregated the data over month, as plotting each single point required a large data file and slowed down the visualization significantly. There are a large number of airports, too large for a legend. I decided to colour-code each point according to carrier and use a legend to show this encoding. Each point on the plot represents a different airport.

The scatterplots for different delay reasons are quite different from each other, and so it does not make sense for these plots to overlap.  Therefore, a drop down menu to enable choice of failure reasons was added to the top of the page. The default option of “Select reason for delay” explains the purpose of this menu to the viewer. The title of the chart changes to indicate the new failure reason when a choice is made from this menu.

The scales of the X and Y axes were fixed, so that when the viewer chooses a different failure reason the change in the distributions of points in the scatterplots is apparent, although this does not always make the best use of the chart area. The default dimplejs option is for the axes to rescale, however this rescaling may not be immediately obvious when the viewer selects a different delay reason, and can hide the changes in the scatterplots.

A log scale was chosen for the X axis, as the flight count varies over a wide range. A log scale was also chosen for Y, as this helps separate out the distributions of flight delay between different carriers. Unfortunately, the maximum in the y-scale could not be set to 500; dimplejs always rounded it up to 1000, which is not optimal.

The first reviewer of my chart pointed out that there is considerable overlap of the scatter points of different carriers, and so making comparisons between particular carriers can be difficult. The legend was therefore made interactive, and so carriers can be selected or deselected in order to make comparisons easier. There is a title for the legend to show the viewer that this legend is interactive. I later made it easier to select single or multiple carriers using CTRL-click and SHIFT-click.

The first reviewer also did not understand what ‘Average delay’ (the initial y-axis title) was, and so I changed this title to be ‘Arrival delay’ and added an explanatory note about averaging at the bottom of the chart. I also added a short explanation of the x-axis.

##Versions:
* original_index.html - (scatter7) - uploaded and presented to first reviewer
* index1.html - (scatter8) added a note explaining the axes – modified after feedback from the first reviewer
* index2.html - (scatter9) changed colour scheme of legend to make airlines more easily distinguishable
* index3.html - (scatter10) add CTRL-click, SHIFT-click to legend. Changed following discussion with the second reviewer
* final_index.html - (scatter11) final version, after receiving feedback from the third reviewer. I added text and increased the font sizes and changed text colour to highlight the interactivity of the legend and the pull-down menu

#Feedback
##First reviewer - Sara
Q1. What do you notice in the visualisation?

*I noticed a graphic which tells me which airline has more number of flights and the possibility of the arrival delays.*

Q2. What do you notice in the visualisation?

*The data interface is not very clear. It's intensive and hardly pick up a single one.*

Q3. What do you notice in the visualisation?

*I noticed the relationship between the number of flights and the possibility of delays of each airline.*

Q4. If I want to avoid delays, I will choose the airline which has less chance of delays.

Q5. What do you notice in the visualisation?

*I can understand it easily.*

In a subsequent discussion with this reviewer I found that they did not really understand the axes, and so I added notes at the bottom of the graphic explaining these axes.
##Second reviewer - Ben
Q1. What do you notice in the visualisation?

*The chart shows a variation of flight arrival delay for all American airliners in 2014. It is noticed that none of flight arrivals delayed more than 200 minutes and the minimum arrival delay was about 20 minutes. It appears that Envoy Air performed the best, with the least delays and the best consistency.*

Q2. What questions do you have about the data?

Q3. What relationships or trends do you notice?

*It tends to become constant for most airliners when flight numbers increased.*

Q4. What do you think is the main takeaway from this visualisation?

*Flight arrival delay is a common in USA whatever airliner a customer uses.*

Q5. Is there something you don’t understand in the graphic?

In a subsequent discussion with this reviewer, he mentioned that the data was very cluttered (i.e. many overlapping data points, too many airlines). The first reviewer mentioned the same. To address this, I improved the interactivity of the legend, adding CTRL/CMD-click to enable easy selection of one or more airlines.
##Third reviewer - Alex
Q1. What do you notice in the visualisation?

*The graph show the quantity of flights with the different delay times. That it’s a very heavy cluster. The weather is a contributing factor to delays. It’s not a normal scale. It appears that the overall quantities are similar between carriers, but some are experiencing longer delays.*

Q2. What questions do you have about the data?

*There is a lot of data in the graph. Maybe the data could be displayed better, much wider and higher. Some colours appear too similar. Different colours and symbols to help separate.*

Q3. What relationships do you notice?

*As the number of flights increase, delays get higher.*

Q4. What do you think is the main takeaway from this visualisation?

*There are many airlines and delay is different for different airlines.*

Q5. Is there something you don’t understand in the graphic?

*Not particularly. The axes are easily identified.*

In a subsequent discussion with this reviewer, he mentioned that he did not find the pull-down menu at the top of the screen. Also, he suggested using symbols in addition to colours to distinguish the different airlines. Given that there are many data points and that these points must be small, I decided not to add different symbols. To highlight the interactivity of the legend, I increased the size of the text above the legend explaining how to use it. Selecting different carriers using the legend helps with the problem of clutter.

The main issues were that the interactivity of the legend and the presence of the pull-down menu were not obvious, and so the reviewers missed many features that were present in the data.

For the final version of the graph, I put some extra text above the pull-down menu to highlight its presence. I considered these changes to the pull-down menu:

1.	Highlight the presence of the pull-down menu using text.
2.	Replace it with a row of buttons for selecting delay reasons.  This is not a bad option, as the viewer can see all delay reasons at once. It would, however, be a little confusing, as it would look like a second legend.
3.	Replace it with some arrows at the bottom of the screen enabling the viewer to move between delay reasons. This option is less flexible, as the viewer cannot jump from one reason to any other one.

In the end, I decided to stay with the pull-down menu, but to highlight it with text to make its presence known.  I made the text blue so that it stands out more. The first reviewer agreed with me that the menu was more visible.
##Resources
  * http://stat-computing.org/dataexpo/2009/the-data.html
  * http://www.transtats.bts.gov/OT_Delay/OT_DelayCause1.asp
  * http://www.transtats.bts.gov/Fields.asp?Table_ID=236
  * http://www.rita.dot.gov/bts/help/aviation/html/understanding.html#q4
  * http://dimplejs.org/examples_index.html
  * http://dimplejs.org/examples_viewer.html?id=bars_vertical_stacked_100pct
  * http://dimplejs.org/advanced_examples_viewer.html?id=advanced_interactive_legends
  * http://dimplejs.org/advanced_examples_viewer.html?id=advanced_storyboard_control
  * http://dimplejs.org/advanced_examples_viewer.html?id=advanced_bar_labels
  * http://dimplejs.org/examples_viewer.html?id=scatter_standard
  * http://www.w3schools.com/cssref/pr_font_font-size.asp
  * http://stackoverflow.com/questions/23810128/wrong-result-in-dimplejs-scatterplot
  * https://github.com/PMSI-AlignAlytics/dimple/wiki/dimple.chart#addSeries
  * https://github.com/PMSI-AlignAlytics/dimple/wiki/dimple.storyboard
  * https://github.com/PMSI-AlignAlytics/dimple/wiki/dimple.eventArgs
  * https://github.com/PMSI-AlignAlytics/dimple/wiki/dimple.chart
  * http://thecodingtutorials.blogspot.com.au/2012/08/using-multi-column-data-with-d3-part-1.html
  * https://github.com/mbostock/d3/wiki/Gallery
  * http://christopheviau.com/d3list/
  * http://mikemcdearmon.com/portfolio/techposts/charting-libraries-using-d3
  * http://annapawlicka.com/pretty-charts-with-dimple-js/
  * http://blog.visual.ly/creating-animations-and-transitions-with-d3-js/
  * http://jsfiddle.net/nf57j/27/
  * http://stackoverflow.com/questions/23530434/in-dimple-how-do-you-change-the-order-of-the-series-ina-legend
  * http://stackoverflow.com/questions/26145982/change-chart-type-in-dimple-js-to-automate-chart-production
  * http://www.w3schools.com/cssref/css_selectors.asp
  * https://github.com/PMSI-AlignAlytics/dimple/wiki/dimple.chart#addLegend
  * https://leanpub.com/D3-Tips-and-Tricks/read
  * https://leanpub.com/D3-Tips-and-Tricks
  * http://stackoverflow.com/questions/23291200/dimple-js-how-can-i-change-the-labels-of-a-chart-axis-without-changing-the-data
  * http://stackoverflow.com/questions/25774821/dimple-js-axis-labels
  * http://stackoverflow.com/questions/20477224/removing-svg-text-elements-with-d3-js
  * http://cdn.oreillystatic.com/en/assets/1/event/91/D3_js%20tutorial%20Presentation.pdf
  * http://stackoverflow.com/questions/19387898/how-to-assign-unique-id-to-svg-text-element-in-d3-javascript
  * http://stackoverflow.com/questions/11903709/adding-drop-down-menu-using-d3-js
  * http://codekea.com/B7jlBrEGwAOo/finding-the-user-selected-options-from-a-multiple-drop-down-menu-using-d3.html
  * http://stackoverflow.com/questions/16805684/javascript-disable-text-select
  * http://fiddle.jshell.net/7KJC7/2/


