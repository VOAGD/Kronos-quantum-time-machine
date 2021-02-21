import pennylane as qml

from pennylane import numpy as np
from pennylane import qnode


dev = qml.device('default.qubit', wires= 2, shots= 1000)
first_circuit = qml.QNode([first_funct @ sec_funct], dev)

def first_funct():
    # Bell state
    qml.Hadamard(wires= 0)
    qml.CNOT(wires=[0, 1])
    
    return qml.sample(qml.PauliZ(0)) @ qml.sample(qml.PauliZ(1))

n_w = 2
wires = range(n_w)

c = [1, 1]
obs = [qml.PauliX(0), qml.PauliX(1)]
hamiltonian = qml.Hamiltonian(c, obs)

def sec_funct(time):
    ApproxTimeEvolution(hamiltonian, time, 1)
    
    a = [qml.expval(qml.PauliZ(wires=i)) for i in wires]
    return a
    
    
