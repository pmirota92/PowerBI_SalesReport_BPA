# 🚀 Automated Power BI Governance & Quality Assurance Pipeline

![Power BI](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![CI/CD](https://img.shields.io/badge/CI/CD-DataOps-success?style=for-the-badge)

## 📋 Project Overview
This project demonstrates a professional **DataOps** approach to Power BI development. It implements an automated **Continuous Integration (CI)** pipeline using **GitHub Actions** and **Tabular Editor CLI** to audit semantic models against industry-standard Best Practices (BPA). 

Instead of manual, error-prone checks, this repository ensures that every model change is automatically validated for performance, security, and maintenance standards before being merged.

---

## 👥 Collaborative Value (Multi-Developer Environment)
In a modern data team where multiple developers contribute to the same repository, maintaining consistency is critical. This pipeline serves as an automated "Quality Gate":

* **Enforcing Unified Standards:** Regardless of the developer's experience level, the model must meet predefined architectural criteria.
* **Streamlined Code Reviews:** Reviewers can focus on high-level logic and business requirements, as the automation handles technical "linting" (formatting, naming, metadata).
* **Scalable Governance:** Prevents technical debt from accumulating, ensuring the model remains performant as it grows in complexity.

---

## 🛠 Technical Architecture
The CI workflow is executed on a `windows-latest` GitHub runner and follows these stages:

1.  **Code Checkout:** Pulls the latest version of the Power BI metadata.
2.  **Environment Setup:** Dynamically downloads and configures the Tabular Editor 2.x binaries.
3.  **BPA Execution:** Runs the Best Practice Analyzer engine against the model definition using a custom `BPARules.json` file.
4.  **Reporting:** Provides detailed, line-by-line feedback in the GitHub Actions console.

---

## 🚧 Key Technical Hurdles Overcome

### 1. Format Compatibility (TMDL to .bim)
Managed the complex transition from the newer **TMDL (Tabular Model Definition Language)** format back to a consolidated **.bim** format. This was necessary to ensure 100% compatibility with open-source CLI tools while maintaining the benefits of a folder-based development structure in Power BI Desktop.

### 2. Environment Pathing & Reliability
Implemented robust **absolute pathing** using the `$env:GITHUB_WORKSPACE` variable. This eliminated "File Not Found" errors common in virtualized runner environments, ensuring the automation is 100% reliable regardless of the internal GitHub folder structure.

### 3. Large-Scale Refactoring (300+ Violations)
Successfully managed an initial audit that revealed **300+ rule violations**. Instead of manual fixes, I categorized these into Performance, Maintenance, and Naming standards, using Tabular Editor's scripting capabilities to batch-fix cosmetic issues and prioritizing manual refactoring for DAX performance optimization.

---

## 📊 Results in Action
The automation provides a transparent, immutable log of all model violations. By integrating this into the workflow, the **"Definition of Done"** for any task is no longer subjective—it requires a passing grade from the Best Practice Analyzer.


---

## 💡 Key Takeaways
* **Analytics Engineering:** Power BI development should follow the same rigorous standards as software engineering.
* **Proactive vs. Reactive:** Finding 300 errors during a CI scan is a success, not a failure—it prevents those 300 issues from impacting end-users in production.
* **Efficiency:** Automating governance allows the team to move faster with higher confidence.
