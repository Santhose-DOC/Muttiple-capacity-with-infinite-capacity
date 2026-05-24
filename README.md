# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival  of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.

## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.

![image](https://user-images.githubusercontent.com/103921593/203238035-1c8109bc-cbf2-4c77-baea-c5b682a752ef.png)

## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)



## Program
```python
import math

# Input values
arr_time = float(input("Enter the mean inter arrival time of objects from Feeder (in secs): "))
ser_time = float(input("Enter the mean service time of Lathe Machine (in secs): "))
robot_time = float(input("Enter the additional time taken for Robot (in secs): "))

# Number of servers
c = 2

# Arrival rate (λ)
lam = 1 / arr_time

# Service rate (μ)
mu = 1 / (ser_time + robot_time)

# Traffic intensity (ρ)
rho = lam / (c * mu)

print("------------------------------------------------------------")
print("Multiple Server with Infinite Capacity - (M/M/c):(∞/FIFO)")
print("------------------------------------------------------------")

print("Arrival rate (λ) : %0.3f" % lam)
print("Service rate (μ) : %0.3f" % mu)
print("Traffic intensity (ρ) : %0.3f" % rho)

if rho < 1:

    # Calculate P0
    s = 0

    for n in range(c):
        s = s + (((lam / mu) ** n) / math.factorial(n))

    p0 = 1 / (s + ((((lam / mu) ** c) /
          math.factorial(c)) * (1 / (1 - rho))))

    # Average number in queue
    Lq = (1 / (c * math.factorial(c))) * \
         (((lam / mu) ** (c + 1)) / ((1 - rho) ** 2)) * p0

    # Average number in system
    Ls = Lq + (lam / mu)

    # Waiting times
    Wq = Lq / lam
    Ws = Ls / lam

    print("\nAverage number of objects in the conveyor (Lq) : %0.3f" % Lq)
    print("Average number of objects in the system (Ls) : %0.3f" % Ls)

    print("\nAverage waiting time in the conveyor (Wq) : %0.3f sec" % Wq)
    print("Average waiting time in the system (Ws) : %0.3f sec" % Ws)

    print("\nProbability that the system is empty (P0) : %0.3f" % p0)

else:
    print("\nWarning! System is unstable because λ ≥ cμ")

print("------------------------------------------------------------")
```

## Output :
<img width="638" height="348" alt="image" src="https://github.com/user-attachments/assets/d8c8469d-4ac7-4f3c-b63a-d63e5a8f92ad" />

## Result : 

The average number of materials in the system, average number of materials in the conveyor, average waiting time in the system, and average waiting time in the conveyor for the multiple server infinite capacity queue model (M/M/2):(∞/FIFO) are calculated successfully using Python.
