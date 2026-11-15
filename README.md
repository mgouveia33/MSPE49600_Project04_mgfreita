# MSPE 49600 Project 04: Ansys Fluent and Gaussian Process Modeling
Author: Maico Freitas

Course: MSPE 49600, Data Analytics for Motorsports

**Overview** 

This project studies how the angle of attack of a two-dimensional NACA 0012 airfoil changes drag and lift at a 50 m/s inlet speed. Ten Ansys Fluent simulations were run at angles selected with a one-dimensional Latin hypercube sampling. Separate Gaussian process (GP) regression models fitted to the data predict drag and lift from angle of attack. The notebook plots predicted means and uncertainty and uses drag-to-downforce ratio to guide a follow-up simulation.


**Python packages**

The notebook uses:
- numpy
- pandas
- scipy
- scikit-learn
- matplotlib
- ipykernel (to run the notebook in Jupyter/VS Code)


The Fluent sweep script additionally requires ansys-workbench-core. The supplied CSV and notebook are sufficient to rerun the modeling and plots. Ansys Fluent is only needed to generate new CFD runs.

Install the analysis packages in the selected Python environment:

> python -m pip install numpy pandas scipy scikit-learn matplotlib ipykernel

For a new Fluent sweep, also install:

> python -m pip install ansys-workbench-core


Rerun the notebook from the submitted CFD CSV

1. Put mgfreita_pr04_notebook.ipynb and airfoil_results.csv in the same directory. 
2. Open the notebook in Jupyter or VS Code and select the environment with the packages above.
3. Run all cells from top to bottom.


**Recomendation**

The fitted GP predicts its lowest eligible drag-to-downforce ratio near 0.85°, with predicted drag of 5.40 N and downforce of 273.22 N. The best sampled ratio occurred at 6.74°, where the observed drag was 9.63 N and downforce was 312 N.

The three held-out validation runs give drag RMSE 43.17 N and lift RMSE 119.38 N. The largest absolute lift error occurs at 0.492°, close to the predicted low-ratio region. The fitted model also reports high lift predictive variance there. With only ten CFD runs, those errors and uncertainty are too large to rank nearby low-angle candidates confidently.

The angle recommended for a follow-up simulation is 1.5°. This run probes the sparsely sampled interval between 0.49° and 3.69° and helps assess the downward ratio trend and predictions near the GP's low-ratio region.



