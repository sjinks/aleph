FROM node:23-slim

ENV DEBIAN_FRONTEND=noninteractive

RUN \
    apt-get -qq -y update && apt-get -qq -y install rsync && rm -rf /var/lib/apt/lists/* /var/cache/apt/archives/* && \
    mkdir /alephui

WORKDIR /alephui

COPY .prettierrc tsconfig.json package.json package-lock.json craco.config.js /alephui/

RUN npm ci && cp -R /alephui/node_modules/ /node_modules

COPY i18n /alephui/i18n
COPY public /alephui/public
COPY src /alephui/src

ENV REACT_APP_API_ENDPOINT=/api/2/
# RUN npm run build
