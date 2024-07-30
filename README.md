# docker development images

Very simple docker images used for the development of software

## How to build and run

To build simply run:

```sh
docker build -t "ams21/dev-ubuntu:24.04" Ubuntu/24.04
```

After that, you can open a shell by simply using

```sh
docker run -it "ams21/dev-ubuntu:24.04"
```

Most likely you want to run the container inside your project folder. For that, you can use something like this:

```sh
docker run -v "$PWD":"$PWD" -w "$PWD" -it "ams21/dev-ubuntu:24.04" /bin/bash
```

If you want to run a different container than `ubuntu:24.04` you just need to replace the name and path.
