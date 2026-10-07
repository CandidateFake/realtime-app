# Cypress E2E Testing

Cypress tests can run in Docker (no local `node_modules` required) or locally against a running app.

## Test Files

✓ `frontend/cypress/e2e/critical-filter.cy.ts` - Filter by CRITICAL status + telemetry
✓ `frontend/cypress/e2e/sorting.cy.ts` - Sort by CPU/Memory/Latency
✓ `frontend/cypress/e2e/infinite-scroll.cy.ts` - Load More + Back to Top

## Docker E2E

```bash
docker compose -f docker-compose.e2e.yml up --abort-on-container-exit
```

## Local Setup

```bash
# 1. Install frontend dependencies
cd frontend
npm install

# 2. Make sure the app is running (in another terminal)
cd realtime-app
docker compose -f docker-compose.dev.yml up

# 3. Run tests
cd frontend

# Option A: interactive UI (recommended for development)
npm run e2e

# Option B: headless (CI/CD)
npm run e2e:run
```

## Test Coverage

### critical-filter.cy.ts
- [x] Filter nodes to CRITICAL status only
- [x] Display telemetry data for selected node
- [x] Show critical alert count in badge

### sorting.cy.ts
- [x] Sort nodes by CPU load
- [x] Sort nodes by Memory usage
- [x] Sort nodes by Latency (default)
- [x] Toggle sort order (asc/desc)

### infinite-scroll.cy.ts
- [x] Display initial 24 nodes
- [x] Show Load More button
- [x] Load more nodes on click
- [x] Auto-load on scroll
- [x] Back to Top button functionality

## Troubleshooting

| Problem | Solution |
|---------|----------|
| Tests fail to connect | Check that the backend is reachable at http://localhost:4000 |
| Elements not found | Increase the timeout in cypress.config.ts |
| Elements not visible | The scroll container may need adjusting |
