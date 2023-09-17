**Repository Overview**

We will perform a multiplication operation on the IBM quantum computer, taking a simple example of multiplying two numbers. As it is suggested that for simple athematic operations using quantum computers is not an excellent choice, but we just want to check and learn how things work on a quantum computer. 

**Environmental setup**
We performed a simple matiplication fuunction, using IMB quantum computer plateform.
https://quantum-computing.ibm.com/
**Code Structure**
**The code itself is well structured but I will explain its different parts and how they work.
Imports**:

**(1)** import qiskit: This statement imports the Qiskit library, which is used for quantum computing.
import numpy as np: This statement imports the NumPy library, often used for numerical operations in Python.
Function Definition:

**(2)** def quantum_multiplication(multiplicand, multiplier):: This line defines a Python function named quantum_multiplication that takes two arguments: multiplicand (the first number to multiply) and multiplier (the second number to multiply).
The function has a docstring (enclosed in triple quotes) that provides a brief description of what the function does, its arguments, and its return value.
Initializing Quantum Registers and Circuit:

**(3)** q = qiskit.QuantumRegister(4) and c = qiskit.ClassicalRegister(4): These lines create quantum and classical registers, each with 4 qubits or bits.
circuit = qiskit.QuantumCircuit(q, c): This line initializes a quantum circuit that uses the created quantum and classical registers.
Encoding Inputs:

**(4)** circuit.x(q[0]) and circuit.x(q[1]): These lines set the first and second qubits of the quantum register to the state |1>, effectively encoding the multiplicand and multiplier as 1 in binary.
Hadamard Gates:

**(5)** circuit.h(q[0]) and circuit.h(q[1]): These lines apply Hadamard gates to the first and second qubits. Hadamard gates prepare the qubits in a superposition of states, which is a key step in quantum algorithms.
Quantum Fourier Transform (QFT):

The code attempts to create a QFT multiplication circuit. However, there is some commented-out code related to this section, and it seems there are issues with the commented-out code. The QFT is a crucial component in quantum multiplication algorithms.
Measurement and Execution:

**(6)** circuit.measure(q, c): This line adds measurements to the quantum circuit, which will be used to obtain the final result.
job = qiskit.execute(circuit, backend=qiskit.Aer.get_backend('qasm_simulator')): This line sends the quantum circuit to a simulator backend for execution.
result = job.result(): It retrieves the result of the quantum computation.
Extracting the Product:

**(7)** product = format(result.get_counts().get('0000', 0), '04b'): This line extracts the product from the measurement outcomes. It looks for the specific outcome '0000' (which represents the product) and converts it to its binary representation.
Returning the Result:

**(8)** return int(product, 2): This line converts the binary product back to an integer and returns it as the output of the quantum_multiplication function.
Overall, this code appears to be an attempt to perform quantum multiplication, but it has some commented-out code and issues related to the QFT part. You may need to resolve these issues for the code to function correctly. Additionally, this code seems to be a simplified example and may not be suitable for practical multiplication of large numbers on a quantum computer. Quantum multiplication algorithms are typically more complex and specialized.

**Quantum Algorithm**

**Unit Testing**
**(1)** Import the unittest library to our environment

**(2)** Defined a function called test_multiplication(). This function has three parts: Set up, Act, and Assert. First, the setup of this function means that we will input a multiplier and a multiplicand, as well as their expected result. Second, we act by multiplying the multiplier and the multiplicand together using our quantum multiplication function, quantum_multiplication(), and we store the result. Finally, we use the assertEqual() function in order to check if our expected product matches the result provided by our quantum_mutiplication() function. If they both match, then our code is working fine and you get no output message. If they do not match then you get an error message that you can customize.

The test_multiplication() function only works when you are multiplying two positive integers.

**(3)** Define a function called test_negative_multtiplication(). This works exactly as the test_multiplication() function, except it only tests for multiplying two negative integers.

**(3)** Define a function called test_mixed_multtiplication(). This works exactly as the test_multiplication() function, except it only tests for multiplying a negative and a positive integer.

**(3)** Define a function called test_large_integer_multtiplication(). This works exactly as the test_multiplication() function, except it only tests for multiplying two positive integers at least one of which is big.






