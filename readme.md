## Local Environment Setup

### Build Docker Image

1. Navigate to the directory containing the `DOCKERFILE`.
2. Build the Docker image:

```bash
docker build -t <YOUR_IMAGENAME> .
```

Example:

```bash
docker build -t env_robot .
```

3. Run the Docker container, replacing `<YOUR_CONTAINER_NAME>` and `<YOUR_IMAGENAME`>:

   ```bash
   docker run -it
    --name <YOUR_CONTAINER_NAME>
    --network host
     --env="DISPLAY"
     --env="QT_X11_NO_MITSHM=1"
     --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw"
     --volume="<YOUR_PATH>/course_ws:/root/course_ws"
     <YOUR_IMAGENAME>

   ```

Example:

```bash
docker run -it \
    --name container_robot \
    --network host \
    --env="DISPLAY" \
    --env="QT_X11_NO_MITSHM=1" \
    --volume="/tmp/.X11-unix:/tmp/.X11-unix:rw" \
    --volume="/home/teacher/桌面/course_ws:/root/course_ws" \
   env_robot
```

#### Start the Docker container

1. Start the Docker container and access its shell:

```bash
docker start <YOUR_CONTAINER_NAME> && docker exec -it <YOUR_CONTAINER_NAME> /bin/bash
```

Example:

```bash
docker start container_robot && docker exec -it container_isaacsim /bin/bash
```
