SUMMARY:

I looked at loans in the Prosper data, only from 2014, to see if there was any apparent relationship between the interest rate (APR) and the purpose of the loan (Listing Category).  I produced two charts: (1) a circle chart showing the average APR for all loans in each category, to show the overall view, and (2) a scatterplot showing each loan, so that the viewer could get a feel for the variation of interest rates within each category.  I do not see any clear relationship between loan purpose and APR, and I find that the range of APRs within each category is larger than the differences in average APR among the various categories.

I made changes to these visualizations, based upon the feedback that I received.  I was  able to achieve some of these using dimple.js, and I was able to achieve the remainder using other data visualization tools (Excel, Minitab).


DESIGN:

> Initial Design:

Both of my charts were scatterplots, with the difference being that the Average chart was aggregated by average, while the intent of the Scatterplot was to have no aggregation at all (more on this below).  Because the scatterplot had many points, I made the circles translucent, in order to better visualize areas where few vs many circles overlapped.  I chose to keep the default display of many different colors, in order to have more contrast between neighboring points.

The animation was in the form of a mouse-over, enabling the viewer to determine the exact value for each data point.  Unfortunately, the default display rounded the data value on the Average chart to the nearest integer, while for the scatterplot it showed both a rounded and exact value.  I was not able to display solely the unrounded value, which does diminish the value of this animation.

I was not able to eliminate aggregation.  The web site https://github.com/PMSI-AlignAlytics/dimple/issues/80 states that one can avoid aggregation by putting an explicit list of the variable names (["Category","APR"]) as the first argument of the addSeries item.  However, it appeared that all loans with the exact same value of Category and APR were still being aggregated.  Without a series.aggregate statement, those values were aggregated by the default (count), which produced a meaningless chart.  Therefore, I aggregated by average.  The resulting scatterplot therefore showed a point for each unique value of API, instead of showing a point for each unique loan.  This is an area for follow-on investigation.

Another area for further investigation is the efficiency of this code.  The Average chart was displayed in a few seconds, but the Scatterplot took about 34 seconds to display its ~10,700 values.  It would be interesting to see how this process could be speeded up.


> Changes in Revised Design (achieved using dimple.js):

- changed y-axis label on both charts to be more descriptive, less jargon
- changed title on both charts to state a conclusion, or to otherwise guide the viewer
- changed Average chart from scatter (dot) plot to bar chart
- changed points on Scatterplot to be all the same color (I needed to adjust the opacity as well)

> Changes in Revised Design (not successful using dimple.js in the time frame for this project, but successful using other tools):

- font size of axis labels
- on x-axis, show actual category names instead of code number
- also show category name on mouseover
- ordering of categories on x-axis, in ascending order of APR, on both charts


> Further revisions, based on feedback from Udacity project evaluator:

The evaluator suggested showing the year-over-year trend in the distribution of interest rates, not just for a single year.  Although a bubble chart was suggested, I chose a scatterplot instead, because the planar variable of position is preferable to the retinal variables of size or area.  This graph still shows that there is not much variation in average interest rate among the categories, but it now shows this for several different years.  It also shows that there is a year-over-year change in overall rate.

The evaluator suggested that I get rid of the scatterplot, because it really did not effectively convey the distribution of interest rates.  However, the scatterplot did convey a sense of the number of loans in each category, so I changed the chart to concentrate on that aspect, now looking year-over-year.  I wanted to create a side-by-side bar chart, but the unstacked bar chart in dimple looked very similar to a scatterplot, so I stayed with a scatterplot.  It shows that Debt Consolidation dominates all other categories, with especially high loan volume in 2013.  It also shows that new categories showed up in 2011.

Other design features added in this iteration:
> Added a legend within the chart, although I still needed to retain the category-number-to-category-description key as a separate text element.
> Changed the colors for the various categories in order to highlight the new categories introduced in 2011.  Used translucency in order to view overlapping data points.
> Explicitly suggested to the viewer that they can use a mouseover to get specific values, if desired.

One drawback of introducing the multiple-year view: the charts now all take a very long time to load.  I have not been able to figure out how to make the dimple code more efficient.  Please be patient!


FEEDBACK RECEIVED:

> From Viewer #1:

·         What do you notice in the visualization?
I notice some categories have a bigger spread/more loans than others
I notice the interest rates are high! (A lot higher than a mortgage loan)
·         What questions do you have about the data?
What kind of company is Prosper LLC?
Since the rates are so varied over a range, what other factors could be the cause?  (amount, payback time, credit rating of the borrower, etc.)
·         What relationships do you notice?
The Baby category and RV categories have low rates – very different clientele!
·         What do you think is the main takeaway from this visualization?
Loans from prosper funding llc can be expensive
·         Is there something that you don’t understand in the graphic?
What do the different colors in chart 2 mean?
Is it just to see the differences among the points?

Comments on your first chart:  With the dots it is hard to see the APR per category at first glance.  Yes, you see that data in the mouseover, but it’s not in your first glance (I forget what they call that, how you can see highlighted things much faster than searching them out among everything).
It’s also hard to see the different categories as they are in a long list at the bottom and you have to map each number to category.  I don’t know if it’s any better or even possible to put the categories in the mouseover?  And maybe vary the shape or color of the point based on the category so you can eyeball the high/low categories? 
Also, perhaps a bar chart would be better because there’s no linear relationship between the different category numbers and plotting points you usually think the x direction has some relationship.
 
The averageAPR rates are very high considering the low interest rates in 2014
 
The comments for the second chart:  Do the colors have any significance?  Like amount of the loan? If so you should state that.  The pastels are pretty. 
Why do you have a rounded and non-rounded APR for each point?
One thing that is interesting is the number of loans per type.  You might want to play with the opacity setting to see the color get darker with higher density of loans.  Certain loans are less frequent or don’t have as big a spread.
 
I don’t really see a story in this – you might want to order the categories by average APR in order to make that more evident.

> From Viewer #2:

·         What do you notice in the visualization?
o   Initial glance on the 1st graph made me look for trends and additional data (loan amt/etc) might be key to tell a better story.
o   It made me look at the markers and the categories to tie them together which can be time consuming
·         What questions do you have about the data? 
o   I felt that I need to see # of loans (or even value of loan) per Interest rate
·         What relationships do you notice?
o   It’s difficult to quickly figure out the relationship and might be easier If both data are combined into one graph.
·         What do you think is the main takeaway from this visualization?
o   Not sure
·         Is there something that you don’t understand in the graphic?
o   It’s difficult to see the overall picture of the loan data.

Improvements:
1st graph
Actual category names on the x-axis instead of #s (or show actual name when mouse-over)
Sorted by values
Probably a bar graph instead of marker point
Probably add # of loans/value per Category as a secondary axis
 
2nd graph
Actual category names on the x-axis instead of #s (or show actual name when mouse-over)
Sorted by values
Instead of marker, probably a stacked bar with interest range. Or to keep it simple, box plot (to combine both graphs)

> From Viewer #3:

This viewer provided only verbal feedback.  She was not aware that APR stands for Annual Percentage Rate, and that this is the interest rate.  She saw the scatterplot as an indicator of loan volume, not interest-rate distribution.  She did not get the message that there was very little relationship between loan category and interest rate.


RESOURCES:

My main resource was the dimple wiki from PMSI-AlignAlytics at https://github.com/PMSI-AlignAlytics/dimple/wiki, supplemented by Google searches as needed.
