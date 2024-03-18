def calculate_solar_efficiency(area, efficiency, sun_hours, is_residential=True):
    """
    Calculate the potential benefits of solar panel implementation.

    Parameters:
    - area (float): Total area available for solar panels (in square meters)
    - efficiency (float): Efficiency of solar panels (as a decimal, e.g., 0.18 for 18%)
    - sun_hours (float): Average daily sunlight hours
    - is_residential (bool): True if the space is residential, False for commercial

    Returns:
    - daily_energy_production (float): Daily energy production (in kWh)
    - monthly_energy_production (float): Monthly energy production (in kWh)
    - yearly_energy_production (float): Yearly energy production (in kWh)
    - cost_savings_yearly (float): Estimated yearly cost savings from solar energy
    """

    if is_residential:
        energy_cost_per_kWh = 0.12  # Example residential energy cost per kWh
    else:
        energy_cost_per_kWh = 0.10  # Example commercial energy cost per kWh

    daily_energy_production = area * efficiency * sun_hours
    monthly_energy_production = daily_energy_production * 30  # Assuming 30 days in a month
    yearly_energy_production = daily_energy_production * 365  # Assuming 365 days in a year
    cost_savings_yearly = yearly_energy_production * energy_cost_per_kWh

    return daily_energy_production, monthly_energy_production, yearly_energy_production, cost_savings_yearly

def main():
    print("Welcome to Solar Efficiency Calculator App")
    print("------------------------------------------")

    space_type = input("Enter space type (residential/commercial): ").lower()
    area = float(input("Enter total area available for solar panels (in square meters): "))
    efficiency = float(input("Enter efficiency of solar panels (as a decimal, e.g., 0.18 for 18%): "))
    sun_hours = float(input("Enter average daily sunlight hours: "))

    is_residential = True if space_type == "residential" else False

    daily_production, monthly_production, yearly_production, cost_savings_yearly = calculate_solar_efficiency(area, efficiency, sun_hours, is_residential)

    print("\nSolar Panel Production Estimates:")
    print("--------------------------------")
    print(f"Daily production: {daily_production:.2f} kWh")
    print(f"Monthly production: {monthly_production:.2f} kWh")
    print(f"Yearly production: {yearly_production:.2f} kWh")

    if is_residential:
        print(f"\nEstimated yearly cost savings: ${cost_savings_yearly:.2f}")
    else:
        print(f"\nEstimated yearly cost savings: ${cost_savings_yearly:.2f} (commercial rates)")

if __name__ == "__main__":
    main()

