# Strapi example

This example deploys self-hosted version of [Strapi](https://strapi.io/). Internally it uses a PostgreSQL database to store the data.

[![Deploy on Railway](https://railway.app/button.svg)](https://railway.app/new/template/strapi?referralCode=milo)

## ✨ Features

- Strapi
- Postgres

## 💁‍♀️ How to use

- Click the Railway button 👆
- Add the environment variables
- Media will automatically be persisted between deploys!

## 💻 Developing locally

Use Node.js 24 LTS (`nvm install && nvm use`) and pnpm 10.28.2. The Node
engine and package manager are pinned in `package.json` for deployment too.
Install reproducibly with `pnpm install --frozen-lockfile` and build with
`pnpm build`. Keep `pnpm-lock.yaml` as the sole dependency lockfile.

Strapi 5.52.3 requires React 17/18 and React Router 6; do not upgrade these
to React 19 or React Router 7 until Strapi declares support. All direct
`@strapi/*` packages should stay on the same pinned release.

Before starting an upgraded app, back up PostgreSQL and test against a copy.
Development uses `DATABASE_PUBLIC_URL`; production uses `DATABASE_URL`.
Verify admin login, image uploads, draft/publish, and the website's blog API
requests before deploying. A successful admin build does not test the database.

When developing locally this Strapi template will connect to the Postgres server from its public [TCP Proxy](https://docs.railway.app/deploy/exposing-your-app#tcp-proxying)

- Enable the feature flag `Template Service Eject` in the [Feature Flags](https://railway.app/account/feature-flags) menu
- Within the service settings of the Strapi service click the `Eject` button on the upstream repository
- Clone that newly created repository locally
- Install Strapi's dependencies with `pnpm install --frozen-lockfile`
- Install the Railway CLI
    - Instructions for that can be found [here](https://docs.railway.app/develop/cli#installation)
    - If this is your first time using the CLI make sure to login with `railway login`
- Within the local repository run `railway link` to link the local repository to the Strapi service on Railway
- Start Strapi for development with `railway run pnpm develop`
    - This command will run Strapi in development mode with the service variables available locally
- Open your browser to `http://127.0.0.1:1337/admin`

## 📝 Notes

- After your app is deployed, visit the `/admin` endpoint to create your admin user.
- Re-run `pnpm audit` after upgrades; transitive findings may require upstream Strapi fixes.
