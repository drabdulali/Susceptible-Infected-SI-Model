# Susceptible-Infected---SI-Model
The Susceptible-Infected (SI) model is a simple mathematical model used to simulate the spread of an infectious disease in a population. 

Here is an explanation of each part of the code:

Define the parameters:

N <- 1000   # Total population
S <- 995    # Initial number of susceptible individuals
I <- 5      # Initial number of infected individuals
alpha <- 0.1 # Rate of infection
time <- 100  # Number of days


Here we are defining the parameters for the SI model, including the total population (N), the initial number of susceptible individuals (S), the initial number of infected individuals (I), the rate of infection (alpha), and the number of days (time) for which we want to simulate the model.

Create the matrix to store the results:

SI <- matrix(nrow=time, ncol=2)
colnames(SI) <- c("S", "I")
SI[1,] <- c(S, I)


In this step, we create a matrix called "SI" to store the results of the simulation. The matrix has time rows and 2 columns, one for the number of susceptible individuals (S) and one for the number of infected individuals (I). We then give the columns descriptive names, "S" and "I", and initialize the first row of the matrix with the initial values of S and I.

Run the simulation:

for (i in 2:time) {
  S <- S - alpha * S * I / N
  I <- I + alpha * S * I / N
  SI[i,] <- c(S, I)
}


This is the main loop that runs the simulation. On each iteration of the loop, the number of susceptible individuals (S) decreases by alpha * S * I / N, and the number of infected individuals (I) increases by the same amount. These updated values of S and I are then stored in the matrix "SI". The loop continues for time iterations, updating the values of S and I on each iteration.

Plot the results:

plot(SI[,1], type="l", xlab="Time", ylab="Population", ylim=c(0,N),
     col="blue", xlim=c(0,time), main="Simple SI Model")
lines(SI[,2], type="l", col="red")
legend("topright", c("S", "I"), col=c("blue", "red"), lty=1:2)


Finally, we plot the results of the simulation. The plot() function creates the basic plot, with the number of susceptible individuals (S) plotted as a blue line. The lines() function adds the number of infected individuals (I) as a red line. The xlab and ylab arguments provide labels for the x and y axes, respectively, and the ylim and xlim arguments set the limits of the y and x axes. The main argument gives the plot a title. The legend() function adds a legend to the plot, indicating which line represents S and which represents I, with the color and line type specified by the col and lty arguments.
