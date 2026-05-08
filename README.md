# CDC Attribute Sync — Insider CDP

Scheduled pipeline that reads approved CDC contract data from BigQuery
and upserts user attributes to Insider's Unification API in batches.

## What it does

1. Queries BigQuery for users with updated CDC contract data (current date)
2. Validates email format before processing
3. Sends user attributes to Insider via `/api/user/v1/upsert` in batches of 1,000
4. Notifies a Microsoft Teams channel on success or failure

## Requirements

- Python 3.8+
- Google Cloud credentials with BigQuery read access
- Insider partner name and request token
- Microsoft Teams incoming webhook URL

## Setup

```bash
pip install pandas requests google-cloud-bigquery tqdm
