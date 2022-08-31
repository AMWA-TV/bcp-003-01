# Controllers

_(c) AMWA 2022, CC Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)_

## Introduction

A Controller is Client software that interacts with the NMOS APIs to discover, connect and manage resources (Nodes, Devices, Senders and Receivers) within a networked media system.

* This document includes normative references to be followed when implementing a secure Controller.
* This document covers how the Controller interacts with the NMOS APIs only.
  It does not cover other features of the Controller software, such as presentation.
* This document does not cover any requirements relating to where a Controller is additionally acting as a Node (e.g. receiving monitoring information via IS-07).

Where this document refers to a User, this can include both human operators who drive a Controller manually and automation systems that drive a Controller programmatically.

## Secure Controller

### Secure Communications

An NMOS system with secure commmunication is one in which Controllers, Nodes, Registries, and other servers, both support and have been configured to enable the security requirements described in this specification.

Where a Controller has been configured to enable secure communication channels the implementation of such secure communication channel MUST follow the requirements in this specification.

### Execution Environment

A secure Controller MAY delegate fully or partially the establishment of secure communication channels to services in the execution environment.

Collectively, the Controller and those services MUST fulfil the requirements in this specification.

A Controller MUST only delegate to services that fulfil the following requirements and recommendations.

## TLS

Secure Controllers MUST follow the requirements set out in the [TLS section of the Secure Communications document](Secure%20Communication.md#tls) in this specification.

A secure Controller MUST check the validity of a server's certificate and MUST NOT continue the communication with a server after a failed TLS handshake, except with the express permission of the user.

## Client Behaviour

Secure Controllers MUST follow the requirements set out in the [Client Behaviour section of the Secure Communications document](Secure%20Communication.md#client-behaviour), along with the following requirements.

### Certificate Management

A secure Controller or its execution environment MUST provide a secure mechanism for installing, storing and removing X.509 v3 client certificate and its associated private key.

Either the Controller or the controller environment SHOULD provide a secure mechanism for installing, storing and removing the Certificate Authority (CA) certificates.

### HTTP

A secure Controller acting as an HTTP client MUST only make HTTPS requests (`https://`) using a TLS version and cipher suite allowed by this specification. It MUST NOT make insecure HTTP requests (`http://`).

### WebSocket

A secure Controller acting as a WebSocket client MUST only make Secure WebSocket (`wss://`) requests using a TLS version and cipher suite allowed by this specification,
and MUST NOT make insecure WebSocket (`ws://`) requests.

### Other Protocols

A secure Controller, acting as a client using any other protocol that supports TLS, MUST only make requests using a TLS version and cipher suite allowed by this document. It MUST only make requests using TLS.
