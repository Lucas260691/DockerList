FROM mjgargani/puppeteer:trybe1.0
WORKDIR /
ADD node_modules.tar.gz ./todotests
COPY . .
CMD ["npm", "test"]
