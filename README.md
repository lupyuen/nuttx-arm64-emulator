# Emulate PinePhone with Unicorn Emulator

_Can we emulate Arm64 PinePhone with [Unicorn Emulator](https://www.unicorn-engine.org/)?_

Let's find out!

# Emulate Arm64 Machine Code

Here's a simple Rust program that calls Unicorn Emulator to emuate some Arm64 Machine Code...

https://github.com/lupyuen/pinephone-emulator/blob/bc5643dea66c70f57a150955a12884f695acf1a4/src/main.rs#L1-L55

The code above works OK for manipulating Arm64 Registers. Let's do something more interesting: Unicorn Hooks...

# Memory Access Hooks for Arm64 Emulation

Unicorn Emulator lets us attach hooks to handle Memory Access.

Here's a Hook Function for Memory Access...

https://github.com/lupyuen/pinephone-emulator/blob/3655ac2875664376f42ad3a3ced5cbf067790782/src/main.rs#L83-L95

This is how we attach the Hook Function to the Unicorn Emulator...

https://github.com/lupyuen/pinephone-emulator/blob/3655ac2875664376f42ad3a3ced5cbf067790782/src/main.rs#L59-L74

When we run this, we'll see the Read and Write Memory Accesses made by the emulator...

```text
hook_memory: 
  mem_type=WRITE, 
  address=0x10008, 
  size=4, 
  value=0x12345678

hook_memory: 
  mem_type=READ, 
  address=0x10008, 
  size=1, 
  value=0x0
```

This will be useful when we emulate Memory-Mapped Input/Output on PinePhone.

(Like for the Allwinner A64 UART Controller)

Unicorn Emulator allows Code Execution Hooks too...

# Code Execution Hooks for Arm64 Emulation

TODO: Call Unicorn Emulator to add Code Execution Hooks

https://github.com/lupyuen/pinephone-emulator/blob/3655ac2875664376f42ad3a3ced5cbf067790782/src/main.rs#L108-L117

TODO: Add hook

https://github.com/lupyuen/pinephone-emulator/blob/3655ac2875664376f42ad3a3ced5cbf067790782/src/main.rs#L52-L57

Output:

```text
hook_code: address=0x10000, size=4
hook_code: address=0x10004, size=4
```

# Block Execution Hooks for Arm64 Emulation

TODO: Call Unicorn Emulator to add Block Execution Hooks

https://github.com/lupyuen/pinephone-emulator/blob/3655ac2875664376f42ad3a3ced5cbf067790782/src/main.rs#L97-L106

TODO: Add hook

https://github.com/lupyuen/pinephone-emulator/blob/3655ac2875664376f42ad3a3ced5cbf067790782/src/main.rs#L48-L50

Output:

```text
hook_block: address=0x10000, size=8
```

TODO: What happens when we run Apache NuttX RTOS for PinePhone?

TODO: Use Unicorn Emulation Hooks to emulate PinePhone's Allwinner A64 UART Controller

TODO: Emulate Apache NuttX NSH Shell on UART Controller
