# QA Automation Suite — Playwright · AI Agent · k6 · gRPC

End-to-end, performance, and gRPC service validation automation framework, featuring an integrated AI agent for assisted test case generation.

## 🧩 Tech Stack

| Area | Tool |
|---|---|
| E2E / UI Testing | Playwright (TypeScript) |
| gRPC Services Testing | Integrated gRPC client |
| Performance Testing | k6 |
| AI Test Generation | Agent powered by the Anthropic API |
| CI/CD | GitHub Actions + Jenkins |
| Language | TypeScript / Node.js |

## 📁 Project Structure

```
.
├── .github/workflows/    # CI pipelines (GitHub Actions)
├── agent/                # AI agent for test generation
├── k6-performance/       # Load/performance test scripts (k6)
├── tests/                # Playwright test suites (E2E / gRPC)
├── util/                 # Shared utilities and helpers
├── .env.dev              # Environment variables - Development
├── .env.qa               # Environment variables - QA
├── connect-cdp.js        # Chrome DevTools Protocol connection
├── Jenkinsfile           # Jenkins CI/CD pipeline
├── playwright.config.ts  # Playwright configuration
├── tsconfig.json         # TypeScript configuration
└── package.json
```

## ⚙️ Prerequisites

- Node.js 18+
- npm
- k6 installed locally ([installation guide](https://grafana.com/docs/k6/latest/set-up/install-k6/))
- Access to the target gRPC services (endpoints configured in `.env.dev` / `.env.qa`)
- Anthropic API key (for the AI agent), set as an environment variable

## 🚀 Installation

```bash
git clone <REPO_URL>
cd <repo-name>
npm install
npx playwright install --with-deps
```

## 🔐 Environment Variables

Configure the appropriate environment before running the tests:

```bash
# .env.dev / .env.qa
BASE_URL=
GRPC_HOST=
GRPC_PORT=
ANTHROPIC_API_KEY=
```

> Select the target environment when running the scripts, e.g. using `dotenv-cli` or passing `--env-file`.

## ▶️ Running Tests

### E2E Tests (Playwright)

```bash
npx playwright test
```

Headed mode (debug):

```bash
npx playwright test --headed
```

HTML report:

```bash
npx playwright show-report
```

### gRPC Service Tests

```bash
npx playwright test tests/grpc
```

### Performance Tests (k6)

```bash
k6 run k6-performance/<script>.js
```

### AI Agent (test generation)

```bash
node agent/<entrypoint>.js
```

## 🤖 AI Agent

The `agent/` module uses the Anthropic API to assist in generating and/or analyzing test cases within the Playwright framework, speeding up the creation of new scenarios and the maintenance of the existing suite.

## 🔄 CI/CD

- **GitHub Actions**: pipelines defined in `.github/workflows/`, running the suite on every push/PR.
- **Jenkins**: pipeline defined in `Jenkinsfile` for integration in on-premise/corporate environments.

## 📊 Reports

- Playwright: native HTML report (`playwright-report/`)
- k6: standard output metrics / integrable with Grafana
