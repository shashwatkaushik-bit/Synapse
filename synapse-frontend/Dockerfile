FROM node:22-alpine

# 1. Install dependencies for native modules
# Alpine uses musl, but many Node binaries expect glibc. 
# libc6-compat provides the necessary compatibility layer.
RUN apk add --no-cache libc6-compat

WORKDIR /app

# 2. Copy only the dependency files first
COPY package.json package-lock.json* ./

# 3. Use 'npm ci' for a clean, reliable install
# This ensures that the native bindings (like rolldown) are 
# downloaded specifically for the Linux/Alpine environment.
RUN npm ci

# 4. Copy the rest of the application
COPY . .

EXPOSE 5173

CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]