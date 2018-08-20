This file describes the structure of the matlab code used to compute the results from ["Redistributing the Gains From Trade Through Progressive Taxation"](http://www.waugheconomics.com/uploads/2/2/5/6/22563786/lw_tax.pdf)

Contents and description of code...

- ``island_solve_calibrate_NAG.m`` which takes a progressivity parameter and then calibrates and solves for an equilibrium to the economy.

- ``clustergrid`` which creats an asset grid with points clustered around places of interest.

- ``open_economy_markovchain`` creates the markov chain which characterizes the joint dynamics of local productivity shocks and world prices. Uses ``rouwenhorst.m``

- ``island_compute_soe`` this is the main file. It takes as given a set of prices and parameters and then computes results from the economy including excess demand functions. The basic algorithm is to (i) solve the household problem, (ii) compute the invariant distribution associated with (i) and (iii) compute allocations and (iv) return excess demand. The contents of this program are essentially broken down along the lines described above:

    1.  ``mobility_labor_supply_smth.m`` given wages, computes the policy functions associated with the households problem by value function iteration.
    2. ``island_invariant.m`` computes the invariant distribution across islands given policy functions from above. Todo: need to explain how this works clearly within the code.
    3. ``compute_consumption.m`` constructs aggregate consumption give policy functions and the invariant distribution.
    4. ``market_clearing_soe.m`` computes market clearing conditions and other quantities such as aggregate and island level trade shares, given aggregate consumption and policy functions. From here, we have essentially everything to return the excess demand functions at the island level. 
    5. ``fischer_burmeister.m`` used to smooth out the objective function given that the market clearing conditions take on a mixed complementarity problem (either zero or prices are at a bound).
    6. ``brewermap.m`` to make a nice colored heat maps. Not important.

---

### Calibration

Simply run ``island_solve_calibrate_NAG.m`` with the argument 0.18. To adjust the calibration targets, lines 16-20 contain the other data moments.

---

### Compute Optimal Policy

---

### Plotting
