# sensor-network

```mermaid
graph TD;
    sensor1A(MSP430 Sensor 1A) -. I2C .-> endDevice1A(End Device 1A);
    sensor2A(MSP430 Sensor 2A) -. I2C .-> endDevice2A(End Device 2A);
    sensor1B(MSP430 Sensor 1B) -. I2C .-> endDevice1B(End Device 1B);
    sensor2B(MSP430 Sensor 2B) -. I2C .-> endDevice2B(End Device 2B);

    endDevice1A --> gateway1(Gateway 1);
    endDevice2A --> gateway1;
    endDevice1B --> gateway2(Gateway 2);
    endDevice2B --> gateway2;

    gateway1 -->|forward messages| networkServer(Network Server);
    gateway2 -->|forward messages| networkServer;

    networkServer -->|manages network| applicationServers(Application Servers);
```

## Introduction

End Devices - sensors or actuators send LoRa modulated wireless messages to the gateways or receive messages wirelessly back from the gateways. .

Gateways - receive messages from end devices and forward them to the Network Server.

Network Server - a piece of software running on a server that manages the entire network.

Application servers - a piece of software running on a server that is responsible for securely processing application data.

https://www.thethingsnetwork.org/docs/lorawan/lorawan-relay/

## Relay

LoRaWAN relays are suitable for bridging wireless communication gaps in areas where the gateway and end device cannot directly communicate with each other due to weak signal strength caused by factors such as extreme distance or obstacles between them. They are low-cost, low-power devices. A relay’s hardware is equivalent to a standard LoRaWAN end device. A single relay can serve up to 16 end devices. For the Network Server, a relay appears as a standard end device.



Gateways are the same as end devices, but they are connected to the network server and maybe on hardwired connections for power and connection to the network server. They are responsible for forwarding messages from end devices to the network server.