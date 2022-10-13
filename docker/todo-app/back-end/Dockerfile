FROM node:14-alpine
WORKDIR /
EXPOSE  3001
ADD node_modules.tar.gz ./todobackend
COPY . .

CMD ["npm", "start"]
