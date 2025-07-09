# Pinterest MCP Server - Server Features

## Overview

The Pinterest MCP Server is a Model Context Protocol (MCP) server that allows AI assistants to interact with Pinterest’s platform via authenticated API operations. With secure OAuth-based access, this server provides comprehensive Pinterest board and pin management capabilities, including sandbox testing for development workflows.

It supports 8+ tools, including full CRUD operations for boards and pins, image uploads (via base64 and URL), and user-specific Pinterest data access.

## Core Capabilities

### Pinterest OAuth Integration

*Operations Available:*
- Generates Pinterest OAuth URL for user authentication
- Supports necessary scopes: boards:read, boards:write, pins:read, pins:write, user_accounts:read, user_accounts:read_followers
- Dynamic redirect URI support for local development

### Board Management

*Operations Available:*
- *Get Boards*: Fetches all boards for an authenticated user
- *Create Board*: Adds new boards with configurable privacy and descriptions
- *Delete Board*: Deletes specific boards with retry prevention (caching deleted IDs)
- Duplicate board name detection and validation

### Pin Management

*Operations Available:*
- *Delete Pin*: Deletes specific pins by ID
- *Create Pin (Base64)*: Upload pins using base64-encoded images
- *Create Pin (Image URL)*: Upload pins using public image URLs
- Metadata fields supported: title, description, alt text, link

### Sandbox Environment Support

*Operations Available:*
- *Create Sandbox Board*: Test board creation in Pinterest Sandbox API
- *Get Sandbox Boards*: Retrieve boards created in the sandbox environment
- Useful for development and staging without affecting production data

## Technical Architecture

### Command Execution Engine

- Built on @modelcontextprotocol/sdk
- Communication handled via StdioServerTransport for CLI integrations
- All tools registered through server.tool() with Zod-based validation
- Encapsulated toText() helper for consistent output formatting

### API Integration

- Uses axios for Pinterest API interaction
- Dynamic accessToken injection per request (OAuth 2.0 based)
- Automatic retry prevention for destructive operations like delete

### Development and Runtime Behavior

- Loads environment variables via dotenv
- Logs Pinterest OAuth URL on startup
- Implements robust error handling and logging

## Authentication & Security

### Credential Management

- No credential storage; access tokens passed at runtime
- Uses Pinterest OAuth 2.0 for secure authentication
- Handles state and scope management dynamically
- Access tokens expected to be scoped appropriately for each operation

## Prerequisites

- Node.js environment with support for ES modules
- @modelcontextprotocol/sdk and axios installed
- Pinterest Developer Account
- Registered Pinterest App with Client ID and callback URL
- Environment variables:
  - PINTEREST_CLIENT_ID
- Internet access to Pinterest public and sandbox APIs

## Use Cases

### Content Creators & Influencers

- Automate board and pin management workflows
- Integrate Pinterest content creation into custom dashboards

### Developers & AI Assistants

- Enable AI tools to manage boards and pins contextually
- Build Pinterest-powered bots, schedulers, or assistants

### Testing & QA

- Isolate testing using sandbox environment without production impact
- Programmatic test data setup and teardown