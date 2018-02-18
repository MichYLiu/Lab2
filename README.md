# Lab2
---
title: "Lab2"
output: html_document
---
```{r}
housing <- read.csv("http://colindawson.net/data/landdata-states.csv")
glimpse(housing)
```
```{r}
h2013q1 <- housing %>% filter(Date == 2013.25)

home_value_plot_point <- ggplot(h2013q1, aes(y = Land.Value, x = Home.Value)) + geom_point()

home_value_plot_line <- ggplot(h2013q1, aes(y = Land.Value, x = Home.Value)) + geom_line()
```
```{r}
home_value_plot_point
```
```{r}
home_value_plot_line
```
##it does not make sense to make a line plot and connect the dots

```{r}
home_value_plot_point <- home_value_plot_point + aes(color = Home.Value)
home_value_plot_point
```
```{r}
home_plot <- ggplot(housing, aes(y= State, x = Home.Price.Index)) + geom_point(aes(color = Date), alpha = 0.3, size = 1.5, position = position_jitter(width = 0, height = 0.5))

home_plot_d <- ggplot(housing, aes(y= State, x = Home.Price.Index)) + geom_point(aes(color = factor(Date)), alpha = 0.3, size = 1.5, position = position_jitter(width = 0, height = 0.5)) + ylab('State') + xlab("Home.Price.Index") + theme(panel.grid.minor = element_blank(), text= element_text(size=10), axis.text.x = element_text(angle = 0, vjust = 0, hjust = 0.5, size = 5, color = 'red'),axis.text.y = element_text(angle = 60, hjust = 0.5, size = 3, color = 'blue'))

home_plot
home_plot_d

```
```{r}
home_plot_2 <- home_plot + scale_y_discrete(name = "State Abbreviation")
home_plot_2
```
```{r}
home_plot_3 <- home_plot_2 + scale_color_continuous(breaks = c(1975.25, 1994.25, 2013.25),
                                                  labels = c(1971, 1994, 2013))
home_plot_3
```
```{r}
home_plot_4 <- home_plot_3 + 
  scale_color_continuous(
    breaks = c(1975.25, 1994.25, 2013.25),
    labels = c(1971, 1994, 2013),
    low = "blue", high = "red")
home_plot_4
```
```{r}
home_plot_5 <- home_plot_2 +
  scale_color_gradient2(
    breaks = c(1975.25, 1994.25, 2013.25),
    labels = c(1971, 1994, 2013),
    low = "blue", high = "red", mid = "gray60",
    midpoint = 1994.25)
home_plot_5
```
```{r}
home_plot_6 <- home_plot_4 + geom_vline(xintercept = 1)
home_plot_6
```
```{r}
home_plot_7 <- home_plot_4 +
  scale_color_gradient2(
    breaks = c(1975.25, 1994.5, 2013.25),
    labels = c(1971, 1994, 2013),
    low = "blue", high = "red", mid = "gray60",
    midpoint = 1994.25) + geom_vline(xintercept = 1)
home_plot_7
```
```{r}
state_plot <- ggplot(housing, aes(x = Date, y = Home.Value))

state_plot + geom_line(aes(color = State))
```
```{r}
state_plot +
  geom_line() +
  facet_wrap(~State, ncol = 10)
```
```{r}
home_plot_f <- ggplot(housing, aes(x = Structure.Cost, y = Home.Value))
home_plot_f +
  geom_line() +
  facet_wrap(~State, ncol = 10)
```



