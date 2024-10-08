# README.md

### Name: Yichun Zhang

### netID: [yz942]

### Design Implementation

For this project, I implemented a register file that supports read and write operations on 32 registers, each 32 bits wide. The design includes several core components:
- **dffe_ref**: A D flip-flop with enable and clear functionality, used to build the 32-bit registers.
- **Register32**: A 32-bit register built using instances of `dffe_ref` to store data values.
- **regfile**: A register file module containing 32 registers, allowing reading and writing of data to/from specified registers.

The register file supports both read and write operations with one-hot write enable signals and decoder logic for address matching.

### Module Functionalities

1. **dffe_ref**: Implements a D flip-flop with enable and clear signals. The output `q` is updated based on the clock, enable, and clear signals. This is used as the building block for the 32-bit registers.

2. **Register32**: A 32-bit register built using `dffe_ref` instances for each bit. It stores a 32-bit value and updates based on the clock, write enable, and reset signals.

3. **regfile**: Implements a register file containing 32 registers, each 32 bits wide. It supports reading two registers and writing to one register in a single clock cycle. The write enable signals are generated using decoder logic, and read data is multiplexed from the registers based on the specified read addresses.

### Bugs or Issues

- **Potential Timing Issue in Register File**: There might be a timing issue with the `regfile` when accessing registers due to propagation delays in the decoder logic, which could cause incorrect data to be read or written.
- **Complexity in Read Data Multiplexing**: The read data multiplexing logic for `data_readRegA` and `data_readRegB` involves multiple levels of OR gates, which could lead to increased delay and affect the overall performance of the register file.

