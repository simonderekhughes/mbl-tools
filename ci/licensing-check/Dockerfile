# Copyright (c) 2019 Arm Limited and Contributors. All rights reserved.
#
# SPDX-License-Identifier: BSD-3-Clause

FROM ubuntu:bionic-20180724.1

RUN apt-get update && apt-get install locales \
    && dpkg-reconfigure locales \
    && locale-gen en_US.UTF-8 \
    && update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8

ENV LANG=en_US.UTF-8

RUN apt-get update && apt-get install -y \
    python3 \
    python3-pip

ADD ./mbl-licensing-checker /mbl-licensing-checker

RUN pip3 install /mbl-licensing-checker

RUN rm -rf /var/lib/apt/lists/* && \
    rm -rf /mbl-licensing-checker

# The build process needs working space to perform the build and
# delivery the build products.
RUN mkdir -m 777 /work

COPY licensing-check.sh ./
