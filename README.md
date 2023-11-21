# Parking times in the Helsinki metropolitan area

This is a Python package to look up expected average parking times at any given
location in the Helsinki metropolitan area, using the values surveyed by
[Vesanen (2020)](http://hdl.handle.net/10138/320835)

This package is used, for instance, for [calculating travel time matrices of the
metropolitan
area](https://github.com/DigitalGeographyLab/Helsinki-Travel-Time-Matrices).

## Use

Instantiate a `ParkingTimesCalculator()` and call its method `parking_times()`,
using a `shapely.Point` as an argument. The return value (`int`) is the expected
delay arising from finding a parking spot and walking to the destination, in
minutes.

```
>>> import parking_times_calculator
>>> import shapely
>>> p = shapely.Point(60.20, 24.95)
>>> parking_times_calculator = parking_times_calculator.ParkingTimesCalculator()
>>> parking_times_calculator.parking_time(p)
4
```

You can `geopandas.apply()` this method to a `geometry` column:

```
df["parking_times"] = df["geometry"].apply(parking_times_calculator.parking_time)
```
