# Fly PgVector

Open-source vector similarity search for Postgres

Fly PgVector leverages the flexibility of Fly's [Postgres Flex](https://github.com/fly-apps/postgres-flex) as a base, integrating with its scalable and configurable environment to store and manage vector data efficiently.

Store your vectors with the rest of your data. Supports:

- exact and approximate nearest neighbor search
- single-precision, half-precision, binary, and sparse vectors
- L2 distance, inner product, cosine distance, L1 distance, Hamming distance, and Jaccard distance
- any [language](#languages) with a Postgres client

Plus [ACID](https://en.wikipedia.org/wiki/ACID) compliance, point-in-time recovery, JOINs, and all of the other [great features](https://www.postgresql.org/about/) of Postgres

[![Build Status](https://github.com/pgvector/pgvector/actions/workflows/build.yml/badge.svg)](https://github.com/pgvector/pgvector/actions)
## Installation

### Fly Setup

To deploy pgvector on Fly, start by installing the Fly CLI and setting up your Fly account:

1. Download and install the Fly CLI from the [Fly official website](https://fly.io/docs/getting-started/installing-flyctl/).
2. Open your terminal and run `flyctl auth signup` to create a new Fly account or `flyctl auth login` to log into an existing account.
3. Once logged in, create a new Fly Postgres app by running `fly postgres`. This command sets up a new Postgres instance on Fly. Note at this stage this is still the base Fly Postgres image instead the one with pgvector.
4. After setting up your Fly Postgres app, copy the output connection string provided. Store this string securely as you will need it to connect to your database. Consider using a password manager or another secure method to keep this information safe.
5. Configure your app by modifying the `fly.toml` file, which was generated during the app creation process, to suit your deployment needs. This file includes settings for regions, resources, and more.
6. To authenticate your Fly CLI with the Fly platform, you need an API token. You can obtain this token by navigating to your Fly dashboard. Go to the 'Account Settings' and click on 'Access Tokens'. Create a new token if you don't have one already, and copy it.
7. To set this token as an environment variable in GitHub Actions, navigate to your repository on GitHub. Go to 'Settings' > 'Secrets' > 'Actions'. Click on 'New repository secret'. Name the secret `FLY_API_TOKEN` and paste your copied token into the value field. This will securely store your token and make it available in your GitHub Actions workflows.
