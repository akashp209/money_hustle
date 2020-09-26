---
title: 'The Man Who Solved The Market'
date: '2020-03-05'
---
![sloved the Market](https://miro.medium.com/max/1200/1*Mt09MFi-PIq7SHHHo618fg.jpeg)

Even the author, Gregory Zuckerman, was doubtful at first refusing to cash his advance until he believed the project was viable [2]. Gregory Zuckerman is a highly acclaimed journalist at the Wall Street Journal and author of other classics like ‘ The Greatest Trade Eve r’ and ‘ The Frackers ’. In this book, he turns his attention to Jim Simons, the mathematician, billionaire hedge fund manager, and philanthropist. Simons was the founder of Renaissance Technologies and architect of the Medallion Fund, the best performing fund in modern financial history. Not surprisingly Simons and Renaissance staff are renowned for their secrecy and very little has leaked out of the organisation over the past 30 years

However, many of the leading characters are approaching their later life and Zuckerman eventually persuaded many to contribute to an accurate account of Renaissance’s history for the record. The result is a fascinating read balancing the human story of the people involved whilst dropping tantalising hints as to how the Medallion Fund performed so spectacularly. He chronicles Jim’s career graduating from MIT, a PhD from Berkeley, a stint breaking codes for the IDA before teaching at MIT, at Harvard and eventually heading up the math department at Stony Brook University.

In 1978 Jim left academia to start Monemetrics and trade currencies. He struggled for 10 years and wasn’t going anywhere until he hired Elwyn Berlekamp, a professor of mathematics at Berkeley. Berlekamp rewrote the algorithms to trade short term patterns with sizing based on the opportunity. These changes delivered the first real success for the firm. In 1990, in its third year of operation, the Medallion fund achieved a 59% return. In 1993 he hired Bob Mercer and Peter Brown who were working on speech recognition and machine translation at IBM research. This partnership proved enduring and highly successful as they cracked the equities market and allowed the Medallion fund to scale to thousands of assets.

Jim was 50 before he had any success with Renaissance and 60 before managing to attract significant investment in the fund. His story is a lesson in resilience, persistence and self-belief. A classic illustration of how difficult it is to run a successful quant fund.

_**“ Work with the smartest people you can… be persistent… be guided by beauty…” — Jim Simons**_

## Performance
![performace](https://miro.medium.com/max/1000/1*L-u9QfKs5S5morv5Zu-bEg.png)
###### Figure 1: (a) the annual profit in comparison with the size of the fund. In most years, the profit is a significant fraction of the fund whilst in 2000, 2007 and 2008, the returns exceeded 100%. (b) The cumulative profit of the fund. The average fund size was $5.4 billion and was capped at $10 billion in later years. “There is beauty in things that work really well” — Jim Simons

The performance of Renaissance Technologies Medallion Fund is one of the wonders of the modern financial world. It is the technological equivalent of a licence to print money. For 30 years from 1988, the Medallion Fund averaged returns of 66% per annum . It has generated over $100 billion in profits despite the average fund size being a mere $4.5 billion. In itself, this performance is remarkable. What is even more astonishing is that 30 years is a long time for competitors to catch up. But they have not. They haven’t even come close.

Over the same period, the S&P 500 Index has gained 5.1% per annum. 90% of funds fail to match this modest index [3] — let alone reach the dizzy heights of Medallion. After a patchy couple of year at the start, the worst performing year was 1997 with a return of 32% . The best year was during the financial crisis of 2008 when Medallion achieved a return of 152% . Over the last 10 years up to 2018, Medallion has performed even better with average returns of 80% per annum .

## Data

_**“Renaissance had better data, older data, more sophisticated data and were better at dealing with it than anyone else” — Zuckerman**_

There are more factors that influence the market than we, as simple humans, are aware of. Statistical techniques can identify subtle and high-dimensional causal relationships between influential factors and inefficiencies in the market. Since the early days, Renaissance has been collecting and curating vast data archives of everything from economic metrics to the weather. The quantity and quality of this data are key in enabling the algorithms to discover subtle and undiscovered predictors of market patterns. Renaissance simply has better, older and more sophisticated data to drive their systems than their competitors. Boring but important!

## Machine Learning

_**“We’re right 50.75% of the time . . . but we’re 100% right 50.75% of the time. You can make billions that way.” — Bob Mercer**_

The fund took off when equities were introduced into the mix. Initially, the focus was on bonds, commodities and currencies. However, for the fund to grow, many more assets were required. Equities had proven difficult for the Renaissance quants to crack and early efforts were disappointing. With the addition of Mercer and Brown to the team, a brand new system was coded which was essentially a sophisticated version of statistical arbitrage. Subtle relationships between stocks were identified and the information used to predict future bias in the price movement. According to Zuckerman, this allowed them to correctly predict the direction of medium-term trades 50.75% of the time.

## Execution

_**“We understand risk, cost, impact and market structure well enough to leverage the hell out of it” — senior Renaissance staffer**_

With systems that are based on the repeated exploitation of very slight edges, the costs of trading are critical. Renaissance was very good at estimating the costs that would be incurred on a trade before placing it. This allowed them to make informed decisions on whether a slight market anomaly could be profitably exploited. Understanding the market liquidity constraints for the asset enabled calculation of the maximum size that could be traded without adversely impacting the trade. A confident prediction, predictable costs and high liquidity would enable Renaissance to maximise its size and leverage to profit from the opportunity.

## Volatility and Drawdown

![volatility](https://miro.medium.com/max/668/1*6wyLpHTF5fWSRms60K0E2A.png)
###### Figure 2: The impact of the number of assets on portfolio drawdown. [ A synthetic geometric Brownian motion for an asset. When run 1K times in a Monte Carlo simulation, 95% of drawdowns are -19% or less. With 100 assets, the drawdown metric is reduced to -2%. With 10K assets, 95% of drawdowns are -0.1% or less . Free lunches available here.

Diversifying into equities was a big break for Renaissance and allowed the fund to scale to its current cap of $10 billion. One key aspect of equities is the number of assets available. Zuckerman mentions that Renaissance may have 4,000 long and 4,000 short positions in equities at any one time [2]. Taking medium-term trades on such a massive number of assets has a profound effect on portfolio risk and drawdown. Figure 2 uses synthetic data to illustrates the dramatic impact of trading a large number of uncorrelated assets on portfolio volatility. Expansive diversification and a proven track record of accurate execution provided Renaissance with access to significant leverage from partners such as Deutsche Bank and Barclays.

## Access to Leverage

![leverage](https://miro.medium.com/max/1280/1*6p8_i3LpIkpd5BLg9N4xGA.png)
######Figure 3: a synthetic example of the effect of leverage and compounding returns — on a Log scale. (a) 30 years with an average daily return of 0.015% and no leverage (b) trading with assets valued at 5x the trading funds © with access to 10x leverage. Zuckerman estimates the average leverage available to Medallion was 12.5x.

Long-Term Capital Management (LTCM) is the textbook case of very clever people not being quite clever enough to understand risk. LTCM initially realised outstanding returns by using up to 25x leverage in their fund. However, a lack of understanding of the risks involved led to its calamitous demise. Renaissance, on the other hand, has demonstrated a degree of suspicion in their models and a deep appreciation of risk. They have architected a solution to utilise leverage whilst managing the risk.

The unleveraged returns of Medallion are underwhelming. The funds raison d’etre is supporting leverage and it is the leveraged performance which is legendary.

Figure 3 illustrates a synthetic example of a system returning 0.015% per day annualised for 30 years. With no leverage, the compound annual return is a modest 4%. However, the same system with access to 12.5x leverage generates a compound annual return of 60% . This is not about creating systems that maximise returns. This is about creating systems that maximise access to leverage whilst controlling risk.

_If there ever was a magic bullet, this is it._
![bullet](https://miro.medium.com/max/1200/1*zAvS7BNCJ9wsAwfBTSU_Sg.jpeg)

## The Big Secret

The Big Secret is that there is no Big Secret.

Medallion’s spectacular success is not down to one well-kept secret. The success is down to doing everything right. Zuckerman recons there are 20–25 aspects of Medallion’s operation at which they excel. Taken in their entirety, all these nuanced competencies add up to deliver a truly outstanding operation.

In summary, some of the key aspects that propel Medallion are:-

* **Data:** Renaissance has a huge amount of quality data on everything that could remotely influence price movements. They were one of the first to start curating data archives and are the most experienced at using them.

* **Machine Learning :** Renaissance applied their statistical learning algorithms very early on to identify predictive data and statistically significant repeating patterns in the market. Their early adoption of machine learning in the equities market has been key.

* **Diversification:** Medallion reputedly trades 8,000 assets long/short with a typical trade lasting about 2 days. Applying a medium-term market neutral approach to such a large asset base massively reduces volatility and drawdowns.

* **Liquidity Constraints:** Each asset is traded within its available liquidity constraints to enable Medallion to enter and exit the market without undue impact or risk.

* **Stealth:** Positions are entered and exited in ways that disguise their activity from the market.

* **Accurate Costings:** When the predictive edge is slight, having an accurate estimate of the costs improves the identification of opportunities that can be profitably traded.

* **Dynamic Sizing:** Leverage up when opportunities abound. Reduce exposure when performance plummets . All models are wrong — but some can be useful.

* **Leverage :** All the above best practices underpin access to significant leverage. Zuckerman estimates Medallion trades with 12.5x leverage on average — with up to 20x leverage accessible when the system is confident in the opportunities. The historical unleveraged returns from Medallion are similar to the S&P 500 Index. The leveraged performance, however, is legendary.

## References

1. **The Man Who Solved the Market** Gregory Zuckerman, ISBN: 9780241422151
2. Chat with traders podcast, [183: Jim Simons — the pinnacle of trading greatness w/ Gregory Zuckerman!](https://chatwithtraders.com/ep-183-gregory-zuckerman/)
