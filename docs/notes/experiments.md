# Experiments

[Experiments](https://en.wikipedia.org/wiki/A/B_testing) are used to test the features that aren't ready for production purposes yet.

By default, experiments are sent in the `READY` gateway event and they may be enabled/disabled manually in the client settings.

## How to enable

The following requirements must be met in order to enable the experimental overrides in the client settings:

  1. You must be the Discord Staff `(public_flags = 1 >> 0)`
  2. `RELEASE_CHANNEL` in `GLOBAL_ENV` must be `staging`
