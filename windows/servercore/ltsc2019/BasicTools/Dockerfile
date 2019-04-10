FROM patrikulus/az-pipelines-agent:windows

ENV chocolateyUseWindowsCompression=false
RUN @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

RUN choco config set cachelocation C:\chococache

RUN choco install \
    git  \
    nodejs \
    curl \
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

# common node tools
RUN npm install gulp -g && npm install grunt -g && npm install -g less && npm install phantomjs-prebuilt -g
