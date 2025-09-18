1. Un espacio en la memoria que cuenta con una dirección donde se alguna

```java

// Ejercicio 1
import java.util.ArrayList;

import java.util.Scanner;

  

public class App {

public static void main(String[] args) throws Exception {

Scanner sc = new Scanner(System.in);

  

// Valor de inicio por defecto

int numStart= 1;

  

// Valor de fin por defecto

int numEnd= 10;

  
  

// ArrayList con todos lo numeros pares encontrados.

ArrayList<Integer> numerosPares = new ArrayList<>();

  

System.out.println("Escribe numero de inicio");

numStart = sc.nextInt();

  

System.out.println("Escribe número de fin");

numEnd = sc.nextInt();

  

for(int i = numStart; i < numEnd ;i++){

if ( i % 2 == 0) {

numerosPares.add(i);

}

}

System.out.println("Numeros pares encontrados: ");

System.out.print(numerosPares);

  

}

}

```

```java

```