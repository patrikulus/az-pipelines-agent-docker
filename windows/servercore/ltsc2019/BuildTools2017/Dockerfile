FROM patrikulus/az-pipelines-agent:windows

ENV chocolateyUseWindowsCompression=false
RUN @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

RUN choco config set cachelocation C:\chococache

RUN choco install \
    git  \
    nodejs \
    jdk8 \
    curl \
    maven \
    gradle \
    ant \
    ruby \
    python \
    --confirm \
    --limit-output \
    --timeout 216000 \
    && rmdir /S /Q C:\chococache

RUN choco install \
    netfx-4.7.2-devpack \
    --confirm \
    --limit-output \
    && rmdir /S /Q C:\chococache

RUN choco install \
   dotnetcore-sdk \
   --confirm \
   --limit-output \
    && rmdir /S /Q C:\chococache

RUN choco install \
    visualstudio2017buildtools \
    --package-parameters "--allWorkloads --includeRecommended --includeOptional --passive --locale en-US" \
    --confirm \
    --limit-output \
    --timeout 216000 \
    && rmdir /S /Q C:\chococache

# common node tools
RUN npm install gulp -g && npm install grunt -g && npm install -g less && npm install phantomjs-prebuilt -g

SHELL ["powershell", "-Command", "$ErrorActionPreference = 'Stop'; $ProgressPreference = 'SilentlyContinue';"]

SHELL ["cmd", "/S", "/C"]

RUN setx /M PATH "%PATH%;%ProgramFiles%\dotnet"

# Trigger the population of the local package cache
ENV NUGET_XMLDOC_MODE skip

RUN mkdir C:\warmup \
    && cd C:\warmup \
    && dotnet new \
    && cd .. \
    && rmdir /S /Q C:\warmup 

