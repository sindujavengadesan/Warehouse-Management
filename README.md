# Warehouse-Management using Reinforcement Learning

## Problem Statement

**Warehouse Optimization Challenge:** Managing a warehouse requires efficiently maneuvering robots to collect items and fulfill requests while minimizing operational expenses and time.

**Current Solutions:** Traditional algorithms sometimes fail to adapt to the dynamic nature of real-world warehouses, resulting in inefficiency. Inefficiencies in robot movement and order processing might result in increased operational expenses, affecting total productivity.

**Comparative Study:** We investigate and compare the performance of four RL algorithms: Q-learning, SARSA, Policy Gradient, and Deep Q-Network (DQN).

**Primary Objective:** The major goal is to create an RL agent that can learn the best policies for navigating the warehouse, picking items, and fulfilling orders while controlling battery levels and inventory.

## State

- **Robot Position:** The current position of the robot on the warehouse grid, represented as coordinates (x, y).
- **Item Locations:** The positions of items in the warehouse, represented as a list of coordinates (x, y).
- **Inventory Levels:** The current stock levels for each item type, represented as a dictionary with item IDs as keys and quantities as values.
- **Order Queue:** A list of item IDs representing the sequence of orders to be fulfilled.
- **Battery Level:** The remaining battery percentage of the robot.
- **Robot Inventory:** The item currently being carried by the robot, if any, represented by its item ID.

## Actions

- **Movement:**
  - **Up:** Move the robot one cell up on the grid.
  - **Down:** Move the robot one cell down on the grid.
  - **Left:** Move the robot one cell left on the grid.
  - **Right:** Move the robot one cell right on the grid.
  - **Pick:** Attempt to pick up an item from the current cell.
  - **Drop:** Attempt to drop the carried item.

## Reward

- **Base Action Cost:** A small negative reward (-0.1) for each action to encourage efficiency and discourage unnecessary movements.
- **Successful Pick:** A positive reward (+10) for successfully picking an item, incentivizing the robot to fulfill orders.
- **Successful Drop:** A significant positive reward (+100) for successfully dropping an item that fulfills an order, with additional bonuses for earlier orders.
- **Battery Depletion Penalty:** A large negative reward (-50) if the robot's battery level drops to zero, penalizing poor battery management.
- **Invalid Actions:** Negative rewards (-5) for attempting to pick without an item or drop without carrying an item, to discourage invalid actions.
- **Order Completion Bonus:** An additional positive reward (+200) when all orders in the queue are fulfilled, encouraging the agent to complete all tasks efficiently.
