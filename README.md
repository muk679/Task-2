## Rollback Strategy

Each Docker image is tagged with the Git commit SHA.

Example:

dockerhubusername/task-app:9f32a1b

If a deployment fails or introduces a bug, we can rollback to the previous stable version.

Steps to rollback:

1. Login to the staging server
2. Pull the previous working Docker image

docker pull dockerhubusername/task-app:<previous_commit>

3. Stop the current container

docker stop task-app

4. Remove the container

docker rm task-app

5. Run the previous image

docker run -d -p 3000:3000 --name task-app dockerhubusername/task-app:<previous_commit>

This restores the application to the last stable state.
