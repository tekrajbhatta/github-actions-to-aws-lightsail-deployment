# GitHub Actions for AWS Lightsail Deployment

This repository contains a GitHub Actions workflow for automating the deployment of a custom-coded React and WordPress website to an AWS Lightsail Bitnami NGINX server. The workflow handles deployment processes such as taking backups, cloning the repository, running necessary build commands, setting permissions, and restarting the NGINX server.

## Features

- Deploys the website to the AWS Lightsail Bitnami NGINX server upon push to the `main` or `development` branches.
- Automated backup of the current `Website_master` folder before deploying new changes.
- Clones the repository and runs Composer and NPM commands on the Lightsail instance.
- Handles environment configuration by copying the `.env` file from a predefined directory.
- Manages file and folder permissions after deployment.
- Restarts the NGINX server to apply the changes.

## Workflow Details

- **Checkout repository**: Pulls the latest code from the selected branch.
- **Set up SSH**: Establishes a secure SSH connection to the AWS Lightsail instance.
- **Handle backup**: Creates a backup of the current website files.
- **Clone repository**: Clones the latest version of the website into a temporary directory on the Lightsail instance.
- **Run Composer and NPM commands**: Installs dependencies and builds the project.
- **Clean up unnecessary files**: Removes unwanted files and folders before deploying.
- **Update uploads folder**: Replaces the old uploads folder with the new one.
- **Set correct file permissions**: Ensures the appropriate file and directory permissions for security.
- **Move new website files**: Replaces the old website files with the new ones.
- **Restart NGINX**: Restarts the NGINX server to reflect changes.

## Usage

1. Clone this repository.
2. Add your AWS Lightsail IP and SSH key to your GitHub repository secrets (`LIGHTSAIL_IP` and `LIGHTSAIL_KEY`).
3. Push your changes to the `main` or `development` branches to trigger the deployment.

## License

This project is licensed under the MIT License.
