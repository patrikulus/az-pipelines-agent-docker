FROM patrikulus/az-pipelines-agent:windows-basic-tools

ENV chocolateyUseWindowsCompression=false

RUN choco config set cachelocation C:\chococache

RUN choco install \
    visualstudio2017buildtools \
    --package-parameters \ 
    "--add Microsoft.VisualStudio.Workload.AzureBuildTools \
     --add Microsoft.VisualStudio.Workload.DataBuildTools \
     --add Microsoft.VisualStudio.Workload.ManagedDesktopBuildTools \
     --add Microsoft.VisualStudio.Workload.MSBuildTools \
     --add Microsoft.VisualStudio.Workload.NetCoreBuildTools \
     --add Microsoft.VisualStudio.Workload.NodeBuildTools \
     --add Microsoft.VisualStudio.Workload.WebBuildTools \
     --includeRecommended --quiet --locale en-US" \
    --confirm \
    && rmdir /S /Q C:\chococache
