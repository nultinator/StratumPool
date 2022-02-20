# StratumPool, StratumSolo & Cenote : Arrow Solo-Mining Stratum Servers

These are a very simple stratum servers for connecting GPU miners to a Arrow full node.

- StratumPool : Clients can specify their own transparent arrow address.
- StratumSolo : All clients mine to the local node wallet.
- Cenote      : Solo pool with more options

All operate as 'solo-pools', miners ONLY get paid if they find a block.

Payments are made within the coinbase transaction, which means :-
- Rewards must mature for 100 blocks before they can be spent.
- The first transaction MUST be to a shielded address (ar2as1).

There's no dev fee but don't expect any support !! 

Please buy beers for the original developer:-
- YCASH : ys1c8cvazsz5gfp2zhdmzxcarfh4gp6jezdcxnywfcpyuau0l0f9uj99tzvrr6sjw5rfhpsw06lc6n

## Requirements :-

- Arrow Full Node (Ubuntu/Debian Linux)
- Quiver Full Node
- GPU Hardware (ie: Nvidia, AMD)
- GPU Mining Software for Equihash 192,7 (ie: miniZ v1.6w)

It doesn't work on Windows or iThings, but I dont care as I dont have any :-)

## Tested Miners :-

- GMiner (v2.64) --TESTED AND WORKING WITH ARROW
- lolMiner (v0.8.4) --TESTED FOR YCASH, NOT ARROW
- miniZ (v1.6w) --TESTED FOR YCASH, NOT ARROW

## Usage :-

stratumpool / stratumsolo

* `-port=3333 (port for miner connections, default 3333)`
* `-password=notsecret (optional password miners need to connect, default not set)`

cenote

* `-text "Coinbase text here" (text to insert in mined blocks)`
* `-scrooge (all block rewards go to local node wallet)`
* `-port 3334 (port for miner connections, default 3334)`
* `-password notsecret (optional password miners need to connect, default not set)`

* default port 3334

## Installation  :-

* sudo apt-get update
* sudo apt-get upgrade
* sudo apt-get install perl build-essential cpan
* sudo cpan
* install CPAN
* reload
* exit

* sudo cpan install POSIX IO::Handle IO::Socket IO::Select JSON	Digest::SHA Text::CSV


## Important !!! Don't forget !!!

You MUST add a line to your node configuration file (arrow.conf) to set a fixed mining address, ie :-

mineraddress=aryouraddressgoeshere

* This MUST be a transparent address (starts with 'ar')
* The address MUST belong to the node wallet (use 'arrow-cli getnewaddress')
* Make sure to back up the private key to this address as well (use 'arrow-cli dumprivkey "armypersonalminingaddress" ')

Before you can spend any coins you have mined, you must :-

* Wait 100 blocks for the reward to mature.
* Send the ENTIRE balance of the "ar" addr to an "as1" addr you control. (Use Quiver FullNode)
* When shielding, Quiver will not suppport sending from a transparent address.
* You must use arrow-cli z_shieldcoinbase "armytransparentaddress" "as1myshieldedaddress" (obviously use real addresses and not these fake ones though)

