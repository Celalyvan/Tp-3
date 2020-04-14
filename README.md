# Tp-3

Ejercicio 1

#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

///ejercicio 1
void cargarPila(Pila * punteroPila);


int main()
{
    Pila pilita;
    inicpila(&pilita);

    cargarPila(&pilita);

    printf("Pila pilita cargada:\n");
    mostrar(&pilita);

    return 0;
}

void cargarPila(Pila * punteroPila)
{
    char control;

    do
    {
        leer(punteroPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

/////////////////////////////////////////////////////////////////////////////////////////////////

Ejercicio 2

#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila * punteroPila);
void pasarPila(Pila *pOrigen, Pila *pDestino);

int main()
{
    Pila pilita,pilota;
    inicpila(&pilita);
    inicpila(&pilota);


    cargarPila(&pilita);

    printf("Pila pilita cargada:\n");
    mostrar(&pilita);

    pasarPila(&pilita,&pilota);

    printf("pasamos elemento de pila a otra");
    mostrar(&pilota);
    return 0;
}

void cargarPila(Pila * punteroPila)
{
    char control='s';

    do
    {
        leer(punteroPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control=='s');

}
void pasarPila(Pila *pOrigen, Pila *pDestino)
{
    while(!pilavacia(pOrigen))
    {
        apilar(pDestino,desapilar(pOrigen));
    }
}

/////////////////////////////////////////////////////////////////////////////////////////////////

Ejercicio 3

#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila * pPila);
void acomodar(Pila *pOrigen, Pila *pDestino);
void intercalar (Pila *pOrigen, Pila *pOrigen2, Pila *pDestino);

int main()
{
    Pila pila1, pila2, aux, pilaFinal;
    inicpila(&pila1);
    inicpila(&pila2);
    inicpila(&aux);
    inicpila(&pilaFinal);

    printf("Ejercicio de intercalado\n");

    //printf("\n\n");

    printf("\nCargamos pila 1\n");
    cargarPila(&pila1);

    printf("\nCargamos pila 2\n");
    cargarPila(&pila2);

    mostrar(&pila1);
    mostrar(&pila2);

    printf("\nIntercalamos las pilas\n");
    intercalar(&pila1, &pila2, &aux);

    printf("\nOrdenamos en pila final\n");

    acomodar(&aux, &pilaFinal);
    mostrar(&pilaFinal);

    return 0;
}

void cargarPila(Pila * pPila)
{
    char control='s';

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control=='s');

}

void intercalar (Pila *pOrigen, Pila *pOrigen2, Pila *pDestino)
{
    while(!pilavacia(pOrigen))
    {
        apilar(pDestino, desapilar(pOrigen));

        if(!pilavacia(pOrigen2))
        {
            apilar(pDestino, desapilar(pOrigen2));
        }
    }

    if(!pilavacia(pOrigen2))
    {
        while(!pilavacia(pOrigen2))
        {
            apilar(pDestino, desapilar(pOrigen2));
        }

    }


    if(!pilavacia(pOrigen))
    {
        while(!pilavacia(pOrigen))
        {
            apilar(pDestino, desapilar(pOrigen));

        }
    }
}

void acomodar(Pila *pOrigen, Pila *pDestino)
{
    while(!pilavacia(pOrigen))
    {
        apilar(pDestino, desapilar(pOrigen));
    }
}

/////////////////////////////////////////////////////////////////////////////////////////////////

Ejercicio 4

#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila *cargar);
void buscaMenor(Pila *origen, Pila *menor, Pila *aux);

int main()
{
    Pila dada, menor, aux;

    inicpila(&dada);
    inicpila(&menor);
    inicpila(&aux);

    printf("Carguemos la pila!\n");
    cargarPila(&dada);

    printf("\nPila original:\n");
    mostrar(&dada);

    printf("\nBuscando el menor\n");
    buscaMenor(&dada, &menor, &aux);

    printf("\nPila Final:\n");
    mostrar(&dada);
    printf("\nEl menor elemento de su pila era %d", tope(&menor));

    return 0;
}

void cargarPila(Pila *cargar)
{
    char control;

    do
    {
        leer(cargar);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }while(control!='n');
}

void buscaMenor(Pila *origen, Pila *menor, Pila *aux)
{
  apilar(menor, desapilar(origen));

  while(!pilavacia(origen))
  {
      if(tope(origen)>tope(menor)){
        apilar(aux, desapilar(origen));
      } else{
        apilar(aux, desapilar(menor));
        apilar(menor, desapilar(origen));
      }

  }

  while(!pilavacia(aux)){
      apilar(origen, desapilar(aux));
  }
}

/////////////////////////////////////////////////////////////////////////////////////////////////

Ejercicio 5


#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila *cargar);
void intercalar(Pila *origen, Pila *destino);
void ordenamiento(Pila *pila, Pila *pFinal);

int main()
{
    Pila pila1, pila2, pilaFinal;

    inicpila(&pila1);
    inicpila(&pila2);
    inicpila(&pilaFinal);

    cargarPila(&pila1);
    printf("Pila 1: \n");
    mostrar(&pila1);

    cargarPila(&pila2);
    printf("\nPila 2: \n");
    mostrar(&pila2);

    intercalar(&pila1, &pila2);
    mostrar(&pila2);

    ordenamiento(&pila2, &pilaFinal);

    printf("\nPila Final: \n");
    mostrar(&pilaFinal);

    return 0;
}

void cargarPila(Pila * pPila)
{
    char control;

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

void intercalar(Pila *origen, Pila *destino)
{

    while(!pilavacia(origen))
    {
        apilar(destino, desapilar(origen));
    }

}

void ordenamiento(Pila *pila, Pila *pFinal)
{

    Pila aux, menor;
    inicpila(&aux);
    inicpila(&menor);



    while(!pilavacia(pila))
    {
        while(!pilavacia(pFinal) && tope(pFinal)<tope(pila)){

            apilar(&aux, desapilar(pFinal));
        }

        apilar(pFinal, desapilar(pila));

        while(!pilavacia(&aux)){
            apilar(pila, desapilar(&aux));
        }

    }

}

/////////////////////////////////////////////////////////////////////////////////////////////////


ejercicio 6


#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila *cargar);
void ordenarPila(Pila *original);
void insertarEnPila(Pila *original);
void mover(Pila *original, Pila *destino);

int main()
{
    Pila pila1;
    inicpila(&pila1);

    ///cargado de la pila
    cargarPila(&pila1);
    printf("Pila 1: \n");
    mostrar(&pila1);

    ///ordenar pila original
    ordenarPila(&pila1);
    mostrar(&pila1);

    ///insertar
    insertarEnPila(&pila1);

    ///muestro el valor final de la pila
    mostrar(&pila1);
    return 0;
}

void cargarPila(Pila * pPila)
{
    char control;

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

void ordenarPila(Pila *original)
{

    Pila aux, ordenada;

    inicpila(&ordenada);
    inicpila(&aux);

    while(!pilavacia(original))
    {

        while(!pilavacia(&ordenada) && tope(&ordenada)>tope(original)){
            apilar(&aux, desapilar(&ordenada));
        }

        apilar(&ordenada, desapilar(original));

        mover(&aux, original);
    }

    mover(&ordenada, &aux);

    mover(&aux, original);
}

void insertarEnPila(Pila *original)
{
    Pila aux, valorInsertar;

    inicpila(&aux);
    inicpila(&valorInsertar);

    printf("\nQué valor dessea insertar?\n");
    leer(&valorInsertar);

    while(!pilavacia(original) && tope(original)>tope(&valorInsertar))
    {
        apilar(&aux, desapilar(original));
    }

    mover(&valorInsertar, original);

    mover(&aux, original);
}

void mover(Pila *salida, Pila *llegada){
    while(!pilavacia(salida)){
        apilar(llegada, desapilar(salida));
    }
}

/////////////////////////////////////////////////////////////////////////////////////////////////

ejercicio 7


#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila *cargar);
void ordenarPila(Pila *original);
void insertarPilaEnPila(Pila *original, Pila *pFinal);
void mover(Pila *original, Pila *destino);

int main()
{
    Pila pila1, pila2;

    inicpila(&pila1);
    inicpila(&pila2);

    ///cargamos las pilas

    printf("cargamos Pila 1: \n");
    cargarPila(&pila1);
    printf("\Cargamos Pila 2: \n");
    cargarPila(&pila2);



    ///ordenamos las pilas

    ordenarPila(&pila1);
    ordenarPila(&pila2);

    printf("\Cargamos Pila 1: \n");
    mostrar(&pila1);
    printf("\Cargamos Pila 2: \n");
    mostrar(&pila2);

    ///intercalamos las pilas

    insertarPilaEnPila(&pila1, &pila2);
    printf("\Cargamos Pila 1: \n");
    mostrar(&pila1);
    printf("\Cargamos Pila 2: \n");
    mostrar(&pila2);

    return 0;
}

void cargarPila(Pila * pPila)
{
    char control;

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

void mover(Pila *salida, Pila *llegada){
    while(!pilavacia(salida)){
        apilar(llegada, desapilar(salida));
    }
}


void ordenarPila(Pila *original)
{

    Pila aux, ordenada;

    inicpila(&ordenada);
    inicpila(&aux);

    while(!pilavacia(original))
    {

        while(!pilavacia(&ordenada) && tope(&ordenada)>tope(original))
        {
            apilar(&aux, desapilar(&ordenada));
        }

        apilar(&ordenada, desapilar(original));

        mover(&aux, original);
    }

    mover(&ordenada, &aux);

    mover(&aux, original);
}

void insertarPilaEnPila(Pila *original, Pila *pFinal)
{
    Pila aux;

    inicpila(&aux);

    while(!pilavacia(original))
    {
        while(!pilavacia(original) && tope(pFinal)>tope(original))
        {
            apilar(&aux, desapilar(pFinal));
        }

        apilar(pFinal, desapilar(original));

        mover(&aux, pFinal);
    }
}

/////////////////////////////////////////////////////////////////////////////////////////////////

ejercicio 8


///Hacer una función que sume y retorne los dos primeros elementos de una pila (tope y anterior)
///sin alterar su contenido.

#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila *cargar);
int suma (Pila *pilita);
///int escanearElemento (Pila *pilita);
void mover(Pila *original, Pila *destino);

int main()
{
    Pila pila1;

    inicpila(&pila1);

    ///cargado de la pila
    cargarPila(&pila1);
    printf("Pila 1: \n");
    mostrar(&pila1);

    ///suma de los elementos
    printf("La suma de los dos primeros elementos es: %d", suma(&pila1));

    return 0;
}

void cargarPila(Pila * pPila)
{
    char control;

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

void mover(Pila *salida, Pila *llegada){
    while(!pilavacia(salida)){
        apilar(llegada, desapilar(salida));
    }
}

int suma (Pila *pilita){

Pila aux;

int a=0, b=0, c=0;
inicpila(&aux);

a=tope(pilita);

apilar(&aux, desapilar(pilita));
b=tope(pilita);

c= a+b;

return c;
}

/////////////////////////////////////////////////////////////////////////////////////////////////

Ejercicio 9


///Hacer una función que calcule el promedio de los elementos de una pila, para ello hacer también
///una función que calcule la suma, otra para la cuenta y otra que divida. En total son cuatro
///funciones, y la función que calcula el promedio invoca a las otras 3.
#include <stdio.h>
#include <stdlib.h>
#include "pila.h"

void cargarPila(Pila *cargar);
int contarPila(Pila *pila);
void mover(Pila *original, Pila *destino);
int acumuladorPila(Pila *pila);
float promedioPila (int cont, int acu);

int main()
{
    ///inicializar
    Pila pilita;

    inicpila(&pilita);
    int contador=0, acumulador=0;
    float promedio=0;

    ///cargar

    cargarPila(&pilita);


    ///contar

    contador = contarPila(&pilita);

    ///sumar

    acumulador = acumuladorPila(&pilita);

    ///promedio

    promedio= promedioPila(contador, acumulador);

    printf("\n el promedio de los elementos de la pila es de: %.02f \n\n", promedio);

    return 0;
}

void cargarPila(Pila * pPila)
{
    char control;

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

int contarPila(Pila *pila)
{
    Pila aux;

    inicpila(&aux);
    int i=0;

    while(!pilavacia(pila))
    {
        apilar(&aux, desapilar(pila));

        i++;
    }

    mover(&aux, pila);

    return i;
}


Ejercicio 10


#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include "pila.h"

void cargarPila(Pila *cargar);
int contarPila(Pila *pila);
void mover(Pila *original, Pila *destino);
int pila_a_decimal (Pila *pilota, int decimal);

int main()
{
    ///inicializo
    Pila pilita;

    inicpila(&pilita);
    int contador=0, numero=0;

    ///cargo la pila
    cargarPila(&pilita);

    ///contar elementos
    contador = contarPila(&pilita);

    ///pasar a decimal
    numero = pila_a_decimal (&pilita, contador);

    printf("\nPila pasada a decimal: %d\n\n", numero);

    return 0;
}

void cargarPila(Pila * pPila)
{
    char control;

    do
    {
        leer(pPila);

        printf("Desea continuar s/n\n");
        fflush(stdin);
        scanf("%c",&control);

    }
    while(control!='n');

}

int contarPila(Pila *pila)
{
    Pila aux;

    inicpila(&aux);
    int i=0;

    while(!pilavacia(pila))
    {
        apilar(&aux, desapilar(pila));

        i++;
    }

    mover(&aux, pila);

    return i;
}

void mover(Pila *salida, Pila *llegada)
{
    while(!pilavacia(salida))
    {
        apilar(llegada, desapilar(salida));
    }
}

int pila_a_decimal (Pila *pilota, int decimal)
{
    Pila aux;

    inicpila(&aux);
    int h=0;

    for(int i = decimal; i>0; i--)
    {
        h += tope(pilota)*(pow(10, i));
        apilar(&aux, desapilar(pilota));
        printf("\n%d\n", h);
    }
    mover(&aux, pilota);

    return h/10; /// tuve que dividirlo por 10 porque no lograba entender por que me lo multiplicaba por 10 una vez mas, y tampoco ///conseguia lograr que me lo multiplicara una vez menos por 10 sin dejar de contar un valor de la pila
}
