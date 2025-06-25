# 📊 E-commerce Test Reports

This repository hosts **automatically deployed test, code coverage, and security analysis reports** for each microservice in the **e-commerce backend**. Each service publishes its reports to a shared GitHub Pages site, providing a centralized and visualized view of code quality across the system.

---

## 🚀 Purpose

As part of CI/CD pipelines, each service generates:

- ✅ **Unit & Integration Test Results**
- ✅ **Code Coverage Reports**
- ✅ **Security Vulnerability Reports** (via tools like OWASP Dependency-Check)

These reports are published via GitHub Actions to this repository's `gh-pages` branch and exposed through GitHub Pages.

This enables:

- 📈 Continuous visibility into service health
- 🧪 CI feedback for developers
- 🔍 Auditable security reports
- 📊 Centralized quality reporting

---

## 🛠️ Architecture Overview

### 📤 How Reports Are Published

1. **Each microservice runs CI** using a shared [reusable workflow](https://github.com/AlexisRodriguezCS/ecommerce-infra) that:
    - Runs tests and generates reports
    - Uploads reports as artifacts
    - Triggers a `repository_dispatch` to this repo with a `service` payload

2. **This repo receives the dispatch** and:
    - Downloads the artifacts
    - Organizes them under `public/{service}/...`
    - Pushes to `gh-pages` using [peaceiris/actions-gh-pages](https://github.com/peaceiris/actions-gh-pages)

3. **GitHub Pages serves reports at:**
    ```
    https://alexisrodriguezcs.github.io/test-repo/<service>/
    ```

Each service's reports are organized like:

```
/<service>/
  ├── test/       ← HTML test reports
  ├── coverage/   ← Code coverage output
  └── security/   ← OWASP / dependency-check HTML report
```
---

## 📄 Example Report URLs

- [auth-service test reports](https://alexisrodriguezcs.github.io/test-reports/auth-service/test/)
- [auth-service coverage](https://alexisrodriguezcs.github.io/test-reports/auth-service/coverage/)
- [auth-service security](https://alexisrodriguezcs.github.io/test-reports/auth-service/security/)

---

## 🧱 Related Services

- **Infrastructure & Core Services**
    - [ecommerce-infra](https://github.com/AlexisRodriguezCS/ecommerce-infra) — Infrastructure setup with Docker, CI/CD, ELK logging, Postman, and documentation
    - [ecommerce-config-repo](https://github.com/AlexisRodriguezCS/ecommerce-config-repo) — Git repo for configs
    - [ecommerce-config-server](https://github.com/AlexisRodriguezCS/ecommerce-config-server) — Centralized configuration service (this repo)
    - [ecommerce-discovery-server](https://github.com/AlexisRodriguezCS/ecommerce-discovery-server) — Eureka-based service registry
    - [ecommerce-api-gateway](https://github.com/AlexisRodriguezCS/ecommerce-api-gateway) — API gateway with routing, JWT validation, and rate limiting
    - [ecommerce-test-reports](https://github.com/AlexisRodriguezCS/ecommerce-test-reports) — GitHub Pages deployment of HTML test, code coverage, and security reports for each microservice

- **Microservices**
    - [ecommerce-auth-service](https://github.com/AlexisRodriguezCS/ecommerce-auth-service) — User authentication and JWT management
    - [ecommerce-user-service](https://github.com/AlexisRodriguezCS/ecommerce-user-service) — User profile management and account details
    - [ecommerce-product-service](https://github.com/AlexisRodriguezCS/ecommerce-product-service) — Product catalog creation, updates, and search
    - [ecommerce-inventory-service](https://github.com/AlexisRodriguezCS/ecommerce-inventory-service) — Inventory tracking and stock adjustments
    - [ecommerce-order-service](https://github.com/AlexisRodriguezCS/ecommerce-order-service) — Order processing and checkout workflows
    - [ecommerce-payment-service](https://github.com/AlexisRodriguezCS/ecommerce-payment-service) — Secure payment processing
    - [ecommerce-notification-service](https://github.com/AlexisRodriguezCS/ecommerce-notification-service) — Email and SMS notifications for order events

---

## 📬 Contact

Maintained by [Alexis Rodriguez](https://github.com/AlexisRodriguezCS)