# Dockerfile challenge

gbcl **58.4MB**

```console
# Étape de construction pour Python
FROM python:3.9-alpine AS python-build

WORKDIR /app

# Installer les dépendances Python
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

# Étape de construction pour Node.js
FROM node:18-alpine AS node-build

WORKDIR /app/frontend

# Installer les dépendances Node.js et construire le frontend
COPY frontend/package*.json ./
RUN npm install && npm cache clean --force
COPY frontend ./
RUN npm run build

# Image finale combinée
FROM python:3.9-alpine

WORKDIR /app

# Copier les fichiers nécessaires des étapes de construction précédentes
COPY --from=python-build /app /app
COPY --from=node-build /app/frontend/dist /app/static

# Installer les dépendances supplémentaires nécessaires et nettoyer
RUN apk --no-cache add --virtual .build-deps \
        gcc musl-dev libffi-dev && \
    apk --no-cache add libstdc++ && \
    pip install --no-cache-dir gunicorn && \
    apk del .build-deps && \
    rm -rf /var/cache/apk/* /tmp/* /root/.cache

CMD ["gunicorn", "--bind", "0.0.0.0:5000", "app:app"]


```