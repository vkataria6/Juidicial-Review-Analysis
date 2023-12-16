# Judicial Branch Analysis
install.packages("igraph")
```{r, message=FALSE, warning=FALSE}
library(igraph)

#Inward citations and outward citations
judicial.csv <- graph( edges=c(1,2, 1,3, 2,3, 3,4), n=4, directed=FALSE)
plot(judicial.csv)
deg_1 <- degree(judicial.csv)
deg_1
degree_distribution(judicial.csv)
## [1] 0.00 0.25 0.50 0.25 
set.seed(1234)
citation.csv <- graph( edges=c(1,2, 1,3, 2,3, 3,4, 4,5, 4,6, 4,7, 
                     4,8, 4,9, 4,10, 3,11, 2,12,
                     4,13, 4,14, 2,15, 6,12, 7,10), 
             n=15, directed=FALSE)

plot(citation.csv)
deg_2 <- degree(citation.csv)
deg_2
degree_distribution(citation.csv)
##  [1] 0.00000000 0.46666667 0.33333333 0.00000000 0.13333333 0.00000000
##  [7] 0.00000000 0.00000000 0.00000000 0.06666667

hist(degree(judicial.csv),
     xlab = "k",
     ylab = "Frequency",
     main = "Histogram of judicial.csv's nodes degrees, without adjusting breaks and ylim",
     col = "skyblue")

set.seed(1234)
Supreme Court Citation Network <- sample_gnp(1000, 1/1000, directed = FALSE, loops = FALSE)
plot(Supreme Court Citation Network,
     main = "Plotting Supreme Court Citation Network")     
deg_random <- degree(Supreme Court Citation Network)
hist(deg_random, 
     main = "Hist of nodes degree for rnd_g, without adjustments",
     xlab = "k",
     col = "skyblue")     
hist(deg_random, breaks = 0:vcount(Supreme Court Citation Network)-1, 
     main = "Hist of nodes degree for rnd_g, using `vcount()-1`",
     xlab = "k", 
     col = "skyblue",
     ylim = range(pretty(c(0,table(deg_random))))
     )     
hist(deg_random, breaks = 0:(max(deg_random)+1), 
     main = "Hist of nodes degree for rnd_g, adjusting breaks using `seq()`",
     xlab = "k", 
     col = "skyblue"
     )     
hist(deg_random, breaks = seq(0,(max(deg_random)+1), by=0.5), 
     main = "Hist of nodes degree for rnd_g, adjusting breaks using `seq()`",
     xlab = "k", 
     col = "skyblue"
     )     
hist(deg_random, breaks = seq(-1,(max(deg_random)+1), by=0.5), 
     main = "Hist of nodes degree for rnd_g, adjusting breaks using `seq()`",
     xlab = "k", 
     col = "skyblue"
     )     
hist(deg_random, breaks = seq(-1,(max(deg_random)+1), by=0.5), 
     main = "Hist of nodes degree for rnd_g, adjusting Y-axis using `range(pretty())`",
     xlab = "k", 
     col = "skyblue",
     ylim = range(pretty(c(0,table(deg_random))))
     )     
     
