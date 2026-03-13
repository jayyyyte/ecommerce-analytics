# ecommerce-analytics
# E-commerce Analytics Streaming Pipeline

This project simulates a **real-time e-commerce event analytics pipeline** built using **Kafka, Python, and Snowflake**. It demonstrates how raw event data can be ingested, validated, cleaned, and loaded into a data warehouse for downstream analytics.

The system mimics how production data platforms process high-volume event streams such as purchases, page views, and cart interactions.

---

## Architecture

Producer → Kafka (raw_events) → Stream Processor → Kafka (clean_events) → Snowflake

1. **Event Producer**
   - Generates synthetic e-commerce events.
   - Publishes events to Kafka topic `raw_events`.
   - Intentionally injects malformed records (~25%) to simulate dirty production data.

2. **Stream Processor**
   - Consumes messages from `raw_events`.
   - Validates schema and filters out invalid events.
   - Publishes clean events to `clean_events`.

3. **Snowflake Consumer**
   - Consumes validated events from `clean_events`.
   - Batches and loads them into Snowflake using `write_pandas`.
   - Stores records in table `KAFKA_EVENTS_SILVER`.

4. **Kafka Infrastructure**
   - Dockerized Kafka broker running in KRaft mode.
   - Kafka UI for monitoring topics and messages.

---

## Tech Stack

- **Python**
- **Apache Kafka**
- **Docker & Docker Compose**
- **Snowflake**
- **Pandas**
- **Kafka-Python**


