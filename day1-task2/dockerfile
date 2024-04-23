FROM registry.opensuse.org/opensuse/leap:15.3

RUN zypper ref && zypper install -y python3 python3-pip

RUN mkdir /app
WORKDIR /app
COPY src/* /app/

RUN pip3 install -r requirements.txt


EXPOSE 8081
CMD ["python3", "/app/main.py"]

#CMD httpd -p 8080 -h /www; tail -f /dev/null
#ENTRYPOINT [ "/bin/sh", "/binn/entrypoint.sh" ]
