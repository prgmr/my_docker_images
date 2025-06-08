FROM node:18-alpine

WORKDIR /var/www/wiki

# Скачиваем и распаковываем Wiki.js (версия будет подставляться из CI)
ARG WIKIJS_VERSION
RUN wget "https://github.com/requarks/wiki/releases/download/v${WIKIJS_VERSION}/wiki-js.tar.gz" && \
    tar -xzf wiki-js.tar.gz && \
    rm wiki-js.tar.gz

RUN npm install --production

EXPOSE 3000
CMD ["node", "server"]