FROM python:3.11.11-bullseye


RUN mkdir scripts
RUN mkdir data_input
RUN mkdir data_output
RUN mkdir /opt/oracle


RUN curl -LO https://download.oracle.com/otn_software/linux/instantclient/2111000/oracle-instantclient-basic-21.11.0.0.0-1.x86_64.rpm
RUN apt-get update
RUN apt-get install -y --no-install-recommends fakeroot alien libaio1
RUN fakeroot alien --scripts --install oracle-instantclient-*.rpm


COPY requirements.txt requirements.txt
#COPY init.sh scripts/init.sh
RUN pip install --upgrade pip
RUN pip install -r requirements.txt 
RUN pip freeze
RUN rm -f oracle-instantclient-*
WORKDIR scripts