### 2025-11-17
Goals:
- Understand how a dynamic comparator works (Strong-Arm topology)
- Comparator circuit and understanding from: [arxiv.org/pdf/2209.07259](https://arxiv.org/pdf/2209.07259) 
- Create schematic for comparator and simulate
- Implement a simple SHA circuit

Achieved:
- Completed a comparator with default nmos1v and pmos1v devices (default sizes)
- Created a very simple SHA circuit (transmission gate + capacitive holding need to add source follower/buffer)

Learned:
- Getting more comfortable with Cadence workflow
- Debugging skills (initially, I forgot to connect the pmos switches)
- How a dynamic comparator works (pre charge capacitances, use the different discharge times to turn on transistors that pull-up or pull-down the output voltage (like 253 H-bridge))

Notes:
- Comparator works well in the regenerative phase but has a lot of spiky behavior (Figures show CLK(white), vout1(red), and vin1(pink) Note vin2 is 500mV)
![Clock waveform]({{ '/assets/img/projects/sar-adc/2025-11-17-clk.png' | relative_url }})




### 2025-11-15
Goals:
- Familizarize with Cadence
- Do a simple inverter simulation

Achieved:
- Simple inverter schematic + simulation
- Set next step (comparator)

Learned:
- Cadence workflow (schematic->symbol->simulation)

