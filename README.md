# #Mawari-Node-Guide

<img width="978" height="551" alt="Opera Snapshot_2025-09-29_034300_chainscan 0g ai" src="https://github.com/user-attachments/assets/a7de3362-9e5a-461a-bbf4-cb7d770dab8b" /><br>

<hr style="border: 2px solid #555; border-radius: 5px; box-shadow: 0 0 5px #555;" />

# #How to Run Mawari Guardian Node Testnet
## #Follow the 4 steps below
1.  Claim Faucet                                             
2. Mint NFT Guardian Node
3. Run Guardian Node
4. Delegate Guardian Node

<hr style="border: 2px solid #555; border-radius: 5px; box-shadow: 0 0 5px #555;" />

# #Step-1 Claim Faucet  [***Here***](https://hub.testnet.mawari.net)  

<img width="911" height="592" alt="Screenshot 2025-09-30 090506" src="https://github.com/user-attachments/assets/c10512d7-8440-4b10-9ac7-a120858c728a" /><br>

<hr style="border: 2px solid #555; border-radius: 5px; box-shadow: 0 0 5px #555;" />

# #Step-2 Mint NFT Guardian Node<br>
* Connect your wallet and Mint NFT Guardian Node  [***Here***](https://testnet.mawari.net/mint)
* Set to max claim: 3 NFT

<img width="1243" height="903" alt="3" src="https://github.com/user-attachments/assets/ad67f092-a0b4-45b4-bffd-2b4677ec4b91" /><br>

<hr style="border: 2px solid #555; border-radius: 5px; box-shadow: 0 0 5px #555;" />

# #Step-3 Run Guardian Node<br>
## 🖥️ Minimum Sysyem Requirements
* NOTE: Higher specs Potentially more Earning Reward.

<img width="484" height="235" alt="4" src="https://github.com/user-attachments/assets/58c578dc-0665-4e3a-b5f6-4c4b570587fc" /><br>

### #Install Packages<br>
```
sudo apt-get update && sudo apt-get upgrade -y
sudo apt install curl ufw iptables build-essential git wget lz4 jq make gcc nano automake autoconf tmux htop nvme-cli \
libgbm1 pkg-config libssl-dev libleveldb-dev tar clang bsdmainutils ncdu unzip -y
```

### #Install Docker<br>
* Skip if docker is already installed
```
sudo apt update -y && sudo apt upgrade -y
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done

sudo apt-get update
sudo apt-get install ca-certificates curl gnupg -y
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update -y && sudo apt upgrade -y
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin -y

# Test Docker
sudo docker run hello-world
```

### #Install Mawari Guardian Node<br>
```
mkdir mawari && cd mawari
nano docker-compose.yaml
```

### #Create Service and Configuration<br>
* Replace <0xYOUR-EVM-ADDRESS-HERE> with the EVM Address that you claimed Faucet on the previous.  

```
services:
  guardian-node:
    image: us-east4-docker.pkg.dev/mawarinetwork-dev/mwr-net-d-car-uses4-public-docker-registry-e62e/mawari-node:latest
    container_name: guardian-node
    restart: always
    environment:
      - OWNERS_ALLOWLIST=0xYOUR-EVM-ADDRESS-HERE # <-- change your EVM address here 
    volumes:
      - ./cache:/app/cache
```

* Save Configuraation file with CTRL+X, then press Y then ENTER<br>

### #Start Your Node<br>
```
docker compose up -d
```

### #Check Logs<br>
```
docker compose logs -f
```

* Don't log out yet. You'll need it to check the delegation process.
* After running the node, you'll receive a Burner Address. Copy and save it, you'll use it to delegate to this Address.
* Send 1 Mawari to your Burner Address from your Owner Address

<img width="1405" height="777" alt="5" src="https://github.com/user-attachments/assets/42465df6-4721-460c-9bff-d808ad4b5e18" /><br>

<hr style="border: 2px solid #555; border-radius: 5px; box-shadow: 0 0 5px #555;" />

# #Step-4 Delegate Guardian Node<br>
### #A. Fund Your Burner Address
* NOTE: Before delegation, Send 1 Mawari to your Burner Address
* Make sure your Burner Address has received 1 Mawari Faucet from your Owner Address.
* Check Explorer [***Here***](https://explorer.testnet.mawari.net)

### #B. Open Delegation Page<br>
* Connect your wallet  and Goto Delegation Page [***Here***](https://app.testnet.mawari.net/licenses)
  
<img width="938" height="513" alt="9" src="https://github.com/user-attachments/assets/e14e0601-5642-4714-baa0-4d2889861c16" /><br>

### #C. Delegate Node<br>
* Checklist all License IDs and click Delegate.
* Paste your Burner Address.
  
<img width="1079" height="628" alt="7" src="https://github.com/user-attachments/assets/eac340eb-f711-4018-a906-0fb377c93f3b" /><br>

<img width="1213" height="603" alt="8" src="https://github.com/user-attachments/assets/7358d223-e47f-46ba-ac28-9fd258a8946b" /><br><br>

* Check your logs, you will see the submit delegate confirmation. 

<img width="760" height="172" alt="9" src="https://github.com/user-attachments/assets/5edc9a6c-17ae-4d15-831f-6bfdbcb891ef" /><br><br>

* Wait until the status changes from Nodelegate → Pending → Running.
  
<img width="970" height="608" alt="Screenshot_1" src="https://github.com/user-attachments/assets/1e5a968d-0ab0-4654-a4a5-e8eaf55d926a" /><br><br>

### ✅ Done! You have successfully Running Mawari Node Testnet. 
### ⏳ Rewards (zMawari) will appear after ~24 hours. 

<hr style="border: 2px solid #555; border-radius: 5px; box-shadow: 0 0 5px #555;" />











  
























