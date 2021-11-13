<script lang="ts">
	import { svelteWeb3 } from '@chiuzon/svelteweb3'
    import { InjectedConnector } from '@web3-react/injected-connector'

    import {ethers} from 'ethers'

    const { activate, error, account } = svelteWeb3()
    
    const injectedConnector = new InjectedConnector({
        //You can specify what chains you want to support
        supportedChainIds: [3]
    })

    const onConnectButton = async () => {
        await activate(injectedConnector, async (e) => {
            //You can ask here the user if he wanna switch networks or show a popup modal
            console.error(e)
        })
    }
</script>

<h1>Hello</h1>

<div class="connect-box">
    {$error ?? 'Please use Ropsten Network'}
    { $account && ethers.utils.getAddress($account)}
    <button on:click={onConnectButton}>
        Connect
    </button>
</div>

<style>
    .connect-box {
        display: flex;
        flex-direction: column;
    }
</style>