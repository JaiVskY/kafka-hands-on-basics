# Kafka KRaft Hands-On Project

This project is a foundational hands-on implementation of **Apache Kafka running in KRaft mode** (Kafka without Zookeeper).  
It includes a simple Python producer and consumer to demonstrate how event streaming works end-to-end using KRaft.

---

## 🧠 What is KRaft Mode?

KRaft (**K**afka **Ra**ft) is Kafka’s new internal consensus protocol that **removes Zookeeper entirely**.

This project helps understand:

- How to run Kafka **in KRaft mode**
- How to create topics directly in a KRaft cluster
- How producers send JSON messages
- How consumers read messages with offsets, partitions, and delivery guarantees
- Basics needed before building advanced data pipelines

✨ Topic Creation (KRaft CLI)

To create a topic in KRaft:
docker exec -it kafka kafka-topics.sh \
  --create \
  --topic orders-topic \
  --bootstrap-server localhost:9092 \
  --partitions 1 \
  --replication-factor 1

List topics:
docker exec -it kafka kafka-topics.sh --list --bootstrap-server localhost:9092

✉️ Running the Producer
producer.py sends JSON messages with fields like:

order_id (UUID)
user
jobname
Quantity

RUN python producer.py

Sample output: Delivered {"order_id":"..."} to orders-topic partition 0 offset 5

📥 Running the Consumer
tracker.py subscribes to the same topic and prints messages:

python tracker.py
Sample output:📦 Received order: 5 from Alice

🛠 Tech Stack

Python
Confluent Kafka Client
Apache Kafka 3.x (KRaft mode)
Docker Compose
