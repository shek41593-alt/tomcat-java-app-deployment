from pathlib import Path
from docx import Document
from pypandoc import convert_text

readme = r"""# Hi 👋 I'm Abhishek K

> DevOps Engineer • Cloud Engineer • Android Developer • AI Enthusiast

This is a starter GitHub profile README for your premium profile.

## 🚀 About Me

- 🌩️ Learning AWS, Kubernetes, Terraform
- 🐳 Building DevOps projects
- 📱 Native Android Developer
- 🤖 Interested in AI & Automation

## 🛠️ Tech Stack

- AWS
- Docker
- Kubernetes
- Terraform
- Jenkins
- GitHub Actions
- Linux
- Python
- Java
- Kotlin

## 📊 GitHub

- Username: **shek41593-alt**

## 📌 Featured Projects

- DevOps Portfolio
- Smart Healthcare System
- Poultry Farm Management
- FinTech Platform

---

Replace `assets/dark.svg` and `assets/light.svg` with your custom animated banner once it's ready.
"""

out = Path("/mnt/data/README.md")
convert_text(readme, "md", format="md", outputfile=str(out), extra_args=["--standalone"])
print(str(out))
