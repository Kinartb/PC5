# PC5
## PARTE 1
Una vez descargado el archivo vamos a visualizar si todo corre con normalidad despues de ejecutar primero `bundle install` y posteriormente `rails server`. A continaucion nos aparecera lo siguiente. 

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini0.png)

Este problema indica que aun no se ha inicialido la tabla `movie` por lo que procederemos a crearlo con el siguiente comnado `rake db:migrate RAILS_ENV=development`.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini1.png)

Vemos que no se ha insertado ningun dato a la tabla por lo que ingresaremos el comando `rake db:seed`.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini2.png)

ahora vemos que se presenta todo con normalidad.

Ahora vamos a modiciar `index` y el `controller` para que nos aparezca un mensaje de error al momento de encontrar una pelicula.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini3.png)


## PARTE 2

## PARTE 3
