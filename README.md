# Lab Results Service

Manages biological test results, supports calendar-based scheduling of lab tests, and provides statistical analysis of result trends for the Nephro Platform.

## Tech Stack

- Java 17, Spring Boot 3.2.5
- MySQL 8 (database: `lab_results_db`)
- SpringDoc OpenAPI / Swagger UI
- Spring Cloud Netflix Eureka Client
- Spring Cloud Config Client

## Port

`9003`

## API Endpoints

| Method | Path | Description |
|---|---|---|
| GET | `/lab-results/lab-reports` | Search reports (paginated, filterable) |
| GET | `/lab-results/lab-reports/{id}` | Get report by ID |
| POST | `/lab-results/lab-reports` | Create lab report |
| PUT | `/lab-results/lab-reports/{id}` | Update lab report |
| DELETE | `/lab-results/lab-reports/{id}` | Delete lab report |
| GET | `/lab-results/lab-reports/patient/{patientId}` | Reports for a patient |
| GET | `/lab-results/lab-reports/calendar` | Calendar view of scheduled tests |
| GET | `/lab-results/lab-reports/statistics` | Aggregated stats for a date range |

## Environment Variables

| Variable | Description |
|---|---|
| `MYSQL_ROOT_PASSWORD` | MySQL root password |

## Features

- **Result tracking** — store creatinine, urea, GFR, hemoglobin, and other nephrology-relevant lab values
- **Calendar integration** — view and schedule lab tests on a calendar
- **Statistical analysis** — trend analysis and aggregation over configurable date ranges
- **Pagination & filtering** — efficient lookup across large result sets
- **Swagger UI** — available at `/lab-results/swagger-ui.html`

## Running Locally

```bash
mvn spring-boot:run
```

## Docker

```bash
docker build -t azizos07/lab-results-service:latest .
docker run -p 9003:9003 \
  -e MYSQL_ROOT_PASSWORD=rootpassword \
  azizos07/lab-results-service:latest
```
