# 🚀 Mogenius Build Workflows

This repository offers a collection of GitHub Actions workflows tailored for seamless integration with [mogenius](https://mogenius.com), facilitating automated CI/CD pipelines on Kubernetes clusters.

## 📦 Overview

mogenius simplifies the deployment of containerized applications to Kubernetes by providing a cloud-agnostic platform that integrates effortlessly with your existing infrastructure.  
By leveraging these workflows, you can automate the build and deployment processes, ensuring consistent and efficient application delivery.

## ⚙️ Features

- **Automated Docker Builds**: Trigger Docker image builds upon commits to specified branches.
- **Continuous Deployment**: Automatically deploy updated images to your Kubernetes clusters with the mogenius operator.
- **Customizable Workflows**: Adapt the provided workflows to fit your project's specific needs.
- **Integration with Git Platforms**: Seamlessly connect with GitHub, GitLab, or Bitbucket repositories.

## 🛠️ Getting Started

### Prerequisites

- A [mogenius](https://mogenius.com) account with a connected Kubernetes cluster (read the [quickstart guide](https://docs.mogenius.com/overview/quickstart)).
- A Git repository (GitHub, GitLab, or Bitbucket) containing your application code.
- A valid `Dockerfile` located at the root or specified path of your repository.

### Using the mogenius pipeline starter

mogenius has a built-in Github integration that allows you to deploy this workflow as a pipeline starter from your mogenius account. This is highly useful for the first deployment of your application, providing you with an automated workflow that you can customize afterwards.

1. In your mogenius workspace, add a new resource from the dashboard and select **pipeline starter**.
2. Set up the Github integration and select the repository where the build workflow should be deployed. You'll also add container registry credentials and create a workspace API key for the deployment.
3. Create the application. The build workflow will be cloned and pushed to your selected repository. At the same time, a deployment is created on your Kubernetes cluster, referencing the image from your build pipeline.
4. The final step of your build workflow was automatically configured with your workspace API key and the metadata of your Kubernetes deployment. This way, after a successful workflow run the image on Kubernetes will be updated automatically by the mogenius operator.

Here's a [detailed guide](https://docs.mogenius.com/deploying-applications/pipeline-starters) on the mogenius pipeline starter.

### Manual setup

The steps performed by the mogenius pipeline starter can also be done manually if you want to modify the build workflow before the initial deployment.

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

6. **Configure the Kubernetes deployment in mogenius**:

1. In your mogenius workspace, add a new resource on the dashboard and select **pipeline starter**.
2. Set up the Github integration and select the repository with your build workflow. You'll also add container registry credentials and create a workspace API key for the deployment.
3. Create the application. This will add a new deployment to your Kubernetes cluster with the image from your build workflow.
4. mogenius will automatically update the final step in your build workflow, adding your workspace API key and the metadata of your Kubernetes deployment. This way, after a successful workflow run the image on Kubernetes will be updated automatically by the mogenius operator.


## 🧩 Workflow Details

The provided workflow performs the following steps:

- **Check out Code**: Retrieves the latest code from the specified branch.
- **Set Up Docker**: Prepares the environment for Docker operations.
- **Build Image**: Constructs the Docker image using the provided `Dockerfile`.
- **Push to Registry**: Uploads the built image to the container registry that you specified in mogenius.
- **Trigger Deployment**: Initiates the deployment to your Kubernetes cluster via mogenius operator.

## 📚 Additional Resources

- **[mogenius Documentation](https://docs.mogenius.com/)**
- **[Quickstart guide](https://docs.mogenius.com/overview/quickstart)**
- **[mogenius Pipeline Starter](https://docs.mogenius.com/deploying-applications/pipeline-starters)**

## 🤝 Contributing

Contributions are welcome! If you have suggestions or improvements, please fork the repository and submit a pull request. For major changes, open an issue first to discuss your proposed modifications.

## 📄 License

This project is licensed under the [MIT License](LICENSE).

---

For any questions or support, please contact the [mogenius support team](https://mogenius.com/contact).
