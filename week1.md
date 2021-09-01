# Week1
All problems can be posed as membership queries in languages.

### Axioms of Computing

* Machines are not omnipresent i.e. it takes non-zeron time to retrieve data from far off locations.
* Machines are not omniscient i.e. we can only store a finite amount of information in finite volume.
* Machines are not omnipotent i.e. finite code can only exert a finite amount of control

In order to determine the quality of the solution or how "good" it is we can use asymptotic analysis to see how it grows, worst case analysis to take care of corner cases, and time and space complexity.

### Problems computers cannot solve 

Cantor's diagonalisation proof can be used to show that the power set of binary strings is uncountable, which in turn implies that the number of computational problems is uncountable (recalling that every power set associated with a  binary string is a language on which we can pose a membership query). Meanwhile the number of solutions is countably infinite as every solution can be conisdered to a binary string. Therefore there exists an infinite number of problems that cannot be solved computationally as we cannot establish a bijection between uncountable and countable infinities.

### Church Turing Hypothesis

It simply states that every effective computation can be carried out by a Turing Machine. A Turing Machine is a 7-tuple with a finite set of control symbols moving over an infinite length tape with finite tape symbols. It moves across the tape, readin the tape symbols and changing its state acccrodingly. Any computable program that we can think of can be done by a Turing Machine. 

### Extra Reading

https://www.youtube.com/watch?v=dNRDvLACg5Q

https://www.youtube.com/watch?v=RPQD7-AOjMI

https://www.youtube.com/watch?v=macM_MtS_w4

The works of and life of Turing and Neumann are fascinating. Their wikipedia pages are treasure troves.

### Implementations

A simple Enigma Machine I made in python after falling down an Alan Turing rabbit Hole.

https://github.com/AnirudhGovil/Enigma-Machine-Project

### Thoughts

Quantum computers in theory are expotentially more efficient than classical Turing Machines, and in some sense can "beat" them. The notion of a quantum Turing Machine was thus created to establish that quantum computers too are Turing Complete. A Quantum Turing Machine's Internal state as well as the location of it's head on the tape is not singular but rather a linear combination of states in "superposition". It's ability to explore multiple computational paths at once gives it unique capabilities. A subtley differnt concept is that of Non-Deterministic Turing Machines whose descisions to trasition from one state to another are probabilistic, as compared to the Quantum Turing Machine which transition with certainity to a "superpostion" of states.
