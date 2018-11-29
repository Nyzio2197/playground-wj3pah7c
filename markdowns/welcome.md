public class idealGas { 
    // derives all equations from:
    // (atmospheres) * (liters) = ((mass) / (molar mass)) * (R [constant equal to 0.082057]) * (kelvin) 

    private double pressure;                        // in atm
    private double volume;                          // in L
    private double mass;                            // in g
    private double molarMass;                       // in g mol^-1
    private final double R = 0.082057;              // in L atm mol^-1 K^-1
    private double temperature;                     // in K

    // new ideal gas
    public idealGas() {
        pressure = 1;
        volume = 22.4;
        mass = 12;
        molarMass = 12;
        temperature = 273.15;
    }

    // resets to default
    public void resetGas() {
        idealGas()

    // returns pressure
    public double pressure() {
        return pressure;
    }

    // returns volume
    public double volume() {
        return volume;
    }

    // returns mass
    public double mass() {
        return mass;
    }

    // returns molar mass
    public double molarMass() {
        return molarMass;
    }

    // returns moles
    public double moles() {
        return mass / molarMass;
    }

    // returns temperature
    public double temperature() {
        return temperature;
    }

    // sets pressure to x
    public void setPressure(double x) {
        pressure = x;
    }
    
    // sets volume to x
    public void setVolume(double x) {
        volume = x;
    }

    // sets mass to x
    public void setMass(double x) {
        mass = x;
    }

    // sets molar mass to x
    public void setMolarMass(double x) {
        molarMass = x;
    }

    // sets moles to x
    public void setMoles(double x) {
        mass *= x;
    }

    // set temperature to x
    public void setTemperature(double x) {
        temperature = x;
    }

    // calculates for pressure
    public double calculatePressure() {
        pressure = ((mass / molarMass) * R * temperature) / volume;
        return pressure;
    }

    // calculates for volume
    public double calculateVolume() {
        volume = ((mass / molarMass) * R * temperature) / pressure;
        return volume;
    }

    // calculates for mass
    public double calculateMass() {
        mass = ((pressure * volume) / (R * temperature)) * molarMass;
        return mass;
    }

    // calculates for molar mass
    public double calculateMolarMass() {
        molarMass = mass / ((pressure * volume) / (R * temperature));
        return molarMass;
    }

    // calculates for moles
    public double calculateMoles() {
        return ((pressure * volume) / (R * temperature));
    }

    // calculates for temperature
    public double calculateTemperature() {
        temperature = (pressure * volume) / ((mass / molarMass) * R);
        return temperature;
    }

    // converts to string
    public String toString() {
        return "Pressure: " + pressure + "\n" +
               "Volume: " + volume + "\n" +
               "Mass: " + mass + "\n" +
               "Molar Mass: " + molarMass + "\n" +
               "Moles: " + (mass / molarMass) + "\n" +
               "Temperature: " + temperature;
    }

    // compares for equality
    public boolean equals(Object o) {
        if( o instanceof idealGas) {
            O = (idealGas) o;
            if(O.pressure() == pressure &&
               O.volume() == volume &&
               O.mass() == mass &&
               O.molarMas() == molarMass &&
               O.temperature() == temperature) {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    }
}
