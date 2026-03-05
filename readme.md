
 Overview

In this activity, I implemented a publish–subscribe system using an MQTT message broker and Node-RED. The system simulates a smart campus environment where different sensors continuously publish data to the broker. A subscriber receives these messages based on topic subscriptions and displays the sensor values on a live dashboard. This project demonstrates how MQTT enables loosely coupled communication between publishers and subscribers using topics, wildcards, QoS, and retained messages.

 System Design

This system contains two publishers: a temperature publisher and a humidity publisher. Each publisher sends a numeric reading to its own MQTT topic. A wildcard subscriber is configured to receive messages from multiple sensor topics using a wildcard subscription. After receiving messages, the flow routes the values to the appropriate dashboard components so that temperature and humidity are shown separately. Additionally, a status message is published on a separate topic to show system state such as “system active” or “online”.

 MQTT Topics Used

The temperature publisher publishes sensor readings to the topic for temperature, and the humidity publisher publishes readings to the topic for humidity. A wildcard subscription is used in the subscriber so that it can listen to all sensor-related topics under a common hierarchy. A separate status topic is used to publish system status messages. This topic structure makes the system scalable because new sensors can be added under the same hierarchy without changing the subscriber design.

Publishers and Subscribers

In this flow, the publishers act as data producers. They generate sensor readings and send them to the MQTT broker using their configured topics. The subscriber acts as a data consumer. It listens using a wildcard topic pattern so that it can receive messages from multiple publishers. This demonstrates the publish–subscribe model where publishers do not directly communicate with subscribers; instead, the broker routes messages based on topic matching.

 Wildcard Subscription

The wildcard subscription allows a single subscriber to receive messages from multiple topics. This is useful when multiple sensors share a common prefix, because the subscriber can receive all sensor readings without subscribing to each topic separately. In this project, wildcard subscription is used to listen to all sensor topics under the same category, which simplifies monitoring and supports easy expansion of the system.

 Dashboard Visualization

A Node-RED dashboard is created to visualize live sensor data. The temperature values are displayed in a live numeric/dial-style display, and humidity values are shown as a live chart/trend display. When new values are published by the sensors, the dashboard updates automatically, showing real-time visualization of the system.

QoS Demonstration

Quality of Service (QoS) is used to demonstrate reliable message delivery in MQTT. In this project, sensor topics are configured with QoS to ensure messages are delivered correctly from publishers to subscribers through the broker. This shows how MQTT can provide different delivery guarantees depending on system requirements.

Retained Messages vs QoS

QoS controls how reliably the broker delivers a message (delivery guarantee). Retained messages are different: a retained message is stored by the broker and sent immediately to any new subscriber that joins later. In this project, the status topic can be configured as retained so that even if the subscriber connects later, it still receives the last known status message immediately.
 Deliverables Included

This repository includes a screenshot of the final Node-RED flow, a short message log showing messages from at least two topics and the status topic, a live dashboard visualization screenshot, and a video demonstration explaining publishers, subscribers, wildcard usage, and QoS versus retained messages.


