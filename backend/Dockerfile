FROM python:3.11-alpine3.18 as builder

ENV LANG ru_RU.UTF-8
ENV LANGUAGE ru_RU:ru
ENV LC_ALL ru_RU.UTF-8
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

WORKDIR /app
RUN pip install gunicorn==20.1.0
COPY ./requirements.txt .
RUN pip install --upgrade pip && pip install -r requirements.txt --no-cache-dir

FROM python:3.11-alpine3.18
WORKDIR /app
COPY . .
CMD ["gunicorn", "--bind", "0.0.0.0:8000", "kittygram_backend.wsgi"]
