# MQTT Publish–Subscribe System using Node-RED

## Project Overview

This project demonstrates a Publish–Subscribe messaging system using the MQTT protocol and Node-RED. The system simulates a smart campus environmental monitoring setup where multiple publishers send sensor data to an MQTT broker, and subscribers receive and visualize the data in real time.

The implementation showcases topic-based routing, wildcard subscriptions, Quality of Service (QoS) levels, retained messages, and live dashboard visualization.

---

## Objectives

* Implement MQTT publish–subscribe architecture
* Use multiple publishers
* Demonstrate wildcard subscription
* Configure and compare QoS levels
* Enable retained messages
* Visualize live data using Node-RED Dashboard

---

## System Architecture

**Publishers → MQTT Broker → Wildcard Subscriber → Dashboard**

### Components

* Node-RED (running in Docker)
* MQTT Broker (HiveMQ public broker)
* Node-RED Dashboard
* Inject nodes simulating sensors

---

## Topics Used

| Publisher             | Topic                      |
| --------------------- | -------------------------- |
| Temperature Publisher | `campus/room1/temperature` |
| Humidity Publisher    | `campus/room2/humidity`    |
| Status Publisher      | `campus/status`            |

### Wildcard Subscription

`campus/+/+`

This allows the subscriber to receive messages from all campus-related topics.

---

## Publishers

### 1. Temperature Publisher

* Simulates room temperature
* Sends random values
* Topic: `campus/room1/temperature`
* QoS: 0

### 2. Humidity Publisher

* Simulates humidity levels
* Topic: `campus/room2/humidity`
* QoS: 1

### 3. Status Publisher

* Sends system status
* Topic: `campus/status`

---

##  Subscriber

A single MQTT subscriber uses the wildcard topic `campus/+/+`.
It receives messages from all publishers and routes them using switch nodes.

---

##  Dashboard Visualization

The Node-RED dashboard provides real-time monitoring:

*  Temperature Gauge
*  Humidity Chart
*  Status Indicator

Access dashboard at:
`http://localhost:1880/ui`

---

## Quality of Service (QoS)

| QoS Level | Meaning                | Used In     |
| --------- | ---------------------- | ----------- |
| QoS 0     | At most once delivery  | Temperature |
| QoS 1     | At least once delivery | Humidity    |
| QoS 2     | Exactly once delivery  | Subscriber  |

This demonstrates different reliability guarantees in MQTT communication.

---

##  Retained Messages

Retained messages are enabled for the temperature topic.

**Purpose:**

* Broker stores the last message
* New subscribers instantly receive the latest value

---

##  How to Run the Project

### Step 1: Run Node-RED in Docker

```bash
docker run -it -p 1880:1880 --name mynodered nodered/node-red
```

### Step 2: Open Node-RED

`http://localhost:1880`

### Step 3: Import Flow

* Menu → Import
* Paste `flows.json`

### Step 4: Deploy

### Step 5: Open Dashboard

`http://localhost:1880/ui`

---

## Deliverables Included

* Node-RED flow screenshot
* Debug log output
* Live dashboard screenshot
* Video demonstration


---

##  Team Member

* Rakshana B


---

## Conclusion

The project successfully implements an MQTT-based publish–subscribe system using Node-RED. It demonstrates topic-based messaging, wildcard subscriptions, QoS reliability, retained messages, and real-time dashboard visualization suitable for IoT monitoring applications.
