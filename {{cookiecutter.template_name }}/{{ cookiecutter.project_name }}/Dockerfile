FROM python:3.11-bullseye AS builder

ENV PYTHONUNBUFFERED=1
WORKDIR /home/ubuntu/webs/{{ cookiecutter.project_name }}/{{ cookiecutter.project_name }}
RUN set -ex; apt-get update ; apt install -y --no-install-recommends gcc python3-dev build-essential ; pip install --upgrade pip --no-cache ;

COPY requirements.txt /home/ubuntu/webs/{{ cookiecutter.project_name }}/{{ cookiecutter.project_name }}
RUN python3 -m venv venv

COPY . .

FROM builder AS local
RUN pip install -r requirements.txt
