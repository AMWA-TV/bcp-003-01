# Controllers

_(c) AMWA 2022, CC Attribution-NoDerivatives 4.0 International (CC BY-ND 4.0)_

## Informative

A Controller is Client software that interacts with the NMOS APIs to discover, connect and manage devices within a networked media system.

* This document includes normative references to be followed when implementing a Controller.
* This document covers how the Controller interacts with the NMOS APIs only.
  It does not cover other features of the Controller software, such as presentation.
* This document does not cover any requirements relating to where a Controller is additionally acting as a Node (e.g. receiving monitoring information via IS-07).

## User

Where this document refers to the "user" of a Controller, this includes both human operators who drive the Controller manually and automation systems that drive the Controller programmatically.

## Secure NMOS Controller

### Secure Communications	

An NMOS system with secure commmunication is one in which Controllers, Nodes, Registries, and other servers, both support and have been configured to enable the security requirements described in this specification.

Where a Controller has been configured to enable secure communication channels the implementation of such secure communication channel MUST follow the requirements in this specification.

### Execution Environment

An Controller MAY delegate fully or partially the establishment of secure communication channel to services in the execution environment.

The Controller and those services MUST collectively fulfill the requirements in this specification.
 
An Controller MUST only delegate to services that fulfill the following requirements and recommendations.

## TLS

Controllers MUST follow the TLS requirements set out in the [TLS section of the Secure Communications document](Secure%20Communication.md#tls) in this specification.

## Client Behaviour

Controllers MUST follow the Client Behaviour requirements set out in the [Client Behaviour section of the Secure Communications document](Secure%20Communication.md#client-behaviour) along with the following requirements:

### Certificate Management

An Controller or its execution environment MUST provide a secure mechanism for installing, storing and removing X.509 v3 client certificate and its associated private key.

Either controller, or controller environment should provide a secure mechanism for installing, storing and removing the CA certificates

### HTTP

An Controller acting as an HTTP client, configured to use a secure communication channel MUST only make HTTPS requests using a TLS version and cipher suite allowed by this specification.

An Controller MUST not allow HTTP requests that do not use TLS.
It MUST check the validity of the server’s certificate and MUST NOT continue the communication with a server after a failed TLS handshake, except with the express permission of the user.

### WebSocket

An Controller acting as a WebSocket (WS) client, configured to use a secure communication channel MUST only make Secure WebSocket (WSS) requests using a TLS version and cipher suite allowed by this specification,
and MUST NOT make non-Secure WebSocket (WS) requests.

### Other Protocols	

An Controller acting as a client, configured to use a secure communication channel using any other protocol that supports TLS MUST only make requests using a TLS version and cipher suite allowed by this document. It MUST only make requests using TLS. 

