# A simple 1-step solution for OpenTelemetry

Welcome to TelemetryHub, the simplest and most efficient solution for storing your OpenTelemetry metrics, logs and traces.

## Who we are 


TelemetryHub is a new offering from [Scout](https://scoutapm.com/). Founded in 2009 with a server monitoring solution, Scout has evolved to provide insight into application performance for an expanding set of supported languages and is now evolving to also offer an observability platform that will enable teams to diagnose issues and reduce Mean Time to Resolution (MTTR) with a simple, affordable, and usable single pane of glass look across distributed systems. 

## The Endpoint
If you're monitoring production systems, it's wise not to try and do your observability data storage on your own stack.

TelemetryHub is a destination for your OpenTelemetry (Otel) data, supporting the [Otel Protocol specification](https://opentelemetry.io/docs/reference/specification/protocol/requirements/). 

## The Dashboard
TelemetryHub is an exploration tool for your [OpenTelemetry Signals](https://opentelemetry.io/docs/concepts/signals/). View and filter Traces, jump to a detailed view of Spans in a Trace, look up a Trace from a related Log record - whatever fits your workflow! Move through your Signals in a single application with no ops required.

## A simple, efficient way to store data
With reasonable storage costs and no per-seat pricing, TelemetryHub is the simplest, easiest way to store your OpenTelemetry data, with great dashboards to make it easy to explore.

## Sending Data
TelemetryHub provides an OTLP Collector endpoint that feeds our durable storage and processing infrastructure. Depending on your environment, you may wish to configure individual services to point their OTLP Exporters directly at our endpoint, or run a local Collector that performs intermediary processing before forwarding to our endpoint. We can accept http-proto and gRPC requests, see the endpoint spec
 and Troubleshooting.

All requests to our endpoint should use TLS and are validated with either a specificheader (`X-TELEMETRYHUB-KEY`) or Resource attribute (`telemetryhub.key`). A local Collector has the benefit of allowing these to be attached to all your exported Signals at a single location.

While we strive to avoid imposing hard limits, individual records must be smaller than 1Mb. Ouringest pipeline is highly scalable, but if you have concerns about resource caps (e.g. "We need to make 1.5 million concurrent connections."), please do reach out. Rate limiting is also an option if you elect to use the [OpenTelemetry Collector](https://github.com/open-telemetry/opentelemetry-collector)
