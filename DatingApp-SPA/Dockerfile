FROM node:16.20.0-alpine as node

WORKDIR /usr/src/app
#COPY package.json package-lock.json ./
COPY package.json ./
RUN npm install
RUN npm install -g @angular/cli@7.3.9
COPY . .
#RUN ng test --watch=false
#RUN ng e2e --port 4200
#RUN ng build --output-path=dist
RUN npm run build

FROM nginx:alpine
COPY --from=node /usr/src/app/dist/DatingApp-SPA/ /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]