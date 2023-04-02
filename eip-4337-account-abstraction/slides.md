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

# ERC-4337: Account Abstraction

Topic 1 Proposal Exploration

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<div class="abs-br m-6 flex gap-2">
  Mark Tang
</div>

<!--
The last comment block of each slide will be treated as slide notes. It will be visible and editable in Presenter Mode along with the slide. [Read more in the docs](https://sli.dev/guide/syntax.html#notes)
-->

---
transition: fade-out
---

# Basic Concepts

- **EOA(Externally-Owned Account)** - Cryptography(private -> public -> Keccak256Hash -> 20bytes)
- **CA(Contract Account)**
- **Smart Contract Wallet** - EOA + CA

<div class="abs-br m-6 flex gap-2">
  Mark Tang
</div>
<!--
You can have `style` tag in markdown to override the style for the current page.
Learn more: https://sli.dev/guide/syntax#embedded-styles
-->

<!--
Here is another comment.
-->


---
transition: fade-out
---

# What is Account Abstraction?

Account abstraction is an upgrade that makes smart contract wallets natively supported on Ethereum. Those smart contract wallets unlock many benefits for the user, including:

- define your own flexible security rules
- recover your account if you lose the keys
- share your account security across trusted devices or individuals
- pay someone else's gas, or have someone else pay yours
- batch transactions together (e.g. approve and execute a swap in one go)
- more opportunities for dapps and wallet developers to innovate on user experiences


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

# History

- **EIP-101(November 15th, 2015)** - Serenity Currency and Crypto Abstraction
- **EIP-86(February 10th, 2017)** - Abstraction of transaction origin and signature
- **EIP-859(January 30th, 2018)** - Account abstraction on Mainnet
- **EIP-2938(September 4th, 2020)** - Account Abstraction
- **ERC-4337(September 29th, 2021)** - Account Abstraction Using Alt Mempool

### Special
- **EIP-3074** - AUTH and AUTHCALL opcodes

<div class="abs-br m-6 flex gap-2">
  Mark Tang
</div>




---
transition: slide-up
---

# Why do we need contract wallets?

- **Security** - Loss of EOA mnemonic phrase or private key string can result in the loss of a huge amount of assets that can never be recovered.
- **experience** - Improving the application experience of abstract accounts: scenario customization, optional algorithms, and manageability


|     |     |
| --- | --- |
| No Seed(No Mnemonic) | No need for mnemonic words |
| No Gas(≠No Pay) | No need to buy ETH separately to pay for Gas |
| Management | Manageable, such as daily limit/highest limit/temporary lock/whitelist |
| Recovery/Replace | Recoverable wallet/Overwritable private key |
| Programming | Similar to Ethereum's smart contracts, they can be upgraded and customized |

---

# ERC-4337 Core Concepts

- **User Operation** - A data structure sent by the user to interact with the Wallet Contract
- **Bundler** - Receive User Operation sent by the user
- **Entry Point** - In theory, it is a unique singleton contract on the entire network, responsible for interacting with Bundler and Wallet Contract
- **Wallet Contract** - Responsible for carrying out user operations

---
class: px-20
---

# Flow Diagram

<div style="background-color: #fff;">
  <img border="rounded" src="https://eips.ethereum.org/assets/eip-4337/image1.png">
</div>

---

# Existing smart contract wallets

Arbitrum, Optimism

- **Argent** - zkSync, StarkNet...
- **Unipass**
- **Gnosis Safe**
- **Wallet3**
- **Safe**


---

# Benefits and Weaknesses

### Benefits
- **No Seed**
- **Social Recovery**
- **Programming**
- **Gasless**
- **No need to run a Relayer separately**

### Weaknesses
- **Every chain needs to deploy a contract.**
- **Gas fee increase (multiple transactions bundled into one operation, so the actual gas used may be less)**

---

# Currentlly

- **ETH Denver**
- **Infrastructure**
  - ERC-4337 Wallet(building)
  - Bundler(building)
  - Entry Point(almost finished)
  - Client SDK(building)
  - ...
- **DevConnect Hackathon**
  - Session Key
  - Dead Man's Switch
  - Multi-signature system for gaming guilds

---

# Product Form and Value Capture

<img style="height:400px;" src="https://s1.locimg.com/2023/03/28/13ac255aaaf56.jpg">

---

# Next Topic

- **User Operation Structure**
- **Bundler**
- **Entry Point**
- **Wallet Contract**

### Future
- **Paymaster**
- **Social Recovery**
- **Implement AA Wallet**
- **MetaMask Snaps**

---
layout: center
class: text-center
---

# Thanks

Mark Tang's · [GitHub](https://github.com/MarkTangCd) · [Email](mailto:MarkTangCd@hotmail.com)
