# pes_riscv


# Day-3 Digital Logic with TL-verilog and Maker chip

<details>
 <summary>Combination logic in TL-verilog using Makerchip</summary>

 
**Logic gates**

![Untitled20](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/2fcfc404-57ac-4c7f-a17e-fa6cd2510064)



**Combinational Circuit**

![21](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/1465b70e-5607-467e-b6bf-30f6de406f96)


**Adder**

![22](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/6f1026c3-22d0-4da9-9c2d-92e1390ecb87)


**Boolean Operators**

![23](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/63dfca31-2e8f-4ea0-af8b-91c5d305f664)



**Mux**

![24](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/be7aade1-8571-4a28-a89a-8d9b03b5f9cf)

**Maker chip**

> Go to the maker chip.com

> take a look at FPGA multiplier

> we can see the waveforms and top level module(desogn)


![Screenshot from 2023-10-16 22-02-53](https://github.com/vishnupriyapesu/pes_class_asic/assets/142419649/28acbfa8-f231-4ead-ba77-b8dbe0a7d98d)


**more examples using makerchip**

**1) Inverter**
<br />

     \TLV
         $reset = *reset;
   
         $out = ! $in1;
   
         // Assert these to end simulation (before Makerchip cycle limit).
         *passed = *cyc_cnt > 40;
         *failed = 1'b0;
         \SV
         endmodule

![Screenshot from 2023-10-16 22-40-20](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/c9f53fcc-133c-489f-bab0-240cafbbf59b)



**2) OR gate**


<br />

       \TLV
        $reset = *reset;
   
       $out = $in1 | $in2;
   
       // Assert these to end simulation (before Makerchip cycle limit).
       *passed = *cyc_cnt > 40;
       *failed = 1'b0;
       \SV
       endmodule

![Screenshot from 2023-10-16 22-50-38](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/61b96a18-5ea5-4f63-bcd7-9226d5982564)


**3)Explicitly adding the only 4 bits of the inputs using +**

<br />

       \TLV
          $reset = *reset;
          
          $out[4:0] = $in1[3:0] + $in2[3:0];
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;
          *failed = 1'b0;
       \SV
          endmodule

          


![Screenshot from 2023-10-16 22-54-21](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/3da109b3-498b-4a4a-bd68-4c381a3af4e7)



**4)Mux with 1-bit input**


<br />
       \TLV
          $reset = *reset;
          
          $out = $sel ? $in1 : $in2;
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;
          *failed = 1'b0;
       \SV
          endmodule

![Screenshot from 2023-10-16 22-56-12](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/60013cc0-de22-483a-aef4-60e167a4fb38)



**5)Mux with 8-bit inputs**

<br />


       \TLV
          $reset = *reset;
          
          $out[7:0] = $sel ? $in1[7:0] : $in2[7:0];
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;
          *failed = 1'b0;
       \SV
          endmodule


 
![Screenshot from 2023-10-16 22-58-37](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/f22d4542-cd75-4be3-a621-7fd1d0647bfd)


</details>



<details>
<summary>Sequential Logic</summary>

**1)D flip flop**

A D flip-flop, also known as a Data or Delay flip-flop, is a fundamental digital electronic circuit that stores a single binary bit of information. 
It is a type of bistable multivibrator, which means it has two stable states.


<br />
       \TLV
          $reset = *reset;
          
          $out = $reset ? 0 : $data_in;
          
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;
          *failed = 1'b0;
       \SV
          endmodule


![Screenshot from 2023-10-16 23-40-55](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/056dc121-dd0d-4968-afcf-55345cee8f6a)



**2)fibonacci series**


 > The Fibonacci series is a sequence of numbers in which each number is the sum of the two preceding ones. It typically starts with 0 and 1. So, the Fibonacci series begins as follows:

0, 1, 1, 2, 3, 5, 8, 13, 21, 34, ...



<br />

       \TLV
          $reset = *reset;
          
          $num[31:0] = $reset ? 1 : (>>1$num + >>2$num);
          
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;
          *failed = 1'b0;


![Screenshot from 2023-10-16 23-46-30](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/a967717d-6d91-48bc-9ba2-ef0e47accc6c)


**3)counters**

<br />

      \TLV
         $reset = *reset;
         
         $cnt[1:0] = $reset ? (0) : (>>1$cnt[1:0] + 1) ;


![Screenshot from 2023-10-16 23-49-43](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/bead905c-b7ac-4707-93c7-66079c4c5b66)

## Representation of constant in verilog

'0: All 0s (width based on context). 'X: All DONT-CARE bits. 16’d5: 16-bit decimal 5. 5'b00XX1: 5-bit value with DONT-CARE bits. 1: 32-bit (signed) 1.

Our simulator configuration: 

● will zero-extend or truncate when widths are mismatched (without warning) 

● uses 2-state simulation (no X’s)

**4)sequential calculator**


<br />

        \TLV
           $reset = *reset;
           
           $val1[31:0] = >>1$out;
           $val2[31:0] = $rand1[3:0];
           $sum = $val1 + $val2;
           $diff = $val1 - $val2;
           $prod = $val1 * $val2;
           $quot = $val1 / $val2;
           
           $out = $reset ? ( $op[1]?($op[0] ? $quot : $prod):($op[0] ? $diff : $sum) ) : 0;
           // $out = op[1]?(op[0] ? $quot : $prod):(op[0] ? $diff : $sum);
           
           
           // Assert these to end simulation (before Makerchip cycle limit).
           *passed = *cyc_cnt > 40;
           *failed = 1'b0;**



   ![Screenshot from 2023-10-16 23-53-00](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/e318c12d-0d16-465c-8083-7c8d97873d51)



</details>

<details>
<summary>pipelined logic</summary>


Pipeline Pythagoras's Theorem

![Screenshot from 2023-10-17 21-59-52](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/d19169c2-6f14-44a4-b955-4378ac087ffb)



<br />
      `include "sqrt32.v";
      |calc\
            @1
               $aa_sq[31:0] = $aa * $aa;
               $bb_sq[31:0] = $bb * $bb;
               
            @2
               $cc_sq[31:0] = $aa_sq + $bb_sq;
            @3
               $cc[31:0] = sqrt($cc_sq);


![Screenshot from 2023-10-17 22-08-22](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/5f897348-3e49-4ba0-be96-13788941e78a)


 **No impact no behavior:**

<br />
      `include "sqrt32.v";
      |calc\
            @1
               $aa_sq[7:0] = $aa * $aa;
               $bb_sq[7:0] = $bb * $bb;
               
            @2
               $cc_sq[7:0] = $aa_sq + $bb_sq;
            @3
               $cc[7:0] = sqrt($cc_sq);



![Screenshot from 2023-10-17 22-11-15](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/f2b8ebb6-77ae-4396-be96-bd56ab79b059)




- Retiming changes in system verilog is very bug-prone, so it is easy to make these vhanges in tlverilog.



- In makerchip waveform viewer the output will be captured according to the time, so if there are 3 stages in the logic then the output of the present inputs will be after two cycles.



**pipeline logic advantage:**


- In a non-pipelined system, a single operation may span multiple clock cycles, resulting in a relatively slow completion time. However, by introducing pipelining, the operation is divided into distinct stages, each executed in a single clock cycle. This architectural approach not only speeds up individual stages but also allows for concurrent execution of multiple stages. When pipelining is coupled with a higher clock frequency, it leads to a substantial reduction in the overall time required to finish an operation.



- Pipelining enables the parallel execution of various stages within an operation. As each stage is designed to be completed swiftly, the entire operation can be processed more efficiently. This enhanced throughput, when combined with an increased clock frequency, results in the ability to handle a greater number of operations within the same unit of time**



    **syntax of TLverilog**

Type of an identifier determined by symbol prefix and case/delimitation style.

Based on the first two letters of the variables:


- $lower_case: pipe signa 
    
- $CamelCase: state signal (technically, this is “Pascal case”)
    
- UPPER_CASE: keyword signal
    
- ">>" 1 : Ahead by 1.



**lab (pipeline)**


<br />
       \TLV
          $reset = *reset;
          
          |comp
             @1
                $err1 = $bad_input | $illegal_op ;
             @3 
                $err2 = $overflow | $err1 ;
             @6
                $err3 = $err2 || $div_by_zero;
          
          
          
          
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;

          *failed = 1'b0;
       \SV
          endmodule

    

![Screenshot from 2023-10-17 22-24-35](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/83df1557-8ffa-45db-b4f4-07ac1455d2c4)



**counter and calculator in pipeline:**


<br />

        \TLV
           
           |calc
              @1
                 $reset = *reset;
                 $cnt[1:0] = $reset ? (0) : (>>1$cnt[1:0] + 1) ;
                 
                 $val1[31:0] = >>1$out;
                 $val2[31:0] = $rand1[3:0];
                 $sum = $val1 + $val2;
                 $diff = $val1 - $val2;
                 $prod = $val1 * $val2;
                 $quot = $val1 / $val2;
                 $out = $reset ? ( $op[1]?($op[0] ? $quot : $prod):($op[0] ? $diff : $sum) ) : 0;
           
           // $out = op[1]?(op[0] ? $quot : $prod):(op[0] ? $diff : $sum);
           

![Screenshot from 2023-10-17 22-29-28](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/96789112-e280-4bae-9c8f-28dabc22e3cb)


**2-cycle calculator**

<br />
      \TLV
         
         |calc
            @1
               $val1[31:0] = >>2$out;
               $val2[31:0] = $rand1[3:0];
               $sum[31:0] = $val1[31:0] + $val2[31:0];
               $diff[31:0] = $val1[31:0] - $val2[31:0];
               $prod[31:0] = $val1[31:0] * $val2[31:0];
               $quot[31:0] = $val1[31:0] / $val2[31:0];
               
      
            @2
               $reset = *reset;
               $valid = $reset ? (0) : (>>1$valid + 1) ;
               $op[1:0] = $reset | $valid ;
               $out[32:0] = $op[1] ? ($op[0] ? $quot[31:0] : $prod[31:0]) : ($op[0] ? $diff[31:0] : $sum[31:0]) ;
         // $out = op[1]?(op[0] ? $quot : $prod):(op[0] ? $diff : $sum);
         
         
         
         // Assert these to end simulation (before Makerchip cycle limit).
         *passed = *cyc_cnt > 40;
         *failed = 1'b0;



![Screenshot from 2023-10-17 22-32-29](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/74dcaaf8-e0cb-49d4-badf-0fc580099338)


</details>

<details>
<summary>validity</summary>


**Validity provides:**

- Easier debug
- Cleaner design
- Better error checking
- Automated clock gating


**clock gating**

- Used to save power while transferring clock.
- Clock signals are distributed to EVERY flip-flop.
- clocks toggle twice per cycle.
- This consumes power.
- Clock gating avoids toggling clock signals.


**file structure in makerchip**

- \m5_TLV_version 1d: tl-x.org :- Version of makerchip being used and tl-x.org contains tyhe documentation
 - m5 :- Macro language used for processsing.
 - m5_makerchip_module :- Expands the inputs and outputs in the NAV file.
 - \sv :- The system verilog codes.
 - \TLV :- Where tlverilog code is defined.


**Distance Accumulator**

![Screenshot from 2023-10-18 18-52-12](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/e1dfdf26-48be-4a72-8769-648513d53d30)

<br />


     \SV
     `include "sqrt32.v";
     
     \TLV
        $reset = *reset;
        
        |calc
           @1
              $reset = *reset ;
           ?$valid
              @1
                 $aa_sq[31:0] = $aa * $aa;
                 $bb_sq[31:0] = $bb * $bb;
     
              @2
                 $cc_sq[31:0] = $aa_sq + $bb_sq;
              @3
                 $cc[31:0] = sqrt($cc_sq);
           @4
              $tot_dst = $reset ? 0 : ($valid ? >>1$tot_dst + $cc : >>1$tot_dst) ;


![Screenshot from 2023-10-18 18-55-22](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/9cdbf1b0-4906-42e1-a44c-12576ddb7ecb)


**cycle calculator with validity**

$valid_or_reset = $valid || $reset; as a when condition for calculation instead of zeroing $out.


<br />

      \TLV
         $reset = *reset;
         |clac  
            @1
               $reset = *reset ;
            ?$valid
               @1
                  
                  $val1[31:0] = >>2$out[31:0];
                  $sum = $val1 + $val2;
                  $diff = $val1 - $val2;
                  $prod = $val1 * $val2;
                  $quot = $val1 / $val2;
                  $valid = >>1$valid +1 ;
                  $valid_or_reset = $valid || $reset;
            @2
               $out[31:0] = $valid_or_reset ? ($op[1]?($op[0] ? $quot : $prod) : ($op[0] ? $diff : $sum) ) : 0 ;


![Screenshot from 2023-10-18 19-11-01](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/429fb532-0287-4bd0-bfcd-64a83c47e7be)


        

</details>


# Day-4 Basic RISC-V CPU micro architecture


<details>
<summary>intoduction to simple RISC-V miceo architecture</summary>

**RISC-V block diagram**

![Screenshot from 2023-10-19 09-20-03](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/4758a11c-1e9e-4c8b-bab8-80d1e361c4b9)

 1) Instruction Fetch (IF):
The processor fetches the instruction from memory. The program counter (PC) is used to determine the address of the next instruction in memory.
The instruction is loaded into the instruction register (IR) for decoding.

2) Instruction Decode (ID):
The processor decodes the instruction in the instruction register.
The opcode (operation code) is identified, and the necessary control signals are generated based on the opcode.

3) Execute (EX):
The processor performs the operation specified by the instruction.
For arithmetic and logical operations, the ALU (Arithmetic Logic Unit) performs the computation.
Memory addresses are calculated for load and store instructions.

4) Memory Access (MEM):
If the instruction involves accessing memory (such as a load or store operation), the memory address is sent to the memory unit.
For a load operation, data is read from memory and stored in a register.
For a store operation, data from a register is written to the memory location.

5) Write Back (WB):
The result of the instruction is written back to the destination register.
For instructions that produce a result (such as arithmetic or logical operations), the result is stored in the specified register.

**implementation**


![Screenshot from 2023-10-19 09-25-52](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/b2ea5415-5793-4f63-9ac5-9543019beaab)

 ![Screenshot from 2023-10-19 09-33-07](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/c2adf2ff-7f37-4adb-ba67-4b9112099ec3)

![Screenshot from 2023-10-19 09-33-50](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/3a01ca7c-9624-40ba-ab60-33b6578180a5)


</details>



<details>
<summary>instruction fetch</summary>

 **Instruction Fetch (IF):**
The processor fetches the instruction from memory. The program counter (PC) is used to determine the address of the next instruction in memory.
The instruction is loaded into the instruction register (IR) for decoding.
<br />


     \TLV
        $reset = *reset;
        
        $pc_out[31:0] = >>1$reset ? (0) : (>>1$pc_prev[31:0] + 32'h4) ;

![Screenshot from 2023-10-19 09-40-05](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/0637a08a-1ca4-4476-a7c4-4013de2b41a2)


<br />

       
       \TLV
          // External to function:
          m4_asm(ADD, r10, r0, r0)             // Initialize r10 (a0) to 0.
          // Function:
          m4_asm(ADD, r14, r10, r0)            // Initialize sum register a4 with 0x0
          m4_asm(ADDI, r12, r10, 1010)         // Store count of 10 in register a2.
          m4_asm(ADD, r13, r10, r0)            // Initialize intermediate sum register a3 with 0
          // Loop:
          m4_asm(ADD, r14, r13, r14)           // Incremental addition
          m4_asm(ADDI, r13, r13, 1)            // Increment intermediate register by 1
          m4_asm(BLT, r13, r12, 1111111111000) // If a3 is less than a2, branch to label named <loop>
          m4_asm(ADD, r10, r14, r0)            // Store final result to register a0 so that it can be read by main program
          
          // Optional:
          // m4_asm(JAL, r7, 00000000000000000000) // Done. Jump to itself (infinite loop). (Up to 20-bit signed immediate plus implicit 0 bit (unlike JALR) provides byte address; last immediate bit should also be 0)
          m4_define_hier(['M4_IMEM'], M4_NUM_INSTRS)
       
          |cpu
             @0
                $reset = *reset;
                
                $pc[31:0] = >>1$reset ? (0) : (>>1$pc[31:0] + 32'd4) ;
             @1
                $imm_rd_en = !$reset;
                $imm_rd_addr[M4_IMEM_INDEX_CNT-1:0] = $pc[M4_IMEM_INDEX_CNT+1:2];
                $instr[31:0] = $imem_rd_data[31:0];
                
          
          // Assert these to end simulation (before Makerchip cycle limit).
          *passed = *cyc_cnt > 40;
          *failed = 1'b0;
       
          |cpu
             m4+imem(@1)    // Args: (read stage)
             //m4+rf(@1, @1)  // Args: (read stage, write stage) - if equal, no register bypass is required
             //m4+dmem(@4)    // Args: (read/write stage)
             m4+myth_fpga(@0)  // Uncomment to run on fpga
       
          m4+cpu_viz(@4)    // For visualisation

![Screenshot from 2023-10-19 09-46-07](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/125bef5d-1a54-4381-ace3-d253bc8b93ce)



</details>

<details>
<summary>decoding</summary>

**Instruction Decode (ID):**
The processor decodes the instruction in the instruction register.
The opcode (operation code) is identified, and the necessary control signals are generated based on the opcode.


- Below image shows hoe decode is determining the TYPE OF RISC V instructions set (Various types of Instructions in RV32 are I, R, S, J, U)


![Screenshot from 2023-10-19 09-47-07](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/8300c71b-3675-4c61-a4fa-118b89901972)



**instruction types in decoding stage**


![Screenshot from 2023-10-19 09-50-19](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/10640dae-33e6-4e64-9e16-0ae4ab24f73d)



<br />

       @1 
                //$pc[31:0] = >>1$reset ? 32'b0 : >>1$taken_br ? >>1$br_tgt_pc : >>1$pc + 32'd4;
                $imem_rd_en = !$reset;
                $instr[31:0] = $imem_rd_data[31:0];
                //$instr[31:0] =  $imem_rd_en ? 32'b0 : >>1$imem_rd_data[$imem_rd_addr];
                $imem_rd_addr[3-1:0] = $pc[3+1:2];
                
                $is_i_instr = $instr[6:2] ==? 5'b0000x ||
                              $instr[6:2] ==? 5'b001x0 ||
                              $instr[6:2] ==? 5'bxx001;
                $is_s_instr = $instr[6:2] ==? 5'b0100x;
                $is_r_instr = $instr[6:2] ==? 5'b01xxx ||
                              $instr[6:2] ==? 5'b011x0 ||
                              $instr[6:2] ==? 5'bxx100;
                $is_u_instr = $instr[6:2] ==? 5'b0x101;
                $is_b_instr = $instr[6:2] ==? 5'b11000;
                $is_j_instr = $instr[6:2] ==? 5'b11011;



  ![Screenshot from 2023-10-20 09-46-48](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/eba3ab6d-b853-4ffe-a70b-7a5f30c8cb50)


  **instructions**

![Screenshot from 2023-10-20 09-48-40](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/76c8acc8-40f3-4004-a1bc-c4d2dc027bb8)


<br />
         $imm[31:0] = $is_i_instr ? { {21{$instr[31]}}, $instr[30:20] } 
                                  : $is_s_instr ? {{21{$instr[31]}}, $instr[30:25],$instr[11:7]} 
                                  : $is_b_instr ? { {19{$instr[31]}} , $inst[7] , $instr[30:25] , $instr[11:8] ,1'b0}
                                  : $is_u_instr ? { $instr[31] , $instr[30:12], 12'b0 }
                                  : { {12{$instr[31]}} , $instr[20], $instr[30:25], $instr[24:21] ,1'b0 };


 ![Screenshot from 2023-10-20 09-53-41](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/3dfa0043-efd3-4bd8-b5e5-de7b56f96471)

  
![Screenshot from 2023-10-20 09-55-02](https://github.com/vishnupriyapesu/pes_riscv/assets/142419649/df040ddd-b75a-48ae-9edf-0a11e17a36c0)

