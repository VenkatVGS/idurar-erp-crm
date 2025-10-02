FROM node:20-alpine

WORKDIR /app

COPY package*.json ./
COPY prisma ./prisma/

RUN npm install

RUN npx prisma generate

COPY . .

RUN echo 'DATABASE_URL="postgresql://idurar_admin:Venkatesh123!@idurar-erp-postgres.c544weocsbra.ap-south-1.rds.amazonaws.com:5432/idurar"' > .env
RUN echo 'NODE_ENV=production' >> .env
RUN echo 'PORT=5000' >> .env

EXPOSE 5000

# Use ts-node to run the TypeScript application
CMD sh -c "npx prisma db push && npx ts-node src/index.ts"
