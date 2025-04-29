# AmmoniaAvengers
Machine Learning and ode function for the optimization for the synthesis of ammonia
import pandas as pd
import matplotlib.pyplot as plt

# Load the Excel file
file_path = "Machinemodel_ammonia.xlsx"  # Make sure it's in the same directory as your notebook
df = pd.read_excel(file_path, skiprows=1)
df = df.iloc[:, 1:]
# Display the first few rows of the dataframe
print(df.head())
# Convert pressure to numeric (if necessary)
df['P(atm)'] = pd.to_numeric(df['P(atm)'], errors='coerce')

# Plot: Temperature vs % NH3, color-coded by Pressure
plt.figure(figsize=(10, 7))
scatter = plt.scatter(
    df['T (C)'],
    df['% NH3 in effluent (exp)'],
    c=df['P(atm)'],
    cmap='viridis',
    s=100,
    edgecolor='black'
)

# Add colorbar
cbar = plt.colorbar(scatter)
cbar.set_label('Pressure (atm)')

# Axis labels and title
plt.xlabel('Temperature (°C)')
plt.ylabel('% NH₃ in Effluent (Experimental)')
plt.title('NH₃ Effluent vs Temperature (Color-coded by Pressure)')
plt.grid(True)
plt.tight_layout()
plt.show()
