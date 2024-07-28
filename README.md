# Streaming-Data-Ingestion-Pipeline-for-Ecommerce-Payments-Solutions

## Overview
  This project involves creating a real-time data ingestion pipeline to manage orders and payments data. The system ensures data integrity through deduplication and handles out-of-order data by using a Dead       Letter Queue (DLQ) for unmatched records.

## Features
- Real-time Data Ingestion: Uses GCP pub/sub for streaming orders and payments data.
- Data Deduplication: Ensures no duplicate orders are entered into the Cassandra fact table.
- Dead Letter Queue: Unmatched payment records are sent to a DLQ for later reprocessing.
- Cassandra Fact Table: Stores ingested data and performs real-time lookups for data matching.

## Architecture

### Data Sources:

- Orders Service
- Payments Service
  
### Data Stream Processing:

- GCP Pub/Sub
  
### Data Ingestion:

- Orders Stream
- Payments Stream

### Cassandra Fact Table:

- Stores orders and payments data
- Performs real-time lookups

### Dead Letter Queue (DLQ):

- Handles unmatched payment records

## Workflow

- Orders and payments data are ingested through respective streams.
- Orders data undergoes deduplication.
- Payments data is checked for corresponding order_id in the orders fact table.
- Unmatched payment records are sent to the DLQ.
- DLQ records are periodically reprocessed to check for new matches.


## Architecture Daigram


