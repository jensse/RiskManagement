# Log levels

## TRACE
Used during development, never turned on in production.

## DEBUG
Anything happening in the application. The state can be used during debugging, reduce the number of entries to a minimum. Leave only statements that give true meaning and insight.

## INFO
All actions that are initiated by schedules or users.

```java
LOGGER.info("User authentication successful for user 'john_doe'. Access granted to resource '/dashboard'. Role: 'Administrator'. IP: 192.168.1.100. Session ID: abc123xyz456.")
LOGGER.info("Application started successfully. Version: 2.0. Environment: Production. Server: prod-server-01. Timestamp: 2024-01-12 08:30:00.")
```

## NOTICE
Runtime state, typically statistic logging lives here.

```java
LOGGER.notice(" Application reached a high traffic threshold. Current requests per minute: 1000. Consider optimizing resources for increased performance.")
```

__NB:__ _This Level is not supported in Log4j2_

## WARN
_"Not a problem yet"_ Typically the slow queries, disk I/O, anything performance-related. Added to a time-series database; bottlenecks will show up here.

```java
LOGGER.warn("Database connection pool reaching maximum capacity. Current connections: 95%. Consider increasing pool size or optimizing queries.")
```

## ERROR
_"A problem but we will recover"_ Queries that don't finish in time, timeouts, 404 (http), external service down.

```java
LOGGER.error("Failed to process payment for transaction ID '123456789'. Payment gateway returned HTTP 500. Retrying in 5 minutes.")
```

## FATAL
_Unable to fulfill the request_, shutting down, corrupt data, data loss.

```java
LOGGER.fatal(" Application encountered an unrecoverable error. Shutting down to prevent data corruption. Error details: NullPointerException at com.example.Application.run()")
```

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
