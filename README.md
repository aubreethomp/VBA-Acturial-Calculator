# VBA-Acturial-Calculator

A user-form-based term life insurance calculator, written in VBA for Excel. It collects policy inputs (age, term, interest rate, gender, death benefit, and number of simulations) from the form, validates them, runs actuarial calculations, and writes results and charts to a "Results" worksheet. 

Form lifecycle

UserForm_Initialize populates the gender dropdown with "Female"/"Male", defaulting to "Female."
ValidateUserInput checks that all fields are filled, numeric where required, and that age falls between 27–99 and simulation count is positive.
SubmitButton_Click orchestrates the full workflow: validate inputs, reset the Results sheet, run calculations, run the Monte Carlo simulation, output results and charts, then reset the form.
CancelButton_Click / ResetCalc clear the form and hide it without calculating.

Actuarial calculations

GetQx looks up a mortality rate (qx) for a given age and gender from the "MortalityTable" worksheet.
CalcDeathBenefit computes the expected present value (EPV) of the death benefit over the policy term, discounting for interest and survival probability.
CalcNetLevelPremium computes the net level premium by dividing the EPV of the benefit by the EPV of a level annuity-due (the premium payment stream).

Monte Carlo simulation

MCSimulation runs a specified number of simulated policy lifetimes, using random draws against mortality rates to determine if/when a simulated death occurs, then compiles summary statistics (survival vs. death counts, average EPV of death claims).
OuputMonteCarlo writes simulation results and summary stats to the Results sheet and inserts a pie chart of survival vs. death outcomes.

Output & reporting

ResetResultsWS creates (or clears, if it already exists) the "Results" worksheet and removes any existing charts.
OutputResults writes the EPV, premium, and all input parameters to the Results sheet with formatting.
DrawTermSensitivityChart builds a line chart showing how net level premium changes across policy terms (1 to the input term), holding other inputs constant.


Want this saved as a Word doc, or would you rather I turn it into inline code comments?

