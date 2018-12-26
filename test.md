### CPU Miner

#### Linux
These instructions assume familiarity with the command line and some linux competence.
Follow these steps:

0. You will need a receiving address for the Merge you help to mine. 
If you don't already have one you can generate a new address by:
```
merge-cli getnewaddress
```

1. You need to choose a pool to mine with. There are details of suitable pools in the merge-pool channel in Discord. 
The pools generally provide the essential parameters you will need for the miner. Some tweaking of the values might be necessary.


2. Download the CPU Miner: 
```
wget TODO-provide-compiled-file -O cpuminer
```
If there is no precompiled binary, or it is incompatible with your machine, you will need to compile it yourself:
```
git clone https://github.com/ProjectMerge/cpuminer-merge.git
cd cpuminer-merge
./autogen.sh
./configure
make
```
If you want the miner to be generally available on your machine then:
```
sudo make install
```

3. Run the CPU Miner:
Either from the cpuminer-merge directory by:
```
./cpuminer -a argon2m -o <value for your chosen pool> -u <receiving address from step 0> <any other parms recommended by your chosen pool> <any other parms>
```
or if installed system-wide or any other location in your path:
```
cpuminer -a argon2m -o <value for your chosen pool> -u <receiving address from step 0> <any other parms recommended by your chosen pool> <any other parms>
```
For example:
```
./cpuminer -a argon2m -o stratum+tcp://stratum.icemining.ca:4240 -u MTqTm4KQq9dbxrtLgpzpxDLZnbR18nHKsp -p c=MERGE
```
which uses values for the icemining pool. This isn't a recommendation, just a known working example. 
Be **VERY** careful to use the correct receiving address. If you get it wrong the rewards will still be sent there 
and you'll never see them.


