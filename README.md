

# **CI/CD Pipeline**

Continuous Integration (CI) and Continuous Delivery/Deployment (CD) together form the backbone of **modern DevOps practices**.
They automate testing, building, and deployment so that teams can **deliver software faster, safer, and more reliably**.

---

## 🧩 **1. Continuous Integration (CI)**

### 🧠 **The Problem**

Imagine you’re part of a big backend development team that’s been building a system for the last two years.
Every day, multiple developers push new code, fix bugs, and write tests. Two major types of work happen:

1. **Feature Implementation** – adding new functionality
2. **Testing** – writing and running tests (unit, integration, and end-to-end tests)

Now consider this:

* You wrote a feature and your tests passed on your local machine.
* But when you merged your changes, some *other developer’s code* broke.
* Or your machine wasn’t powerful enough to run all heavy tests (load, performance, etc.).
* Or you needed to set up multiple backend microservices to test integration — which takes hours.

Manually running every test for every change is slow and error-prone.

### ✅ **The Solution – Continuous Integration**

**Continuous Integration (CI)** automates the process of building and testing code every time changes are made.
It ensures your new code integrates properly with the existing codebase.

**How CI works (Step-by-Step):**

1. Developer writes a new feature.
2. Writes unit/integration tests for it.
3. Commits and pushes code to a shared repository (e.g., GitHub, GitLab, Bitbucket).
4. **CI pipeline** automatically starts:

   * Clones the repo
   * Installs dependencies
   * Runs linters (code quality checks)
   * Builds the project
   * Runs **unit tests**, **integration tests**, **performance tests**, and **end-to-end tests**

If **all tests pass**, the feature is considered stable and ready for delivery.

If **any test fails**, the developer is notified immediately — preventing broken code from reaching production.

> 🧪 **Example:**
> Suppose you push code to GitHub. GitHub Actions automatically runs your test suite.
> If your “Card Component” test passes but another dependent test fails, the CI system alerts you right away — so you can fix it before merging.

### ⚙️ **CI Pipeline**

A **CI pipeline** is the automation setup that runs the above steps in sequence.
You define it using a configuration file (like a `.yml` file) that describes the workflow.

**In short:**

> Continuous Integration ensures that your new code integrates smoothly with the existing system — through automated testing and validation.

### 🌍 **Used By:**

Big tech companies like **Google, Microsoft, Amazon, Netflix,** and **Meta** rely on CI pipelines to ensure every change is tested before deployment.

### 💡 **Benefits of CI**

* Detect bugs **early** in development.
* Prevent “integration hell” (broken code after merge).
* Improve code quality and reliability.
* Automate repetitive testing tasks.
* Ensure team collaboration without conflicts.

---

## 🚢 **2. Continuous Delivery (CD)**

Once CI approves your code (all tests passed ✅), the next step is **delivering** it to various environments.

### 🧠 **The Problem**

In real-world software projects, you don’t directly deploy to production after testing.
There are **multiple environments** to ensure quality and stability:

| Environment            | Purpose                                                      |
| ---------------------- | ------------------------------------------------------------ |
| **Dev**                | Developer’s local setup – writing and testing new code.      |
| **Test / QA**          | Tested by QA engineers for bugs and quality assurance.       |
| **Pre-Prod / Staging** | Replica of production; used for final checks before go-live. |
| **Production**         | The real environment where users interact with the system.   |

Without automation, moving code across these environments is manual and time-consuming — especially in large teams with multiple features in progress.

### ✅ **The Solution – Continuous Delivery**

**Continuous Delivery (CD)** automates the **release process** so that after CI testing is done,
your application can be automatically deployed to **staging**, **QA**, or even **production** with a single click or automatically (if Continuous Deployment is set up).

> ⚙️ **Continuous Delivery ensures your code is always in a deployable state.**

**Workflow Example:**

1. Developer pushes code → CI runs tests.
2. CI passes → CD automatically deploys code to a **staging/pre-prod** environment.
3. QA team tests it → if approved → deployed to **production**.

This process ensures that your code is **always ready for release**, without human errors or delays.

---

## 🔁 **3. Continuous Deployment**

> 💡 *Continuous Deployment* is an extension of Continuous Delivery.

In Continuous Delivery — deployment to production is **manual**.
In Continuous Deployment — deployment to production is **fully automated** after passing tests.

That means once your code passes all stages, it’s automatically released to users.
(Used by companies like Facebook and Amazon who release multiple times a day.)

---

## 🧱 **4. What Is a Pipeline?**

A **pipeline** is simply a **series of automated steps** that code passes through — from writing → testing → deployment.

**Example Pipeline Flow:**

```
1️⃣ Pull code from GitHub repository
2️⃣ Install dependencies
3️⃣ Run linting (code quality checks)
4️⃣ Run unit and integration tests
5️⃣ Build the project
6️⃣ Deploy to staging environment
7️⃣ Deploy to production (manual or automatic)
```

Each of these steps (build, test, deploy) is called a **stage** in your CI/CD pipeline.

---

## 🧰 **5. Common CI/CD Tools**

| Tool                 | Description                                                             |
| -------------------- | ----------------------------------------------------------------------- |
| **GitHub Actions**   | Built-in automation for GitHub repos; easy to use YAML-based workflows. |
| **GitLab CI/CD**     | Integrated into GitLab; supports pipelines, runners, and auto-deploys.  |
| **Jenkins**          | Open-source automation server; highly customizable with plugins.        |
| **Travis CI**        | Popular with open-source projects; simple YAML config.                  |
| **CircleCI**         | Cloud-based, fast, and easy setup for small and large teams.            |
| **Azure DevOps**     | Microsoft’s CI/CD platform for cloud and enterprise apps.               |
| **AWS CodePipeline** | Amazon’s native CI/CD service for AWS-based deployments.                |

---

## 🧾 **6. YAML File in CI/CD**

**YAML** = *YAML Ain’t Markup Language*
It’s used to define pipeline configurations.

### 🧩 **Features of YAML**

* Human-readable and easy to understand.
* Used for **configuration and data serialization**.
* Strict indentation (spaces, not tabs!).
* Commonly used in CI/CD tools like GitHub Actions, GitLab CI, and Jenkins.

**Example GitHub Actions YAML:**

```yaml
name: CI Pipeline

on:
  push:
    branches: [ "main" ]

jobs:
  build-and-test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

---

## 💪 **7. Benefits of CI/CD**

* 🕒 **Faster Delivery:** Automates the entire process from coding to deployment.
* 🧠 **Early Bug Detection:** Issues caught before reaching production.
* 🧱 **Consistency:** Every change goes through the same reliable steps.
* 🔐 **Improved Security:** Code scanning and secret management before release.
* 🔄 **Continuous Feedback:** Developers get quick feedback after each commit.
* 💰 **Reduced Costs:** Less manual intervention → fewer production errors.
* 🌍 **Better Collaboration:** Developers, testers, and ops work in sync.

---

## ⚡ **8. CI/CD in Production – Best Practices**

1. Use **feature branches** and **pull requests** for clean code integration.
2. Keep **pipelines fast** — parallelize tests where possible.
3. Add **code quality tools** (like ESLint, SonarQube).
4. Store secrets securely using **Vaults** or **Environment Variables**.
5. Implement **rollback strategies** — in case a deployment fails.
6. Keep your CI/CD configuration under **version control**.
7. Monitor deployments with **Prometheus, Grafana, or Datadog**.

---

## 🎯 **Conclusion**

**Continuous Integration** ensures your code works well with others.
**Continuous Delivery/Deployment** ensures it’s safely and quickly deployed to users.

Together, they form a **CI/CD pipeline**, which is the foundation of modern **DevOps automation** — enabling teams to build, test, and release high-quality software **at scale and speed**.

---

# ⚙️ **GitHub Actions**

GitHub Actions is a **powerful automation tool built directly into GitHub**.
It allows developers to **automate workflows** such as building, testing, and deploying projects right from their GitHub repositories.

You can think of it as a way to say:

> “When something happens in my repository (like a code push), do these steps automatically.”

---

## 🧠 **Key Terminologies**

Let’s break down the most important concepts you’ll use in GitHub Actions 👇

### 1. **Workflow**

* A **workflow** is an automated process defined inside your repository.
* It’s made up of **one or more jobs**, and each job contains steps to execute.
* Workflows are defined in a **YAML configuration file** inside the `.github/workflows` folder.
* Example workflows:

  * Run tests whenever code is pushed.
  * Build and deploy app on every new release.

> 📁 Example file path:
> `.github/workflows/ci.yml`

---

### 2. **Job**

* A **job** is a group of steps that run together on the **same virtual machine (runner)**.
* Each job runs in a clean environment (like a fresh Ubuntu or Windows VM).
* By default, jobs run **sequentially**, but you can configure them to run in **parallel**.

> 🧩 Example:
> One job might build your app, another might run tests, and a third could deploy it.

---

### 3. **Step**

* A **step** is an individual task that runs inside a job.
* Steps can either:

  * Run **commands** (like `npm install` or `echo "Hello"`)
  * Or **use actions** (reusable commands provided by GitHub or the community).

> 💡 Example step:
>
> ```yaml
> - name: Run tests
>   run: npm test
> ```

---

### 4. **Action**

* An **action** is a **reusable unit of code** that performs a specific task in your workflow.
* You can use:

  * **Pre-built actions** from the GitHub Marketplace (like `actions/checkout`).
  * Or create your **own custom actions**.

> 🧠 Think of actions like “functions” in a workflow.
> You can call them inside steps to save time and avoid repeating the same logic.

> 💡 Example action:
>
> ```yaml
> - name: Checkout code
>   uses: actions/checkout@v4
> ```

---

## 🔄 **How Workflows Are Structured**

Here’s how everything fits together:

```
Action → Step → Job → Workflow
```

Or in words:

> **Actions** are combined into **Steps**,
> **Steps** form **Jobs**,
> **Jobs** together make a **Workflow**.

---

## 🏗️ **Workflow Folder Structure**

GitHub automatically looks for workflows in a specific folder path.

✅ **Correct folder structure:**

```
ci-cd_pipeline/
├── .github/
│   └── workflows/
│       └── helloworld.yml
```

🚫 **Wrong folder structure:**

```
ci-cd_pipeline/github-action-workflow/.github/workflows/helloworld.yml
```

> ❗ If your `.yml` file is not in `.github/workflows`, GitHub Actions won’t detect or trigger it.

---

## ⚙️ **How GitHub Actions Works**

A typical GitHub Actions workflow goes through these stages:

1. **Trigger Event** – Something happens in your repo (e.g., `push`, `pull_request`, or a scheduled `cron` job).
2. **Runner Setup** – GitHub starts a fresh virtual machine (like `ubuntu-latest` or `windows-latest`).
3. **Checkout Code** – The workflow clones your repository using the `actions/checkout` action.
4. **Install Dependencies** – Tools like Node.js, Python, Java, etc., are installed.
5. **Build Project** – Your source code is compiled or built.
6. **Run Tests** – Unit tests, integration tests, or any other validation runs.
7. **Deploy** (optional) – The app can be deployed to production, AWS, or other environments.

---

## 🧪 **Example: Hello World Workflow**

Here’s a simple example to start your first workflow.

**Folder Structure:**

```
Sample_Github_Action/
└── .github/
    └── workflows/
        └── helloworld.yml
```

**`helloworld.yml` content:**

```yaml
name: Hello World Workflow

# 1️⃣ Trigger workflow on any push to the main branch
on:
  push:
    branches: [ "main" ]

# 2️⃣ Define the job
jobs:
  hello_world:
    runs-on: ubuntu-latest   # or windows-latest / macos-latest

    steps:
      # Step 1: Checkout repository code
      - name: Checkout code
        uses: actions/checkout@v4

      # Step 2: Print a message
      - name: Print Hello World
        run: echo "Hello, GitHub Actions!"
```

### 🔍 **Explanation:**

* The workflow runs **every time** code is pushed to the `main` branch.
* It uses an **Ubuntu virtual machine** (`ubuntu-latest`).
* The job has two steps:

  1. **Checkout code** – pulls your repository files into the runner.
  2. **Print message** – runs a shell command to print text in the logs.

---

## ⚡ **Triggering Workflows (Events)**

Workflows are triggered by **events** in your repository.
Some common ones are:

| Event               | Description                                   |
| ------------------- | --------------------------------------------- |
| `push`              | Trigger when code is pushed to a branch.      |
| `pull_request`      | Trigger when a PR is opened or updated.       |
| `schedule`          | Run workflow on a schedule using cron syntax. |
| `workflow_dispatch` | Trigger manually from the GitHub UI.          |

> 💡 Example: Run a workflow every day at midnight
>
> ```yaml
> on:
>   schedule:
>     - cron: "0 0 * * *"
> ```

---

## 🖥️ **Choosing Runners (Operating Systems)**

You can run your workflow on different operating systems using the `runs-on` key.

| Platform | Example                   |
| -------- | ------------------------- |
| Ubuntu   | `runs-on: ubuntu-latest`  |
| Windows  | `runs-on: windows-latest` |
| macOS    | `runs-on: macos-latest`   |

> 🧠 These environments are **GitHub-hosted virtual machines**, meaning your code runs in GitHub’s secure infrastructure — not your local system.

---

## 🐞 **Common Mistakes (and Fixes)**

| Problem                        | Fix                                                                             |
| ------------------------------ | ------------------------------------------------------------------------------- |
| Workflow not triggering        | Make sure `.yml` file is under `.github/workflows/`.                            |
| Wrong indentation              | YAML is space-sensitive! Use **2 spaces** instead of tabs.                      |
| Invalid event syntax           | Check that your event name (e.g., `push`, `pull_request`) is spelled correctly. |
| Workflow doesn’t run on branch | Verify branch name matches (`main`, `master`, etc.)                             |

---

## 🧰 **Real-World Example – Node.js CI Pipeline**

```yaml
name: Node.js CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v4

      - name: Setup Node.js
        uses: actions/setup-node@v4
        with:
          node-version: 18

      - name: Install dependencies
        run: npm install

      - name: Run tests
        run: npm test
```

This workflow:

* Runs on **push or pull request** to the `main` branch.
* Uses Node.js 18.
* Installs dependencies and runs tests automatically.

---

## 🏁 **Summary**

| Concept      | Description                                             |
| ------------ | ------------------------------------------------------- |
| **Workflow** | A complete automation defined in YAML.                  |
| **Job**      | A collection of steps that run on a single runner.      |
| **Step**     | A single command or action in a job.                    |
| **Action**   | A reusable piece of code that performs a specific task. |
| **Runner**   | The virtual environment where jobs execute.             |

### In simple terms:

> GitHub Actions automates your development workflow —
> from **code push → test → build → deploy** —
> all happening **automatically** on GitHub’s cloud servers.

---

Excellent — you’re doing a great job building this step-by-step! 🙌
Your explanation of GitHub Actions events is good, but we’ll now make it **clearer, properly formatted, corrected, and more complete**.
I’ll fix syntax issues, expand on event types, and show practical examples so that **any beginner** can easily follow and understand it.

---

# ⚡ **Events That Trigger GitHub Workflows**


## 🧠 **What Are Events in GitHub Actions?**

An **event** is something that happens in a repository that can **start (trigger)** your workflow automatically.
These can include:

* 🟢 **Code-based events**

  * `push` → when someone pushes code to a branch.
  * `pull_request` → when a pull request is opened, synchronized, or merged.
  * `create` → when a branch or tag is created.
  * `delete` → when a branch or tag is deleted.

* 🟣 **Project management events**

  * `issues` → when an issue is opened, edited, labeled, or closed.
  * `fork` → when someone forks your repository.
  * `release` → when a new release is published.

* 🟠 **Manual and scheduled events**

  * `workflow_dispatch` → run workflow manually from the GitHub UI.
  * `schedule` → run automatically at a specific time (using **cron syntax**).

---

## ⚙️ **Example: Multi-Event Workflow**

Here’s an example of a GitHub Actions workflow triggered by **multiple events** (`push` and `pull_request`):

```yaml
name: "Multi-Event Pipeline"

# 🧩 Define events that trigger this workflow
on:
  push:                # Trigger when code is pushed
    branches:
      - master         # Only run for master branch
      - test           # Also run for test branch

  pull_request:        # Trigger when a PR targets master branch
    branches:
      - master

# 💼 Define jobs (what tasks to perform)
jobs:
  on-push:
    runs-on: ubuntu-latest
    steps:
      - name: "Running on master/test push"
        run: echo "Code pushed to master/test branch"

  on-pull-request:
    runs-on: ubuntu-latest
    steps:
      - name: "Running on master pull request"
        run: echo "Pull request created or updated for master"
```

---

## 🔍 **Explanation**

* The **`on:`** keyword defines which events will trigger the workflow.
* In this example:

  * When a **push** happens on the `master` or `test` branch → the workflow starts.
  * When a **pull request** targets the `master` branch → the workflow also starts.
* Both jobs (`on-push` and `on-pull-request`) are defined separately.
* Each job will run **independently** based on the event type.

---

## 🎯 **Running Specific Jobs Conditionally**

If you want to run **only certain jobs** based on which event triggered the workflow,
you can use the **`if:`** conditional expression.

```yaml
jobs:
  conditional-job:
    runs-on: ubuntu-latest
    if: github.event_name == 'push'
    steps:
      - name: "This runs only on push"
        run: echo "Triggered by a push event"

  pr-job:
    runs-on: ubuntu-latest
    if: github.event_name == 'pull_request'
    steps:
      - name: "This runs only on pull request"
        run: echo "Triggered by a pull request event"
```

> 💡 **Note:** Use a **single equals sign (`==`)** in YAML expressions, not triple (`===`) like in JavaScript.

### ✅ **Useful Conditional Contexts**

GitHub provides several built-in context variables you can use:

| Context             | Description                                                                      |
| ------------------- | -------------------------------------------------------------------------------- |
| `github.event_name` | The name of the event that triggered the workflow (`push`, `pull_request`, etc.) |
| `github.ref`        | The branch or tag that triggered the workflow                                    |
| `github.actor`      | The username who triggered the event                                             |
| `github.repository` | The full repo name (`user/repo`)                                                 |

> Example:
>
> ```yaml
> if: github.ref == 'refs/heads/master'
> ```

---

## 🧭 **Triggering Workflows Manually**

Sometimes, you may want to **run a workflow manually** — for example, to rebuild or redeploy your app.
For this, GitHub provides the **`workflow_dispatch`** event.

### 🧩 Example:

```yaml
name: "Manual Trigger Example"

on:
  workflow_dispatch:    # allows manual run from GitHub UI

jobs:
  manual-job:
    runs-on: ubuntu-latest
    steps:
      - name: "Manual trigger example"
        run: echo "This workflow was triggered manually!"
```

Once you add `workflow_dispatch`:

* Go to your repository → **Actions** tab → select the workflow → click **“Run workflow”**.
* You can even define **input fields** to pass custom data.

### ✨ Example with Inputs:

```yaml
on:
  workflow_dispatch:
    inputs:
      environment:
        description: 'Select environment to deploy'
        required: true
        default: 'staging'

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: "Deploy to environment"
        run: echo "Deploying to ${{ github.event.inputs.environment }}"
```

Now when you click **“Run workflow”**, you’ll see a dropdown asking for the environment name (e.g., `staging` or `production`).

---

## 🕒 **Triggering Workflows on Schedule**

You can also trigger workflows **automatically at specific times** using the **`schedule`** event and **cron syntax**.

### Example:

```yaml
on:
  schedule:
    - cron: "0 0 * * *"   # Runs every day at midnight (UTC)

jobs:
  nightly-build:
    runs-on: ubuntu-latest
    steps:
      - name: "Nightly build"
        run: echo "Running scheduled nightly build"
```

> 🧠 **Cron format:** `"minute hour day month day-of-week"`
> Example:
>
> * `"0 0 * * *"` → Every day at midnight
> * `"*/30 * * * *"` → Every 30 minutes
> * `"0 9 * * 1"` → Every Monday at 9 AM

---

## 🧩 **Common Events Cheat Sheet**

| Event               | Description                                | Typical Use Case               |
| ------------------- | ------------------------------------------ | ------------------------------ |
| `push`              | When new code is pushed to a branch        | Run tests or build app         |
| `pull_request`      | When a PR is opened/updated/merged         | Run CI checks before merge     |
| `workflow_dispatch` | Manual trigger from GitHub UI              | Manually deploy app            |
| `schedule`          | Runs automatically at a specific time      | Nightly builds, backups        |
| `release`           | When a new GitHub release is created       | Deploy a production version    |
| `issues`            | When an issue is opened, edited, or closed | Send Slack/Email notifications |
| `fork`              | When someone forks the repo                | Analytics or security alerts   |

---


##



