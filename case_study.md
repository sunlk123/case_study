case\_study
================
Lorraine Kwok
October 8, 2019

## case study

``` r
library(p8105.datasets)
data("nyc_airbnb")
```

## Questions

  - how are airbnb prices related to rent in the neighborhood?
  - which neighborhood is most expensive and which is cheapest?
  - do hosts with multiple sites have higher prices or ratings?
  - does price have any relation to ratings?
  - is average length of stay related to neighborhood? price? etc?

## Does price have any relation to ratings?

``` r
nyc_airbnb_price_rate = 
  nyc_airbnb %>%
  mutate(.data = ., 
         stars = review_scores_location/2,
         borough = neighbourhood_group, 
         borough = as.factor(borough)) %>%
  drop_na(dat = ., review_scores_location) %>%
  select(.data = ., id, price, stars, number_of_reviews, name, borough, neighbourhood, room_type) %>%
  ggplot(aes(price, stars)) + 
  geom_point()
```
