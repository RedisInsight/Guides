It's possible to combine values of one or more time series by leveraging aggregation functions

```redis Calculate average
TS.RANGE sensor1 - + + AGGREGATION avg 3600000 // Calculates the average temperature per hour in the sensor1 series
 
TS.MRANGE - + AGGREGATION avg 3600000 FILTER area_id=32 // Calculates the average temperature across multiple sensors from the area with id of 3
```
 
Since RedisTimeSeries v1.6, you can use the GROUPBY and REDUCE options to group results of time series by label and apply an additional aggregation.

```redis Find minimum value
TS.MRANGE - + FILTER region=(east,west) GROUPBY region REDUCE min // Finds minimum temperature per region

```