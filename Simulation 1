import numpy as np
import matplotlib.pyplot as plt
import scipy.stats as stats

def monte_carlo_simulation(n_collisions=1000, n_particles=10000, step_size=1.0):
    """
    Simulate the net displacement of particles undergoing n_collisions.
    Each collision results in a displacement of +step_size or -step_size with equal probability.
    
    Parameters:
        n_collisions (int): The number of collisions (steps) each particle experiences.
        n_particles (int): The number of particles to simulate.
        step_size (float): The displacement per collision.
    
    Returns:
        np.array: An array of net displacements for each particle.
    """
    outcomes = np.random.choice([-step_size, step_size], size=(n_particles, n_collisions))
    displacements = outcomes.sum(axis=1)
    return displacements

def analyze_and_plot(displacements, n_collisions, step_size):
    """
    Analyze the net displacement data and compare it with the theoretical Gaussian distribution.
    
    Parameters:
        displacements (np.array): The net displacement of each particle.
        n_collisions (int): The number of collisions (steps).
        step_size (float): The displacement per collision.
    """
    empirical_mean = np.mean(displacements)
    empirical_std = np.std(displacements)
    theoretical_std = np.sqrt(n_collisions) * step_size
    
    print(f"Empirical Mean: {empirical_mean:.4f}")
    print(f"Empirical Standard Deviation: {empirical_std:.4f}")
    print(f"Theoretical Standard Deviation: {theoretical_std:.4f}")
    
    plt.figure(figsize=(8, 6))
    plt.hist(displacements, bins=50, density=True, alpha=0.6, color='g', label='Simulated Data')
    
    xmin, xmax = plt.xlim()
    x = np.linspace(xmin, xmax, 100)
    p = stats.norm.pdf(x, 0, theoretical_std)
    
    plt.plot(x, p, 'k', linewidth=2, label='Theoretical Normal PDF')
    plt.xlabel("Net Displacement")
    plt.ylabel("Probability Density")
    plt.title("Monte Carlo Simulation of Particle Collisions")
    plt.legend()
    plt.show()

# Simulation Parameters
n_collisions = 1000   # Number of collisions per particle
n_particles = 10000   # Number of particles to simulate
step_size = 1.0       # Displacement per collision

# Run Simulation
displacements = monte_carlo_simulation(n_collisions, n_particles, step_size)

# Analyze and Plot Results
analyze_and_plot(displacements, n_collisions, step_size)
