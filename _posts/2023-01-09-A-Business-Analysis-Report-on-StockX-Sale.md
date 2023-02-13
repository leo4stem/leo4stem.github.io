## Introduction  
I am a sneaker seller. StockX is one of the selling platform I usually use. I am interested in how to maximize my profits and what factors affect profits.

## Data and Report  
The data in this sheet consist of a random sample of all U.S. Off-White x Nike and Yeezy 350 sales from between 9/1/2017 and 2/13/2019. The sample consists of a random, fixed percentage of StockX sales for each colorway, on each day, since September 2017. The data include eight variables: order date, brand, sneaker name, sale price, retail price, release date, shoe size, and buyer region (the state the buyer shipped to). The sample was limited to US sales only.  

The data can be downloaded from StockX Sneaker Data Contest hold by [Kaggle](https://www.kaggle.com/datasets/hudsonstuck/stockx-data-contest).

The full analysis report I made is [here](/_pages/StockX_v01_Leo.html).


## Findings  
### Brand
According to the data, Off-White has the highest mean profit, followed by Yeezy. Off-White records profit margins way higher than any other brand, including Yeezy. This is likely due to the highly limited stock of their shoes and also the amount of "hype" behind them. The amount of sales of Off-White shoes is not even half of the amount of sales from Yeezy shoes, yet they still generate on average over $350 more profit than Yeezys. This shows that the hype and limited stock are whats driving Off-White to be the most profitable brand.

I list the data table in my analysis [report](/_pages/StockX_v01_Leo.html).  

### Sneaker 
This data shows that the more transactions a shoe has the less profit the shoe generates. According to the data, the Adidas Yeezy Boost 350 V2 Butter had over 11,000 sales, however, the shoe only generated a mean profit of $49.76. While the Adidas Yeezy Boost 350 Low Turtledove only had 68 sales but generated a mean profit of over 1,300 dollars per shoe. This shows that less transactions means that there is more limited stock of the shoe which drives up the price.

I list the data table in my analysis [report](/_pages/StockX_v01_Leo.html).  

### Order Month  
The data shows that December, November, and January have the highest number of sales. This makes sense because that is when holiday season is. The lowest amount of sales come from the month of March. This could be due the fact that there are no major holidays or events in March, so there is no incentive to buy expensive shoes. Lower profit margins tend to be in December and November. This could be the result of sellers wanting to move all their inventory during holiday season because that is when there are the most buyers. The largest profit margins are recorded in March. This is because not as many shoes are being sold in March, so the stock is more limited, leading to the prices rising.

![](/assets/images/StockX_relation_btw_profit_omonth.png)  

### Release Month  
The majority of transactions occur during November and December. The least number of transactions occur during August and September. This could be due to the fact that there are more releases during the holiday season. The months with the most profit happen to be August and September. Due to the decrease in the number of releases during those months, the prices rise.November and December are among the months with the lowest mean profit. This could be due to the increased amount of releases that drive the prices of shoes down.

![](/assets/images/StockX_relation_btw_profit_rmonth.png)  
 
### Size  
According to the data, size 9.5 to 11 sell the most, while sizes 3.5, 17, and 16 sell the least. This is because the majority of people are sizes 9.5 to 11, while only a few people are have super big feet or super small feet so 3.5, 16, and 17 don't really sell. The shoe sizes with the least profit are sizes 4 to 5, while the sizes generating the most profit are sizes 16 and 17. This is likely due to the increased demand of really big sizes, but not much are being produced. While sizes 4 through 5 are also in demand, they are more mass produced than sizes 16 and 17. As a result, the prices for sizes 4 through 5 are not as high.

![](/assets/images/StockX_relation_btw_profit_size.png)  

### Number of Weeks to Keep 
Most transactions occur right after the shoe is released. This is because everybody wants the new shoe when it comes out. As a result, most sales happen between 0 and 2 weeks within the release date.

![](/assets/images/StockX_relation_btw_profit_weeks.png)  

### Number of Days to Keep Sneakers  
The graph mostly supports the idea that the longer shoe is kept, the more profit is generated. The line of best fit has a positive slope, showing that the longer a shoe is kept, the more profit is generated. Of course this is not always the case, but generally speaking, Yeezys and Off-Whites appreciate over time. 

![](/assets/images/StockX_relation_btw_profit_days.png)  

## What factors affect profits?  
This graph shows bi-relationships between the factors. Blue means positive relationship, while orange means negative relationship. In addition, circle size shows the magnitude of the relationship. A great profits is associated with a great sale price and a low retail price. But it seems not related to shoe size and time to keep.  

![](/assets/images/StockX_relation_btw_profit_allfactor.png)  



