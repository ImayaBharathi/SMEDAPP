# SMEDAPP
An application that runs on block chain using the hyperledger fabric.

#Instruction to run this application


The following are prerequisites for installing the required development tools:

Operating Systems: Ubuntu Linux 14.04 / 16.04 LTS (both 64-bit), or Mac OS 10.12
Docker Engine: Version 17.03 or higher
Docker-Compose: Version 1.8 or higher
Node: 8.9 or higher (note version 9 is not supported)
npm: v5.x
git: 2.9.x or higher
Python: 2.7.x


Once You have all the prerequisites ready now its time to run the Business network application on the blockchain using hyper ledger 

1.Move to the fabric-dev-servers folder (cd fabric-dev-servers).
2.Start the docker image to get the business network( run ./startFabric.sh)
3.Now create a card to access the network (./createPeerAdminCard.sh)
4.Run yo hyperledger-composer
  4.1.4.1.choose Business network model
	4.2.Business network name =====> test-bna
	4.3.auth name,email,license,namespace(mention as your need)
	4.4.Generate populated network template
5.cd (network model name) 
6.mkdir dist (under test-bna)
7.composer archive create -t dir -n ../
8.take the created file(test-bna@0.0.1 zip file) to fabric-dev-servers folder
9.cd fabric-dev-servers
10.composer network install -a test-bna@0.0.1(name of the archive file)  -c PeerAdmin@hlfv1(card name)
11.composer network start  -c(card name flag) PeerAdmin@hlfv1 -n(network file flag) new-test-bna -V(version flag) 0.0.1 -A(admin name) admin -S(admin secret) adminpw
12.composer card import -f (file name flag)  ./card name
13.composer-rest-server
   13.1.Enter the card name you want to use: (card name)
14.yo hyperledger-composer:angular
	14.1.yes
	14.2.project name
	14.3.description,authorname,email,license,name of the business card()
	14.4.connect to exixting rest api, localhost,port,
15.Move to the deployed folder using cd command
16.Run npm start


The above command will tunnel the rest server to the local host : 4200
and the webapp to the local host :3000#explorer

This application can also be viewed on "https://composer-playground.mybluemix.net/test#" once deployed in the locaal machine it will send a request to IBM bluemix 
so we can also run it in bluemix
