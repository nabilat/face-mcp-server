# azure-ai-vision-face-mcp-server-preview
## add dependency
go to liveness-server-typescript folder, run
```
$ npm install --save-dev typescript @types/node
$ npm install
$ npm run build
```
then in the build folder, you have index.js
## sample for vs code
add .vscode/mcp.json

```
{
    "servers": {
        "liveness-server": {
            "type": "stdio",
            "command": "node",
            "args": [
                "${workspaceFolder}/liveness-server-typescript/build/index.js"
            ],
            "env": {
                "FACEAPI_ENDPOINT": "apiendpoint",
                "FACEAPI_KEY": "apikey",
                "FACEAPI_WEBSITE": "https://liveness-webapp.azurewebsites.net",
                "SESSION_IMAGE_DIR": "${workspaceFolder}/liveness-server-typescript/build/"
            }
        }
    }
}

```





## Sample Claude config should be:

```
{
  "mcpServers": {
    "liveness-server": {
      "command": "node",
      "args": ["YOUR_PATH/build/index.js"],
      "env": {
                "FACEAPI_ENDPOINT": "apiendpoint",
                "FACEAPI_KEY": "apikey",
                "FACEAPI_WEBSITE": "https://yourexample.azurewebsites.net",
                "SESSION_IMAGE_DIR": "D:\somePATH"
        }
    }
  }
}

```

## Localation of session image
If you don't set the variable for session image dir, it will be saved at user folder, ~ for linux, which is /home/username usually, or C:\Users\username in windows usually.

## Liveness with verify
When you have a verify image set, it will switch liveness with verify mode.  sample:

```
"VERIFY_IMAGE_FILE_NAME": "${workspaceFolder}/liveness-server-typescript/build/0b5db043-951c-49d4-9109-e11cb558bb79/sessionImage.jpg",

```