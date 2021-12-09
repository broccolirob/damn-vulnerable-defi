# Solution Write-ups

## 1. Unstoppable

The goal of this first challenge is to break the contract's flash lending
capability. The `UnstoppableLender` contract takes deposits of an ERC20 token
through its `depositTokens(uint)` function. Balances are tracked by the state
variable `uint public poolBalance;`. The `flashLoan(uint)` function uses a
strict equality check here:

- [UnstoppableLender.sol L40](https://github.com/broccolirob/damn-vulnerable-defi/blob/master/contracts/unstoppable/UnstoppableLender.sol#L40)

```solidity
assert(poolBalance == balanceBefore);
```

There is no limitation, however, that token transfers to this contract must be
made through the `depositTokens(uint)` function. Anyone can forcibly send an
ERC20 to any contract they wish. So, to break this contract simply transfer a
token directly to the contract like this:

```javascript
await this.token.transfer(this.pool.address, 1)
```

Now the assertion of line 40 will fail every time, and we've achieved our goal
of DoS'ing the `UnstoppableLender` contract.

## 2. Naive receiver

## 3. Truster

## 4. Side entrance

## 5. The rewarder

## 6. Selfie

## 7. Compromised

## 8. Puppet

## 9. Puppet v2

## 10. Free rider

## 11. Backdoor

## 12. Climber
