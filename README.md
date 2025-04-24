# ok-withdrawal

<div align="center">
  <a href="https://github.com/opstack-kit">
    <img src="https://avatars.githubusercontent.com/u/176029081?s=200&v=4" title="Logo" alt="Logo" width="200" height="200"/>
  </a>
  <br><br>
  <a href="https://opstack-kit.pages.dev"><img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=800&size=30&pause=1000&center=true&repeat=false&random=false&width=435&lines&color=F70000&width=435&lines=Opstack+Kit" alt="Typing SVG" />
  </a>

</div>
<p align="center">
  Bridging hooks for OP Stack Chains
    <br><br>
  <a href="https://www.npmjs.com/package/opstack-kit">
    <picture>
      <img src="https://img.shields.io/npm/v/opstack-kit" alt="Npm Badge">
    </picture>
  </a>
</p>

<div align="center" style="display: flex; justify-content: center; flex-wrap: wrap; gap: 10px;">
  <a href="https://github.com/opstack-kit/opstack-kit/stargazers">
    <img src="https://img.shields.io/github/stars/opstack-kit" alt="Stars Badge" />
  </a>
  <a href="https://github.com/opstack-kit/opstack-kit/forks"><img src="https://img.shields.io/github/forks/opstack-kit/opstack-kit" alt="Forks Badge"/>
  </a>
  <a href="https://github.com/opstack-kit/opstack-kit/pulls">
    <img src="https://img.shields.io/github/issues-pr/opstack-kit/opstack-kit" alt="Pull Requests Badge" />
  </a>
  <a href="https://github.com/opstack-kit/opstack-kit/issues">
    <img src="https://img.shields.io/github/issues/opstack-kit/opstack-kit" alt="Issues Badge" />
  </a>
  <a href="https://github.com/opstack-kit/opstack-kit/graphs/contributors">
    <img alt="GitHub contributors" src="https://img.shields.io/github/contributors/opstack-kit/opstack-kit?color=2b9348">
  </a>
</div>

<br/>

<div align="center">
Easily Prove &amp; Finalize with Opstack-Kit (ok) just pass in the &lt;WithdrawalTxHashL2> to decode the args and reduce complexity.
</div>

## Installation

Recommend: use [Nodejs v20+](https://nodejs.org/en/download/prebuilt-installer/current) and add `-g` is a **global** package installation. ([guide](https://docs.npmjs.com/cli/v9/commands/npm-install#global-installation))

```bash [npm]
npm i -g opstack-kit
```

<br/>

> [!WARNING]  
> Security and transparency are top priorities.  
> The `--privateKey` must start with `0x-key`, and dependencies use [Viem](https://viem.sh/docs/accounts/local/privateKeyToAccount#privatekeytoaccount) for secure handling.  
> 
> You can review the code for more details:  
> [View source](https://github.com/opstack-kit/opstack-kit/blob/main/src/cli/commands/prove.ts#L5), [npm package](https://www.npmjs.com/package/opstack-kit?activeTab=code)  
> 
> *If you're just testing, we recommend using a freshly generated wallet to stay safe.*

## proveWithdrawalTransaction (on L1)
Prove withdrawal using transaction hash, "OptimismPortal.[proveWithdrawalTransaction](https://github.com/ethereum-optimism/optimism/blob/op-contracts/v2.0.0-beta.3/packages/contracts-bedrock/src/L1/OptimismPortal.sol#L243C1-L322C6)" `L2StandardBridge` address. ([Read more](https://opstack-kit.pages.dev/docs/cli#prove-provewithdrawal))
> [!NOTE]  
> For **Non-Fault proofs**:  
> `disputeGameFactory = 0x_l2OutputOracle`  
>  
> For **Fault proofs**:  
> `l2OutputOracle = 0x_disputeGameFactory`  
>  
> Also, the `--privateKey` must start with `0x-key`.

```
ok prove <WithdrawalTxHashL2> \
--privateKey <0x-key> \
--chainIdL1 <id> \
--rpcUrlL1 <url> \
--chainIdL2 <id> \
--rpcUrlL2 <url> \
--portal <address> \
--l2OutputOracle <address> \
--disputeGameFactory <address> \
--scanL1Url <url>
```

---

## finalizeWithdrawalTransaction (on L1)
Finalize withdrawal using transaction hash after proving, "OptimismPortal.[finalizeWithdrawalTransaction](https://github.com/ethereum-optimism/optimism/blob/op-contracts/v2.0.0-beta.3/packages/contracts-bedrock/src/L1/OptimismPortal.sol#L324C1-L444C6)" address. ([Read more](https://opstack-kit.pages.dev/docs/cli#finalize-finalizewithdrawal))
> [!NOTE]  
> For **Non-Fault proofs**:  
> `disputeGameFactory = 0x_l2OutputOracle`  
>  
> For **Fault proofs**:  
> `l2OutputOracle = 0x_disputeGameFactory`  
>  
> Also, the `--privateKey` must start with `0x-key`.

```
ok prove <WithdrawalTxHashL2> \
--privateKey <0x-key> \
--chainIdL1 <id> \
--rpcUrlL1 <url> \
--chainIdL2 <id> \
--rpcUrlL2 <url> \
--portal <address> \
--scanL1Url <url>
```
