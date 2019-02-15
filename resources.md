# Data scraping

1. leagues: General league data in Baden already in `data` via fussball.de
2. teams: [https://github.com/mauricewipf/unofficial-fussball-de-api](unofficial-fussball-de-api) to get list of teams from all the leagues
3. pitches: Variation of ufda to get location names of pitches (todo)
4. coordinates: Get gps coordinates from location name with [MapQuest geocoding](https://developer.mapquest.com/documentation/geocoding-api/) (add geofence so only avoid results outside Baden area; how to check data for validity?)
5. distances: Basic distance calculation how the crow flies using trigonometry [getting-distance-between-two-points-based-on-latitude-longitude](https://stackoverflow.com/questions/19412462/getting-distance-between-two-points-based-on-latitude-longitude) and average travel speeds (should be enough to get the clustering running)
6. reduce: filter out matchups that are too far apart and that are not supposed to play against each other; try to filter out distances, that are redundant (A to C ≈ A to B to C)
7. times: Proper distance calc using [MapQuest directions](https://developer.mapquest.com/documentation/directions-api/) and expected time of match (one-directional, advantage of two-directional is probably minimal; how to verify quality of data?)
8. improve: Two directional distances, use real schedule (matches in Verbandsliga, sometimes Landesliga & Kreisliga can be on week days in addition to fr, sa, su!) to calculate travel times

# Clustering
* k-means
* EM clustering
* ML to minimize function of
  * sum of squares of travel times for single team
  * and it's variation (equality)
  * sum of squares of travel times for league
  * and it's variation (equality)
  * sum of squares of travel times for federation
* [spectral clustering](https://scikit-learn.org/stable/modules/clustering.html#spectral-clustering)