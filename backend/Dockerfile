FROM node:19.4.0
WORKDIR /app
COPY package.json package.json
COPY package-lock.json package-lock.json
RUN npm install
COPY . .
EXPOSE 8000
USER node
CMD [ "npm", "start" ]
