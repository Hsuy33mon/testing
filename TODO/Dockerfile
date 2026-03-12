# ---------- Stage 1: Build Frontend ----------
FROM node:22 AS frontend-build
 
WORKDIR /app
 
COPY todo_frontend ./todo_frontend
 
WORKDIR /app/todo_frontend
 
RUN npm install
RUN npm run build
 
 
# ---------- Stage 2: Backend ----------
FROM node:22
 
WORKDIR /app
 
COPY todo_backend ./todo_backend
 
# copy frontend build to backend static folder
RUN mkdir -p /app/todo_backend/static
 
COPY --from=frontend-build /app/todo_frontend/build /app/todo_backend/static/build
 
WORKDIR /app/todo_backend
 
RUN npm install
 
ENV PORT=5000
ENV MONGODB_URI=mongodb://mongo:27017/todo
 
EXPOSE 5000
 
CMD ["npm", "start"]