# Avanced-Programming
#include <fstream>
#include <iomanip>
#include <iostream>
#include <math.h>
#include <sstream>

//Hecho por: Juan Martín Sánchez - Juan Tellez - Juan Esteban Valencia - Santiago Martínez - Nicolás Álvarez//

using namespace std;

struct Aula {
    float aula1[20];
    float aula2[20];
};

Aula leerDatosDesdeArchivo(const string &rutaArchivo) {
    Aula miAula;
    ifstream archivo(rutaArchivo);
    string linea;
    int i = 0;

    getline(archivo, linea);

    while (getline(archivo, linea)) {
        istringstream ss(linea);
        string valor;

        getline(ss, valor, ',');
        miAula.aula1[i] = stof(valor);

        getline(ss, valor, ',');
        miAula.aula2[i] = stof(valor);
        i++;
    }
    archivo.close();
    return miAula;
}

void ordenarDatos(float datos[], int tamano) {
    for(int i = 0; i < tamano - 1; i++) {
        for(int j = 0; j < tamano - i - 1; j++) {
            if(datos[j] > datos[j + 1]) {
                float temp = datos[j];
                datos[j] = datos[j + 1];
                datos[j + 1] = temp;
            }
        }
    }
}

int calcularNumIntervalos(int tamano) {
    return ceil(1 + 3.3 * log10(tamano));
}

float calcularAnchoIntervalo(float rango, int numIntervalos) {
    return rango / numIntervalos;
}

void crearTablaFrecuencias(float datos[], int tamano, int numIntervalos, float anchoIntervalo) {
    int frecuencia[numIntervalos] = {0};
    float limiteInferior = datos[0];
    int indiceFrecuencia = 0;

    cout<<"Intervalo | ni | Ni | fi | Fi"<<endl;

    for(int i = 0; i < tamano; i++) {
        if(datos[i] >= limiteInferior+anchoIntervalo) {
            cout<<fixed<<setprecision(2)<<"["<< limiteInferior<<", "<<limiteInferior + anchoIntervalo<<") | "
                <<frecuencia[indiceFrecuencia]<<" | "<<i<<" | "
                <<fixed<<setprecision(4)<<(static_cast<float>(frecuencia[indiceFrecuencia]) / tamano)<<" | "
                <<(static_cast<float>(i) / tamano)<< endl;

            limiteInferior += anchoIntervalo;
            indiceFrecuencia++;
        }
        frecuencia[indiceFrecuencia]++;
    }

    cout<<fixed<<setprecision(2)<<"["<<limiteInferior<<", "<<limiteInferior + anchoIntervalo<<") | "
        <<frecuencia[indiceFrecuencia]<<" | "<<tamano<<" | "
        <<fixed<<setprecision(4)<<(static_cast<float>(frecuencia[indiceFrecuencia]) / tamano)<<" | "
        <<(static_cast<float>(tamano) / tamano)<<endl;
}

float calcularRango(float datos[], int tamano) {
    return datos[tamano - 1] - datos[0];
}

void imprimirHistograma(float datos[], int tamano, int numIntervalos, float anchoIntervalo) {
    int frecuencia[numIntervalos] = {0};
    float limiteInferior = datos[0];
    int indiceFrecuencia = 0;

    cout<<"Histograma:"<<endl;

    for(int i = 0; i < tamano; i++) {
        if(datos[i] >= limiteInferior + anchoIntervalo) {
            cout<<fixed<<setprecision(2)<<"["<<limiteInferior<<", "<<limiteInferior + anchoIntervalo<<") | ";
            for(int j = 0; j < frecuencia[indiceFrecuencia]; j++) {
                cout<<"*";
            }
            cout<<endl;

            limiteInferior += anchoIntervalo;
            indiceFrecuencia++;
        }
        frecuencia[indiceFrecuencia]++;
    }

    
    cout<<fixed<<setprecision(2)<<"["<<limiteInferior<<", "<<limiteInferior+anchoIntervalo<<") | ";
    for(int j = 0; j < frecuencia[indiceFrecuencia]; j++) {
        cout<<"*";
    }
    cout<<endl;
}

int main() {
    Aula miAula = leerDatosDesdeArchivo("estaturas.csv");

    int tamanoTotal = 20;
    int numIntervalos = calcularNumIntervalos(tamanoTotal);
    float datosTotales[tamanoTotal * 2]; // Se multiplicó por 2 ya que se unirán los dos conjuntos de datos

    // Unir los dos conjuntos de datos para obtener un solo arreglo
    for (int i = 0; i < 20; i++) {
        datosTotales[i] = miAula.aula1[i];
        datosTotales[20 + i] = miAula.aula2[i];
    }

    float rango = calcularRango(datosTotales, tamanoTotal * 2);
    float anchoIntervalo = calcularAnchoIntervalo(rango, numIntervalos);

    cout<<"Aula 1:"<< endl;
    ordenarDatos(miAula.aula1, tamanoTotal);
    crearTablaFrecuencias(miAula.aula1, tamanoTotal, numIntervalos, anchoIntervalo);
    imprimirHistograma(miAula.aula1, tamanoTotal, numIntervalos, anchoIntervalo);

    cout<<"Aula 2:"<<endl;
    ordenarDatos(miAula.aula2, tamanoTotal);
    crearTablaFrecuencias(miAula.aula2, tamanoTotal, numIntervalos, anchoIntervalo);
    imprimirHistograma(miAula.aula2, tamanoTotal, numIntervalos, anchoIntervalo);

    return 0;
}