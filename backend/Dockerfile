FROM node:20-alpine

WORKDIR /app

# Copy package files and prisma schema
COPY package*.json ./
COPY prisma ./prisma/

# Install dependencies
RUN npm ci

# Generate Prisma client
RUN npx prisma generate

# Copy source code
COPY . .

# Create production .env file with database URL
RUN echo 'DATABASE_URL="postgresql://idurar_admin:Venkatesh123!@idurar-erp-postgres.c544weocsbra.ap-south-1.rds.amazonaws.com:5432/idurar"' > .env
RUN echo 'NODE_ENV=production' >> .env
RUN echo 'PORT=5000' >> .env

EXPOSE 5000

# Use npm start instead of node dist/index.js
CMD ["npm", "start"]
