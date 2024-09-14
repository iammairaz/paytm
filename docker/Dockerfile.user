FROM node:20.12.0-alpine3.19

WORKDIR usr/src/app

COPY package.json package-lock.json turbo.json tsconfig.json ./

COPY apps ./apps
COPY packages ./packages

#Install Dependencies
RUN npm install 

# can you add a script to global pacakge.json that does this?
RUN cd packages/db && npx prisma generate && cd ../..

# Can you filter the build down to just one app?
RUN npm run build

CMD [ "npm", "run", "start-user-app" ]