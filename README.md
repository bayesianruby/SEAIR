# SEAIR-project

The aim of this project is to conduct an uncertainty quantification analysis (including sensitivity analysis) on a complex model. The study of a compartmental (simplified) model appeared to be a natural choice.

The SEIR (Susceptible-Exposed-Infected-Recovered) model that we present is a compartmental deterministic model that has been known for almost a century and has been used for many years. is a deterministic compartmental model that has been known for almost a century and used in in epidemiology since the 1980s. It is also the one used by epidemiologists studying COVID-19. This model is presented in the form of a system of the number of infected and contagious individuals, etc.

In order to be representative of this 'epidemy', certain specific characteristics of COVID-19 were taken into account (presence of asymptomatic individuals) and we therefore propose to study here a SEAIR model (Susceptible, Asymptomatic, Infected, Established). We will not consider a complete model including regional and age stratification, but we will however, exploit data on hospitalizations collected by region.


## The model : 

- S: Susceptible (to be infected) individuals. During the epidemy, they may remain in this compartment or be infected and move to the
compartiment E.
- E: Exposed individuals. They are in the incubation phase and are not yet contagious. They then move into compartments A or I.
- I: Infected (symptomatic) individuals. They are contagious. They then move to compartment R.
- A: Asymptomatic infected individuals. They are contagious (but a little less than the individuals in compartment I). They then move to compartment R.
- R: individuals who are settled, admitted to hospital, or dead. They are no longer contagious.


The evolution of the epidemy is governed by the following system of ordinary differential equations (where the unit of time is the day) which gives the "number" of individuals present in each compartment :


<p align="center">
<img width="220" alt="Capture d’écran 2022-06-18 à 16 05 00" src="https://user-images.githubusercontent.com/80846462/174442031-6132ec3d-cd39-492d-a6b1-f7de40126878.png">
</p>


This system maintains the size of the population:
$N = S + E + I + A + R = constant.$


A final "compartment" H is added for calibration purposes (see below).
This is the number of daily hospitalisation, which can be taken to be equal to $\gamma \frac{I(t)}{T_I}$ to simplify. This is not a real compartment, but it is interesting because this number is observed and can therefore be used for calibration purposes.


## The parameters : 

- The transmission rate $\beta(t)$ is of the form : 
<img width="455" alt="Capture d’écran 2022-06-18 à 16 37 49" src="https://user-images.githubusercontent.com/80846462/174443271-04183fc6-491d-4829-8da0-268f2f43cafe.png">


The assumption is that before any containment measures are taken, the transmission rateis constant and decreases then when the measures are taken.

- $\beta_0$: transmission rate before containment.
- $f$: effective reduction in transmission rate by containment.
- $\mu$: factor of decrease in contagiousness of asymptomatic vs. symptomatic individuals.
- $\alpha$: proportion of symptomatic individuals among the infected.
- $T_E$: average time spent in the incubation phase.
- $T_I$: average time spent in the infectious phase (contagious).
- $\gamma$: propability for a symptomatic infected to have to go to the hospital.



## Results : 
 
 
 When we consider the model for a region. It is efficient if we well adapt the parameters, the forecast is corresponds to what occured :  
 ![téléchargement](https://user-images.githubusercontent.com/80846462/174444050-ab90bfd9-a6c2-466a-8d58-3e67d146b6a1.png)
