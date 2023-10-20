# Integration with NexusFleet

## API URLs
1. Development - https://api-development.integration.nexusfleet.io
2. Production - https://api.integration.nexusfleet.io

## Machine-to-machine integration

This scenario covers integrating your back-end application with NexusFleet Integration API back-end.

### How it works

1. Get API key
    
    1.1 It is linked only to your tenant

    1.2 It provides access only to your tenant's data

    1.3 Other tenants can't access your tenant's data by using their API keys

2. Configure HTTP request

    2.1 Specify tenant in context of which request is made

    2.2 Specify API key

3. Send request to NexusFleet API

### Integrate via API client

Integration API client represents the app which you want to integrate with NexusFleet. You can integrate many apps. Each API clients provides you with API Keys needed to call NexusFleet Integration API.

#### Register your tenant

Go to NexusFleet web app https://app.nexusfleet.io and register you tenant.

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
