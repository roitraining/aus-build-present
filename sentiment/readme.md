# Batch Sentiment Analysis

## Goals

The business objective is to be able to easily track sentiment trends within comments, on a per customer basis. With this information, Technical Account Managers can proactively reach out to customers when there is a trend downwards in user happiness, and attempt to remediate any issues

## Details

- You can use data in the `jwd-gcp-demos.events.user_events` table
- Look at the comment data for the last 60 days
- You want to avoid making more than 600 calls/minute to the ML API, assuming you're using the ML API. One way to do this is to not make one call per comment, but bundle all the comments into a single text block and send that to the API. You can still ask to have every line rated individually. If you write your query correctly, it will do this for you.
- You can look at some related code for insipiration: https://github.com/jwdavis/success-hq/tree/master/demo_data

## Tips

- The following query finds all comments ever, in every event, grouped by company. Modify it to find only comments from anyfor the last 60 days of comment events.

    ```
    SELECT
        company,
        STRING_AGG(comment, "\n")
    FROM
        events.user_events
    GROUP BY
        company
    ```
- If you are using the linked code for inspiration, your pipeline should be simpler/better because of the query above. You really only need to adapt the following transforms:
    - read
    - get sentiment scores
    - get stats
    - write into BQ

Note that you will have to tweak the code to work with the data returned by your clever query.

## Extra credit

- Figure out how to have this process run every day.

## Presentation instructions

1. Show what you built in action
2. Show how your built it
3. What did was easy/hard?
4. What was the biggest learning you had?
5. Explain your thoughts on pros/cons of this approach compared to alternate solutions


