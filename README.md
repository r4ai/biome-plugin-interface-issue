# biome-plugin-interface

## Steps to reproduce the issue.

1. Install dependencies.

   ```shell
   $ bun install
   ```

2. Check that it matches the interface when you run with grit cli.

   ```shell
   $ bun grit apply interface
   Log in ./src/interface.ts: found interface

   - Range: 1:11 - 1:15
   - Source:
   Zero
   - Syntax tree:
   (identifier)
   ./src/interface.ts
       1  interface Zero {}
       3  interface Single {
       4    f1: string
       5  }
       7  interface Multi {
       8    id: number
       9    name: string
       10    email: string
       11  }

   Processed 1 files and found 3 matches
   ```

3. Check that it doesn't match the interface when you run it with biome.

   ```
   $ bun biome check ./src
   src/interface.ts:1:6 lint/correctness/noUnusedVariables ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

   ⚠ This type alias Zero is unused.

   > 1 │ type Zero = {};
       │      ^^^^
       2 │
       3 │ interface Single {

   ℹ Unused variables are often the result of an incomplete refactoring, typos, or other sources of bugs.


   src/interface.ts:1:13 lint/complexity/noBannedTypes ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

   ⚠ Don't use '{}' as a type.

   > 1 │ type Zero = {};
       │             ^^
       2 │
       3 │ interface Single {

   ℹ Prefer explicitly define the object shape. '{}' means "any non-nullable value".


   src/interface.ts:3:11 lint/correctness/noUnusedVariables ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

   ⚠ This interface Single is unused.

       1 │ type Zero = {};
       2 │
   > 3 │ interface Single {
       │           ^^^^^^
       4 │         f1: string;
       5 │ }

   ℹ Unused variables are often the result of an incomplete refactoring, typos, or other sources of bugs.


   src/interface.ts:7:11 lint/correctness/noUnusedVariables ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

   ⚠ This interface Multi is unused.

       5 │ }
       6 │
   > 7 │ interface Multi {
       │           ^^^^^
       8 │         id: number;
       9 │         name: string;

   ℹ Unused variables are often the result of an incomplete refactoring, typos, or other sources of bugs.


   Checked 1 file in 2ms. No fixes applied.
   Found 4 warnings.
   ```
