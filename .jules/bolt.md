## 2023-11-20 - Endianness checking in LZ4 macro optimization
**Learning:** `LZ4_isLittleEndian` was a function causing runtime overhead in tight loops. I checked for standard macros like `__BYTE_ORDER__ == __ORDER_LITTLE_ENDIAN__` and used them to conditionally define `LZ4_isLittleEndian` to `1` at compile time, eliminating the function call overhead.
**Action:** Use compiler-defined macros to inline endianness checks for zero runtime cost, and conditionally fallback to runtime checks if the compiler definitions are missing.
