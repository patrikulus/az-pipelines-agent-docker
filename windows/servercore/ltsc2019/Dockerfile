FROM mcr.microsoft.com/windows/servercore:ltsc2019
ENV WINDOWS_IMAGE_VERSION=10.0.17763

RUN mkdir C:\BuildAgent
WORKDIR C:/BuildAgent
COPY ./Start.* ./

CMD ["Start.cmd"]