# Log levels

## TRACE
Used duting developement, never turned on in probduction.

## DEBUG
Anything happening in the application.  The state can be used during debugging, reduce det number of entried to a minumum. leave only statements that give true meaning and insight.

## INFO
All actions that are initiated by by shedules og users

## NOTICE
Runtime state, typically statistic logging lives here.

## WARN
_"Not a problem yet"_ Typically the slow queries, disk-io, annything performance related.  Added to a timeseries database, bottlenecks will show upp here.

## ERROR
_"A problem but we will recover"_  Queries that dont finnish in time, timeouts, 404 (http), external service down.

## FATAL
_Unabel to fullfill the request_, Shutting down, corrupt data, dataloss.

## 
