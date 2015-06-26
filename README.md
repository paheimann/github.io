SUMMARY:

I looked at loans in the Prosper data, only from 2014, focusing on the relationship between the interest rate (APR) and the purpose of the loan (Listing Category).  I wanted to see if there was any apparent relationship.  I produced two charts: (1) a circle chart showing the average APR for all loans in each category, to show the overall view, and (2) a scatterplot showing each loan, so that the viewer could get a feel for the variation of interest rates within each category.


DESIGN:

Both of my charts were scatterplots, with the difference being that the Average chart was aggregated by average, while the intent of the Scatterplot was to have no aggregation at all (more on this below).  Because the scatterplot had many points, I made the circles translucent, in order to better visual areas where few vs many circles overlapped.

I was not able to eliminate aggregation.  According to https://github.com/PMSI-AlignAlytics/dimple/issues/80, one can avoid aggregation by putting an explicit list of the variable names (["Category","APR"]) as the first argument of the addSeries item.  However, it appeared that all loans with the same value of Category and APR were still aggregated.  Without a series.aggregate statement, those values were aggregated by the default count, which produced a meaningless chart.  Therefore, I aggregated by average.  The resulting scatterplot therefore showed a point for each unique value of API, instead of showing a point for each unique loan.  This is an area for follow-on investigation.

Another area for further investigation is the efficiency of this code.  The Average chart was displayed in a few seconds, but the Scatterplot took about 34 seconds to display its ~10,700 values.  It would be interesting to see how this process could be speeded up.


FEEDBACK:


RESOURCES:

My main resource was the dimple wiki from PMSI-AlignAlytics at https://github.com/PMSI-AlignAlytics/dimple/wiki, supplemented by Google searches as needed.