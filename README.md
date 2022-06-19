# Node Filebase IPFS Uploader

This repository for the tutorial on how to [Create A Backend NodeJS IPFS File Uploader With Filebase]().
If you got value from it, please retweet it out on twitter and follow me at [@codingwithmanny](https://twitter.com/codingwithmanny).

---

## Requirements

- NVM or NodeJS `16.15.1`
- Yarn
- Postman (Optional - will also show with curl)
- Filebase Account - [https://filebase.com](https://filebase.com)

---

## Local Setup

### 1 - Install Dependencies

```bash
yarn install;
```

### 2 - Set Environment Variables

```bash
cp env.example .env;
```

```bash
PORT=5001
NODE_ENV=development
FILEBASE_ACCESS_KEY=key
FILEBASE_SECRET_KEY=secret
FILEBASE_BUCKET=bucket
FILEBASE_REGION=us-east-1
FILE_SERVER_URL=http://localhost:5002
```

---

## Run Local Development

```bash
# ./node-filebase-ipfs-uploader

yarn dev;

# Expected Output
# $ nodemon src/server.ts
# [nodemon] 2.0.16
# [nodemon] to restart at any time, enter `rs`
# [nodemon] watching path(s): *.*
# [nodemon] watching extensions: ts,json
# [nodemon] starting `ts-node src/server.ts`
# Listening on PORT 5001
# Environment: development
```

**Testing Upload:** (In Another Terminal)

```bash
# ./node-filebase-ipfs-uploader

curl --location --request POST 'http://localhost:8080/upload' \
--form 'file=@"/full/path/to/node-filebase-ipfs-uploader/test/test-forever.jpg"';

# Expected Output
# {"data":{"file":"test-forever.jpg","url":"http://localhost:5002/test-forever.jpg"}}
```

---

## Run Local Production

```bash
# ./node-filebase-ipfs-uploader

yarn start;

# Expected Output
# yarn run v1.22.18
# $ export NODE_ENV=production && tsc && node build/server.js
# Listening on PORT 8080
# Environment: production
```

**Testing Upload:** (In Another Terminal)

```bash
# ./node-filebase-ipfs-uploader

curl --location --request POST 'http://localhost:8080/upload' \
--form 'file=@"/full/path/to/node-filebase-ipfs-uploader/test/test-forever.jpg"';

# Expected Output
# {"data":{"file":"test-forever.jpg","url":"ipfs://QmY8UXb7Nka5VWkXXRAMC1DQtamc1s8xzcjoQY6GaEbTdn"}}
```
