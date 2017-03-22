---
title       : Visualizing relational data with `ggraph`
description : The `ggraph` package brings `ggplot2` like syntax to network visualizations.
attachments :
  slides_link : https://s3.amazonaws.com/assets.datacamp.com/course/teach/slides_example.pdf
--- type:NormalExercise lang:r key:1085797f84
## Create an `igraph` object and plot it

We'll be using the `hagelloch.df` dataframe from the `surveillance` package to
create a graph of the transmission of a measles outbreak.

*** =instructions
- Use the patient ID number (`PN`) column and the putative source of infection
(`IFTO`) column to make an `igraph` object where the vertices are patients and
the edges show who infected who.

- Plot this graph using `ggraph` with straight edges and points for nodes.

*** =hint
Read the docs

*** =pre_exercise_code
```{r}
library(igraph)
library(surveillance)
library(ggraph)
library(dplyr)
data("hagelloch")
```

*** =sample_code
```{r}
my_arrow = arrow(length = unit(5, "mm"), type = "closed")

# create an igraph object
measles_net <- ___

# plot measles_net
ggraph(___)
```

*** =solution
```{r}
my_arrow = arrow(length = unit(2, "mm"), type = "closed")

# create an igraph object
measles_net <- hagelloch.df %>% 
  select(PN, IFTO) %>%
  filter(IFTO != -1) %>% 
  as.matrix() %>% 
  graph_from_edgelist()

# plot measles_net
ggraph(measles_net) +
  geom_edge_link(arrow = my_arrow, end_cap = circle(1, "mm")) +
  geom_node_point()
```

*** =sct
```{r}
test_error()
```

--- type:NormalExercise lang:r xp:100 skills:1 key:c33d19efe0
## Testing Vincent


*** =instructions

*** =hint

*** =pre_exercise_code
```{r}

```

*** =sample_code
```{r}
library(igraph)
library(surveillance)
library(ggraph)
library(dplyr)
data("hagelloch")
my_arrow = arrow(length = unit(2, "mm"), type = "closed")

# create an igraph object
measles_net <- hagelloch.df %>% 
  select(PN, IFTO) %>%
  filter(IFTO != -1) %>% 
  as.matrix() %>% 
  graph_from_edgelist()

# plot measles_net
ggraph(measles_net) +
  geom_edge_link(arrow = my_arrow, end_cap = circle(1, "mm")) +
  geom_node_point()
```

*** =solution
```{r}

```

*** =sct
```{r}

```
