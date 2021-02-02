# Spring Cloud GCP for Cloud Monitoring

Cloud Monitoring collects metrics, events, and metadata from Google Cloud.

- Black-box monitoring
  - By requesting a web page, connecting to a TCP port, or making a REST API call.
  - Cloud Monitoring provides this type of monitoring with uptime checks.
- White-box monitoring
  - You can instrument your service to write time-stamped data by using a library like OpenCensus
  - You can write custom time-series data by using the Cloud Monitoring API
- Grey-box monitoring
  - Google Cloud services generate metrics that provide information about how the service is operating
    - [Google Cloud Metrics](https://cloud.google.com/monitoring/api/metrics_gcp)
  - Cloud Monitoring agent gathers system and application metrics.
    - [Cloud Monitoring Agent](https://cloud.google.com/monitoring/agent)
  - Third-party plugins provide service-level data on your Linux VMs.
    - [Monitoring 3rd Party Applications](https://cloud.google.com/monitoring/agent/plugins)
  - Logs-based metrics are metrics collected from the content of logs written to Cloud Logging
## Description
### Dependency
- com.google.cloud
  - `spring-cloud-gcp-starter-metrics`

### Enable Cloud Monitoring API
```shell script
$ gcloud services enable monitoring.googleapis.com
```

## Demo
### Build Container Image
```shell script
$ gcloud builds submit --tag us-central1-docker.pkg.dev/(gcloud config get-value project)/shinyay-docker-repo/hello-metrics:1.0.0
```

### Deploy App to Cloud Run
```shell script
$ gcloud run deploy hello-metrics \
    --image=us-central1-docker.pkg.dev/shinyay-works-201123-296509/shinyay-docker-repo/hello-metrics:1.0.0 \
    --no-allow-unauthenticated \
    --memory=512Mi \
    --platform=managed
```

### Access App with Bearer Token
```shell script
$ curl -H "Authorization: Bearer $(gcloud auth print-identity-token)" https://cloudrun.xxxxxx.run.app/
```

### Open Cloud Monitoring
- Access [Cloud Monitoring](https://console.cloud.google.com/monitoring?_ga=2.260239437.1773434359.1611797762-983599867.1599137884)
- Click **Metrics Explorer**
  - Resource Type: `cloud_run_revision`
  - Metrics: [Cloud Run Metrics](https://cloud.google.com/monitoring/api/metrics_gcp#gcp-run)
## Features

- feature:1
- feature:2

## Requirement

## Usage

## Installation

## Licence

Released under the [MIT license](https://gist.githubusercontent.com/shinyay/56e54ee4c0e22db8211e05e70a63247e/raw/34c6fdd50d54aa8e23560c296424aeb61599aa71/LICENSE)

## Author

[shinyay](https://github.com/shinyay)
