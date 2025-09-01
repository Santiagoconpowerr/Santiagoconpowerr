import java.util.*;

public class GrafoMatriz {
    private List<String> vertices;
    private int[][] matrizAdyacencia;
    
    public GrafoMatriz() {
        vertices = new ArrayList<>();
    }
    
    public void agregarVertice(String vertice) {
        if (!vertices.contains(vertice)) {
            vertices.add(vertice);
            actualizarMatriz();
        }
    }
    
    private void actualizarMatriz() {
        int size = vertices.size();
        int[][] nuevaMatriz = new int[size][size];
        
        if (matrizAdyacencia != null) {
            for (int i = 0; i < matrizAdyacencia.length; i++) {
                for (int j = 0; j < matrizAdyacencia[i].length; j++) {
                    if (i < size && j < size) {
                        nuevaMatriz[i][j] = matrizAdyacencia[i][j];
                    }
                }
            }
        }
        matrizAdyacencia = nuevaMatriz;
    }
    
    public void agregarArista(String origen, String destino) {
        int idxOrigen = vertices.indexOf(origen);
        int idxDestino = vertices.indexOf(destino);
        
        if (idxOrigen == -1 || idxDestino == -1) {
            System.out.println("Error: Vértice no encontrado");
            return;
        }
        
        matrizAdyacencia[idxOrigen][idxDestino] = 1;
        matrizAdyacencia[idxDestino][idxOrigen] = 1; 
    }
    
    public void mostrarMatriz() {
        System.out.print("  ");
        for (String vertice : vertices) {
            System.out.print(vertice + " ");
        }
        System.out.println();
        
        for (int i = 0; i < matrizAdyacencia.length; i++) {
            System.out.print(vertices.get(i) + " ");
            for (int j = 0; j < matrizAdyacencia[i].length; j++) {
                System.out.print(matrizAdyacencia[i][j] + " ");
            }
            System.out.println();
        }
    }
    
    public static void main(String[] args) {
        GrafoMatriz grafo = new GrafoMatriz();
        
        
        grafo.agregarVertice("A");
        grafo.agregarVertice("B");
        grafo.agregarVertice("C");
        grafo.agregarVertice("D");
        
    
        grafo.agregarArista("A", "B");
        grafo.agregarArista("B", "C");
        grafo.agregarArista("C", "D");
        grafo.agregarArista("D", "A");
        
        
        System.out.println("Matriz de Adyacencia:");
        grafo.mostrarMatriz();
    }
}

<!--
**Santiagoconpowerr/Santiagoconpowerr** is a ✨ _special_ ✨ repository because its `README.md` (this file) appears on your GitHub profile.

Here are some ideas to get you started:

- 🔭 I’m currently working on ...
- 🌱 I’m currently learning ...
- 👯 I’m looking to collaborate on ...
- 🤔 I’m looking for help with ...
- 💬 Ask me about ...
- 📫 How to reach me: ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...
-->
