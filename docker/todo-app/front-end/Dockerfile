FROM node:14-alpine
WORKDIR /
EXPOSE  3000
ADD node_modules.tar.gz ./todofrontend
COPY . .
CMD ["npm", "start"]
