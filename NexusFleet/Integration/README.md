# Integration with NexusFleet

## API URLs
1. Development - https://api-development.integration.nexusfleet.io
2. Production - https://api.integration.nexusfleet.io

## Health check UI

You can check health status of the NexusFleet Integration infrastructure by visiting the public dashboard. For instance, you can check it to see if NexusFleet Integration API is up and running.

1. Development - https://hc-development.integration.nexusfleet.io
2. Production - https://hc.integration.nexusfleet.io

## Machine-to-machine integration

This scenario covers integrating your back-end application with NexusFleet Integration API back-end.

### How it works

1. Get API key
    
    1.1 It's linked only to your tenant

    1.2 It provides access only to your tenant's data

    1.3 Other tenants can't access your tenant's data by using their API keys

2. Configure HTTP request

    2.1 Specify tenant in context of which request is made

    2.2 Specify API key

3. Send request to NexusFleet API

### Integrate via API client

Integration API client represents the app which you want to integrate with NexusFleet. You can integrate many apps. Each API clients provides you with API Keys needed to call NexusFleet Integration API.

#### Register your tenant

Go to the NexusFleet web app and register you tenant or login if you already have tenant.

1. Development - https://app-development.nexusfleet.io
2. Production - https://app.nexusfleet.io

#### Create API client

1. Login into your tenant.
2. Switch to your tenant.
3. Go to Management -> Integration -> API clients.
4. Create new client.
5. Go to created client and copy one of the API Keys.

#### Specify tenant

Add your tenant identifier to HTTP request either in:

1. Header `NexusOps-Tenant={TenantIdentifier}`
1. Query string parameter `NexusOps-Tenant={TenantIdentifier}`

#### Specify API key

Add your API key to request in HTTP header `NexusOps-API-Key`.

#### Call NexusFleet API

You can call test endpoint to ensure setup is correct:

```
GET /api/v1/test/identity
```

## Swagger and OpenAPI

The API supports OpenAPI specification and Swagger UI.

Swagger UI is available on development instances at `/swagger` path.

### Code generation

You can generate API definitions from OpenAPI specification. We recommend to utilize OpenAPI generator tools for that.

You can check out [OpenAPI Generator](https://openapi-generator.tech/) which has support of many languages and HTTP clients (50+ client [generators](https://openapi-generator.tech/docs/generators)). 

Usage example on JavaScript/TypeScript:

```sh
# install via NPM
npm install @openapitools/openapi-generator-cli -g
# or
npm install @openapitools/openapi-generator-cli --save-dev

# Generate APIs for TypeScript and Axios
npx openapi-generator-cli generate --input-spec http://localhost:5050/swagger/v1/swagger.json --generator-name typescript-axios --output ./src/core/api/generated --config openapi-generator-cli-typescript-axios-config.json
```

