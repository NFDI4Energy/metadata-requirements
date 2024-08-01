# Time series module

A time series is a mapping of a point or range in time towards a value. The value at this point can be a scalar / primitive or multidimensional.

## Scope

This module is focusing explicitly on any type of data set that is a mapping as described above.
It does specify the characteristics of the represented data.
It can link to additional modules like sensor information or database information if applicable.

## Requirements

### 1) Available data time interval
The time period for which data exists must be specifiable.

### 2) Time resolution
The time resolution of the mappings needs to be specifiable.
This also applies if it changes over time e.g. through reduction after a given age.

### 3) Specification of data content
The data values of each time point need to be specified in their shape and used units.

