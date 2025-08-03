# RISC-V Pipelined Processor

A 5-stage pipelined implementation of the RISC-V processor in Verilog. This implementation includes hazard detection and forwarding units for handling data hazards.

## Architecture Overview

The processor implements a classic 5-stage RISC-V pipeline:
1. **Fetch Stage**: Fetches instructions from instruction memory
2. **Decode Stage**: Decodes instructions and reads registers
3. **Execute Stage**: Performs ALU operations
4. **Memory Stage**: Handles memory operations
5. **Writeback Stage**: Writes results back to registers

### Key Features
- Full 5-stage pipeline implementation
- Data hazard handling through forwarding
- Support for core RISC-V instructions
- Modular design with separate components for each stage

## Module Structure

- `Pipeline_Top.v`: Top-level module integrating all pipeline stages
- `Fetch_Cycle.v`: Instruction fetch logic
- `Decode_Cycle.v`: Instruction decode and register read
- `Execute_Cycle.v`: ALU and execution logic
- `Memory_Cycle.v`: Memory access operations
- `Writeback_Cycle.v`: Register writeback logic
- `Hazard_Unit.v`: Data hazard detection and forwarding
- Supporting modules:
  - `ALU.v`: Arithmetic Logic Unit
  - `Register_File.v`: Register bank
  - `Data_Memory.v`: Data memory
  - `Instruction_Memory.v`: Instruction memory
  - Various multiplexers and control units

## Test Setup

The testbench (`pipeline_tb.v`) provides:
- Clock generation
- Reset sequence
- Basic test infrastructure
- VCD dump for waveform viewing

## Getting Started

### Prerequisites
- Icarus Verilog (iverilog)
- GTKWave (for viewing waveforms)

### Running the Simulation
1. Compile the design:
```bash
iverilog pipeline_tb.v -o pipeline_tb.out
```

2. Run the simulation:
```bash
vvp pipeline_tb.out
```

3. View waveforms:
```bash
gtkwave dump.vcd
```

## Memory Configuration

Instructions can be loaded into instruction memory using the hex file `memfile.hex`. The format follows the RISC-V instruction encoding.

## Implementation Details

### Hazard Handling
- Data hazards handled through forwarding
- Forwarding unit monitors pipeline registers
- Supports forwarding from Memory and Writeback stages

### Control Signals
- `RegWrite`: Register write enable
- `MemWrite`: Memory write enable
- `ALUSrc`: ALU source selection
- `ResultSrc`: Result source selection
- `Branch`: Branch instruction indicator

## License

This project is open source and available under the MIT License.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Author

- Sarthak Sharma
