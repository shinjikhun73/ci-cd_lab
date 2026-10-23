# ci-cd-lab

A small Express 5 web app with a Continuous Integration pipeline built on GitHub Actions.
Lab 1 – CI/CD, DevOps.

**Student:** Sokhunmony Soun · **Class:** CS-SE_G4

## Tech stack

- Node.js 24, JavaScript ES Modules
- Yarn 4 (package manager)
- Express 5 (web server)
- Mocha, Chai, Supertest (tests)
- ESLint (linting)
- c8 (code coverage)

## Endpoints

| Method | Path      | Response                        |
|--------|-----------|---------------------------------|
| GET    | `/`       | `Hello, GitHub Actions!`        |
| GET    | `/health` | `{ "status": "ok" }`            |

## Getting started

```bash
yarn install
yarn start        # http://localhost:3000
```

## Scripts

| Command         | What it does                                       |
|-----------------|----------------------------------------------------|
| `yarn start`    | Start the server (uses `PORT`, default 3000)       |
| `yarn lint`     | Run ESLint                                         |
| `yarn test`     | Run the Mocha test suite                           |
| `yarn coverage` | Run tests with c8; HTML report in `coverage/`      |

## Continuous Integration

The workflow in `.github/workflows/ci.yml` runs on every push to `main` and on
pull requests targeting `main`. It:

1. Checks out the code and enables Corepack (Yarn 4)
2. Sets up Node.js 24 with Yarn caching
3. Installs dependencies with `yarn install --immutable`
4. Runs ESLint, the tests, and coverage
5. Uploads the HTML coverage report as the `code-coverage-report` artifact

## Project structure

```text
ci-cd-lab/
├── .github/workflows/ci.yml   # CI pipeline
├── test/test.js               # Mocha tests
├── app.js                     # Express app (routes)
├── server.js                  # Starts the server
├── eslint.config.js           # ESLint flat config
├── .yarnrc.yml                # Yarn config (node-modules linker)
└── package.json
```
