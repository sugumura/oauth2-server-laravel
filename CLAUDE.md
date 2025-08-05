# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is OAuth 2.0 Server for Laravel - a deprecated package that was superseded by Laravel Passport for Laravel 5.3+. It's built on top of The League of Extraordinary Packages' OAuth 2.0 server and provides both authorization server and resource server functionality for Laravel and Lumen applications.

## Architecture

### Core Components

- **Authorizer** (`src/Authorizer.php`): Main class that wraps both authorization server (issuer) and resource server (checker) functionality
- **Service Provider** (`src/OAuth2ServerServiceProvider.php`): Registers OAuth2 services, middleware, and configuration
- **Storage Layer** (`src/Storage/`): Fluent-based storage adapters for OAuth2 entities (access tokens, auth codes, clients, etc.)
- **Middleware** (`src/Middleware/`): HTTP middleware for OAuth2 protection and validation

### Database Schema

The package includes comprehensive migrations in `database/migrations/` for all OAuth2 entities:
- OAuth scopes, grants, clients, sessions
- Access tokens, refresh tokens, authorization codes
- Relationship tables for client-scope and session-scope mappings

### Grant Types Support

Configuration in `config/oauth2.php` supports multiple OAuth2 grant types:
- Client Credentials Grant
- Password Grant  
- Authorization Code Grant
- Refresh Token Grant
- Custom grant types

## Development Commands

### Testing
```bash
# Run PHPUnit tests
./vendor/bin/phpunit

# Run PHPSpec tests  
./vendor/bin/phpspec run

# Run integration tests
./vendor/bin/phpunit tests/integration/

# Run unit tests (PHPSpec)
./vendor/bin/phpspec run tests/unit/
```

### Dependencies
```bash
# Install dependencies
composer install

# Update dependencies
composer update
```

## Framework Support

The package supports both Laravel and Lumen with version compatibility:
- Laravel 4.0.x - 5.2.x (various package versions)
- Lumen support via separate service provider (`src/Lumen/OAuth2ServerServiceProvider.php`)
- PHP >= 5.5.9 required

## Configuration

- Main config: `config/oauth2.php` - defines grant types, token lifetimes, and other OAuth2 settings
- Database migrations automatically create required OAuth2 tables
- Middleware registration happens in the service provider

## Documentation

Extensive documentation available in `docs/` covering:
- Getting started guides for Laravel 4/5 and Lumen
- Authorization server implementation for each grant type  
- Resource server endpoint protection
- Configuration and middleware setup