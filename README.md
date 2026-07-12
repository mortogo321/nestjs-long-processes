# NestJS Long-Running Process Scaffold (RabbitMQ)

A NestJS monorepo scaffold for offloading long-running work out of the HTTP request/response cycle using RabbitMQ. It sets up a multi-app workspace (`producer`, `consumer`, `worker`) plus a shared RabbitMQ client module, as the foundation for a producer -> queue -> worker pipeline.

## What's inside

- Nest CLI monorepo with three separately deployable apps: `producer`, `consumer`, `worker`
- Shared `RmqModule` / `RmqService` (`libs/common`) that registers a RabbitMQ client per app via `@nestjs/microservices`, with manual message acknowledgment and persistent messages
- RabbitMQ connection URL and queue names are configuration-driven via `@nestjs/config`
- Docker Compose setup that runs the `worker` app alongside a RabbitMQ broker (management UI included)

## Current state

This is infrastructure scaffolding rather than a finished pipeline: the shared RabbitMQ module, config wiring, and Docker setup are in place, but the `producer`, `consumer`, and `worker` controllers currently only expose the default Nest starter endpoint. The actual message publish/consume logic between the apps has not been wired up yet.

## Tech stack

- NestJS (`@nestjs/common`, `@nestjs/core`, `@nestjs/microservices`, `@nestjs/platform-express`, `@nestjs/config`)
- RabbitMQ via `amqplib` and `amqp-connection-manager`
- TypeScript, Jest for unit tests

## Quickstart

```bash
yarn install

# copy the env template for the worker app
cp apps/worker/.env.example apps/worker/.env

# start the worker app + RabbitMQ broker
docker compose up -d
```

- Worker app: http://localhost:3000
- RabbitMQ management UI: http://localhost:15672 (`admin` / `password@01`)

To run an individual app directly (without Docker):

```bash
yarn start:dev worker   # or producer / consumer
```

## Tests

```bash
yarn test
```
