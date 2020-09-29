FROM ubuntu:14.04
#Prepare platform
RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections; \
    apt-get update; \
    apt-get install apt-utils -y; \
    apt-get install python-all python-pip -y -q
WORKDIR /tmp
COPY /webapp/app/requirements.txt requirements.txt
RUN pip install -qr requirements.txt
WORKDIR /opt/webapp
COPY /webapp/app/app.py app.py
#Execute 
EXPOSE 5000
CMD ["python","app.py"]