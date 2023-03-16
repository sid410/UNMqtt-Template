# UNMqtt-Template
Template for Unity-Nodered communication using Mqtt

## Prerequisites

- [github](https://github.com/) account
- [git tools](https://git-scm.com/downloads) installed
- [docker](https://www.docker.com/) installed

## Steps

1. Fork the [Node-RED source Repo](https://github.com/sid410/UNMqtt-Node-RED-Source)

2. Clone this [UNMqtt-Template Repo](https://github.com/sid410/UNMqtt-Template)

3. Use the command: (replace the [*LocalRepoPath] with your local path, e.g. C:\Users\My-Username\...)
```
docker run -itd -p 1880:1880 -v [*LocalRepoPath]\UNMqtt-Template\UNMqtt-Docker-Compose\NRdata:/data -e NODE_RED_ENABLE_PROJECTS=true --name mynodered nodered/node-red
```

4. Open the Node-RED instance with browser on address http://localhost:1880

5. Choose Clone Repository

6. Enter your github account info, then put in the git repo URL your forked UNMqtt-NodeRED-Source

7. (ignore the errors of missing dependencies) For now, close the browser

8. Run the commands:
```
docker stop mynodered
docker rm mynodered
```

9. To enable the projects feature for source control, cd to `...\UNMqtt-Docker-Compose\NRdata` folder, open `settings.js` and in **editorTheme** under **projects**, changed `enabled` value to `true`

10. cd to `...\UNMqtt-Docker-Compose` folder then run the commands:
```
npm install
npm start
```

If there is another instance of mosquitto, kill the process[^1].

[^1]: To kill the process, run:
`netstat -ano | findstr 1883` then
`taskkill /F /PID [corresponding PID#]`

11. Open a browser and go to the address http://localhost:1880/ui/

12. Open UNMqtt-Unity with Unity, then open the TestMqttMessage Scene

13. Enter PlayMode and whenever you click the button `Hello` in browser, it will print in Unity console `Hello World`

14. Lastly, to clean up the docker containers, in the running CMD:
```
[ctrl + c] to interrupt
npm stop
```
