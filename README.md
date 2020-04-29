Blackholechain [BHC] (Sigma protocol)
===============================



Blackholechain
----------------
* Coin Suffix: BHC
* Algorithm: lyra2z330
* Algo params: LYRA2(BEGIN(thash), 32, BEGIN(nVersion), 80, BEGIN(nVersion), 80, 2, 330, 256)
* Target Spacing: 150 Seconds
* Retarget: every block
* Confirmation: 6 Blocks
* Maturity: 120 Blocks
* Blocks: ~576 per day
* Total Coins: 21,000,000 BHC
* Min TX Fee: 0.001 BHC
* Block Size: 4MB

Net Parameters
----------------
* P2P Port=19800
* RPC Port=19900
* Client core=13.4
* Client name=Blackholechain.qt
* Conf file=Blackholechain.conf

Installation folder
----------------
* Windows: C:\Users\Username\AppData\Roaming\Blackholechain
* Mac: /Library/Application Support/Blackholechain
* Unix: /.Blackholechain

Debian/Ubuntu Linux Daemon Build Instructions
================================================

	install dependencies:
	Build a node or qt:

	if you need a swap memory:
	free
	dd if=/dev/zero of=/var/swap.img bs=2048 count=1048576
	mkswap /var/swap.img
	swapon /var/swap.img
	free


	sudo apt-get update
	sudo apt-get upgrade

	sudo apt-get install git build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils libboost-all-dev

	sudo apt-get install software-properties-common
	sudo add-apt-repository ppa:bitcoin/bitcoin
	sudo apt-get update
	sudo apt-get install libdb4.8-dev libdb4.8++-dev

	sudo apt-get install libminiupnpc-dev libzmq3-dev
	for qt:
	sudo apt-get install libqt5gui5 libqt5core5a libqt5dbus5 qttools5-dev qttools5-dev-tools libprotobuf-dev protobuf-compiler libqrencode-dev

	git clone https://github.com/Blackholechain/Blackholechain

	cd Blackholechain
	for vps:
	./autogen.sh
	./configure  --without-gui
	make -j 4   (-j is optional, number of your cores, -j 4)

	for qt:
	./autogen.sh
	./configure
	make -j 4   (-j is optional, number of your cores, -j 4)

	cd src
	strip Blackholechaind
	strip Blackholechain-cli
	or:
	cd src
	cd qt
	strip Blackholechain-qt

	files are:
	Blackholechaind
	Blackholechain-cli

	Blackholechain-qt
	Blackholechain.conf
	xnode.conf
	data folder:
	Blackholechain

	port 19800
	rpc port 19900

Example Blackholechain.conf Configuration
===================================================

	#listen=1
	#server=1
	#rpcpassword=
	#rpcusername=
	#maxconnections=16
	#connect=
	#addnode=
	#rescan=0
	#reindex=0
	#reindex-chainstate=0
	#xnode=1
	#xnodeprivkey=123123123123123123123123 ## Replace with your xnode private key
	#externalip=123.123.123.123:19800 ## Replace with your node external IP

