# Experiments

[Experiments](https://en.wikipedia.org/wiki/A/B_testing) is used to test features that not yet ready to production.

By default, experiments sent in the READY gateway event, but can be changed manually in the client settings.

## How to enable manual experiment changing

The following requirements must be met in order to enable the experiment overrides in the client settings:  

  1. You're need to be Discord Staff (public_flags = 1 >> 0)
  2. RELEASE_CHANNEL in GLOBAL_ENV must be "staging"
