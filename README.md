# ffmpeg-git

Available on Docker Hub at https://cloud.docker.com/repository/docker/five82/ffmpeg-git

```git pull five82/ffmpeg-git```

FFmpeg container compiled from git master HEAD with the following configuration:

```--pkg-config-flags=--static --extra-libs='-lpthread -lm' --disable-debug --disable-doc --disable-ffplay --enable-ffprobe --enable-gpl --enable-libfreetype --enable-libopus --enable-libx264 --enable-libx265```

This is intended as a base image for five82/batchtranscode but can be run as a standalone container.

For example:

    docker run \
    --name ffmpeg-git \
    -v <path/to/input/dir>:/input \
    -v <path/to/output/dir>:/output \
    five82/ffmpeg-git \
    ffmpeg -i /input/input.mkv -c:v libx264 -preset medium -crf 20 -c:a aac -b:a 384k /output/output.mkv
