
package com.mycompany.exp2_s6_felipe_borbaran;

    import java.util.Scanner;
/*Exp2_S6_felipe_borbaran*/
public class TeatroMoro {

    // Variables estáticas - estadísticas globales

    static int totalEntradasVendidas = 0;
    static int totalReservas = 0;
    static int totalIngresos = 0;

    // Variables de instancia - información de entradas
    /*Al parecer no habia que utilizar Arrays, pero 
    estaba un poco apremiado con el tiempo de la entrega */
    String[] ubicaciones = new String[10];
    int[] precios = new int[10];
    boolean[] vendidas = new boolean[10];
    boolean[] reservadas = new boolean[10];

    // Constructor
    public TeatroMoro() {
        for (int i = 0; i < 10; i++) {
            ubicaciones[i] = "Asiento " + (i + 1);
            precios[i] = 5000; // Precio base
            vendidas[i] = false;
            reservadas[i] = false;
        }
    }

    // Menú principal
    public void mostrarMenu() {
        Scanner sc = new Scanner(System.in);
        int opcion;

        do {
            System.out.println("\n--- Bienvenido al Teatro Moro ---");
            System.out.println(" Porfavor indicanos que desas hacer \n");
            System.out.println("1. Reservar entrada");
            System.out.println("2. Comprar entrada");
            System.out.println("3. Modificar venta");
            System.out.println("4. Imprimir boleta");
            System.out.println("5. Salir");
            System.out.print("Seleccione una opción: \n");
            opcion = sc.nextInt();

            switch (opcion) {
                case 1:
                    reservarEntrada(sc);
                    break;
                case 2:
                    comprarEntrada(sc);
                    break;
                case 3:
                    modificarVenta(sc);
                    break;
                case 4:
                    imprimirBoleta(sc);
                    break;
                case 5:
                    System.out.println("Gracias por usar el sistema.");
                    break;
                default:
                    System.out.println("Opción no válida.");
            }
        } while (opcion != 5);
    }

    // Reservar entradas
    public void reservarEntrada(Scanner sc) {
        mostrarAsientos();
        System.out.print("Seleccione el número de asiento a reservar (1-10): ");
        int asiento = sc.nextInt() - 1;

        // Punto de depuración 1
        if (asiento >= 0 && asiento < 10) {
            if (!vendidas[asiento] && !reservadas[asiento]) {
                reservadas[asiento] = true;
                totalReservas++;
                System.out.println("Asiento reservado correctamente.");
            } else {
                System.out.println("Asiento no disponible.");
            }
        } else {
            System.out.println("Asiento inválido.");
        }
    }

    // Comprar entradas
    public void comprarEntrada(Scanner sc) {
        mostrarAsientos();
        System.out.print("Seleccione el número de asiento a comprar (1-10): ");
        int asiento = sc.nextInt() - 1;

        // Punto de depuración 2
        if (asiento >= 0 && asiento < 10) {
            if (!vendidas[asiento]) {
                vendidas[asiento] = true;
                if (reservadas[asiento]) {
                    reservadas[asiento] = false;
                    totalReservas--;
                }
                totalEntradasVendidas++;
                totalIngresos += precios[asiento];
                System.out.println("Compra realizada correctamente.");
            } else {
                System.out.println("Asiento ya vendido.");
            }
        } else {
            System.out.println("Asiento inválido.");
        }
    }

    // Modificar venta (permite cambiar asiento vendido)
    public void modificarVenta(Scanner sc) {
        System.out.print("Ingrese el número de asiento vendido que desea cambiar (1-10): ");
        int asientoActual = sc.nextInt() - 1;

        // Punto de depuración 3
        if (asientoActual >= 0 && asientoActual < 10 && vendidas[asientoActual]) {
            vendidas[asientoActual] = false;
            totalEntradasVendidas--;
            totalIngresos -= precios[asientoActual];

            System.out.print("Ingrese el nuevo número de asiento (1-10): ");
            int nuevoAsiento = sc.nextInt() - 1;

            if (nuevoAsiento >= 0 && nuevoAsiento < 10 && !vendidas[nuevoAsiento]) {
                vendidas[nuevoAsiento] = true;
                totalEntradasVendidas++;
                totalIngresos += precios[nuevoAsiento];
                System.out.println("Modificación realizada.");
            } else {
                System.out.println("Nuevo asiento no disponible.");
                vendidas[asientoActual] = true;
                totalEntradasVendidas++;
                totalIngresos += precios[asientoActual];
            }
        } else {
            System.out.println("Asiento inválido o no vendido.");
        }
    }

    // Imprimir boleta
    public void imprimirBoleta(Scanner sc) {
        System.out.print("Ingrese número de asiento comprado (1-10): ");
        int asiento = sc.nextInt() - 1;

        // Punto de depuración 4
        if (asiento >= 0 && asiento < 10 && vendidas[asiento]) {
            System.out.println("\n--- Boleta ---");
            System.out.println("Asiento: " + ubicaciones[asiento]);
            System.out.println("Precio: $" + precios[asiento]);
            System.out.println("Gracias por su compra.");
            System.out.println("Disfruta la función");

        } else {
            System.out.println("No se ha comprado ese asiento.");
        }
    }

    // Mostrar disponibilidad de asientos
    public void mostrarAsientos() {
        System.out.println("\nDisponibilidad de Asientos:");
        for (int i = 0; i < 10; i++) {
            String estado = vendidas[i] ? "VENDIDO" : (reservadas[i] ? "RESERVADO" : "DISPONIBLE");
            System.out.println((i + 1) + ". " + ubicaciones[i] + " - " + estado);
        }
    }

    // Main
    public static void main(String[] args) {
        TeatroMoro sistema = new TeatroMoro();
        sistema.mostrarMenu();
    }
}

   

