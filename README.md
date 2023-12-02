# Zora-Node

sudo apt-get update && sudo apt-get upgrade -y

# Install the essential libraries: 
sudo apt install curl build-essential git screen jq pkg-config libssl-dev libclang-dev ca-certificates gnupg lsb-release -y

# Let’s install Docker now. This will Add Docker's Official GPG Key :
sudo install -m 0755 -d /etc/apt/keyrings

curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add the repository to Apt sources :
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
  
sudo apt-get update

# Let’s install the dependencies :
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose -y

# Press Y and Enter if required 

# Clone the Conduit Github repository.
git clone https://github.com/Hoanghienvi/node_zora.git

cd node_zora

./download-config.py zora-mainnet-0

export CONDUIT_NETWORK=zora-mainnet-0

cp .env.example .env

nano .env

# Login web Alchemy get API:
![image](https://github.com/Hoanghienvi/Zora-Node/assets/87926002/52b53e48-4916-4ef5-97d2-07a3f5ee368a)
![image](https://github.com/Hoanghienvi/Zora-Node/assets/87926002/9a87383a-b6fb-4664-997e-9a1d67066a52)
![image](https://github.com/Hoanghienvi/Zora-Node/assets/87926002/ffa3a3b3-3c0f-4504-aafc-d9f8370a8935)
![image](https://github.com/Hoanghienvi/Zora-Node/assets/87926002/28e4f804-15bb-4ca0-a280-b4b88f9bb40a)
![image](https://github.com/Hoanghienvi/Zora-Node/assets/87926002/c9661b5f-4eca-434d-82b0-dfea593b8fb7)

# Edit file config:  nano .env

# "Replace <http://11rpc>" with your Alchemy Account API key (HTTPS)
![image](https://github.com/Hoanghienvi/Zora-Node/assets/87926002/fd93845b-b639-4f6d-900e-5102b640a2fe)



Close the file by pressing CTRL + X . You’ll be asked if you want to save the file, press Y and hit Enter.

# Start a screen session with :
screen -S log
docker compose up --build

# Your Node Is Up and Running. You can detach from the screen by pressing CTRL + A + D

# Check Log:
screen -r log
