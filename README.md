# testing-action-check

Shared Github Actions for ioBroker testing workflows: Check and lint step

## Inputs

| Input                   | Description                                                                                                                                                                                          | Required? |      Default      |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- | :---------------: |
| `node-version`          | Node.js version to use in tests. Should be LTS.                                                                                                                                                      | ✔         |         -         |
| `install-command`       | Overwrite the default install command. When changing this, `package-cache` may need to be disabled.                                                                                                  | ❌        |    `'npm ci'`     |
| `package-cache`         | For which package manager dependencies should be cached. Set to `'false'` or `''` to disable caching. More documentation [here](https://github.com/actions/setup-node#caching-global-packages-data). | ❌        |      `'npm'`      |
| `type-checking`         | Set to `'true'` when the adapter should be type-checked                                                                                                                                              | ❌        |     `'false'`     |
| `type-checking-command` | Overwrite the default type checking command                                                                                                                                                          | ❌        | `'npm run check'` |
| `lint`                  | Set to `'true'` when the adapter has a linter configured                                                                                                                                             | ❌        |     `'false'`     |
| `lint-command`          | Overwrite the default lint command                                                                                                                                                                   | ❌        | `'npm run lint'`  |
| `test-command`          | Overwrite the default test command                                                                                                                                                                   | ❌        | `'npm run test:package'`  |


## Usage

```yml
# ... rest of your workflow ...

jobs:
  check-and-lint:
    runs-on: ubuntu-latest

    steps:
      - uses: ioBroker/testing-action-check@v1
        with:
          node-version: "14.x" # This should be LTS
          # type-checking: 'true' # optional
          # lint: 'true' # optional

  # ... other jobs
```
