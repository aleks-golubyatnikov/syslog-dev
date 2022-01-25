FROM ubuntu:latest

RUN apt-get update && apt-get install -y rsyslog logrotate

RUN echo '$ModLoad imudp' >> /etc/rsyslog.conf
RUN echo '$UDPServerRun 514' >> /etc/rsyslog.conf
RUN echo '$ModLoad imtcp' >> /etc/rsyslog.conf
RUN echo '$InputTCPServerRun 514' >> /etc/rsyslog.conf
RUN echo '$template AgentLogs, "/var/log/agentlogs/%FROMHOST-IP%/%PROGRAMNAME%.log"' >> /etc/rsyslog.conf
RUN echo '*.* ?AgentLogs' >> /etc/rsyslog.conf

RUN echo '$PrivDropToUser syslog' >> /etc/rsyslog.conf
RUN echo '$PrivDropToGroup syslog' >> /etc/rsyslog.conf

ENTRYPOINT ["rsyslogd", "-n"]