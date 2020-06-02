# Machine Learning Library
Custom functions that interact with Python libraries to streamline data cleaning, feature engineering, etc. for machine learning tasks.

## Dataset
A csv file of 50,000 wines from Argentina, Australia, Chile, France, Germany, Italy, New Zealand, Portugal, South Africa, Spain, and USA.
Data points include wine name, country, region, subregion, appellation, vineyard, grape, score, popularity, and price. Food suggestion, style, ABV, and wine notes will be added later. The complete location for a wine is Country-Region-Subregion-Appellation-Vineyard. Some wines (because of how they were scraped) are listed directly under Region, Subregion, or Appellation, with none of the subsequent sublocations included in that data point.

```Python
wine_df = pd.read_csv('../WineData.csv')
wine_df[11445:11462]
```

<p align="center">
  <img src="/Git_0_InitialDF.jpg">
</p>

```Python
wine_df["Popularity"] = pd.to_numeric(wine_df["Popularity"].str[:-2].str.replace(",",""))
wine_df[11445:11462]
```

<p align="center">
  <img src="/Git_1_Popularity.jpg">
</p>

```Python
wine_df["PriceBucket"] = bucket(wine_df, "Price", [0, 5, 10, 15, 20, 30, 50, 100, 200, 100000], ["Extreme Value", "Value", "Popular Premium", "Premium", "Super Premium", "Ultra Premium", "Luxury", "Super Luxury", "Icon"])
wine_df[11445:11462]
```

<p align="center">
  <img src="/Git_1_Bucket.jpg">
</p>
