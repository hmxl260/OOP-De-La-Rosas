package delarosasfloraindex;
import java.io.*;
import java.util.*;
import java.util.regex.*;

public class DeLaRosasFloraIndex {
    private static final String FILE_NAME = "DeLaRosas.txt";
    private static final String SEPARATOR = "----------------------------------------------------";
    private List<Flower> flowers;
    
    public DeLaRosasFloraIndex() {
        flowers = new ArrayList<>();
        loadFlowersFromFile();
    }
    
    public static void main(String[] args) {
        DeLaRosasFloraIndex program = new DeLaRosasFloraIndex();
        program.run();
    }
    
    public void run() {
        Scanner scanner = new Scanner(System.in);
        
        while (true) {
            displayMenu();
            System.out.print("\nChoose an option (1-7): ");
            String choice = scanner.nextLine().trim();
            
            switch (choice) {
                case "1":
                    searchByName(scanner);
                    break;
                case "2":
                    listAllFlowers();
                    break;
                case "3":
                    flowerIdentifier(scanner);
                    break;
                case "4":
                    identifyFloriographyByName(scanner);
                    break;
                case "5":
                    keywordSearchFloriography(scanner);
                    break;
                case "6":
                    addNewFlowerEntry(scanner);
                    break;
                case "7":
                    System.out.println("Thank you for usnig De La Rosas - Flora Index!");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid option. Please try again.");
            }
            
            System.out.println("\nPress Enter to continue...");
            scanner.nextLine();
        }
    }
    
    private void displayMenu() {
        System.out.println("\n" + SEPARATOR);
        System.out.println("De La Rosas - Flora Index");
        System.out.println(SEPARATOR);
        
        System.out.println("\nFlower Index (Options):");
        System.out.println("  1. [Search by Name]");
        System.out.println("  2. [List all flowers]");
        
        System.out.println("\nFlower Identifier: (Type \"-\" to leave blank)");
        System.out.println("  3. [Search by Attriubtes:]");
        System.out.println("  - [Flower Color/s:]");
        System.out.println("  - [Petal Count/s:]");
        System.out.println("  - [Petal Shape/s:]");
        System.out.println("  - [Height:]");
        System.out.println("  - [Stem Type:]");
        System.out.println("  - [Root Type:]");
        System.out.println("  - [Texture:]");
        
        System.out.println("\nFloriography Identifier (Options):");
        System.out.println("  4. [Identify by Name]");
        System.out.println("  5. [Keyword search by Floriography]");
        
        System.out.println("\nAdd New Flower Entry:");
        System.out.println("  6. [(Fill in the Flower Entry Format)]");
        System.out.println("  7. [Exit]");
    }
    
    static class Flower {
        String commonName;
        String scientificName;
        String cultivar;
        String family;
        String genus;
        String species;
        String floriography;
        String etymology;
        String flowerColors;
        String petalCounts;
        String petalShapes;
        String fragrance;
        String height;
        String stemType;
        String rootType;
        String bloomShape;
        String texture;
        String bloomCalendar;
        String seasonalConditions;
        String naturalHabitat;
        
        @Override
        public String toString() {
            StringBuilder sb = new StringBuilder();
            sb.append(SEPARATOR).append("\n");
            sb.append("[Flower Name:]\n");
            sb.append("    @ Common Name: ").append(commonName).append("\n");
            sb.append("    @ Scientific Name: ").append(scientificName).append("\n");
            sb.append("    @ Cultivar: ").append(cultivar).append("\n");
            sb.append("    @ ----\n");
            sb.append("    @ Family: ").append(family).append("\n");
            sb.append("    @ Genus: ").append(genus).append("\n");
            sb.append("    @ Species: ").append(species).append("\n");
            sb.append("    @ ----\n");
            sb.append("    @ Floriography: ").append(floriography).append("\n");
            sb.append("    @ Etymology: ").append(etymology).append("\n");
            sb.append("    @ ----\n");
            sb.append("    @ Flower Color/s: ").append(flowerColors).append("\n");
            sb.append("    @ Petal Count/s: ").append(petalCounts).append("\n");
            sb.append("    @ Petal Shape/s: ").append(petalShapes).append("\n");
            sb.append("    @ Fragrance: ").append(fragrance).append("\n");
            sb.append("    @ Height: ").append(height).append("\n");
            sb.append("    @ Stem Type: ").append(stemType).append("\n");
            sb.append("    @ Root Type: ").append(rootType).append("\n");
            sb.append("    @ Bloom Shape: ").append(bloomShape).append("\n");
            sb.append("    @ Texture: ").append(texture).append("\n");
            sb.append("    @ ----\n");
            sb.append("    @ Bloom Calendar: ").append(bloomCalendar).append("\n");
            sb.append("    @ Seasonal Conditions: ").append(seasonalConditions).append("\n");
            sb.append("    @ Natural Habitat: ").append(naturalHabitat).append("\n");
            sb.append(SEPARATOR);
            return sb.toString();
        }
    }
    
    private void loadFlowersFromFile() {
        flowers.clear();
        try (BufferedReader reader = new BufferedReader(new FileReader(FILE_NAME))) {
            String line;
            Flower currentFlower = null;
            
            while ((line = reader.readLine()) != null) {
                if (line.equals(SEPARATOR)) {
                    if (currentFlower != null) {
                        flowers.add(currentFlower);
                        currentFlower = null;
                    }
                    continue;
                }
                
                if (line.equals("[Flower Name:]")) {
                    currentFlower = new Flower();
                    continue;
                }
                
                if (currentFlower != null && line.startsWith("    @ ")) {
                    parseFlowerAttribute(line.substring(6), currentFlower);
                }
            }
            
            if (currentFlower != null) {
                flowers.add(currentFlower);
            }
            
        } catch (FileNotFoundException e) {
            System.out.println("Database file not found. Creating new file...");
 
        } catch (IOException e) {
            System.out.println("Error reading file: " + e.getMessage());
        }
    }
    
    private void parseFlowerAttribute(String line, Flower flower) {
        if (line.startsWith("Common Name: ")) {
            flower.commonName = line.substring(13);
        } else if (line.startsWith("Scientific Name: ")) {
            flower.scientificName = line.substring(17);
        } else if (line.startsWith("Cultivar: ")) {
            flower.cultivar = line.substring(10);
        } else if (line.startsWith("Family: ")) {
            flower.family = line.substring(8);
        } else if (line.startsWith("Genus: ")) {
            flower.genus = line.substring(7);
        } else if (line.startsWith("Species: ")) {
            flower.species = line.substring(9);
        } else if (line.startsWith("Floriography: ")) {
            flower.floriography = line.substring(14);
        } else if (line.startsWith("Etymology: ")) {
            flower.etymology = line.substring(11);
        } else if (line.startsWith("Flower Color/s: ")) {
            flower.flowerColors = line.substring(16);
        } else if (line.startsWith("Petal Count/s: ")) {
            flower.petalCounts = line.substring(15);
        } else if (line.startsWith("Petal Shape/s: ")) {
            flower.petalShapes = line.substring(15);
        } else if (line.startsWith("Fragrance: ")) {
            flower.fragrance = line.substring(11);
        } else if (line.startsWith("Height: ")) {
            flower.height = line.substring(8);
        } else if (line.startsWith("Stem Type: ")) {
            flower.stemType = line.substring(11);
        } else if (line.startsWith("Root Type: ")) {
            flower.rootType = line.substring(11);
        } else if (line.startsWith("Bloom Shape: ")) {
            flower.bloomShape = line.substring(13);
        } else if (line.startsWith("Texture: ")) {
            flower.texture = line.substring(9);
        } else if (line.startsWith("Bloom Calendar: ")) {
            flower.bloomCalendar = line.substring(16);
        } else if (line.startsWith("Seasonal Conditions: ")) {
            flower.seasonalConditions = line.substring(21);
        } else if (line.startsWith("Natural Habitat: ")) {
            flower.naturalHabitat = line.substring(17);
        }
    }
    
    private void searchByName(Scanner scanner) {
        System.out.print("Enter flower name to search: ");
        String searchTerm = scanner.nextLine().trim().toLowerCase();
        
        List<Flower> matches = new ArrayList<>();
        for (Flower flower : flowers) {
            if (flower.commonName.toLowerCase().contains(searchTerm) || 
                flower.scientificName.toLowerCase().contains(searchTerm)) {
                matches.add(flower);
            }
        }
        
        displayFlowersInTable(matches, "Search Results for: " + searchTerm);
    }
    
    private void listAllFlowers() {
        displayFlowersInTable(flowers, "All Flowers");
    }
    
    private void flowerIdentifier(Scanner scanner) {
        System.out.println("Enter flower characteristics (type '-' to skip):");
        
        System.out.print("Flower Color/s: ");
        String color = scanner.nextLine().trim();
        
        System.out.print("Petal Count/s: ");
        String petalCount = scanner.nextLine().trim();
        
        System.out.print("Petal Shape/s: ");
        String petalShape = scanner.nextLine().trim();
        
        System.out.print("Height: ");
        String height = scanner.nextLine().trim();
        
        System.out.print("Stem Type: ");
        String stemType = scanner.nextLine().trim();
        
        System.out.print("Root Type: ");
        String rootType = scanner.nextLine().trim();
        
        System.out.print("Texture: ");
        String texture = scanner.nextLine().trim();
        
        List<Flower> matches = new ArrayList<>();
        for (Flower flower : flowers) {
            if (matchesFilter(flower, color, petalCount, petalShape, height, stemType, rootType, texture)) {
                matches.add(flower);
            }
        }
        
        displayFlowersInTable(matches, "Flower Identification Results");
    }
    
    private boolean matchesFilter(Flower flower, String color, String petalCount, String petalShape, 
                                 String height, String stemType, String rootType, String texture) {
        if (!color.equals("-") && !color.isEmpty() && 
            !flower.flowerColors.toLowerCase().contains(color.toLowerCase())) {
            return false;
        }
        if (!petalCount.equals("-") && !petalCount.isEmpty() && 
            !flower.petalCounts.toLowerCase().contains(petalCount.toLowerCase())) {
            return false;
        }
        if (!petalShape.equals("-") && !petalShape.isEmpty() && 
            !flower.petalShapes.toLowerCase().contains(petalShape.toLowerCase())) {
            return false;
        }
        if (!height.equals("-") && !height.isEmpty() && 
            !flower.height.toLowerCase().contains(height.toLowerCase())) {
            return false;
        }
        if (!stemType.equals("-") && !stemType.isEmpty() && 
            !flower.stemType.toLowerCase().contains(stemType.toLowerCase())) {
            return false;
        }
        if (!rootType.equals("-") && !rootType.isEmpty() && 
            !flower.rootType.toLowerCase().contains(rootType.toLowerCase())) {
            return false;
        }
        if (!texture.equals("-") && !texture.isEmpty() && 
            !flower.texture.toLowerCase().contains(texture.toLowerCase())) {
            return false;
        }
        return true;
    }
    
    private void identifyFloriographyByName(Scanner scanner) {
        System.out.print("Enter flower name: ");
        String name = scanner.nextLine().trim().toLowerCase();
        
        for (Flower flower : flowers) {
            if (flower.commonName.toLowerCase().contains(name) || 
                flower.scientificName.toLowerCase().contains(name)) {
                System.out.println("\nFloriography for " + flower.commonName + ":");
                System.out.println(flower.floriography);
                return;
            }
        }
        System.out.println("Flower not found.");
    }
    
    private void keywordSearchFloriography(Scanner scanner) {
        System.out.print("Enter keyword to search in floriography: ");
        String keyword = scanner.nextLine().trim().toLowerCase();
        
        List<Flower> matches = new ArrayList<>();
        for (Flower flower : flowers) {
            if (flower.floriography.toLowerCase().contains(keyword)) {
                matches.add(flower);
            }
        }
        
        displayFloriographyResults(matches, keyword);
    }
    
    private void addNewFlowerEntry(Scanner scanner) {
        Flower newFlower = new Flower();
        
        System.out.println("Enter new flower details (type '-' to leave blank):");
        System.out.println(SEPARATOR);
        System.out.println("[Flower Name:]");
        
        System.out.print("    @ Common Name: ");
        newFlower.commonName = scanner.nextLine().trim();
        
        System.out.print("    @ Scientific Name: ");
        newFlower.scientificName = scanner.nextLine().trim();
        
        System.out.print("    @ Cultivar: ");
        newFlower.cultivar = scanner.nextLine().trim();
        
        System.out.println("    @ ----");
        
        System.out.print("    @ Family: ");
        newFlower.family = scanner.nextLine().trim();
        
        System.out.print("    @ Genus: ");
        newFlower.genus = scanner.nextLine().trim();
        
        System.out.print("    @ Species: ");
        newFlower.species = scanner.nextLine().trim();
        
        System.out.println("    @ ----");
        
        System.out.print("    @ Floriography: ");
        newFlower.floriography = scanner.nextLine().trim();
        
        System.out.print("    @ Etymology: ");
        newFlower.etymology = scanner.nextLine().trim();
        
        System.out.println("    @ ----");
        
        System.out.print("    @ Flower Color/s: ");
        newFlower.flowerColors = scanner.nextLine().trim();
        
        System.out.print("    @ Petal Count/s: ");
        newFlower.petalCounts = scanner.nextLine().trim();
        
        System.out.print("    @ Petal Shape/s: ");
        newFlower.petalShapes = scanner.nextLine().trim();
        
        System.out.print("    @ Fragrance: ");
        newFlower.fragrance = scanner.nextLine().trim();
        
        System.out.print("    @ Height: ");
        newFlower.height = scanner.nextLine().trim();
        
        System.out.print("    @ Stem Type: ");
        newFlower.stemType = scanner.nextLine().trim();
        
        System.out.print("    @ Root Type: ");
        newFlower.rootType = scanner.nextLine().trim();
        
        System.out.print("    @ Bloom Shape: ");
        newFlower.bloomShape = scanner.nextLine().trim();
        
        System.out.print("    @ Texture: ");
        newFlower.texture = scanner.nextLine().trim();
        
        System.out.println("    @ ----");
        
        System.out.print("    @ Bloom Calendar: ");
        newFlower.bloomCalendar = scanner.nextLine().trim();
        
        System.out.print("    @ Seasonal Conditions: ");
        newFlower.seasonalConditions = scanner.nextLine().trim();
        
        System.out.print("    @ Natural Habitat: ");
        newFlower.naturalHabitat = scanner.nextLine().trim();
        
        saveFlowerToFile(newFlower);
        flowers.add(newFlower);
        
        System.out.println("Flower entry added successfully!");
    }
    
    private void saveFlowerToFile(Flower flower) {
        try (FileWriter writer = new FileWriter(FILE_NAME, true)) {
            writer.write(flower.toString());
            writer.write("\n");
        } catch (IOException e) {
            System.out.println("Error saving flower to file: " + e.getMessage());
        }
    }
    
    private void displayFlowersInTable(List<Flower> flowerList, String title) {
        if (flowerList.isEmpty()) {
            System.out.println("No flowers found.");
            return;
        }
        
        System.out.println("\n" + SEPARATOR);
        System.out.println(title);
        System.out.println(SEPARATOR);
        
        System.out.printf("%-20s %-25s %-15s %-12s %-15s%n", 
            "Common Name", "Scientific Name", "Color", "Height", "Bloom Calendar");
        System.out.println(SEPARATOR);
        
        for (Flower flower : flowerList) {
            String commonName = truncate(flower.commonName, 18);
            String scientificName = truncate(flower.scientificName, 23);
            String color = truncate(flower.flowerColors, 13);
            String height = truncate(flower.height, 10);
            String bloomCalendar = truncate(flower.bloomCalendar, 13);
            
            System.out.printf("%-20s %-25s %-15s %-12s %-15s%n", 
                commonName, scientificName, color, height, bloomCalendar);
        }
        System.out.println(SEPARATOR);
        System.out.println("Total flowers: " + flowerList.size());
    }
    
    private void displayFloriographyResults(List<Flower> flowerList, String keyword) {
        if (flowerList.isEmpty()) {
            System.out.println("No flowers found with keyword '" + keyword + "' in floriography.");
            return;
        }
        
        System.out.println("\n" + SEPARATOR);
        System.out.println("Floriography Search Results for: " + keyword);
        System.out.println(SEPARATOR);
        
        for (Flower flower : flowerList) {
            System.out.printf("%-20s: %s%n", flower.commonName, truncate(flower.floriography, 50));
        }
        System.out.println(SEPARATOR);
    }
    
    private String truncate(String text, int length) {
        if (text == null) return "";
        if (text.length() <= length) return text;
        return text.substring(0, length - 3) + "...";
    }
}
