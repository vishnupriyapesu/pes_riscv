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



