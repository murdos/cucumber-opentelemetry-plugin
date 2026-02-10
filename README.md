# cucumber-jvm-opentelemetry

This plugin for Cucumber allows traces to be generated.

The following example code allows setting up in a graceful manner:
```java
    @BeforeAll
    public static void setupOtel() {
        if (System.getenv("OTEL_EXPORTER_OTLP_ENDPOINT") != null) {
            System.setProperty("otel.service.name", "your-service-name");
            AutoConfiguredOpenTelemetrySdk.initialize().getOpenTelemetrySdk();
        } else {
            log.info("""
                     OpenTelemetry plugin for cucumber steps is disabled, set env OTEL_EXPORTER_OTLP_ENDPOINT to a \
                     valid URL to enable.""");
        }
    }
```

Enable the plugin by adding `io.github.murdos.cucumber.opentelemetry.OpenTelemetryTracingEventListener` to the `cucumber.plugin` property.
