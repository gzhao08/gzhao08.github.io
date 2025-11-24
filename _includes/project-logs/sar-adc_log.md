### 2025-11-19
Goals:
- test inverted comparator

Notes:
- comparator works great for lower voltages and actually has less settling time when compared to the original (as the cross-coupled latches are now nmos and electrons have higher mobility than holes)



### 2025-11-19
Goals:
- think of solutions to fixing comparator for lower voltages

Notes:
- flipping the comparator and creating it with nmos switches and pmos inputs will work well for low voltage (might not work well at higher though)



### 2025-11-18
Goals:
- Comparator testing

Notes:
- Learn about cdac
- Compared 499.5mV, 499.95mV, 500.5mV, and 500.05mV against 500mV and was able to successfully compare (settling time ~ 4ns)
- comparator works well for higher voltages (>5V) but works worse and worse. this makes sense as eventially the input voltages are not enough to bias the nmos into strong inversion






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

| ![img1]({{ '/assets/img/projects/sar-adc/2025-11-17-clk.png' | relative_url }}) | ![img2]({{ '/assets/img/projects/sar-adc/2025-11-17-vin.png' | relative_url }}) | ![img3]({{ '/assets/img/projects/sar-adc/2025-11-17-vout.png' | relative_url }}) |

- SHA Simulation:  

![SHA Sim]({{ '/assets/img/projects/sar-adc/2025-11-17-sha.png' | relative_url }})










### 2025-11-15
Goals:
- Familizarize with Cadence
- Do a simple inverter simulation

Achieved:
- Simple inverter schematic + simulation
- Set next step (comparator)

Learned:
- Cadence workflow (schematic->symbol->simulation)

