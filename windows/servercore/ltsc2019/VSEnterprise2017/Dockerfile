FROM patrikulus/az-pipelines-agent:windows-basic-tools

ENV chocolateyUseWindowsCompression=false

RUN choco config set cachelocation C:\chococache

RUN choco install \
    visualstudio2017enterprise \
    --package-parameters "--allWorkloads --includeRecommended --includeOptional --quiet --locale en-US" \
    --confirm \
    && rmdir /S /Q C:\chococache
