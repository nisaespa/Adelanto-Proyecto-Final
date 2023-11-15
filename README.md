# 🔥 INDUSPLAYTHON - ADELANTO PROYECTO FINAL 🔥
*Nicolas Estupiñan* - 
*Santiago Avendaño*
## 👽 Logo IndusPlaython 👽
<div align='center'>
<figure> <img src="https://raw.githubusercontent.com/nisaespa/Taller1/main/logoindusplaython.png" alt="" width="900" height="auto"/></br>
<figcaption><b></b></figcaption></figure>
</div>

# 🕹️ SALÓN DE JUEGOS INDUSPLAYTHON 🕹️

### 🔥 Nuestra definición de alternativa fue unir 3 juegos en un salón de juegos, es decir, que el jugador cuando inicie el programa de python, podrá entrar a uno de los 3 juegos, que son el ahorcado, piedra, papel o tijera y sopa de letras.
### 🔥 En donde el juego iniciará dando una bienbenida, y dando una explicación corta de como funciona cada juego, para que luego el usuario seleccione el juego que quiera jugar.
## 🎮AHORCADO🎮

<div align='center'>
<figure> <img src="https://raw.githubusercontent.com/nisaespa/Adelanto-Proyecto-Final/main/Imagenes_adelanto/ahorcado.png" alt="" width="500" height="auto"/></br>
<figcaption><b></b></figcaption></figure>
</div>

### 🔥 En el juego del ahorcado el jugador podrá escoger la dificultad que desee, entre fácil, medio y difcil, entre más facil tendrá más intentos y las palabras serán más cortas. Funciona de tal manera en que hay 3 listas, cada lista por nivel de dificultad, con su hangman respectivo con número de intentos. Cuando el jugador elija el nivel de dificultad, el programa seleccione aleatoriamente una palabra de la lista, la cual expresa con guion bajo "_" el número de letras que tenga la palabra, es decir, si la palabra fuera gato sería _ _ _ _ . Entonces cuando ya se muestra la cantidad de guiones bajos el jugador escribirá las letras con las que intentará adivinar la palabra, esas letras se iran almacenando en otra lista, que funciona para que el jugador no repita las letras que ya ha escrito. Cuando acierta la letra, la letra pasa a estar en lugar del guión bajo. Cuando no acierta, se irá dibujando el hangman para la cantidad de intentos, según sea el nivel de dificultas seleccionado.
## 🎮SOPA DE LETRAS🎮

<div align='center'>
<figure> <img src="https://raw.githubusercontent.com/nisaespa/Adelanto-Proyecto-Final/main/Imagenes_adelanto/sopa_de_letras.png" alt="" width="500" height="auto"/></br>
<figcaption><b></b></figcaption></figure>
</div>

### 🔥 En la sopa de letras el jugador podrá escoger las dimensiones de la sopa de letras, siendo esta de forma cuadrada. Además escogerá las palabras que estarán escondidas en la sopa de letras. Según las dimensiones que haya dado el jugador, se creará una matriz vacia con esas dimensiones la cual se llenará con letras aleatorias, y las palabras escogidas por el jugador se pondrán organizadas de forma aleatoria. Ya que se pueda visualizar la sopa de letras, el jugador mediante coordenadas i , j encontrará las palabras, cuando encuentré una palabra, esta cambiará de aspecto visual.
## 🎮PIEDRA, PAPEL O TIJERA🎮

<div align='center'>
<figure> <img src="https://raw.githubusercontent.com/nisaespa/Adelanto-Proyecto-Final/main/Imagenes_adelanto/piedra_papel_tijera.png" alt="" width="500" height="auto"/></br>
<figcaption><b></b></figcaption></figure>
</div>

### 🔥 En el juego de piedra papel o tijera, el jugador jugará contra la computadora. En una lista se colocan las 3 opciones, y la computadora escogerá aleatoriamente entre la lista. En el caso del jugador, el podrá escribir la opción que prefiera, y el juego mediante condiciones decidirá quien gana, siguiendo estas reglas: piedra aplasta tijera, tijera corta papel y papel envuelve piedra. El jugador como la computadora empezaran con 3 vidas, pierde el que se quede primero sin vidas.
### 🔥 Para cada juego luego de que termina, el jugador tendrá la opción de devolverse al menú para escoger de nuevo algún juego o salirse del salón de juegos (cerrar programa de python) o si quiere puede volver a iniciar el juego que estaba jugando.

## 🤔 DIAGRAMA DE FLUJO 🤔
### 🔥 En el siguiente diagrama de flujo se puede ver de forma general como se abordará el programa para los 3 juegos.
###### En el editor de mermaid se podía ahcer más bonito y claro, pero al pasar el código a github daba error, entonces tocó dejarlo así 😔.
```mermaid
    flowchart TD;
    inicio[INICIO] --> seleccion[Escriba 1 para jugar sopa de letras, escriba 2 para jugar ahorcado, escriba 3 para jugar piedra papel o tijera o escriba 4 para salir del juego]
    seleccion -----> |1| sopa[Sopa de letras]
    seleccion --> |2| ahorcado[Ahorcado]
    seleccion --> |3| piedra[Piedra, papel y tijera]
    seleccion --> |4| salir[FIN]
    ahorcado --> datos[Lista1 con 1000 palabras, Intentos = 7, Palabra a encontrar que sea aleatoria entre la Lista1, Crear Lista2 vacia para almacenar letras]
    datos --> ocultar[Con el caracter de _ , guión bajo, mostrarlo la cantidad de letras de la Palabra a encontar]
    ocultar --> bucle{Mientras Intentos > 0}
    bucle --> |True|pedir[Pedir letra al jugador]
    pedir --> condicion{Sí la letra ya está en la Lista2, entonces}
    condicion -->|True|bucle
    condicion -->|False|almacenar[Almacenar letra en la Lista2]
    almacenar -->está{Sí la letra está en la Palabra a encontrar, entonces}
    está -->|True|reemplazar[Reemplazar letra encontrada, por el _ , guión bajo]
    reemplazar -->guion{Sí se encuentran _ , guiones bajos, en la Palabra a encontrar, entonces}
    guion -->|True|bucle
    guion -->|False|ganaste[El jugador encontró la Palabra a encontrar]
    ganaste --> volver
    está -->|False|restarintentos[Intentos = Intentos - 1]
    restarintentos --> bucle
    bucle --> |False|perdio[jugador pierde]
    perdio -------> volver{Sí escribes 1 puedes volver a jugar el juego del ahorcado, Sí escribes 2 puedes salir al menú de juegos}
    volver -->|1|ahorcado
    volver -->|2|seleccion
    sopa --> solicitar[Solicitar al jugador un número de 10 a 30, para las dimensiones de la sopa de letras de forma cuadrada]
    solicitar --> pide[Pedir al jugador las palabras que desea incluir en la sopa]
    pide --> crea[Crear una matriz vacía con las dimensiones especificadas por el jugador]
    crea --> llena[Llenar la matriz con letras aleatorias]
    llena --> ingresada[Para cada palabra ingresada por el jugador, decidir aleatoriamente  la orientación de la palabra]
    ingresada --> selecciona[Para cada palabra se selecciona aleatoriamente una posición en la matriz]
    selecciona --> verifica[Verificar si es posible colocar la palabra sin superponer con otra palabra y sin salirse de la matriz]
    verifica --> coloca[Colocar la palabra en la matriz si es posible, de lo contrario vuelve a intentar con una nueva posición y orientación]
    coloca --> ver[Visualización de la sopa de letras en la consola]
    ver --> encontrada[Por cada palabra encontrada, el usuario ingresa la coordenada en terminos de i, j]
    encontrada --> coordenadas[Coordenada primer letra, coordenada última letra]
    coordenadas --> si[Sí lo anterior ocurreo, la palabra encontrada tendrá un cambio visual]
    si --> sisi[Sí lo anterior ocurre agrega un puntaje positivo]
    sisi --> volverr{Sí escribes 1 puedes volver a jugar el juego de la sopa de letras, Sí escribes 2 puedes salir al menú de juegos}
    volverr --> |1|sopa
    volverr --> |2|seleccion
    piedra --> datoss[Lista con tres palabras = piedra, papel, tijera]
    datoss --> vidas[vidas jugador = 3, vidas computador = 3]
    vidas --> bucless{Mientras vidas jugador > 0 and vidas computador > 0}
    bucless -->|True|computador[computador escoja aleatoriamente entre las palabras de la Lista]
    computador --> jugador[Pedir al jugador que escriba piedra, papel o tijera]
    jugador --> condiciones{Sí jugador = piedra y computador = piedra, entonces}
    condiciones -->|True|empate[Empate, nadie pierde vidas]
    condiciones -->|False|condiciones2{Sí jugador = papel y computador = piedra, entonces}
    condiciones2 -->|True|jugadorgana[Gana jugador, vidas computador = vidas computador - 1]
    condiciones2 --> |False|condiciones3{Sí jugador = tijera y computador = piedra, entonces}
    condiciones3 -->|True|computadorgana[Gana computador, vidas jugador = vidas jugador - 1]
    condiciones3 --> |False|condiciones4{Sí jugador = piedra y computador = papel, entonces}
    condiciones4 -->|True|computadorgana[Gana computador, vidas jugador = vidas jugador - 1]
    condiciones4 --> |False|condiciones5{Sí jugador = papel y computador = papel, entonces}
    condiciones5 -->|True|empate[Empate, nadie pierde vidas]
    condiciones5 --> |False|condiciones6{Sí jugador = tijera y computador = papel, entonces}
    condiciones6 -->|True|jugadorgana[Gana jugador, vidas computador = vidas computador - 1]
    condiciones6 --> |False|condiciones7{Sí jugador = piedra y computador = tijera, entonces}
    condiciones7 -->|True|jugadorgana[Gana jugador, vidas computador = vidas computador - 1]
    condiciones7 --> |False|condiciones8{Sí jugador = papel y computador = tijera, entonces}
    condiciones8 -->|True|computadorgana[Gana computador, vidas jugador = vidas jugador - 1]
    condiciones8 --> |False|condiciones9{Sí jugador = tijera y computador = tijera, entonces}
    condiciones9 -->|True|empate[Empate, nadie pierde vidas]
    empate --> bucless
    computadorgana --> bucless
    jugadorgana --> bucless
    bucless -->|False|sisisi{Sí vidas jugador = 0}
    sisisi --> |True|perdiste[La computadora ganó]
    sisisi --> |False|gana[El jugador ganó]
    perdiste --> volverrr{Sí escribes 1 puedes volver a jugar el juego de piedra papel y tijera, Sí escribes 2 puedes salir al menú de juegos}
    gana --> volverrr{Sí escribes 1 puedes volver a jugar el juego de piedra papel y tijera, Sí escribes 2 puedes salir al menú de juegos}
    volverrr --> |1|piedra
    volverrr --> |2|seleccion
```
