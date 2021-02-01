ARG BUILD_FROM
FROM $BUILD_FROM

ENV LANG C.UTF-8

# Run updates
# RUN apt-get clean && apt-get update && apt-get upgrade -y

# Set the locale
# RUN apt-get install -y locales && locale-gen en_US.UTF-8

# Install python/pip
ENV PYTHONUNBUFFERED=1
RUN apk add --update --no-cache python3 && ln -sf python3 /usr/bin/python
RUN python3 -m ensurepip
RUN pip3 install --no-cache --upgrade pip setuptools

#Install required python packages 
RUN pip3 install paho-mqtt
RUN pip3 install requests 
RUN pip3 install influxdb
RUN pip3 install influxdb-client 


#RUN curl -k https://codeload.github.com/johanmeijer/grott/zip/master --output files.zip && unzip files.zip
#RUN unzip files.zip

# Copy data for add-on
#COPY grott.py /app/grott.py
#COPY grottconf.py /app/grottconf.py
#COPY grottdata.py /app/grottdata.py
#COPY grottproxy.py /app/grottproxy.py
#COPY grottsniffer.py /app/grottsniffer.py

COPY script.sh /app/script.sh
WORKDIR /app
RUN curl -k https://codeload.github.com/johanmeijer/grott/zip/master --output files.zip && unzip files.zip
#RUN unzip files.zip
#COPY grott-master/grott.py /app/grott.py
#COPY grott-master/grottconf.py /app/grottconf.py
#COPY grott-master/grottdata.py /app/grottdata.py
#COPY grott-master/grottproxy.py /app/grottproxy.py
#COPY grott-master/grottsniffer.py /app/grottsniffer.py

RUN chmod a+x script.sh
CMD [ "./script.sh" ]