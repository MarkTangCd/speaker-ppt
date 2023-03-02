---
# try also 'default' to start simple
theme: seriph
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/collections/94734566/slidev
background: https://source.unsplash.com/collection/94734566/1920x1080
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: false
# some information about the slides, markdown enabled
info: |
  ## Slidev Starter Template
  Presentation slides for developers.

  Learn more at [Sli.dev](https://sli.dev)
# persist drawings in exports and build
drawings:
  persist: false
# page transition
transition: slide-left
# use UnoCSS
css: unocss
---
<!-- ./components/MetamaskLogo.vue -->
<MetamaskLogo />

# MetaMask Snaps

Plugins in Plugins

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Getting Started <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

---
transition: fade-out
---

# What is MetaMask Snaps?

Snaps is a system that allows anyone to safely extend the capabilities of MetaMask.(Plugins In Plugins)

- 📝 **Extensibility** - It will give MetaMask more possibilities
- 👷‍♂️ **Safety** -  EIP-2255 wallet permissions specification and a “fully virtualizable” execution environment
- 🎨 **Custom UI** - Display a custom confirmation screen in MetaMask
- 📢 **Notice** - Notify users in MetaMask
- 🗳 **Store** - Store and manage data on users' device
- 💰 **Assets** - Control non-EVM accounts and assets in MetaMask
- 👀 **Insights** - Populate MetaMask's pre-transaction window with custom transaction insights
- ⏰ **Cron** - Schedule actions with cron jobs

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<style>
h1 {
  background-color: #2B90B6;
  background-image: linear-gradient(45deg, #4EC5D4 10%, #146b8c 20%);
  background-size: 100%;
  -webkit-background-clip: text;
  -moz-background-clip: text;
  -webkit-text-fill-color: transparent;
  -moz-text-fill-color: transparent;
}
</style>

<!--
Here is another comment.
-->

---
transition: slide-up
---

# Extend the functionality of MetaMask

<br />
<br />
<p style="font-size:18px">
  A snap is a program that we run in an isolated environment that can customize the wallet experience.
  <br />
  <br />
  For example, a snap can add new APIs to MetaMask, add support for different blockchain protocols, or modify existing functionality using internal APIs. Snaps is a new way to create web3 end user experiences, by modifying MetaMask in ways that were impossible before.
</p>

## Focus
- add new APIs to MetaMask
- add support for different blockchain protocols
- modify existing functionality

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>


---
transition: slide-up
---

# Execution environment

<br />
<p style="font-size:18px">
  Snaps are untrusted JavaScript programs that execute safely inside the MetaMask application.
  To isolate snaps from the rest of the application and to provide a "Fully virtualizable" execution environment,
  MetaMask uses Secure ECMAScript(SES), a subset of JavaScript developed by Agoric.
</p>

## Note
- Agoric is a JavaScript Smart Contracts Platform built on Cosmos.
- At the moment, snaps must be distributed as npm packages on the official npm registry, but different distribution mechanisms will be supported in the future.

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

---
layout: full
---

# MetaMask Flask

Download URL: [https://metamask.io/flask/](https://metamask.io/flask/)

<div class="flex w-full">
  <img class="w-full h-sm" src="https://images.ctfassets.net/9sy2a0egs6zh/1E2XReKl9De03Pmei4yFLs/67e2387c0f100b7ca1e7269986f93054/Flask_Hero_Dark.png?w=1920&q=100&fm=webp" />
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>


---
layout: full
---

# Detecting Version

When developing a website/Dapp that depends on Snaps,it's important to know whether MetaMask Flask is installed.

```ts {all|1|7-9|11|all}
import detectEthereumProvider from '@metamask/detect-provider';

// This resolves to the value of window.ethereum or null
const provider = await detectEthereumProvider();

// web3_clientVersion returns the installed MetaMask version as a string
const isFlask = (
  await provider?.request({ method: 'web3_clientVersion' })
)?.includes('flask');

if (provider && isFlask) {
  console.log('MetaMask Flask successfully detected!');

  // Now you can use Snaps!
} else {
  console.error('Please install MetaMask Flask!', error);
}
```

<arrow v-click="3" x1="400" y1="420" x2="260" y2="350" color="#564" width="3" arrowSize="1" />

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

<style>
.footnotes-sep {
  @apply mt-20 opacity-10;
}
.footnotes {
  @apply text-sm opacity-75;
}
.footnote-backref {
  display: none;
}
</style>

---

# The way to install snap

<div grid="~ cols-2 gap-4">
<div>

Install a snap to MetaMask.

```ts {all|10}
/**
 * @param snapId - The ID of the snap.
 * @param params - The params to pass with the snap to connect.
 */
export const installSnap = async (
  snapId: string = defaultSnapOrigin,
  params: Record<'version' | string, unknown> = {},
) => {
  await window.ethereum.request({
    method: 'wallet_requestSnaps',
    params: {
      [snapId]: params,
    },
  });
};
```
</div>
<div>

<img style="width:260px;height:420px" src="https://i.328888.xyz/2023/03/01/6Apdy.jpeg" alt="6Apdy.jpeg" border="0" />

</div>
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>


---
layout: image-right
image: https://source.unsplash.com/collection/94734566/1920x1080
---

# Examples

Here are some examples, including an official example, an example written by me, and a third-party example.

- The official example
- Solana Snap (the example written by me)
- The third-party example (the example written by UniPass Wallet)

> Note: UniPass Wallet is a smart contract wallet solution that supports on-chain Email social recovery.

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

---
---

# Twitter

Some news about MetaMask Snaps.

<div class="flex w-full">
  <div>
    <img class="w-full h-xs" src="/assets/twitter2.png" />
  </div>
  <div>
    <img class="w-full h-xs" src="/assets/twitter3.png" />
  </div>
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>


---
---

# ETH Denver 2023

<div class="flex w-full">
  <img class="w-full h-sm" src="/assets/twitter4.png" />
</div>

[Load More](https://www.ethdenver.com/)

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

---
---

# ETH Denver 2023

<div class="flex w-full">
  <img class="w-8\/12  h-sm" src="/assets/twitter5.png" />
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

---
---

# ETH Denver 2023

<div class="flex w-full">
  <img class="w-8\/12 h-1\.5" src="/assets/twitter6.png" />
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>


---
---

# ETH Denver 2023

<div class="flex w-full">
  <img class="w-8\/12 h-1\.5" src="/assets/twitter7.png" />
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>

---
---

# ETH Denver 2023

<div class="flex w-full">
  <img class="w-8\/12 h-1\.5" src="/assets/twitter8.png" />
</div>

<div class="abs-br m-6 flex gap-2">
  Author: Mark Tang
</div>


---
layout: center
class: text-center
---

# Thanks

Mark Tang's · [GitHub](https://github.com/MarkTangCd) · [Email](mailto:MarkTangCd@hotmail.com)
