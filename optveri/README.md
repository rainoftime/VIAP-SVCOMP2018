##Compiler optimization verification



- Code hoisting
- Constant propagation
- Copy propagation
- If-conversion
- Partial redandancy elimin


- Loop invariant code motion
- Loop peeling
- Loop unrolling
- Loop unswitching
- Loop fission
- Loop fusion
- Loop interchange
- ...


###Examples

Partial redundancy elimination
~~~~

if B then
    S1
    V1 := E
    S2
else
    S3
V2 := E

//
 
if B then
    S1
    V1 := E
    S2
    V2 := V1
else
    S3
    V2 := E   

~~~~


Code hoisting

~~~~

if B then
    S1
    S2
else
    S1
    S3

//

S1
if B then
    S2
else
    S3


~~~~


Loop unrolling

~~~~

while V1 < V2 do
    S
    V1 := V1 + 1


//

while (V1 + 1) < V2 do
    S
    V1 := V1 + 1
    S
    V1 := V1 + 1

if V1 < V2 then
    S
    V1 := V1 + 1


~~~~


Strength reduction

~~~~
while V1 < V2 do
    V3 := V1 * E
    S 
    V1 := V1 + 1


//

V4 := V1 * E
while V1 < V2 do
    V3 := V4
    V4 = V4 + E
    S
    V1 := V1 + 1

~~~~



###Related Work

- Automatic Equivalence Checking of UF+IA Programs, SPIN 13
- Weakest Precondition Synthesis for Compiler Optimizations, VMCAI 14
