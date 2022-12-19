ARG REGION

FROM tensorflow/tensorflow

RUN apt-get update
RUN apt-get install -y python3 python3-pip 
RUN apt-get install -y nginx

RUN python3 -m pip install --no-cache-dir -U \
    numpy pandas boto3 awscli s3fs \
    flask gevent gunicorn

RUN mkdir -p /opt/program
RUN mkdir -p /opt/ml

COPY app.py /opt/program
COPY model.py /opt/program
COPY nginx.conf /opt/program
COPY wsgi.py /opt/program
WORKDIR /opt/program

EXPOSE 8080

ENTRYPOINT ["python", "app.py"]
