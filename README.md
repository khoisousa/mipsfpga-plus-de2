MIPSfpga+ / mipsfpga-plus / MFP is a cleaned-up and improved variant of MIPSfpga-based system defined in MIPSfpga Getting Started package (MFGS). The new features include:

<ol>
<li>The ability to load a software program using ubiquitous $5 FTDI-based USB-to-UART connector instead of $50 Bus Blaster that is difficult to get in some places of the globe</li>
<li>The ability to change the clock frequency on the fly from 50 or 25 MHz down to 1 Hz (one cycle a second) to observe the work of CPU in real time, including cache misses and pipeline forwarding</li>
<li>An example of integration of a light sensor with SPI protocol</li>
<li>Smaller software initialization sequence that fits in 1 KB instead of 32 KB memory, which allows porting MIPSfpga to a wider selection of FPGA boards, without using external memory</li>
<li>Miscellaneous fixes like improving AHB-Lite slave to handle narrow uncached writes of sizes 1 or 2-bytes</li>
<li>Easy to use configurable SDRAM interface module</li>
<li>Altera MAX10 ADC interface module support</li>
<li>Widely used UART16550 interface module</li>
<li>External interrupt controller that is working throw MIPS microAptiv core Interrupt Interface</li>
</ol>

The hierarchy of synthesizable modules for Digilent Nexys 4 DDR with Xilinx Artix-7 FPGA:

<a href="https://cdn.rawgit.com/zhelnio/mipsfpga-plus/a36be531/documentation/edited_figures/hierarchy_nexys4_ddr_full.html"><img src="https://raw.githubusercontent.com/zhelnio/mipsfpga-plus/master/documentation/edited_figures/hierarchy_nexys4_ddr_full.png"></a>

MIPSfpga+ currently works on these FPGA boards:

<ol>
<li><a href="http://store.digilentinc.com/nexys-4-ddr-artix-7-fpga-trainer-board-recommended-for-ece-curriculum/">Digilent Nexys 4 DDR</a> board with Xilinx Artix-7 FPGA. See the Appendix A about how the board is connected with the applicable peripherals.</li>
<li><a href="http://store.digilentinc.com/nexys-4-artix-7-fpga-trainer-board-limited-time-see-nexys4-ddr/">Digilent Nexys 4</a> board with Xilinx Artix-7 FPGA (no DDR, soon to be discontinued).</li>
<li><a href="http://store.digilentinc.com/basys-3-artix-7-fpga-trainer-board-recommended-for-introductory-users/">Digilent Basys 3</a> with Xilinx Artix-7.</li>
<li><a href="http://de0-cv.terasic.com.tw">Terasic DE0-CV</a> with Altera Cyclone V. See the Appendix B about how the board is connected with the applicable peripherals.</li>
<li><a href="http://de2-115.terasic.com">Terasic DE2-115</a> with Altera Cyclone IV</li>
<li><a href="http://de0-nano.terasic.com.tw">Terasic DE0-Nano</a> board with Altera Cyclone IV FPGA.</li>
<li><a href="http://de0.terasic.com">Terasic DE0</a> with Altera Cyclone III</li>
<li><a href="http://de1.terasic.com">Terasic DE1</a> with Altera Cyclone II</li>
<li><a href="http://de2.terasic.com">Terasic DE2</a> with Altera Cyclone II</li>
<li><a href="http://de10-lite.terasic.com">Terasic DE10-Lite</a> with Altera MAX10</li>
<li><a href="http://de10-nano.terasic.com">Terasic DE10-Nano</a> with Altera Cyclone V</li>
</ol>

There are two planned ports:

<ol>
<li><a href="http://marsohod.org/plata-marsokhod3">Marsohod 3</a> board with Altera MAX10 FPGA</li>
<li><a href="http://store.digilentinc.com/arty-board-artix-7-fpga-development-board-for-makers-and-hobbyists/">Digilent Arty</a> with Xilinx Artix-7. MIPSfpga+ is likely to work on this board with no modification except adding the board wrapper (top-level Verilog and pin constraints).</li>
</ol>

The source code for MIPSfpga+ is located at <a href="http://github.com/MIPSfpga/mipsfpga-plus">http://github.com/MIPSfpga/mipsfpga-plus</a>; this code does not include any source code of MIPS microAptiv UP CPU core from MIPSfpga Getting Started package. Check `core/README` for more info.

After downloading both MIPSfpga from Imagination site and MIPSfpga+ from GitHub, the user is expected to install MIPSfpga under 64-bit Microsoft Windows (either Windows 7 or Windows 8) by placing MIPSfpga core source files to MIPSfpga+\core directory. To do this one need to copy to MIPSfpga+\core all the files from 'MIPSfpga_GSG_1.3\MIPSfpga\rtl_up' when using MIPSfpga 1.3 or from 'MIPSfpga_GSG_v2.0\MIPSfpga_GSG\rtl_up\core' in the case of using MIPSfpga 2.0. The paths inside MIPSfpga+ synthesis and simulation scripts rely on such installation.

MIPSfpga+ (as well as the original MFGS package) can be also used on a workstation with 32-bit Windows, 32-bit Linux, 64-bit Linux, with or without Windows or Linux virtual machine. It is possible to install MIPSfpga+ in different directories, and use it with a number of Verilog simulators and synthesis tools: Synopsys VCS, Cadence IES, Mentor ModelSim, Icarus Verilog with GTKWave, Xilinx ISim and Vivado, Altera Quartus II, Synopsys Synplify Pro and others. Some usage scenarios require modifying the scripts and adhering to specific versions of EDA and software development tools, for example:

<ul>
<li>In order to use MIPSfpga or MIPSfpga+ on a workstation with 32-bit Windows, it is necessary to use <a href="https://sourcery.mentor.com/GNUToolchain/subscription3537?lite=MIPS">Mentor Sourcery CodeBench Lite Edition for MIPS ELF</a> instead of Imagination Codescape MIPS SDK Essentials. This requires some minimal modifications of certain scripts (changing the program name prefixes).</li>
<li>In order to use MIPSfpga or MIPSfpga+ with Altera FPGAs on a workstation with 32-bit Windows <i>or</i> 32-Linux, it is necessary to use <a href="http://dl.altera.com/13.1/?edition=web">Altera Quartus II Web Edition version 13.1</a> instead of later versions that does not work on workstations with 32-bit operating systems.</li>
</ul> 

How to synthesize mipsfpga-plus for Terasic DE0-CV board:

<ol>
<li>Unzip MIPSfpga 2.0 Getting Started Guide to C:\MIPSfpga</li>
<li>Get mipsfpgfa-plus into C:\github\mipsfpga-plus</li>
<li>copy all the files from C:\MIPSfpga\MIPSfpga_GSG\rtl_up\core to C:\github\mipsfpga-plus\core</li>
<li>cd C:\github\mipsfpga-plus\boards\de0_cv</li>
<li>make_project.bat</li>
<li>Run Altera Quartus II</li>
<li>Open project C:\github\mipsfpga-plus\boards\de0_cv\project\de0_cv.qpf</li>
<li>Analyze/Synthesize/Place&Route/Assemble</li>
<li>Open Device / Hardware Setup / ByteBlaster / Set file / ouput_files / de0_cv.sof / Start</li>
</ol>

How to load a software example into mipsfpga-plus using BusBlaster and OpenOCD:

<pre>
cd C:\github\mipsfpga-plus\programs\00_counter
02_compile_and_link.bat
11_upload_to_the_board.bat
</pre>

How to load a software example into mipsfpga-plus using USB-to-UART-based serial loader:

<pre>
cd C:\github\mipsfpga-plus\programs\00_counter
02_compile_and_link.bat
08_generate_motorola_s_record_file.bat
09_check_which_com_port_is_used.bat
</pre>

Modify <i>10_upload_to_the_board_using_uart.bat</i>.

<pre>
10_upload_to_the_board_using_uart.bat
</pre>

Some details about scripts using: <a href="programs/README.md">programs/README.md</a>


