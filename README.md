# Customized Label Studio on Hetzner

This repository contains a customized version of Label Studio, running on a Hetzner machine. Below are the steps to modify the application locally and deploy changes to the server.

## Customization

To run the customized Label Studio locally and make changes:

1. Start the application using Docker Compose:
   ```sh
   docker compose -f docker-compose-old.yml up
   ```
2. Modify any necessary files (e.g., UI, backend configurations, plugins).
3. Once your changes are complete, test them locally.
4. Push your local changes to the `customized` branch:
   ```sh
   git add .
   git commit -m "Your commit message"
   git push origin customized
   ```

## Deployment

To publish your changes to the Hetzner machine:

1. Connect to the Hetzner machine using SSH with the appropriate certificate:
   ```sh
   ssh -i ~/.ssh/keys/250304_labelstudio_remote root@94.130.190.89
   ```
2. Navigate to the Label Studio directory:
   ```sh
   cd /home/user/label-studio
   ```
3. Pull the latest changes from the `customized` branch:
   ```sh
   git pull origin customized
   ```
4. If the permission is denied, make sure to add the deploy key:
   ```sh
   ssh-add ~/.ssh/github_deploy_key
   ```
5. Rebuild and restart the Docker containers:
   ```sh
   docker compose up -d --build
   ```

Your changes should now be live on the server.
