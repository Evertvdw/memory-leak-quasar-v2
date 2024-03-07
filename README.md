# Quasar App (memory-leak-test-v2)

A demo project to demonstrate a memory leak when using `vue-i18n`. During development I cannot see this issue but when running the production build it will become visible.

## Reproduction

1. Install the dependencies `yarn install`
2. Build the project `yarn run build`
3. Run the project `yarn run start`

The server will now run at `localhost:9100`. You can fire off 100 request in sequence by running `yarn run load`. The server will log the initial and current memory usage on every request. It will go down by a bit from time to time but it will never go back to it's initial memory usage and grow slowly over time.

Compared to the [memory-leak-quasar-v1](https://github.com/Evertvdw/memory-leak-quasar-v1) which will drop to its initial memory usage from time to time.

## Packages used in this repo

quasar - 2.14.6
@quasar/app-vite - 2.0.0-beta.4
vue - 3.4.21
vue-router - 4.3.0
vite - 5.1.5
@intlify/unplugin-vue-i18n - 2.0.0
vue-i18n - 9.10.1

## Disabling boot file 'i18n' will not result in a memory leak

If you comment out line 27 inside the `quasar.config.ts` and run the reproduction again you will not see the memory issue, so something with regards to using i18n is causing this.
