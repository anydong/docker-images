FROM node:18.12-bullseye-slim

LABEL maintainer="liuzhaowei55@gmail.com"

# 设置时区
ARG TZ=Asia/Chongqing
ENV TZ ${TZ}
RUN ln -snf /usr/share/zoneinfo/$TZ /etc/localtime && echo $TZ > /etc/timezone

ENV LANG C.UTF-8

# node
# optionally if you want to run npm global bin without specifying path
ENV NPM_CONFIG_PREFIX=/home/node/.npm-global
ENV PATH=$PATH:/home/node/.npm-global/bin 

# 安装软件
RUN set -eux \
    && apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates \
       fonts-liberation \
       libappindicator3-1 \
       libasound2 \
       libatk-bridge2.0-0 \
       libatk1.0-0 \
       libc6 \
       libcairo2 \
       libcups2 \
       libdbus-1-3 \
       libexpat1 \
       libfontconfig1 \
       libgbm1 \
       libgcc1 \
       libglib2.0-0 \
       libgtk-3-0 \
       libnspr4 \
       libnss3 \
       libpango-1.0-0 \
       libpangocairo-1.0-0 \
       libstdc++6 \
       libx11-6 \
       libx11-xcb1 \
       libxcb1 \
       libxcomposite1 \
       libxcursor1 \
       libxdamage1 \
       libxext6 \
       libxfixes3 \
       libxi6 \
       libxrandr2 \
       libxrender1 \
       libxss1 \
       libxtst6 \
       lsb-release \
       wget \
       unzip \
       git \
       fontconfig \
       xdg-utils \
       xfonts-utils \
       fonts-droid-fallback \
       xfonts-intl-asian

WORKDIR /tmp

# 安装字体
RUN wget https://fonts.google.com/download?family=Roboto -O Roboto.zip \
    && unzip -o Roboto.zip -d /usr/share/fonts \
    && fc-cache \
    && wget https://fonts.google.com/download?family=Noto%20Sans%20SC -O Noto_Sans_SC.zip \
    && unzip -o Noto_Sans_SC.zip -d /usr/share/fonts \
    && fc-cache \
    && wget https://fonts.google.com/download?family=Noto%20Sans%20TC -O Noto_Sans_TC.zip \
    && unzip -o Noto_Sans_TC.zip -d /usr/share/fonts \
    && fc-cache \
    && wget https://github.com/atelier-anchor/smiley-sans/releases/download/v1.0.0/smiley-sans-v1.0.0.zip -O smiley-sans-v1.0.0.zip \
    && unzip -o smiley-sans-v1.0.0.zip "SmileySans-Oblique.otf" -d /usr/share/fonts \
    && fc-cache

# 清理
RUN apt-get autoremove \
    && apt-get autoclean \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

WORKDIR /home/data/apps/url-to-pdf-api

RUN git clone --depth 1 https://github.com/alvarcarto/url-to-pdf-api . \
    && git reset --hard 2a02f0c14a8eec2d63d1f7ff0e7d369e0c8cad20 \
    && npm install \
    && mv .env.sample .env \
    && sed -i 's/9000/80/g' .env

# At the end, set the user to use when running this image
USER node

CMD [ "npm", "run", "start" ]