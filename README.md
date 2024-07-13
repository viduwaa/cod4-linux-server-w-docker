# Call of Duty 4 Server Setup with Docker

**This is the 1st time I worked with docker there might be some errors, but currently I did not find any**

### Prerequisites
Ensure Docker is installed on your system. If not, download it
```bash
sudo apt get-update && sudo apt get-install docker.io
```

### 1. Pull the Docker Image
```bash
docker pull viduwa/cod4-linux-server:latest
```


### 2. Run the Docker Container

```bash
docker run -d -t --name cod4server -p 28960:28960/tcp -p 28960:28960/udp viduwa/cod4-linux-server:latest
```

### 3. Connect to the Docker Container

```bash
docker exec -it cod4server /bin/bash
```

### 4. Edit server.cfg

- Inside the container, edit `main/server.cfg` using `vim`:
```bash
vim main/server.cfg
```
- add the token obtained from [cod4master.cod4x.ovh](https://cod4master.cod4x.ovh) to line 15.
- then configure the server.cfg as you wish.

### 6. Attach to tmux Session to start the server



```bash
tmux attach-session -t cod4server
```

### 7. Start the Server

#### Normal 
```bash
./cod4x18_dedrun +set dedicated 2 +set net_ip 000.000.000.000 +set net_port 28960 +set modstats 0 +set rcon_password “Password” +set sv_maxclients 16 +exec server.cfg
```
#### Promod 
- Start a promod server
```bash
./cod4x18_dedrun +set dedicated 2 +set fs_game "Mods/pml220" +set net_ip 000.000.000.000 +set net_port 28960 +set modstats 0 +set rcon_password “Password” +set sv_maxclients 16 +exec server.cfg
```

- Cod4 Promod Commands
    - Start 5v5 match with 24 rounds and knife round:  ```promod_mode mr12_match_knife_pb```





## Why tmux ?

- It's easy to connect back into console while server is running.
- while server run on tmux you can use container bash for edit server.cfg

## Other Ways ?

- Use rcon pw to control server using ```set rcon_password “Password” ```
- Login to rcon in client using ```rcon login "Password" ```

###
## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://viduwa.me/)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/viduladeneth/)


