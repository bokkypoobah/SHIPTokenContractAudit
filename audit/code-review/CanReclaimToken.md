# CanReclaimToken

Source file [../../POC/contracts/token-contract-v5/CanReclaimToken.sol](../../POC/contracts/token-contract-v5/CanReclaimToken.sol).

<br />

<hr />

```javascript
// BK Ok
pragma solidity ^0.4.18;

// BK Next 3 Ok
import "./Ownable.sol";
import "./ERC20Basic.sol";
import "./SafeERC20.sol";


/**
 * @title Contracts that should be able to recover tokens
 * @author SylTi
 * @dev This allow a contract to recover any ERC20 token received in a contract by transferring the balance to the contract owner.
 * This will prevent any accidental loss of tokens.
 */
 //https://github.com/OpenZeppelin/zeppelin-solidity/blob/master/contracts/ownership/CanReclaimToken.sol
// BK Ok
contract CanReclaimToken is Ownable {
  // BK Ok
  using SafeERC20 for ERC20Basic;

  /**
   * @dev Reclaim all ERC20Basic compatible tokens
   * @param token ERC20Basic The address of the token contract
   */
  // BK Ok - Only owner can execute
  function reclaimToken(ERC20Basic token) external onlyOwner {
    // BK Ok
    uint256 balance = token.balanceOf(this);
    // BK Ok
    token.safeTransfer(owner, balance);
  }

}
```