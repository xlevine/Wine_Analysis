# An analysis of wines sold in France on Vivino.com (2020)

## Goal

**For a desired price range and wine robe (e.g. red, white), which characteristics (Region, Year, Name) are most auspicious for choosing a well-rated wine bottle?**

## Production and Consumption of Wines in France

- In 2017 in France, there were 46,600 vineyards producing AOP (Appellation d’Origine Contrôlée) wines, which covered 446,588 ha of land (Agrimer 2018).

- AOP represents ⅔ of all wine produced in France; About 60% of all wines produced in France are consumed there (Agrimer 2018).

- A french person drinks about 45 liters of wine per year on average today (eq. to about 60 standard size bottles), made of 52% red, 31% rosé, and 17% (still or sparkling) white (Vinexpo/IWSR 2020).

- Wine production in 2017 generated over 11,2bn euros, i.e. about 16 % of the total value of french agriculture (Agrimer 2018).

![Image description](https://github.com/xlevine/Wine_Analysis/blob/master/plots/carte_vin_france_petit.jpg)

- Main regions of AOP production: (1) Alsace, (2) Bordeaux, (4) Bourgogne, (6) Champagne, (9) Languedoc-Roussillon, (12) Provence, (11) Val de Loire, (14) Vallée du Rhône

## Database and methodology

- Vivino.com is an online marketplace and rating app for wine founded in 2010 and headquartered in San Francisco.

- Its database contains more than 10 million wines (Wikipedia).

![Image description](https://github.com/xlevine/Wine_Analysis/blob/master/plots/Vivino_screen.png)

Using a web scraping tool (Selenium) compatible with Python3, we extract the following data:

- Country, Region, and Estate name

- Robe (red, still white, sparkling white, rosé) & Vintage (year)

- Ratings (1 to 5 scale) & number of reviews

- Price of sale

For more details on how the data was scrapped, please refer to script [web_scrapping.py](https://github.com/xlevine/Wine_Analysis/blob/master/web_scraping.py)

## Selection Criteria: 

(a) Items produced and sold in France, (b) cheaper than 100 euros, and (c) reviewed by at least 20 people. Red and white (non-sparkling) wines were analyzed separately. Combining all criteria give **13729 red** and **5207 white** wines.

For more details on how the data was analyzed, please refer to script [vin_analysis.py](https://github.com/xlevine/Wine_Analysis/blob/master/vin_analysis.py)

## Price by Robe

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/price_hist_red_FR.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/price_hist_white_FR.png" width="400">

Probability distribution function (PDF) of the sale price for (L) red and (R) white wines. Data is shown in an histogram with uniform bin size of 2 euros (black line), and by its Gaussian kernel density estimation [KDE] (orange line). Histogram and KDE are normalized such that all probabilities sum to 1 when integrating over the 0-100 euros price range. 

## Price by Regions and Robe

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/Price_density_red_Francia.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/Price_density_white_Francia.png" width="400">

PDF of the sale price for (L) red and (R) white wines, for each region of AOP production. The legend shows the percentage of wines coming from each region for each robe; the percentage of wine coming from all 5 regions with respect to all AOP wines of the same robe is shown in each panel's title. 

## Ratings by Regions and Robe

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_density_red_Francia.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_density_white_Francia.png" width="400">

Probability distribution function (PDF) for the Ratings for (L) red and (R) white wines. Ratings is on a scale of 1 (poor) to 5 (excellent). Same graphical conventions as previous figure apply. 

## Vintage by Regions and Robe

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/Year_density_red_Francia.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/Year_density_white_Francia.png" width="400">

PDF of the Vintage (year of production) for (L) red and (R) white wines. Same graphical conventions as previous figure apply.

## Rating vs. Price by Robe

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_vs_Price_red_FR.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_vs_Price_white_FR.png" width="400">

Ratings vs. price for (L) red and (R) white wines; each dot is one item. The average (red line), median (magenta line), and the 95% enveloppe of all ratings (blue lines) are shown as a function of the price. 

## Quality by Regions and Price Range

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_prob_median_red_FR.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_prob_median_white_FR.png" width="400">

Likelihood of a (L) red or (R) white wine from each region being better rated than the average among its peers in 4 different price range: 5 to 15 euros, 15 to 25, 25 to 35, 35 to 45 euros. A 95% confidence interval on the Likelihood estimate is shown for each region and price range.       

## Variability in Quality explained by its main Predictors

<img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_predictors_red_FR.png" width="400"><img src="https://github.com/xlevine/Wine_Analysis/blob/master/plots/ratings_predictors_white_FR.png" width="400">

Fraction of variance in the item ratings for (L) red and (R) white wines explained by its 3 main predictors (Vintage Year, Province, and Price) in 4 different price range: 5 to 15 euros, 15 to 25, 25 to 35, 35 to 45 euros.
