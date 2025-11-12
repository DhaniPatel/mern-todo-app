# ---- Build Stage ----
FROM node:18-alpine AS deps
WORKDIR /usr/src/app
COPY backend/package*.json ./
RUN npm ci --production

# ---- Runtime Stage ----
FROM node:18-alpine AS runner
WORKDIR /usr/src/app
COPY --from=deps /usr/src/app/node_modules ./node_modules
COPY backend/ ./
EXPOSE 5000
CMD ["node", "server.js"]
