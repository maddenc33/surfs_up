# surfs_up

#### Christopher Madden

---


## Software

- Python 3.9.7

- Jupyter Notebook 6.4.5

- VS Code 1.66.2

- Anaconda 4.12.0

  -  conda-build version : 3.21.6

---

## Purpose

The purpose of the analysis is to determine if an ice cream shop business in Oahu could be profitable year round by comparing data from June and December.

## Analysis

Using a flask application, I gathered statistical data as shown below:

```python

def stats(start=None, end=None):
    sel = [func.min(Measurement.tobs), func.avg(Measurement.tobs), func.max(Measurement.tobs)]

    if not end:
        results = session.query(*sel).\
            filter(Measurement.date >= start).all()
        temps = list(np.ravel(results))
        return jsonify(temps)

    results = session.query(*sel).\
        filter(Measurement.date >= start).\
        filter(Measurement.date <= end).all()
    temps = list(np.ravel(results))
    return jsonify(temps)

```

Here are images of the resulting summary statistics:

![June Stats](https://github.com/maddenc33/surfs_up/blob/main/analysis/june_stats.png?raw=true)

![December Stats](https://github.com/maddenc33/surfs_up/blob/main/analysis/dec_stats.png?raw=true)

The three key differences in weather between June and December:

  1. Average temperatures between June and December are 75 and 71 degrees respectively.  There is little variation year-round in overall temperature.

  2. Maximum temperatures between June and December, 85 and 83, also demonstrate stable temperature patterns throughout the year.

  3. The coldest temperatures experienced are the minimum temperatures in December, which may not be good for ice cream sales.  December also has the highest standard deviation of temperatures, so probably the most unpredictable weather.

In summary, the temperature data seems to support the prospect of opening a successful shop in Oahu.

I would recommend two additional queries: 
  1. Examinine precipitation data as .  Although temperatures in the Oahu climate are relatively stable, perhaps there is a rainy season and a dry season.
  2. Examine tourist flow throughout the year.  Perhaps there are slower and busier seasons.

An additional recommendation would be to gather monthly data and examine all twelve months of the year for a more detailed analysis.

---

