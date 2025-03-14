import java.util.ArrayList;


// Base class: Aircraft
class Aircraft {
    protected String wings;


    public Aircraft() {
        this.wings = "Fixed wings";
    }


    @Override
    public String toString() {
        return "Aircraft with " + wings;
    }
}


// Child class: SingleEnginePlane
class SingleEnginePlane extends Aircraft {
    protected String engine;


    public SingleEnginePlane() {
        super();
        this.engine = "Rotary engine";
    }


    @Override
    public String toString() {
        return "SingleEnginePlane with " + wings + " and " + engine;
    }
}


// Grandchild class: Helicopter
class Helicopter extends SingleEnginePlane {
    protected String rotorBlades;


    public Helicopter() {
        super();
        this.rotorBlades = "Rotating helicopter blades";
    }


    @Override
    public String toString() {
        return "Helicopter with " + rotorBlades + ", " + engine + ", and no fixed wings";
    }
}


// Main class to test the hierarchy
public class ProjectMorphism {
    public static void main(String[] args) {
        // Create an ArrayList to store different types of Aircraft
        ArrayList<Aircraft> aircraftList = new ArrayList<>();


        // Add objects of different types
        aircraftList.add(new Aircraft());
        aircraftList.add(new SingleEnginePlane());
        aircraftList.add(new Helicopter());


        // Print each object
        for (Aircraft aircraft : aircraftList) {
            System.out.println(aircraft);
        }
    }
}


