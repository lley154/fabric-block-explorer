# fabric-blockchain-explorer
Note: You must complete Lab #1, Lab #2 and Lab #3 first which will include the required binary files.

## Install and make sure you have a private admin key available for the blockchain explorer

Go to your home directory and issue the following commands
```
cd ~
git clone https://github.com/lley154/fabric-blockchain-explorer.git
cd fabric-block-expoler
sudo cp -r ../fabric-samples/test-network/organizations/ .
sudo chmod a+rwx organizations ## only required for lab env
```
Copy the generated private key for admin in org1 to priv_sk

For example
```
cd /home/ubuntu/fabric-blockchain-explorer/organizations/peerOrganizations/org1.example.com/users/Admin@org1.example.com/msp/keystore/
cp d5c3c0946461845e5cf9a02d7cb7b25c04ca3827567733ef912dd99d16847b41_sk priv_sk
sudo chmod a+rwx priv_sk  ## this is only done for lab env
```
Now bring up docker images for postgresDB and explorer UI
```
docker-compose up -d
```
You can look at the logs from the explorer and check that there are no errors
```
sudo docker logs explorer.mynetwork.com -f
```

To shutdown the explorer but keeping persistent data
```
docker-compose down
```

To shudwon the explorer and remove all data
```
docker-compose down -v
```


Next, log into the server using a new terminal window to set up port forwarding to access the blockchain explorer UI using port 8080.

ssh usage
```
ssh -L local_port:destination_server_ip:remote_port ssh_server_hostname
```
For example
```
ssh -i lab2.pem -L 8080:ec2-54-91-100-220.compute-1.amazonaws.com:8080 ubuntu@ec2-54-91-100-220.compute-1.amazonaws.com
```
Now use a browser on your local machine and access the Hyperledger Blockchain Explorer UI
```
http://localhost:8080/
user: exploreradmin
pass: exploreradminpw
```

