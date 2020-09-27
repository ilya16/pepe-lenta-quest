# Personalized in-app tasks based on the user retail transaction data

> Solution produced during "Lenta Hackathon" as part of the "Hack Lab" course in Skotech, September 18-20, 2020
>
> Team PEPEtoners: [Ilya Borovik](https://github.com/ilya16), [Vladislav Kniazev](https://github.com/Vladoskn), [Vanessa Skliarova](https://github.com/Vanessik), [Bulat Khabibullin](https://github.com/MrWag2), and [Zakhar Pichugin](https://github.com/zakharpichugin)

[Solution and demonstration](demo.ipynb): [![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ilya16/pepe-lenta-quest/blob/master/demo.ipynb)

## Problem statement

Current system of personalized recommendations in Lenta app:
* Complicated system of special offers: personal offers in the app + general offers in SMS + surprize cards in the stores
* No possibility to affect on special offers

## Concept

The solution is a symbiosis of two pillars:
* Personalized tasks based on the history of transactions for engaging customers
  * tasks based on previously bought and novel products
  * tasks in different product categories
* A system of achievements with rewards and bonuses
  * category based
  * product based
  * location based
  
Task personalization is provided by a multilayer recommendation system working with the following levels of item granularity in transaction data:
* `material`s (products)
* `hier_level_2` categories
* `hier_level_3` categories
* `hier_level_4` categories
* `vendor`s

Each model is a Collaborative Filtering for implicit feedback datasets based on Alternating Least Squares.

Using multiple models we can offer personalized recommendations with various levels of product description: from raw products and their properties to vendors and categories.

See [demo](demo.ipynb) for more details. The business side of the solution is shortly presented in the [video]().

### Tasks 
Example tasks shown in the [demo](demo.ipynb):
* *Buy and rate*: recommending known or previously bought products to buy and rate them in the app
* *Fan of Lenta's goods*: recommending to buy Lenta's products
* *New vendor*: recommending to buy goods of several vendors
* *Diversity in category*: recommending to buy goods from one of the most likeable categories
* *Diverse Basket*: filling your cart with products from at least 7/10 previously bought (or 1/2 novel) `hier_level_2` categories.

## Achievements
Example achievements shown in the [demo](demo.ipynb):
* *Krusenstern*: visit more than 3 Lenta stores
* *PartyGoer*: buy alcohol on more than 10000 rubles
* *Sweet Tooth*: buy sweets on >500 rubles
* *Greta Thunberg*: buy 10 reusable bags
* *Milk King*: buy all brands of Milk
* *Lucky Devil*: buy products with discounts 300 times
* *Loyal Customer*: buy something in Lenta 4 weeks in a row
