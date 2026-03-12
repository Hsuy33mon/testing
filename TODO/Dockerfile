FROM node:18

WORKDIR /app

COPY . .

RUN cd todo_frontend && npm install && npm run build
RUN cd todo_backend && npm install

RUN mkdir -p todo_backend/static
RUN cp -r todo_frontend/build todo_backend/static/

WORKDIR /app/todo_backend

ENV PORT=5000
ENV MONGODB_URI=mongodb://mongo:27017/todo

EXPOSE 5000

CMD ["npm","start"]