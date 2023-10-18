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

 
