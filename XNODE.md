Xnode Instructions and Notes
=============================
 - Version 0.2.2
 - Date: 20 jan 2020

Prerequisites
-------------
 - Ubuntu 16.04+
 - Port **19800** is open
 - Libraries to build from Blackholechain source if you want to build it yourself

Step 0. ON VPS: Acquire the binaries
----------------------


<details>
<summary><strong>Build from source</strong></summary>
<strong>0.1.</strong>  Check out from source:

    git clone https://github.com/Blackholechain/Blackholechain

<strong>0.2.</strong>  See [README.md](README.md) for instructions on building.
</details>
	

Step 1. ON VPS: Open port 19800 (Optional - only if firewall is running)
----------------------
**1.1.**  Run:

    sudo ufw allow ssh 
    sudo ufw allow 19800
    sudo ufw default allow outgoing
    sudo ufw enable

Step 2. ON LOCAL MACHINE: First run on your Local Wallet
----------------------

<details open>
<summary><strong>If you are using the qt wallet</strong></summary>
<strong>2.0.</strong>  Open the wallet

<strong>2.1.</strong>  Click Help -> Debug window -> Console

<strong>2.2.</strong>  Generate xnodeprivkey:

    xnode genkey

(Store this key)

<strong>2.3.</strong>  Get wallet address:

    getaccountaddress XN1

<strong>2.4.</strong>  Send to received address <strong>exactly 2000 BHC</strong> in <strong>1 transaction</strong>. Wait for 15 confirmations.

<strong>2.5.</strong>  Close the wallet
</details>

<details>
<summary><strong>If you are using the daemon</strong></summary>
<strong>2.0.</strong>  Go to the checked out folder or where you extracted the binaries

    cd Blackholechain/src

<strong>2.1.</strong>  Start daemon:

    ./Blackholechaind -daemon -server

<strong>2.2.</strong>  Generate xnodeprivkey:

    ./Blackholechain-cli xnode genkey

(Store this key)

<strong>2.3.</strong>  Get wallet address:

    ./Blackholechain-cli getaccountaddress XN1

<strong>2.4.</strong>  Send to received address <strong>exactly 5000 BHC</strong> in <strong>1 transaction</strong>. Wait for 15 confirmations.

<strong>2.5.</strong>  Stop daemon:

    ./Blackholechain-cli stop
</details>


## For both:

**2.6.**  Create file **xnode.conf** (in **~/.Blackholechain**, **C:\Users\USER\AppData\Roaming\Blackholechain** or **~/Library/Application Support/Blackholechain** depending on your Operating System) containing the following info:
 - LABEL: A one word name you make up to call your node (ex. XN1)
 - IP:PORT: Your xnode VPS's IP, and the port is always 19800.
 - XNODEPRIVKEY: This is the result of your "xnode genkey" from earlier.
 - TRANSACTION HASH: The collateral tx. hash from the 5000 BHC deposit.
 - INDEX: The Index from the transaction hash

To get TRANSACTION HASH, run:

```
./Blackholechain-cli xnode outputs
```
or
```
xnode outputs
```

depending on your wallet/daemon setup.

The output will look like:

    { "d6fd38868bb8f9958e34d5155437d009b72dfd33fc28874c87fd42e51c0f74fdb" : "0", }

Sample of xnode.conf:

    XN1 111.111.222.222:19800 XrxSr3fXpX3dZcU7CoiFuFWqeHYw83r28btCFfIHqf6zkMp1PZ4 d6fd38868bb8f9958e34d5155437d009b72dfd33fc28874c87fd42e51c0f74fdb 0

**2.7.** Lock unspent

As long as the xnode is listed in your xnode.conf file the funds are automatically locked so you don't accidentially spend them.

Step 3. ON VPS: Update config files
----------------------
**3.1.**  Create file **Blackholechain.conf** (in folder **~/.Blackholechain**)

    server=1
    xnode=1
    xnodeprivkey=XXXXXXXXXXXXXXXXX  ## Replace with your xnode private key
    externalip=XXX.XXX.XXX.XXX ## Replace with your node external IP


Step 4. ON LOCAL MACHINE: Start the xnode
----------------------

<details open>
<summary><strong>With qt wallet</strong></summary>
<strong>4.1</strong> Start the xnode via your gui wallet in the xnodes tab
</details>

<details>
<summary><strong>With daemon</strong></summary>
<strong>4.1</strong> Start xnode:

    ./Blackholechain-cli xnode start-alias <LABEL>

For example:

    ./Blackholechain-cli xnode start-alias XN1

<strong>4.2</strong>  To check node status:

    ./Blackholechain-cli xnode debug

</details>


If not successfully started, just repeat start command
