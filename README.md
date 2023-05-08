Download Link: https://assignmentchef.com/product/solved-ve270-assignment-6-keypad-reader
<br>
To design a Finite State Machine that reads the keys from a 4-by-4 keypad and displays the corresponding hexadecimal value on an SSD.

2. Background

Keypad readers are used to interpret data entered from keypads for digital devices such as phones, calculators, digital lock, etc. A keypad reader decodes a pressed key and outputs the corresponding binary code. Figure 1 shows the connection between a hexadecimal keypad and the keypad reader circuit.

When a button is pressed, it connects a row and a column at the location of the button. By providing a 1 to a column of the keypad, a 1 will be received from the connected row. In other words, the pressed key creates a loop for the signal 1 to travel from the keypad reader, through the loop created by the pressed key, and back to the keypad reader.

<strong>Figure 1. Keypad Reader </strong>




The keypad reader must be able to fire a column line to detect the location of a pressed button. A keypad reader detects a pressed key in three steps:

<ul>

 <li>Detects whether a key is pressed;</li>

 <li>Identifies which key is pressed;</li>

 <li>Generates the corresponding 4-bit hexadecimal code for the pressed key.</li>

</ul>

Step (1) can be achieved by outputting “1111” on the <em>col</em> output, so that one of the <em>row</em> inputs will be asserted whenever there is a key pressed. An OR logic of all the <em>row</em> inputs (<em>OR_row</em>) will be used to indicate whether any row is high. If the keypad reader detects a high on the <em>OR_row</em> output, it performs step (2) in which the <em>col </em>outputs will be turned on sequentially. This will tell which row and column are connected. Thus, the pressed key can be located. Step (3) will be done by looking it up in Table 1.

<strong>Table 1. Keypad code for the Hex keypad </strong>

<table width="0">

 <tbody>

  <tr>

   <td width="40"><strong>Key </strong></td>

   <td width="79"><strong>row (3 : 0) </strong></td>

   <td width="73"><strong>col (3 : 0) </strong></td>

   <td width="83"><strong>code (3 : 0) </strong></td>

  </tr>

  <tr>

   <td width="40">0</td>

   <td width="79">0001</td>

   <td width="73">0001</td>

   <td width="83">0000</td>

  </tr>

  <tr>

   <td width="40">1</td>

   <td width="79">0001</td>

   <td width="73">0010</td>

   <td width="83">0001</td>

  </tr>

  <tr>

   <td width="40">2</td>

   <td width="79">0001</td>

   <td width="73">0100</td>

   <td width="83">0010</td>

  </tr>

  <tr>

   <td width="40">3</td>

   <td width="79">0001</td>

   <td width="73">1000</td>

   <td width="83">0011</td>

  </tr>

  <tr>

   <td width="40">4</td>

   <td width="79">0010</td>

   <td width="73">0001</td>

   <td width="83">0100</td>

  </tr>

  <tr>

   <td width="40">5</td>

   <td width="79">0010</td>

   <td width="73">0010</td>

   <td width="83">0101</td>

  </tr>

  <tr>

   <td width="40">6</td>

   <td width="79">0010</td>

   <td width="73">0100</td>

   <td width="83">0110</td>

  </tr>

  <tr>

   <td width="40">7</td>

   <td width="79">0010</td>

   <td width="73">1000</td>

   <td width="83">0111</td>

  </tr>

  <tr>

   <td width="40">8</td>

   <td width="79">0100</td>

   <td width="73">0001</td>

   <td width="83">1000</td>

  </tr>

  <tr>

   <td width="40">9</td>

   <td width="79">0100</td>

   <td width="73">0010</td>

   <td width="83">1001</td>

  </tr>

  <tr>

   <td width="40">A</td>

   <td width="79">0100</td>

   <td width="73">0100</td>

   <td width="83">1010</td>

  </tr>

  <tr>

   <td width="40">B</td>

   <td width="79">0100</td>

   <td width="73">1000</td>

   <td width="83">1011</td>

  </tr>

  <tr>

   <td width="40">C</td>

   <td width="79">1000</td>

   <td width="73">0001</td>

   <td width="83">1100</td>

  </tr>

  <tr>

   <td width="40">D</td>

   <td width="79">1000</td>

   <td width="73">0010</td>

   <td width="83">1101</td>

  </tr>

  <tr>

   <td width="40">E</td>

   <td width="79">1000</td>

   <td width="73">0100</td>

   <td width="83">1110</td>

  </tr>

  <tr>

   <td width="40">F</td>

   <td width="79">1000</td>

   <td width="73">1000</td>

   <td width="83">1111</td>

  </tr>

 </tbody>

</table>




This keypad reader can be designed as a Finite State Machine. The key detecting algorithm is captured in Figure 2. The machine begins in State0, with all of the <em>col</em> outputs asserted, until one of the <em>row</em> inputs is asserted. From State1 to State4, only one of the <em>col</em> outputs is asserted. If one of the <em>row</em> inputs is also asserted, the pressed key is located. An output code can be determined by the combination of <em>col</em> outputs and <em>row</em> inputs. The FSM then moves to State5 where it outputs the <em>code</em> with all the <em>col</em> outputs asserted until the <em>OR_row</em> is de-asserted which indicates the key is released.




<strong>Figure 2. State diagram of the keypad reader </strong>

<strong>Note: use a 1 Hz clock to trigger the state machine, and use LEDs on the board to display the current state of the FSM. </strong>

<strong> </strong>

<h2>3. Verilog Coding</h2>




Write a Verilog module for the Kaypad Reader as an FSM following the state diagram shown in Figure 2. The FSM should have an asynchronous reset. Connect the SSD Driver developed in Lab 3 to display the interpreted hexadecimal value.




<h2>4. Simulation, Synthesis, and FPGA Implementation</h2>




Simulate the top-level integrated circuit using HDL Bencher. Synthesize and implement your design on the Basys 3 FPGA board.