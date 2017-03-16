#Tarea 5

Se entrega el lunes 27 de marzo. De forma individual crear una carpeta con nombre igual a su clave única, debajo del nivel: 

```
analisis-numerico-computo-cientifico/MNO/entrega_tareas_de_C/tarea5
```

Considera el programa formado por los archivos:

`definiciones.h` :

```
#define NUM_REN_MAT1 3
#define NUM_COL_MAT1 2
#define NUM_REN_MAT2 2
#define NUM_COL_MAT2 3 
void imprime_matrices(void);
void imprime_matriz_resultado(void);
void multiplica_matrices(void);
```

`funciones.c`:

```
#include<stdio.h>
#include<stdlib.h>
#include"definiciones.h"
//definiciones de variables que serán externas
static int i=0,j=0, k=0;
static double matriz1[NUM_REN_MAT1][NUM_COL_MAT1]={
        {0, 1.5},
        {4, -5},
        {-1, 2.5}
    };
static double matriz2[NUM_REN_MAT2][NUM_COL_MAT2]={
        {1, 0, 0},
        {0, -1, 1}
    };
static double matriz_resultado[NUM_REN_MAT1][NUM_COL_MAT2];

void imprime_matrices(void){
	printf("Matriz1\n");
		for(i=0;i<NUM_REN_MAT1;i++){ //el nombre: NUM_REN_MAT1 está definido en "definiciones.h"
			for(j=0;j<NUM_COL_MAT1;j++){
				if(j<NUM_COL_MAT1-1)
				printf("matriz1[%d][%d]=%4.2f\t",i,j,matriz1[i][j]);
				else
				printf("matriz1[%d][%d]=%4.2f\n",i,j,matriz1[i][j]);
			}
		}
	printf("\n");
	printf("Matriz2\n");
		for(i=0;i<NUM_REN_MAT2;i++){
			for(j=0;j<NUM_COL_MAT2;j++){
				if(j<NUM_COL_MAT2-1)
				printf("matriz2[%d][%d]=%4.2f\t",i,j,matriz2[i][j]);
				else
				printf("matriz2[%d][%d]=%4.2f\n",i,j,matriz2[i][j]);
			}
		}
	printf("\n");
}

void imprime_matriz_resultado(void){
	printf("Matriz resultado\n");
		for(i=0;i<NUM_REN_MAT1;i++){
			for(j=0;j<NUM_COL_MAT2;j++){
				if(j<NUM_COL_MAT2-1)
				printf("matriz_res[%d][%d]=%4.2f\t",i,j,matriz_resultado[i][j]);
				else
				printf("matriz_res[%d][%d]=%4.2f\n",i,j,matriz_resultado[i][j]);
			}
		}

	printf("\n");

}

void multiplica_matrices(void){
	for(i=0;i<NUM_REN_MAT1;i++){
		for(k=0;k<NUM_COL_MAT2;k++){
	 		matriz_resultado[i][k]=0;
 			for(j=0;j<NUM_COL_MAT1;j++)
  				matriz_resultado[i][k]=matriz_resultado[i][k]+matriz1[i][j]*matriz2[j][k];
		}
	}
}

```

`main.c`:

```
#include"definiciones.h"
int main(void){
    imprime_matrices();
    multiplica_matrices();
    imprime_matriz_resultado();
return 0;
}
```

Compila teniendo los tres archivos en una carpeta con la línea:

```
$gcc main.c funciones.c -o programa.out
```

Observa los resultados al ejecutar el `programa.out` y realiza lo siguiente:

a) Investiga por qué se usan `""` en la línea que tiene `include` en `main.c` y en `funciones.c` en lugar de usar `< >`.

b) Modifica el archivo `funciones.c` para que inicialices a las matrices `matriz1`, `matriz2` y `matriz_resultado` con `malloc` y modifica `main.c` para que llame a una función dentro del archivo `funciones.c` que inicialice y aloje a las matrices anteriores y llame a otra función para que las desaloje una vez hecha la multiplicación: 

```
#include"definiciones.h"
int main(void){
    aloja_espacio_e_incializa_matrices();
    imprime_matrices();
    multiplica_matrices();
    imprime_matriz_resultado();
    libera_espacio();
return 0;
}

```



