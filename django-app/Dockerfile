FROM ubuntu:22.04

WORKDIR /app

COPY requirements.txt .

RUN apt-get update && \
    apt-get install -y python3 python3-pip && \
    pip install -r requirements.txt

COPY . .

ENTRYPOINT ["python3"]

CMD ["manage.py", "runserver", "0.0.0.0:8000"]


