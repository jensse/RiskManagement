# Log levels

## TRACE
Used during development, never turned on in production.

## DEBUG
Anything happening in the application. The state can be used during debugging, reduce the number of entries to a minimum. Leave only statements that give true meaning and insight.

## INFO
All actions that are initiated by schedules or users.

## NOTICE
Runtime state, typically statistic logging lives here.

## WARN
_"Not a problem yet"_ Typically the slow queries, disk I/O, anything performance-related. Added to a time-series database; bottlenecks will show up here.

## ERROR
_"A problem but we will recover"_ Queries that don't finish in time, timeouts, 404 (http), external service down.

## FATAL
_Unable to fulfill the request_, shutting down, corrupt data, data loss.

## How to log

Add value not noise.

### DO NOT

```java
LOGGER.warn("error");
```
### DO: Add context and event

```java
LOGGER.warn("Sending document %s to Events File-service failed, response code %d, response message %s. Retry in %d milliseconds", documentId, responseCode, responseMessage, timeToRetry);
```
