## Integer Overflow

We are able to specify the size of integers we use for variables - e.g uint256, uint64, int8, int128.

The number indicates the number of bits long the number can be. We can calculate the max number it can hold by using $2^{num}$ - 1$. For example, uint8 can hold up to 255, uint256 can hold up to 2^256 - 1 which is a very very large number!

If we were using a uint8 variable and we had the number `255` stored in it and it was `unchecked`, or existed in version of solidity prior to Version ^0.8.0, and we did a simple `+1` then the unit8 variable would become `0`

Version ^0.8.0 and later of solidity will simply revert if the value or calculation will break the restricted size specified.

### Integer Overflow Mitigation

For versions of solidity prior to ^0.8.0, we can use the `SafeMath` library by Open Zeppelin which has checks in place to prevent integer overflow and underflow issues.

Use newer version of solidity, upwards of ^0.8.0 which nativeyl has checks for overflowsz and underflows and will cause a revert if an overflow or underflow occurs.

If using a smaller restricted number of bits, size - increase the the number of bits! instead of uint64 use uint256.