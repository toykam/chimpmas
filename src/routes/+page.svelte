<script>
    import { onMount } from 'svelte';
    import { ethers } from 'ethers';
  
    let provider;
    let signer;
    let walletAddress = "";
  
    async function connectWallet() {
      if (window.ethereum) {
        provider = new ethers.BrowserProvider(window.ethereum);
        await provider.send("eth_requestAccounts", []);
        signer = await provider.getSigner();
        walletAddress = await (signer).getAddress();
      } else {
        alert("Please install MetaMask!");
      }
    }
  
    function participateInDraw() {
        alert("Christmas NFT draw participation functionality goes here!");
        // logic to call the smart contract function to participate in the draw
        
    }
  </script>
  
  <div class="flex flex-col items-center min-h-screen bg-gradient-to-br from-green-500 to-red-400 text-white">
    <h1 class="text-4xl font-bold mt-10">🎄 Win Christmas Gifts as NFTs! 🎁</h1>
    <button
      class="mt-5 px-6 py-3 bg-yellow-500 rounded shadow-md hover:bg-yellow-400"
      on:click={connectWallet}
    >
      {walletAddress ? "Connected: " + walletAddress : "Connect Wallet"}
    </button>
    {#if walletAddress}
      <button
        class="mt-5 px-6 py-3 bg-blue-500 rounded shadow-md hover:bg-blue-400"
        on:click={participateInDraw}
      >
        Participate in Gift Draw
      </button>
    {/if}
  </div>
  