# Pandas_personalNotes

I recommend this short course introduction [Kaggle: learn Pandas](https://www.kaggle.com/learn/pandas)

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