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

An NMOS system with secure commmunication is one in which NMOS Nodes and NMOS Controllers both support and have been configured to enable the security requirements described in this specification.

An NMOS Controller MAY be configured to enable secure communication channels with other components of an NMOS environment such as Nodes and other servers. 
The implementation of such secure communication channel SHALL follow the requirements in this specification.

### Execution Environment

An NMOS Controller MAY delegate fully or partially the establishment of secure communication channel to services in the execution environment.

The NMOS Controller and those services SHALL collectively fulfill the requirements in this specification.
 
An NMOS Controller SHALL only delegate to services that fulfill the following requirements and recommendations.

## TLS

NMOS Controllers MUST follow the TLS requirements set out in the [TLS section of the Secure Communications document](Secure%20Communication.md#tls) in this specification.

## Client Behaviour

NMOS Controllers MUST follow the Client Behaviour requirements set out in the [Client Behaviour section of the Secure Communications document](Secure%20Communication.md#client-behaviour) along with the following requirements:

### Certificate Management

An NMOS Controller or its execution environment SHALL provide a secure mechanism for installing, storing and removing X.509 v3 client certificate and its associated private key.

Either controller, or controller environment should provide a means of installing and removing the CA certificate.

### HTTP

An NMOS Controller acting as an HTTP client, configured to use a secure communication channel SHALL only make HTTPS requests using a TLS version and cipher suite allowed by this specification.

An NMOS Controller SHALL not allow HTTP requests that do not use TLS.
It SHALL check the validity of the server’s certificate and SHALL NOT continue the communication with a server after a failed TLS handshake, except with the express permission of the user.

### WebSocket

An NMOS Controller acting as a WebSocket (WS) client, configured to use a secure communication channel SHALL only make Secure WebSocket (WSS) requests using a TLS version and cipher suite allowed by this specification,
and SHALL NOT make non-Secure WebSocket (WS) requests.

### Other Protocols	

An NMOS Controller acting as a client, configured to use a secure communication channel using any other protocol that supports TLS SHALL only make requests using a TLS version and cipher suite allowed by this document. It shall only make requests using TLS. 

