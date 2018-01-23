FROM golang:1.10beta2-alpine
MAINTAINER Matthew Lu <matthewlujp@gmail.com>

RUN apk update
RUN apk add --no-cache zlib-dev libressl-dev yasm-dev lame-dev libogg-dev libvpx-dev libvorbis-dev x264-dev x265-dev freetype-dev libass-dev libwebp-dev rtmpdump-dev libtheora-dev opus-dev
RUN apk add --no-cache --virtual=build-dependencies git build-base curl nasm tar bzip2

RUN cd /tmp && \
  git clone https://github.com/FFmpeg/FFmpeg.git && \
  cd FFmpeg && \
  ./configure --enable-version3 --enable-gpl --enable-nonfree --enable-small --enable-libmp3lame --enable-libx264 --enable-libx265 \
    --enable-libvpx --enable-libtheora --enable-libvorbis --enable-libopus --enable-libass --enable-libwebp --enable-librtmp \
    --enable-postproc --enable-libtls --enable-avresample --enable-libfreetype --disable-debug && \
  make && \
  make install && \
  make distclean && \
  cd .. && \
  rm -rf FFmpeg

RUN apk del build-dependencies
