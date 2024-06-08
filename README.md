# NATS

Before running NATS with Docker, ensure that the necessary ports are open on the host's firewall. This is required to allow connections to the NATS server.

## Firewall Configuration with UFW

If you are using UFW (Uncomplicated Firewall) on the Docker host, execute the following commands to allow traffic on the standard NATS ports:

```bash
sudo apt install ufw
sudo ufw enable
sudo reboot 

# Allow the main NATS port for client connections
sudo ufw allow 4222

# Allow the NATS monitoring port for the HTTP monitoring dashboard
sudo ufw allow 8222

# Allow the NATS routing port for routing between NATS servers
sudo ufw allow 6222
```

These rules will configure UFW to accept connections on the ports that the NATS server uses. Adjust the port numbers if you are using different values from the defaults.

## Execution

To run the NATS server, go to the directory that contains your `docker-compose.yml` file and execute:

```bash
cd nats
docker compose up
```

Make sure to replace `nats` with the correct path to your directory if necessary.
```

Keep in mind that using `sudo reboot` will restart the machine, so all non-essential services should be closed before this command is executed, and you may want to inform users about this.

Additionally, note that firewall configuration may vary depending on the operating system and the specific network setup of the host. Ensure that these instructions align with the best security practices for the environment in which NATS is being installed.