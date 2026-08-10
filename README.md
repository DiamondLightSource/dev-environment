# Diamond Compose Collections

This repository is a collection of Docker Compose files used to stand up several Diamond Light Source-related service stacks for local development, testing, and beamline-style deployments.

The repository currently contains two main areas:

- `controls-services/`: a set of EPICS and beamline control services for an example BL01T-style environment. See [controls-services/README.md](controls-services/README.md) for the full reference and deployment details.
- `daq-services/`: a set of data acquisition and integration services for authentication, messaging, policy enforcement, and data access.

## Controls services

The control stack provides a small example beamline environment built around EPICS containers. It includes services for gateway access, graphical interfaces, and simulated IOCs.

Key services include:

- `bl01t-di-cam-01`: an area-detector simulation IOC.
- `bl01t-ea-test-01`: a simple example IOC for testing and experimentation.
- `bl01t-mo-sim-01`: a motor simulation IOC.
- `gateway`: CA/PV gateway services for exposing EPICS PVs.
- `pvagw`: a PV Access gateway.
- `phoebus`: the Phoebus control-system client.
- `epics-opis`: a lightweight OPI host for serving operator interfaces.

This stack is intended to be a useful reference for running EPICS containers locally or on a workstation without needing a full production deployment.

## DAQ services

The DAQ stack provides supporting services for messaging, authentication, authorization, and data access. It is designed to work alongside the control services and provide the backend components needed for a more complete beamline environment.

Key services include:

- `numtracker`: a service for tracking beamline visit-related metadata.
- `rabbitmq`: a RabbitMQ message broker with management and messaging endpoints.
- `keycloak`: an authentication server used for identity and access management.
- `tiled`: a data access service for serving scientific data.
- `tiled-postgres`: the PostgreSQL backing store for Tiled metadata and data.
- `opa`: Open Policy Agent for policy-based access control.
- `blueapi-oauth2-proxy`: an OAuth2 proxy used to front the BlueAPI-related services.

## Repository layout

- `controls-services/` - EPICS and beamline control services.
- `daq-services/` - DAQ, messaging, auth, policy, and data access services.

This repository is meant to serve as a collection of Compose-based deployment definitions for Diamond-style environments.
