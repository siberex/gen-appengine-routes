# Google AppEngine Static Handlers Generator

Using static directory as an input automatically generates static handlers yaml to include in the main GAE deployment config.

# Usage

```bash
# This will create routes.yaml
npm run static
```

app.yaml:

```yaml
# https://cloud.google.com/appengine/docs/standard/reference/app-yaml?tab=node.js#top
runtime: nodejs22
instance_class: F1

automatic_scaling:
  min_instances: 0
  max_instances: 1
  max_idle_instances: 1
  max_pending_latency: 2500ms

entrypoint: node --enable-source-maps build/index.js

env_variables:
  NODE_ENV: production

default_expiration: "7d"

# Static routes are generated before `gcloud app deploy`
# Use `npm run static`
includes:
  - routes.yaml
```
