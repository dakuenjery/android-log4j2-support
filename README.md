# android-log4j2-support

This library adds the basic support for log4j-2.3 for Android. The libraries relying on log4j work on Android and Logcat appender is used to log their output.

## Usage in Android applications

### Setting up Gradle build

```
repositories {
    maven {
        url 'http://dev.atteq.com/maven2/'
    }
}

dependencies {
    compile 'com.atteq:android-log4j2-support:2.3'
}
```

### Initialization of log4j

In the `onCreate` method of your application you may use the following code

```
AndroidLog4jHelper.initialise(getApplicationContext(), R.raw.log4j);
```

The contents of `src/main/res/raw/log4j.xml` then may look as follows.

```
<?xml version="1.0" encoding="UTF-8"?>

<Configuration status="debug">
    <Appenders>
        <Logcat name="Logcat">
            <ThresholdFilter
                level="ALL"
                onMatch="ACCEPT"
                onMismatch="DENY" />
            <PatternLayout pattern="%m" />
        </Logcat>
    </Appenders>

    <Loggers>
        <Root level="DEBUG">
            <AppenderRef ref="Logcat" />
        </Root>
    </Loggers>
</Configuration>
```
