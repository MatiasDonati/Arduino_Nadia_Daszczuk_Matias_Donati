## :rocket: Proyecto: :rocket:
 - Contador de dos cifras con dos Display de 7 segmentos.
 - Swtich para mostrar contador de numeros primos.
 - Adicion de Motor, sensor de temperatura y ( fotoresistor ó sensot de luz ambiental)

![Tinkercad](./imgs/img.png)

## :coffee: Integrantes
- Nadia Daszczuk
- Matias Donati

## :pencil2: Descripción
El programa esta desarrolado en lengia C++ mediante la web https://www.tinkercad.com/

En esta primera parte del parcial domiciliario realizamos mediante el uso de la multiplexación, un contador de 00 al 99, con dos displays de 7 segmentos.

El contador cuenta con tres botones, uno para subir, otro para bajar y el tercero para volver a cero.
Luego adicionamos un Switch el cual, dependiendo de su posición, deja el peoyecto funcionando como previamente estaba, o en los displays solo se muestra un contador de numeros primos del 00 al 99, se puede subir y bajar al numero primo mas próximo o bien ir a 0 con el boton de Reset.

Tambien mediante la funcion map obtuvimos el rango correcto de temperatuda mediante un un sensor de temperatura e incorporamos un motor y un fotoresistor o un sensor de luz ambiental dependiendo el codigo.

El arranque del motor depende del sensor de temperatura que a su vez depende de los valores del fotoresistor o del sensot de luz ambiental.

 - Ej: si el fotoresistor es mayor a 940 o el sensor de luz ambiental es menor que 18 (dependieno codigo 1 o codigo 2) la temperatura se setea en 35 por lo que se enciende el motor. (El motor se encuendo cuando la teperatura igual o mayor a 30, caso contrario se apaga.)

## :mag: Funciónes principales
* **imprimir_contador(int contador)**

         void imprimir_contador(int contador)
         {
  	       prender_led(APAGAR_LED);
	       prender_numero(contador/10);
  	       prender_led(DECENA);
  	       prender_led(APAGAR_LED);
  	       prender_numero(contador - 10*((int)contador/10));
  	       prender_led(UNIDAD);
  	       prender_led(APAGAR_LED);
         }

 Esta funcion es la que se encarga de alternar la visualización de cada display en un intervalo de tiempo muy corto,  para que parezca que ambos están encendidos al mismo tiempo.

 * **int keypressed(void)**

      int keypressed(void)
      {
        sube = digitalRead(UP);
        baja = digitalRead(DOWN);
        reset = digitalRead(RESET);

        if(sube == 1)
        {
            subePrevia = 1;
        }
        
        if(baja) // no presione
        {
            bajaPrevia = 1;
        }
        if(reset) // no presione
        {
          resetPrevia = 1;
        }
      
        if (sube == 0 && sube != subePrevia)
        {
          subePrevia=sube;
          return UP;
        }
        
        if (baja == 0 && baja != bajaPrevia)
        {
          bajaPrevia=baja;
          return DOWN;
        }
        
        if (reset == 0 && reset != resetPrevia)
        {
          resetPrevia=reset;
          return RESET;
        }
       }

 Esta funcion lee los estados de los botones. Se manjea en base a dos valores: el boton principal 0 o 1, y un valor para saber si el boton ya se presionó.


Ej: Como el programa loopea de forma rapida, cuando se ejecuta, el botón no está presionado, por lo que la variable que define si se presionó, toma su valor en 1. Cuando el botón se presiona (0), se verifica si está distnto del valor presionado(1), de así ser, se iguala el valor del botón con el valor de boton presionado previamente y se retorna dicho boton.
 La igualacion de valores se realiza para que si el boton queda presionado no se tome como presionado mas de una vez.

- **bool es_primo(int numero)**
Como su nombre indica, luego de realizar un calculo con el modulo %, retorna un booleano para saber si el numero es primo.

## :robot: Link al proyecto
- [Proyecto terminacion 0-3](https://www.tinkercad.com/things/hhzmKLDNCTP-parcial-domicilaior-arduino-nadia-daszczuk-matias-donati/editel?sharecode=XlhfunB_HZDaU7JE3eJscTtCSTudx3zqby0YumbzlvU)

- [Proyecto terminacion 7-9](https://www.tinkercad.com/things/41yyffxaWwO-copy-of-parcial-domicilaior-arduino-nadia-daszczuk-matias-donati/editel?sharecode=CT462ZGyd9uN4jaChU0jfaKNmfP3cf43y9_2FOy9WHI)
