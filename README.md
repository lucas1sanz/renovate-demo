# Renovate Demo

## Authentication

You need to select a user account for `renovate` to assume the identity of, and generate a Personal Access Token. It is recommended to be `@renovate-bot` if you are using a self-hosted server and can pick any username you want.
It is also recommended that you configure `config.gitAuthor` with the same identity as your Renovate user, e.g. like `"gitAuthor": "Renovate Bot <bot@renovateapp.com>"`.

### GitLab CE/EE

First, [create a personal access token](https://docs.gitlab.com/ee/api/README.html#personal-access-tokens) for the bot account (select "api" scope).
Configure it either as `token` in your `config.js` file, or in environment variable `RENOVATE_TOKEN`, or via CLI `--token=`.
Don't forget to configure `platform=gitlab` somewhere in config.

## Running with Docker

You need to create a file named `config.js`:

```js
module.exports = {
  "token": "<your-personal-token",
  "repositories": [ // the repos you want to scan
    "lucas1sanz/renovate-demo"
  ]
};
```

Then run:

```sh
$ docker run --rm -v "/path/to/your/config.js:/usr/src/app/config.js" renovate/renovate
```