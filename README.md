# docker-dev-images

Very simple docker images used for development of software

## How to build and run

To build simply run:

```sh
docker build -t "ams21/dev-ubuntu:22.04" Ubuntu/22.04
```

After that can open a shell by simply using

```sh
docker run -it "ams21/dev-ubuntu:22.04" /bin/bash
```

If you wan't to run a different container than `ubuntu:22.04` you just need to replace the name and path.
