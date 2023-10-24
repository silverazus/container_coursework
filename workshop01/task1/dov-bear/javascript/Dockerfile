From node:21

LABEL name=bearjs

workdir /javascript
#inside /app
copy package.json .
copy package-lock.json .
copy main.js main.js
copy public public
copy views views

run npm ci

env APP_PORT=3000 INSTANCE_NAME='javascript dov bear' INSTANCE_HASH=abc123

healthcheck --interval=30s --timeout=5s --retries=3 \
   cmd curl -s http://localhost:${APP_PORT}/health || exit 1


expose ${APP_PORT}
EntryPoint node main.js 