FROM ubuntu:latest

ARG PATH_LOGS_INSIDE

RUN apt-get update && apt-get install -y rsyslog

RUN echo '$ModLoad imudp \n \
    $UDPServerRun 514 \n \
    $ModLoad imtcp \n \
    $InputTCPServerRun 514 \n \
    $template AgentLogs, "'$PATH_LOGS_INSIDE'/%FROMHOST-IP%/%PROGRAMNAME%.log" \n \
    *.* ?AgentLogs \n \
    &~ ' >> /etc/rsyslog.conf
ENTRYPOINT ["rsyslogd", "-n"]