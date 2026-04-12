FROM node:18
WORKDIR /app

COPY package.json package.json
COPY package-lock.json package-lock.json

RUN npm ci

COPY . .
RUN npm run build
RUN npm install --global http-server

# В проде статику раздаёт gateway (nginx) из общего volume; копируем build в /staticfiles при старте.
CMD cp -r /app/build/. /staticfiles/
