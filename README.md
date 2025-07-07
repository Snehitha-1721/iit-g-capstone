# iit-g-capstone
Dynamic Pricing for Urban Parking Lots

Project Overview

This project implements a dynamic pricing engine for urban parking lots using real-time and historical data. The system determines optimal prices for parking based on occupancy levels, queue length, nearby traffic conditions, vehicle type, special events, and competitor pricing.

The primary goal is to optimize revenue, balance demand, and prevent overcrowding or underutilization by adjusting prices in a data-driven, explainable, and smooth manner.

Dataset Description

The dataset contains 18 time points per day for 14 parking lots, spanning 73 days. Each record includes:

SystemCodeNumber: Parking lot identifier

Capacity: Maximum number of vehicles allowed

Occupancy: Number of currently parked vehicles

QueueLength: Number of vehicles waiting to enter

VehicleType: Type of incoming vehicle (bike, car, truck)

TrafficConditionNearby: Traffic level (low, medium, high)

IsSpecialDay: Whether it's a holiday or event (0/1)

Latitude/Longitude: Parking lot coordinates

LastUpdatedDate & Time: Timestamp of observation

Models Implemented

Model 1: Linear Occupancy-Based Pricing

Formula: Price(t+1) = Price(t) + alpha * (Occupancy / Capacity)

Simple, interpretable model

Reacts linearly to rising occupancy

Model 2: Demand-Based Pricing

Uses multiple features to compute a demand score:

Occupancy

Queue length

Traffic level

Special day

Vehicle type

Normalized demand controls smooth price changes

Formula: Price = BasePrice * (1 + lambda * NormalizedDemand)

Model 3: Competitive Pricing

Adjusts demand-based price using competitor analysis

Uses geographical proximity (lat-long) to nearby lots

If lot is full and competitors are cheaper → lower price

If competitors are expensive → increase price slightly

Output

For every timestamped entry per parking lot, the output includes:

LinearPrice: From Model 1

DemandPrice: From Model 2

FinalPrice: Adjusted by competitor analysis in Model 3

Additional calculated metrics:

Revenue: FinalPrice * Occupancy

Utilization: Occupancy / Capacity

Technologies Used

Python, Pandas, NumPy

Datetime Processing

(Optional) Pathway for real-time simulation

(Optional) Bokeh/Matplotlib for visualizations

Evaluation Metrics

As this is a regression-style pricing system, standard classification metrics like accuracy or F1-score are not used. Instead, evaluation is based on:

MAE / RMSE: If ground truth prices are available

Revenue Generation

Utilization Balance

Smoothness and explainability of price changes

How to Run

Place dataset.csv in your working directory or Colab

Load and process the data

Run the three pricing models sequentially

Export or visualize the final pricing DataFrame

Credits

Developed for the Summer Analytics 2025 Capstone Project organized by the Consulting & Analytics Club × Pathway.
