# PHP (Symfony) service for Kubernetes on Wodby

Build and run PHP (Symfony) applications on Kubernetes with Wodby.

This repository defines the Wodby service manifests and operational
configuration for PHP (Symfony).

- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Start with a boilerplate

Use one of the boilerplates exposed by this service to start with compatible
build configuration and Wodby CI:

- [Symfony on Wodby](https://github.com/wodby/symfony-boilerplate)

## Wodby stacks using this service

- [Symfony application stack](https://github.com/wodby/stack-symfony)

## Service overview

| Property | Manifest configuration |
| --- | --- |
| Service name | `symfony-php` |
| Type | Application service |
| Inherits from | [`php`](https://github.com/wodby/service-php) with version constraint `^3.0.0` |
| Versions | Inherited from `php`: `8.5` by default; also available: `8.4`, `8.3`, `8.2` |
| Workloads | `main` (Deployment), primary, inherited from `php` |
| Containers | `php` using `wodby/php`, build target |
| Service links | Database and mail, optional, with `DATABASE_URL` and `MAILER_DSN` |
| Application build | Git source connection enabled; boilerplates: Symfony on Wodby |
| Configuration | 1 generated token (`APP_SECRET`) |
| Operations | 1 post-deployment action (Doctrine migrations) |
| Development workspace | Inherited from `php`, with migrations during setup |

The Wodby Symfony boilerplate requires PHP `^8.4`. PHP 8.2 and 8.3 remain
available when using a connected repository.

## Use this service

Use this service through [Symfony application stack](https://github.com/wodby/stack-symfony), or reference `symfony-php` from a
custom Wodby stack.

A service is a reusable component and does not deploy by itself. The stack
defines its links, settings, versions, resources, and relationship to the rest
of the application.

## Maintain a custom version

1. Fork this repository.
2. Edit the service manifest and referenced files.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference the service from a stack manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time.

Validate the manifests with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
