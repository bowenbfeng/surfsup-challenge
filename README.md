# SurfsUp Challenge

## Overview of the Analysis

In this project, we have analyzed the weather data hawaii.sqlite through SQLAlchemy, including two major measurements, temperatures and the precipitations from 2010 to 2017. We have queried the data from June and December and summarized the differences. 

## Results

Below is the summary statistics of the temperatures in June. 

![](/Resources/temps_june.png)

Below is the summary statistics of the temperatures in December. 

![](/Resources/temps_december.png)

We are able to draw the following conclusions based on the results. 

- Naturally, the temperatures, no matter the mean, min, or max, in June are higher than those in December. 
- Naturally, the quartiles of June temperatues are higher than those of December temperatures. 
- The range of December temperatures (27 °F) is wider than that of June temperatures (21 °F). The standard deviation of December temperatures (3.75 °F) is higher than that of June temperatures (3.26 °F). 

## Summary

Through the analysis of the weather data in hawaii.sqlite via SQLAlchemy in Jupyter Notebook, we have found out that the temperature statistics of June are basically higher than those of December, as expected. In addition, the dispersion of December temperatures is larger than that of June temperatures. 

Apart from that, we have created two additional queries to pull the precipitation data for further analysis. 

Below shows the query to gather the data of the precipitation in June. 

```
results = session.query(Measurement.prcp).filter(extract("month", Measurement.date) == 6).all()
june_precipitation = list(np.ravel(results))
df_june_precipitation = pd.DataFrame(june_precipitation, columns=["June Precipitation"])
df_june_precipitation.describe()
```

Below shows the results of the precipitation in June. 

![](/Resources/precipitation_june.png)

Below shows the query to gather the data of the precipitation in December. 

```
results = session.query(Measurement.prcp).filter(extract("month", Measurement.date) == 12).all()
december_precipitation = list(np.ravel(results))
df_december_precipitation = pd.DataFrame(december_precipitation, columns=["June Precipitation"])
df_december_precipitation.describe()
```

Below shows the results of the precipitation in December. 

![](/Resources/precipitation_december.png)

As can be concluded from the analysis that the precipitations in June are generally higher than those in December, which also makes sense. The maximum precipitations and quartiles in June are all higher than those in December. As a matter of dispersion, the range and the standard deviation of the precipitations in June are higher than those in December. 
