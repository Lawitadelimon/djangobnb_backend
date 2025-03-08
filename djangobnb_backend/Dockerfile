FROM python:3.13.2-slim-bullseye

WORKDIR /usr/src/djangobnb_backend

# Configuración de entorno
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# Instalar dependencias del sistema necesarias para compilar psycopg2
RUN apt-get update && apt-get install -y netcat

# Actualizar pip
RUN pip install --upgrade pip

# Copiar e instalar dependencias de Python
COPY ./requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY ./entrypoint.sh .
RUN sed -i 's/\r$//g' /usr/src/djangobnb_backend/entrypoint.sh
RUN chmod +x /usr/src/djangobnb_backend/entrypoint.sh

# Copiar el código de la aplicación
COPY . .

ENTRYPOINT [ "/usr/src/djangobnb_backend/entrypoint.sh" ]
