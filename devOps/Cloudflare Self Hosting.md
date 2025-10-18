Here is a step-by-step guide to using Cloudflare to self-host a website or application, based on recent detailed resources and best practices:

***

## Step-by-Step Guide to Self-Hosting with Cloudflare

### 1. Register Domain and Create Cloudflare Account
- Obtain a domain name from any registrar (e.g., Porkbun, Namecheap).
- Create a free Cloudflare account.
- Add your domain to your Cloudflare dashboard.
- Change your domain’s nameservers to the Cloudflare nameservers provided.

### 2. Install Cloudflared on Your Server
- Choose your server environment (Linux, macOS, Windows, Docker).
- Download and install the `cloudflared` client on your self-hosted server.
- Authenticate the client by running `cloudflared login` to link it to your Cloudflare account. This opens a browser window for your Cloudflare login and grants permissions.

### 3. Create a Tunnel
- In the Cloudflare Zero Trust dashboard, go to **Access > Tunnels**.
- Click **Create a Tunnel**, give it a name to identify it.
- This generates a tunnel UUID and credentials file on your server.

### 4. Configure Tunnel
- Create a configuration file at `~/.cloudflared/config.yml`.
- Define the tunnel UUID, credentials file path, and ingress rules directing traffic from your domain or subdomain to your local service.
- Example configuration snippet:
  ```
  tunnel: <Tunnel-UUID>
  credentials-file: /path/to/credentials.json
  ingress:
    - hostname: yourdomain.com
      service: http://localhost:8080
    - service: http_status:404
  ```
- Adjust hostname and service URL for your setup.

### 5. Route DNS through the Tunnel
- Run the command to create a CNAME DNS record mapping your domain/subdomain to Cloudflare’s tunnel:
  ```
  cloudflared tunnel route dns <tunnel-name> yourdomain.com
  ```
- Verify the DNS route is active.

### 6. Run the Tunnel
- Start the tunnel with:
  ```
  cloudflared tunnel run <tunnel-name>
  ```
- Optionally, install it as a service to run on boot automatically:
  ```
  sudo cloudflared service install
  sudo systemctl enable cloudflared
  sudo systemctl start cloudflared
  ```

### 7. Set Up SSL/TLS
- In the Cloudflare dashboard, go to **SSL/TLS** settings.
- Choose your SSL/TLS mode (Automatic or Full/Strict recommended).
- This provides HTTPS protection between Cloudflare and your visitors, securing your self-hosted site.

### 8. Access Your Website
- Your self-hosted service should now be accessible securely via your domain through Cloudflare’s network.
- Test by navigating to `https://yourdomain.com`.

***

This approach uses Cloudflare Tunnel, which avoids opening inbound ports on your home or cloud server and benefits from Cloudflare’s security and performance features.

---

Here is a detailed step-by-step guide to installing and configuring cloudflared on a server, specifically tailored for Linux (Ubuntu), which can be adapted for other Linux distros:

***

## Step 1: Install cloudflared

### Option 1: Install via Package Manager (Ubuntu/Debian)
- Add Cloudflare's GPG key for repository verification:
  ```
  curl -L https://pkg.cloudflare.com/cloudflare-main.gpg | sudo tee /usr/share/keyrings/cloudflare-archive-keyring.gpg >/dev/null
  ```
- Add the Cloudflare repository:
  ```
  echo "deb [signed-by=/usr/share/keyrings/cloudflare-archive-keyring.gpg] https://pkg.cloudflare.com/cloudflared $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/cloudflared.list
  ```
- Update and install cloudflared:
  ```
  sudo apt update
  sudo apt install cloudflared
  ```
  
### Option 2: Manual Download & Install
- Download the latest binary for your system:
  ```
  wget https://github.com/cloudflare/cloudflared/releases/latest/download/cloudflared-linux-amd64.deb
  ```
- Install the package:
  ```
  sudo dpkg -i cloudflared-linux-amd64.deb
  ```
- Alternatively, download the binary, move it to `/usr/local/bin`, and make executable:
  ```
  sudo mv cloudflared /usr/local/bin/cloudflared
  sudo chmod +x /usr/local/bin/cloudflared
  ```

- Verify installation:
  ```
  cloudflared -v
  ```

## Step 2: Authenticate cloudflared with Cloudflare

- Run:
  ```
  cloudflared tunnel login
  ```
- This command provides a URL; open it in a browser and log in with your Cloudflare account.
- Authorize cloudflared; this downloads a certificate file (`cert.pem`) to authenticate your instance.

## Step 3: Create a Tunnel

- Create a named tunnel:
  ```
  cloudflared tunnel create <TUNNEL_NAME>
  ```
- Note the generated tunnel UUID and the location of the credentials file (usually in `~/.cloudflared/`).

## Step 4: Create a Configuration File

- Create or edit the config at `~/.cloudflared/config.yml` with ingress rules and tunnel info. Example:
  ```yaml
  tunnel: <TUNNEL_UUID>
  credentials-file: ~/.cloudflared/<TUNNEL_UUID>.json

  ingress:
    - hostname: yourdomain.com
      service: http://localhost:8080
    - service: http_status:404
  ```
- Adjust hostname and port according to your setup.

## Step 5: Route DNS

- Map your domain/subdomain to the tunnel:
  ```
  cloudflared tunnel route dns <TUNNEL_NAME> yourdomain.com
  ```

## Step 6: Run cloudflared Tunnel

- To start the tunnel interactively:
  ```
  cloudflared tunnel run <TUNNEL_NAME>
  ```
- To run as a service on Linux (auto starts on boot):
  ```
  sudo cloudflared service install
  sudo systemctl enable cloudflared
  sudo systemctl start cloudflared
  ```

***

This setup establishes a secure Cloudflare Tunnel connecting your server application to your domain through Cloudflare's network, without exposing ports directly.

---

