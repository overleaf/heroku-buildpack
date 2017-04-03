# Overleaf Heroku buildpack

Based on https://github.com/nonrational/heroku-buildpack-hub-spoke

### Usage

For each app, set `APP_BASE` and `APP_DEPS` ENV vars, and add the buildpack.

When you push to the relevant app's heroku remote this buildpack will:
- move the contents of `APP_BASE` into the root of the project
- move each folder listed by `APP_DEPS` into the root of the project
- all other files (except the git dir) will then be removed

#### Locally

To test your Procfiles work when folders are moved:
- create files to represent env vars (`echo 'app1' > tmp/env/APP_BASE`, `echo 'shared' > tmp/env/APP_DEPS`)
- from a clone of this buildpack run (where `app_repo` is the directory of your monorepo):
  `bin/compile app_repo /tmp tmp/env`
