<p align="center">
  <a href="http://nestjs.com/" target="blank"><img src="https://nestjs.com/img/logo-small.svg" width="200" alt="Nest Logo" /></a>
</p>

[circleci-image]: https://img.shields.io/circleci/build/github/nestjs/nest/master?token=abc123def456
[circleci-url]: https://circleci.com/gh/nestjs/nest

  <p align="center">A progressive <a href="http://nodejs.org" target="_blank">Node.js</a> framework for building efficient and scalable server-side applications.</p>
    <p align="center">

## Description

Nest.js and RabbitMQ for long processes

## Dockernize
```bash
Up:
$ docker-composer up -d

Down:
$ docker-compose down --rmi all -v --remove-orphans
```

## Development

Worker: http://localhost:3000  
RabbitMQ: http://localhost:15672  
(u: admin, p: password@01)