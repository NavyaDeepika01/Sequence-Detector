
module seq_generator (
  input   logic        clk,
  input   logic        reset,

  output  logic [31:0] seq_o
);
  logic [31:0] state,currentstate,nextstate;
  
always@(posedge clk) 
    begin 
      if(reset)
        begin 
        
          state<=1;
          currentstate<=1;
          nextstate<=32'h0;
        end
      else
        begin 
           state<=currentstate+nextstate;
          currentstate<=state;
          nextstate<=currentstate;
         
        end
    end
  assign seq_o=nextstate;
endmodule
