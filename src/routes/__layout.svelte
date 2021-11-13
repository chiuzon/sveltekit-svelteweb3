<script lang="ts">
    import Web3Wrapper from '@chiuzon/svelteweb3/Web3Wrapper.svelte'
    import { ethers } from 'ethers'

    const fetchLibrary = (provider: any) => {
        const _provider = new ethers.providers.Web3Provider(provider)
        _provider.pollingInterval = 1000
        return _provider
    }
</script>


<Web3Wrapper fetchLibrary={fetchLibrary}>
    <slot />
</Web3Wrapper>