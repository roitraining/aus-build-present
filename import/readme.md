# Import data and build tables 

## Goals

Customer needs to load raw data into BigQuery, and needs to create
tables with subsets of the raw data for use by analyst teams.

They would love to add the ability to have new raw data files
automatically uploaded to the raw data table. They would also like
to have the specialized tables re-generated on a daily basis.

## Details

- Data files to import are found at `gs://aus-bp/bq-*`
- Schema file for the table is found at `gs://aus-bp/schema.json`
- For first subset table...
    - Rows from last 30 days that are registration events
    - Date, email, and company columns
- For second subset table...
    - Rows that are calls for the last 7 days
    - Date, time, company, duration, type, os, num users columns

## Tips

- Think BQ for generating subset tables
- Think scheduled queries for daily table updates
- Think Cloud Functions for automated upload of files placed in bucket
    - Look at https://github.com/asaharland/functions-bq-load-job

## Presentation instructions

1. Show what you built in action
2. Show how your built it
3. What did was easy/hard?
4. What was the biggest learning you had?
5. Explain your thoughts on pros/cons of this approach compared to alternate solutions


