# Streaming events

## Goals

Customer wants to write all events sent by clients into a database for
permanent storage.

They'd also like to have the system check every incoming event, and if
it's a rating event, and the rating is low, they'd like to send a
message to another service that handles unhappy customers.

## Details

- To generate the "stream" of incoming events...
    - Create a Dataflow job from a template
    - Use the Text Files to Pub/Sub template
    - For input files, use `gs://aus-bp/json/*`
- For the target tables, receiving events...
    - Create the target table
    - Use the schema found in `gs://aus-bp/schema.json`
- If you do alerting, just publish to a bad rating topic
    - You don't acutally need any service subscriving to it

## Tips

- You can use a Dataflow Template for Pub/Sub to BQ
- However, you won't be able to do alerting
    - For this you'll need to write a dataflow pipeline

## Extra credit

- Add windowing to the pipeline
    - Time stamp messages based on timestamp field value
    - Use fixed windows of 24 hours
    - Calculate the total dialin events and write those into BQ

## Presentation instructions

1. Show what you built in action
2. Show how your built it
3. What did was easy/hard?
4. What was the biggest learning you had?
5. Explain your thoughts on pros/cons of this approach compared to alternate solutions


