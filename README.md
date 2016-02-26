# Experiment to see if population can be predicted from map tiles

## Method

Grab tiles from CartoDB and calculate population in those tiles from the census:

```postgresql
SELECT CDB_OVERLAP_SUM(
        ST_TRANSFORM(
          CDB_XYZ_Extent(603,769,11), 4326),
          'us_census_acs2013_5yr_census_tract_copy ',
          'total_pop',
          'stuartlynn')
```

Download tiles to ./tiles

Train NN to predict the population off the tile set using keras.
