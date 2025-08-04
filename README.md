# spring-cloud-config-git-server-repo

## Overview

This repository serves as a **Spring Cloud Config Server** configuration repository that centralizes configuration management for microservices in a distributed system. It contains configuration files for various services that can be dynamically loaded and updated without requiring application restarts.

## Purpose

This repository is designed to work with Spring Cloud Config Server to provide:

- **Centralized Configuration Management**: All service configurations are stored in one place
- **Dynamic Configuration Updates**: Services can refresh their configuration without restarts
- **Environment-Specific Configurations**: Different configurations for different environments
- **Secure Configuration Storage**: Encrypted sensitive configuration values
- **Version Control**: Configuration changes are tracked through Git

## Services Included

The repository contains configuration files for the following services:

### 1. Book Service (`book-service.yaml`)
- **Port**: 8092 (configurable via PORT environment variable)
- **Features**: 
  - SSL/TLS enabled with PKCS12 keystore
  - Eureka client registration with secure communication
  - Encrypted keystore passwords using Spring Cloud Config encryption
  - Service discovery integration

### 2. Client Service (`client-service.yaml`)
- **Port**: 8081 (configurable via PORT environment variable)
- **Features**:
  - Basic authentication (username/password)
  - RabbitMQ integration
  - Management endpoints exposed for monitoring
  - Custom properties for application configuration

### 3. Discovery Service (`discovery-service.yaml`)
- **Port**: 8760 (configurable via PORT environment variable)
- **Features**:
  - Eureka Server implementation
  - SSL/TLS enabled with mutual authentication
  - Service registry for microservices
  - Secure communication between services

## Usage

This repository should be configured as the backend for a Spring Cloud Config Server. The Config Server will serve these configuration files to client applications based on their application name and profile.

## Security

- Sensitive configuration values are encrypted using Spring Cloud Config encryption
- SSL/TLS is enabled for secure communication
- Mutual authentication is configured for the discovery service
- Keystore passwords are encrypted and stored securely

## Configuration Management

The repository follows Spring Cloud Config conventions:
- Configuration files are named as `{application-name}.yaml`
- Environment-specific configurations can be added as `{application-name}-{profile}.yaml`
- Encrypted values are prefixed with `{cipher}` for secure storage