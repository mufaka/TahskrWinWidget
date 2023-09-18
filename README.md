# TahskrWinWidget

This is a [Tahskr](https://github.com/Dullage/tahskr-server) widget for [WinWidgets](https://github.com/beyluta/WinWidgets)

![image](https://github.com/mufaka/TahskrWinWidget/assets/8632538/275bb463-0105-465e-ac08-8e31e315d16d)

## Installation
Copy tahskr.html and the tahskr directory to your widget directory. By default, widgets are located in your Documents\Widgets directory.

![image](https://github.com/mufaka/TahskrWinWidget/assets/8632538/caccbd72-0bbb-4fab-99a4-12b4254e5295)

### A note on running Tahskr
Tahskr is most easily run using Docker, however there are some additional instructions not readily available in the documentation.

Set an admin password for the server when running in Docker.
```
docker run \
  -d \
  --name tahskr-server \
  -v "[YOUR DATA PATH]:/app/data" \
  -p [YOUR PORT]:8080 \
  -e "TAHSKR_ADMIN_PASSWORD=[YOUR ADMIN PASSWORD]" \
  --restart=always \
  dullage/tahskr-server:latest
```

1. Replace [YOUR PORT] with the tcp port for tahskr-server to listen on
2. Replace [YOUR DATA PATH] with a path on your filesystem where you want the data to be stored.
3. Replace [YOUR ADMIN PASSWORD] with an admin password of your choice.

Create a user example with curl

`curl -X POST http://[SERVER IP OR NAME]:[YOUR PORT]/user -H 'Content-Type: application/json' -H 'x-admin: [YOUR ADMIN PASSWORD]' -d '{ "username": "[YOUR USERNAME]", "password": "[YOUR PASSWORD]"}'`

1. Replace [YOUR PORT] with the tcp port the tahskr-server listens on
2. Replace [SERVER IP OR NAME] with the server name or ip address of the tahskr-server
3. Replace [YOUR ADMIN PASSWORD] with an admin password of your choice.
4. Replace [YOUR USERNAME] with the username you want to create
5. Replace [YOUR PASSWORD] with the password you want to create for the user

If all goes well you should see an output from the curl command similar to the following:

`{"config":null,"created":"2023-09-17T22:34:57.068144","id":1,"username":"[YOUR USERNAME]"}`
