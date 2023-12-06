# PC5
## PARTE 1
Una vez descargado el archivo vamos a visualizar si todo corre con normalidad despues de ejecutar primero `bundle install` y posteriormente `rails server`. A continaucion nos aparecera lo siguiente. 

![]()

Este problema indica que aun no se ha inicialido la tabla `movie` por lo que procederemos a crearlo con el siguiente comnado `rake db:migrate RAILS_ENV=development`.

![]()

Vemos que no se ha insertado ningun dato a la tabla por lo que ingresaremos el comando `rake db:seed`.

![]()

ahora vemos que se presenta todo con normalidad.


## PARTE 2

## PARTE 3
