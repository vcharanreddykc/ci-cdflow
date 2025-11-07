## 🧱 1️⃣ Workflow-Level Keywords

Define when and how the workflow runs.

| **Keyword** | **Purpose** | **Example** |
|--------------|-------------|--------------|
| `name` | Gives the workflow a name (shown in Actions tab). | `name: CI Pipeline` |
| `on` | Defines the trigger (event) for the workflow. | `on: push`, `on: workflow_dispatch` |
| `permissions` | Sets token access (fine-grained permissions). | `permissions: contents: read` |
| `env` | Defines global environment variables for all jobs. | `env: { ENVIRONMENT: dev }` |
| `defaults` | Defines default settings for steps (like `run: shell`). | `defaults: run: shell: bash` |

---

## ⚙️ 2️⃣ Job-Level Keywords

Define how each job behaves.

| **Keyword** | **Purpose** | **Example** |
|--------------|-------------|--------------|
| `jobs` | Main container for all jobs. | `jobs: build:` |
| `runs-on` | Specifies the runner OS/environment. | `runs-on: ubuntu-latest` |
| `needs` | Defines job dependencies (execution order). | `needs: build` |
| `if` | Conditional job execution. | `if: github.ref == 'refs/heads/main'` |
| `strategy` | Creates matrix builds (multiple OS/versions). | `strategy: matrix: node: [14, 16, 18]` |
| `env` | Environment variables specific to this job. | `env: { REGION: us-east-1 }` |
| `timeout-minutes` | Limits job execution time. | `timeout-minutes: 10` |
| `continue-on-error` | Allows job to fail but continue workflow. | `continue-on-error: true` |

---

## 🧩 3️⃣ Step-Level Keywords

Define actions or shell commands within jobs.

| **Keyword** | **Purpose** | **Example** |
|--------------|-------------|--------------|
| `steps` | List of actions or commands. | `steps:` |
| `uses` | Use a prebuilt GitHub Action. | `uses: actions/checkout@v4` |
| `run` | Run a command or script. | `run: npm install` |
| `name` | Name of the step (for readability). | `name: Build Project` |
| `id` | Assigns an ID to reference outputs later. | `id: build` |
| `with` | Inputs passed to an action. | `with: { node-version: 18 }` |
| `env` | Environment variables for this step. | `env: { IMAGE_TAG: latest }` |
| `if` | Step-level conditional execution. | `if: always()` |

---

## 🔄 4️⃣ Reusable Workflow Keywords

Used when modularizing or chaining workflows.

| **Keyword** | **Purpose** | **Example** |
|--------------|-------------|--------------|
| `uses (workflow)` | Call another reusable workflow. | `uses: org/repo/.github/workflows/deploy.yml@main` |
| `with` | Pass inputs to the called workflow. | `with: { environment: dev }` |
| `secrets` | Pass secrets to the called workflow. | `secrets: inherit` |

---

## 🔒 5️⃣ Contexts and Expressions

Used for dynamic logic and referencing data.

| **Type** | **Example** | **Description** |
|-----------|-------------|-----------------|
| `${{ github.event_name }}` |  | Access GitHub event data. |
| `${{ env.VARIABLE }}` |  | Use an environment variable. |
| `${{ job.status }}` |  | Get job result status. |
| `${{ secrets.AWS_ACCESS_KEY_ID }}` |  | Access a secret securely. |
| **Functions** | `contains()`, `startsWith()`, `success()`, `failure()`, `always()` | Used inside `if:` conditions for logic control. |

---

📘 **Tip:**  
These keywords define the structure of every GitHub Actions pipeline — from workflow triggers to job dependencies, conditional logic, and reusability.
