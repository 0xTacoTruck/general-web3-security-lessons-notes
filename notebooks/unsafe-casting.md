## Unsafe Casting from Type to Type

When we cast from different types, theres a risk of causing an unrealiable number due to how the type conversion is carried out and the difference in size of number variables (in bits).

For example, the max number of uint256 is very very large, while the number that can be stored in uint64 is significantally smaller. When we type convert from a bigger number to a smaller number, we can cause: wrapping around of the number like an overflow, significant precision loss, all kinds of issues. This is becuase it is trying to use the last X number of bits of the larger number when trying to convert it.

```bash
        -->> type(uint64).max
        Type: uint64
        -- Hex: 0xffffffffffffffff
        -- Hex (full word): 0x000000000000000000000000000000000000000000000000ffffffffffffffff
        --- Decimal: 18446744073709551615
        -->> uint64 my64Uint = type(uint64).max
        -->> my64Uint
        Type: uint64
        -- Hex: 0xffffffffffffffff
        -- Hex (full word): 0x000000000000000000000000000000000000000000000000ffffffffffffffff
        --- Decimal: 18446744073709551615
        -->> uint256 twentyEth = 20e18
        -->> twentyEth
        Type: uint256
        -- Hex: 0x000000000000000000000000000000000000000000000001158e460913d00000
        -- Hex (full word): 0x000000000000000000000000000000000000000000000001158e460913d00000
        --- Decimal: 20000000000000000000
        -->> my64Uint = uint64(twentyEth)
        Type: uint64
        -- Hex: 0x158e460913d00000
        -- Hex (full word): 0x000000000000000000000000000000000000000000000000158e460913d00000
@=>     --- Decimal: 1553255926290448384
        
```