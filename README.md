This is a reproduction of an issue with the Marko TypeScript plugin that causes the tsserver to crash when a `.ts` file is opened.

1. npm i.
2. Open `+middleware.ts` in VSCode.
3. The tsserver will attempt to load 5 times and before failing with the error message:

In the TypeScript output:
```
 2024-03-13 10:23:57.342 [info] Using tsserver from: c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js
 2024-03-13 10:23:57.343 [info] <syntax> Forking...
 2024-03-13 10:23:57.343 [info] <syntax> Starting...
 2024-03-13 10:23:57.343 [info] <semantic> Forking...
 2024-03-13 10:23:57.343 [info] <semantic> Starting...
 2024-03-13 10:23:58.077 [info] Killing TS Server
 2024-03-13 10:23:58.086 [error] TSServer exited. Code: null. Signal: SIGTERM
```

In the Extension Host output:
```
 2024-03-13 10:23:59.093 [error] Error: <semantic> TypeScript Server Error (5.3.2)
 Cannot read properties of undefined (reading 'getSourceFiles')
 TypeError: Cannot read properties of undefined (reading 'getSourceFiles')
     at ConfiguredProject2.getScriptInfos (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:177062:29)
     at _ProjectService.sendProjectTelemetry (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:180122:17)
     at ConfiguredProject2.updateGraph (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:178489:25)
     at _ProjectService.createLoadAndUpdateConfiguredProject (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:180204:13)
     at _ProjectService.assignProjectToOpenedScriptInfo (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:181297:26)
     at c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:181577:64
     at flatMap (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:2597:17)
     at _ProjectService.applyChangesInOpenFiles (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:181577:24)
     at updateOpen (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:182775:29)
     at c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:185377:69
     at IpcIOSession.executeWithRequestId (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:185369:14)
     at IpcIOSession.executeCommand (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:185377:29)
     at IpcIOSession.onMessage (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:185419:51)
     at process.<anonymous> (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\node_modules\typescript\lib\tsserver.js:187001:14)
     at process.emit (node:events:514:28)
     at emit (node:internal/child_process:937:14)
     at process.processTicksAndRejections (node:internal/process/task_queues:83:21)
     at Function.create (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\typescript-language-features\dist\extension.js:2:503003)
     at v.dispatchResponse (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\typescript-language-features\dist\extension.js:2:496983)
     at v.dispatchMessage (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\typescript-language-features\dist\extension.js:2:495837)
     at ChildProcess.<anonymous> (c:\Users\USER\AppData\Local\Programs\Microsoft VS Code\resources\app\extensions\typescript-language-features\dist\extension.js:2:495330)
     at ChildProcess.emit (node:events:514:28)
     at emit (node:internal/child_process:937:14)
     at processTicksAndRejections (node:internal/process/task_queues:83:21)
```
