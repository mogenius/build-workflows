# 🚀 Mogenius Build Workflows

This repository offers a collection of GitHub Actions workflows tailored for seamless integration with [mogenius](https://mogenius.com), facilitating automated CI/CD pipelines on Kubernetes clusters.

## 📦 Overview

Mogenius simplifies the deployment of containerized applications by providing a cloud-agnostic platform that integrates effortlessly with your existing infrastructure.  
By leveraging these workflows, you can automate the build and deployment processes, ensuring consistent and efficient application delivery.

## ⚙️ Features

- **Automated Docker Builds**: Trigger Docker image builds upon commits to specified branches.
- **Continuous Deployment**: Automatically deploy updated images to your Kubernetes clusters managed by mogenius.
- **Customizable Workflows**: Adapt the provided workflows to fit your project's specific needs.
- **Integration with Git Platforms**: Seamlessly connect with GitHub, GitLab, or Bitbucket repositories.

## 🛠️ Getting Started

### Prerequisites

- A [mogenius](https://mogenius.com) account with an integrated Kubernetes cluster.
- A Git repository (GitHub, GitLab, or Bitbucket) containing your application code.
- A valid `Dockerfile` located at the root or specified path of your repository.

### Setup Instructions

1. **Clone the Repository**:

   ```bash
   git clone https://github.com/mogenius/build-workflows.git
   cd build-workflows
   ```

2. **Review the Workflow File**:

   Examine the `github-build-workflow.yaml` file to understand the build and deployment steps.

3. **Integrate with Your Repository**:

   Copy the workflow file into your repository's `.github/workflows/` directory:

   ```bash
   mkdir -p .github/workflows
   cp path/to/github-build-workflow.yaml .github/workflows/
   ```

4. **Customize the Workflow**:

   Modify the workflow file as needed to match your project's structure, such as setting the correct Dockerfile path or specifying environment variables.

5. **Commit and Push**:

   ```bash
   git add .github/workflows/github-build-workflow.yaml
   git commit -m "Add mogenius build workflow"
   git push origin main
   ```

6. **Configure mogenius**:

   In your mogenius dashboard, set up the service to connect with your repository and specify the branch to monitor for changes.

## 🧩 Workflow Details

The provided workflow performs the following steps:

- **Checkout Code**: Retrieves the latest code from the specified branch.
- **Set Up Docker**: Prepares the environment for Docker operations.
- **Build Image**: Constructs the Docker image using the provided `Dockerfile`.
- **Push to Registry**: Uploads the built image to the container registry associated with your mogenius account.
- **Trigger Deployment**: Initiates the deployment process on your Kubernetes cluster via mogenius.

## 📚 Additional Resources

- **[Mogenius Documentation](https://docs.mogenius.com/)**
- **[CI/CD Pipeline Overview](https://docs.mogenius.com/development/cicd-pipeline)**
- **[Deploying Applications](https://docs.mogenius.com/deploying-applications)**

## 🤝 Contributing

Contributions are welcome! If you have suggestions or improvements, please fork the repository and submit a pull request. For major changes, open an issue first to discuss your proposed modifications.

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

For any questions or support, please contact the [mogenius support team](https://mogenius.com/contact).
