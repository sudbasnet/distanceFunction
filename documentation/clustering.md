# Clustering

## Experiments with spatiotemporal clustering
Now, we can apply the `dbscan` function on these distance matrices. To apply the `dbscan` function we need to supply the distance matrix as a `dist` object, the `eps` parameter which is essentially the radius of neighborhood for each event. The last parameter that the `dbscan` function uses is `minPts` , this is the minimum number of points that should be inside a neighborhood of size `eps` for it to be considered a cluster. For our experiments, we will supply these points arbitarily by choosing 4 as the `minPts` and 10% of the maximum distance value in each of the distance matrices.

Our goal is to find closely related events by evaluating the spatiotemporal distance along with the difference in the socioeconomic environment of the event location. We are using DBSCAN as the clustering algorithm as it is efficient in finding clusters of similar densities in spatial database with noise. As this algorithm clusters objects based on the similar densities, it does not perform very well on datasets with varying densities and is very sensitive to the input parameters eps and minPts, the optimal values for these parameters is hard to determine. Hence, we will be choosing values of eps and minPts randomly for this preliminary analysis. For this experiment, we are using 10% of the max distance between all pair of events as the eps and take 4 as the minPts. Note that the distances calculated by the distance function are always in the range of [0-1].
 
### Spatiotemporal distances
While considering only the spatiotemporal distances, we take 10% of the max distance between events as eps and take minPts as 4. Running DBSCAN clustering on the spatiotemporal distances among 1770 events with these parameters, we get 69 clusters and 540 noise points. For our analysis, we will examine three of the largest clusters and then three of the smallest clusters formed after the DBSCAN clustering. In DBSCAN clustering, a cluster might have border points that are shared among different core points of different clusters, in this case the border point is assigned to a cluster at random and so a cluster may have less number of points than the minPts. For the 3 smallest clusters, will only be examining clusters with at least 4 (minPts) points.
![Number of events in each cluster (noise not included), SPATIOTEMPORAL](https://github.com/sudbasnet/distanceFunction/blob/master/documentation/Picture1.png)

Cluster    Events    Distance Summary    Event Dates    Spatial Distances (km)
Min.    Median    Mean    Max.    Standard deviation    Min.    Max.    Min.    Avg.    Max.
0 (noise)    540    0    1    0.9275    1    0.1578    1/1/14    12/31/14    0    250.71    727.23

