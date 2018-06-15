# Convivio Drupal Stack with Docker

This is a Docker stack for local Drupal development. Future versions may incorporate features for production environments, but for now this if for local development.

This stack is largely based on [Drupal4Docker](https://wodby.com/stacks/drupal/docs/) by [Wodby](https://wodby.com/) (GitHub repo: [wodby/docker4drupal](https://github.com/wodby/docker4drupal)), but with a Convivio flavour.

The stack is built to work pretty much out-of-the-box with the [Drupal Composer](https://github.com/drupal-composer/drupal-project) project.

## Usage

#### Assumptions:

- Docker is installed locally already.

To use this out-of-the-box:
- Your Drupal files are in ./web
  - Note: everything in the root directory of your instance is added as a [bind mount](https://docs.docker.com/storage/bind-mounts/) in your Docker stack Nginx and PHP containers.

### Getting started

#### Installation and configuration

1) Start a new Drupal Composer site to begin your project.
2) Download the [latest stable release](https://github.com/ConvivioTeam/Convivio-DrupalDocker/releases) of this repo.
    - unzip it to the root of your Drupal project.
3) **Copy .env.example » .env**
4) **Edit .env settings to suit your needs.** Most settings should be obvious and/or self-evident.
    - you should change `PROJECT_NAME` and `PROJECT_BASE_URL` for your project.
        - `PROJECT_NAME` is used to create a persistent data volume. It should be a unique name so that data for your project persists in your local dev environment.
        - You will be able to access your installation at `PROJECT_BASE_URL` when your stack is running.
    - The other thing you'll likely want to change is `NGINX_SERVER_ROOT`. If your project is does not have Drupal installed in `./web` (mounted at `/var/www/html/web`) then you should change this value as appropriate.

#### Start it up!

The Makefile and docker.mk included in this project.