### 2025-09-12
Goals:
- Get a general understanding of gameboy architecture 

Achieved:
- Looked through [gbdev.io/pandocs/CPU_Instruction_Set.html](https://gbdev.io/pandocs/CPU_Instruction_Set.html) for instruction decoding

Notes:
- The instruction set looks like

<img src='\..\..\assets\img\projects\gameboy-clone\instruction_set.png' width="600">
- I should try to implement a block-2 decoder which seems to be the simplest. Block 2 corresponds to arithmetic operations between the A register and another register (does not include imm8)

