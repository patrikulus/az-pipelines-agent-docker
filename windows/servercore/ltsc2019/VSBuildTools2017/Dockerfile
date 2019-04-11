FROM patrikulus/az-pipelines-agent:windows

ENV chocolateyUseWindowsCompression=false
RUN @powershell -NoProfile -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin"

RUN choco config set cachelocation C:\chococache


RUN choco install \
    git  \
    nodejs \
    curl \
    visualstudio2017buildtools \
    --package-parameters \ 
    "--add Microsoft.VisualStudio.Workload.AzureBuildTools \
     --add Microsoft.VisualStudio.Workload.MSBuildTools \
     --add Microsoft.VisualStudio.Workload.NetCoreBuildTools \
     --add Microsoft.VisualStudio.Workload.NodeBuildTools \
     --add Microsoft.VisualStudio.Workload.WebBuildTools \
     --quiet --locale en-US" \
    --confirm \
    && rmdir /S /Q C:\chococache
