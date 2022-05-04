# Pandas_personalNotes

I recommend this short course introduction [Kaggle: learn Pandas](https://www.kaggle.com/learn/pandas), most of the code snippets are taken as personal reminder from there.

There is a similarity with numpy arrays. The main objects of this module Pandas are:
* panda.Series
* panda.DataFrames

The main different from numpy arrays, is now we are working with dictionaries instead of list.

``` python
pd.DataFrame({'Bob': ['I liked it.', 'It was awful.'], 
              'Sue': ['Pretty good.', 'Bland.']},
             index=['Product A', 'Product B'])
```

``` python
pd.Series([30, 35, 40], index=['2015 Sales', '2016 Sales', '2017 Sales'], name='Product A')
```

---

You could access to `DataFrame` with; "dot notation", `reviews.country` ; or "dictionary notation", `reviews['country']`. The last is preferect when the columns name has spaces and you can't use it in dot notation `reviews.country LA` vs `reviews["country LA"]`.

## indexing
When you call a column `reviews['country'][0]`, it works as a panda.Series, which can be called as a list.

### pd.iloc vs pd.loc

# Conditional selection
``` python
reviews.country == 'Italy'
reviews.loc[reviews.country == 'Italy']
reviews.loc[(reviews.country == 'Italy') & (reviews.points >= 90)]
reviews.loc[reviews.country.isin(['Italy', 'France'])]
reviews.loc[reviews.price.notnull()]
```

# Summary
``` python
reviews.points.describe()

reviews.points.mean()
reviews.points.map(lambda p: p - review_points_mean)

reviews.taster_name.value_counts()

def remean_points(row):
    row.points = row.points - review_points_mean
    return row

reviews.apply(remean_points, axis='columns')

reviews.head(5)
reviews.tail(5)

reviews.country + " - " + reviews.region_1
```

# groups
``` python
reviews.groupby('points').points.count()
reviews.groupby('points').price.min()
reviews.groupby('winery').apply(lambda df: df.title.iloc[0])
reviews.groupby(['country', 'province']).apply(lambda df: df.loc[df.points.idxmax()])
reviews.groupby(['country']).price.agg([len, min, max])
```
