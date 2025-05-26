# Implementation Of News paper Seller Simulation
What is Newspaper Seller Simulation?
It’s a simple discrete-event simulation that models the daily operation of a newspaper seller. The goal is to simulate multiple days of selling newspapers, considering daily demand randomness, costs, selling price, leftover scrap value, and lost sales due to unmet demand.

Key Concepts & Inputs
Number of days (N) to simulate — how long the simulation runs.

Newspapers ordered daily — the fixed number of newspapers the seller stocks each day.

Costs and prices:

Cost price per newspaper

Selling price per newspaper

Scrap price per unsold newspaper (newspapers leftover at day end)

Demand distribution: Daily newspaper demand is random but follows a known probability distribution, e.g.:

Demand can be 40 papers with 30% probability

Demand can be 50 papers with 50% probability

Demand can be 60 papers with 20% probability

Random number generator: To simulate daily demand based on the probability distribution.

Step-by-step Implementation Approach
Step 1: Define Inputs and Data Structures
Fix the number of newspapers ordered daily.

Define the cost, selling price, and scrap price.

Store the demand probabilities and their corresponding demand values.

Create variables to store cumulative results like total profit, total lost sales, total scrap value, etc.

Step 2: Simulate Daily Demand
For each day, generate a random number between 0 and 1.

Use this random number and your demand distribution to determine the demand for that day.

For example, if the random number is 0.45 and demand probabilities are:

Demand=40 with 0.3 probability

Demand=50 with 0.5 probability

Demand=60 with 0.2 probability

Then 0 to 0.3 → demand=40, 0.3 to 0.8 → demand=50, 0.8 to 1 → demand=60

Since 0.45 lies between 0.3 and 0.8, demand = 50 for the day.

Step 3: Calculate Daily Outcomes
Newspapers Sold: minimum of demand and newspapers ordered.

Lost Sales: if demand > newspapers ordered, lost sales = demand - newspapers ordered; else 0.

Leftover newspapers: if demand < newspapers ordered, leftover = newspapers ordered - demand; else 0.

Step 4: Calculate Daily Profit
Revenue = Newspapers Sold × Selling Price

Cost = Newspapers Ordered × Cost Price

Scrap Value = Leftover Newspapers × Scrap Price

Daily Profit = Revenue + Scrap Value - Cost

Step 5: Update Cumulative Stats
Keep a running total of profit, lost sales, leftover newspapers, etc.

Step 6: Repeat for N Days
Loop steps 2 to 5 for all days of simulation.

Step 7: Report Results
At the end, output:

Total profit

Average daily profit

Total lost sales

Total scrap

Other statistics you want.

Optional: Structure the Program
You could design your program with:

Classes or functions:

A function to generate demand based on random number and distribution

A function to simulate one day

A main loop to run the simulation over N days

Data recording:

Store day-by-day results in a table or list

Print or write to file for analysis

Summary Example Flow:
sql

START
Input simulation parameters
FOR each day in simulation period:
    Generate random number
    Determine daily demand from random number
    Calculate newspapers sold, lost sales, leftover
    Calculate daily profit
    Update cumulative totals
END FOR
Calculate and output summary statistics
END
