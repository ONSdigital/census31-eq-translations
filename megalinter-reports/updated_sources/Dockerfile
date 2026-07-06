FROM python:3.13-slim

WORKDIR /usr/src/app

COPY . .

RUN pip install --no-cache-dir \
    "poetry==2.1.2" && \
    poetry config virtualenvs.create false && \
    poetry install --only main
