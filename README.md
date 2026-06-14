

## 🚀 Features

- ✅ TypeScript-based Playwright tests
- ✅ Page Object Model (POM) for maintainability
- ✅ Parallel execution
- ✅ Cross-browser support (Chromium, Firefox, WebKit)
- ✅ Allure reporting (HTML, CI artifacts, and GitHub Pages)
- ✅ Docker support for consistent CI/CD runs
- ✅ CI/CD via GitHub Actions (with Docker)
- ✅ GitHub Pages publishing for Allure reports

---

## 🧪 Running Tests Locally

```bash
# Install dependencies
npm ci

# Install Playwright browsers
npx playwright install

# Run all Playwright tests (headless)
npm test

# Run in headed mode
npm run test:headed

# Generate Allure report
npm run allure:generate

# Open Allure report in browser
npm run allure:open
```

---

## 🐳 Running Tests in Docker

Build and run tests in a Docker container (as in CI):

```bash
# Build Docker image
docker build -t my-playwright-runner -f DockerFile.playwright .

# Run tests (Allure report will be generated inside the container)
docker run --rm -v $(pwd)/allure-report:/app/allure-report my-playwright-runner npm run test:allure
```

---

## 📦 NPM Scripts

```json
"scripts": {
  "test": "npx playwright test",
  "test:headed": "npx playwright test --headed",
  "test:allure": "npx playwright test && npm run allure:generate",
  "allure:generate": "allure generate --clean allure-results -o allure-report",
  "allure:open": "allure open allure-report"
}
```

## ✅ GitHub Actions CI/CD

This project uses **GitHub Actions** to automate test execution and reporting.

### 📍 When it Runs

- On every push to `main`, `qa`, `dev`, or any `feature/*` branch
- On every pull request to those branches
- Manually via workflow dispatch

### 📁 Workflow Location

.github/workflows/playwright.yml

### 🐳 Docker in CI

- Builds and runs tests inside a Docker container for consistency
- Generates and uploads Allure reports as CI artifacts

### 📂 CI Artifacts

- 🧪 `playwright-report/` — HTML report of test run
- 📊 `allure-results/` — Raw Allure results
- 📁 `allure-report/` — Rich HTML Allure report (on demand)

---
angatisetty
