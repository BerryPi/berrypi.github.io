---
title: Docker
---

### Running Pygame Apps
Look, sometimes you just want to run a graphical application in a Docker container.

Using the base `python` Docker image and installing pygame isn't enough to get a window to render on the host. The image also needs `libsdl2-dev` to be installed (the non-dev package, `libsdl2-2.0.0`, won't cut it.)

Dockerfile:

```bash
RUN apt update && apt install -y libsdl2-dev
```

Additionally, the container needs to be launched with the `DISPLAY` env var set.

Docker command line: `-e DISPLAY=:0`

Docker Compose File:
```yaml
environment:
  - DISPLAY=:0
```

On a Windows host, an X display server (e.g. VcXsrv) needs to be running.