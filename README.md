# Flint Task

This project is a starting point for a Flutter application.
It aims to use the web3 package to for the API call.
Ref: https://pub.dev/packages/web3dart

# Connecting to RPC server:

var httpClient = Client();
var ethClient = Web3Client(apiUrl, httpClient);

var credentials = EthPrivateKey.fromHex("0x...");
var address = credentials.address;

// You can now call rpc methods. This one will query the amount of Ether you own
EtherAmount balance = ethClient.getBalance(address);
print(balance.getValueInUnit(EtherUnit.ether));

# Alternate Approach:
The approach using Flutter is not the best suited approach. I found that viem library supporting React with TypeScript is better suited for this use case.
Not having much experience with React and TypeScript I chose Flutter approach but following TypeScript code can be used after setting up uri. 

import { createPublicClient, http } from 'viem'
import { mainnet } from 'viem/chains'

export const publicClient = createPublicClient({
  chain: mainnet,
  transport: http()
})

const balance = await publicClient.getBalance({
  address: '0xA0Cf798816D4b9b9866b5330EEa46a18382f251e', 
})

const balanceAsEther = formatEther(balance) 
