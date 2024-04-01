module fulladder (sum, cout, a,b,c);

input a,b,c;

output sum, cout;

wire w1,w2,w3,w4,w5;

xor x1(w1,a,b);

xor x2(sum,w1,c);

and al(w2,a,b);

and a2(w3,b,c);

and a3(w4,a,c);

or o1(w5,w2,w3); or o2(cout,w5,w4);

endmodule

Full Subractor:

module full_subtractor(a, b, c,D, Bout);

input a, b, c;

output D, Bout;

assign D = a^b^c;

assign Bout = (a & b) | ((a^ b) & c);

endmodule

Half Adder:

module half_adder(a,b,sum,carry);

input a,b;

output sum,carry;

or(sum,a,b);

and(carry,a,b);

endmodule

Half Subractor:

module half_subtractor(D,Bo,A,B);

input A,B;

output D,Bo;

assign D=A^B;

assign Bo=(~A)&B;

endmodule

Logic Gates:

module logicgates(a,b,andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate);

input a,b;

output andgate,orgate,xorgate,nandgate,norgate,xnorgate,notgate;

and(andgate,a,b);

or(orgate,a,b);

xor(xorgate,a,b);

nand(nandgate,a,b);

nor(norgate,a,b);

xnor(xnorgate,a,b);

not(notgate,a);

endmodule

Ripple Carry Adder 4Bit:

module rippe_adder(S, Cout, X, Y,Cin);

input [3:0] X, Y;// Two 4-bit inputs

input Cin;

output [3:0] S;

output Cout;

wire w1, w2, w3;fulladder u1(S[0], w1,X[0], Y[0], Cin);

fulladder u2(S[1], w2,X[1], Y[1], w1);

fulladder u3(S[2], w3,X[2], Y[2], w2);

fulladder u4(S[3], Cout,X[3], Y[3], w3);

endmodule

module fulladder(S, Co, X, Y, Ci);

input X, Y, Ci;

output S, Co;

wire w1,w2,w3;

xor G1(w1, X, Y);

xor G2(S, w1, Ci);

and G3(w2, w1, Ci);

and G4(w3, X, Y);

or G5(Co, w2, w3);

endmodule

