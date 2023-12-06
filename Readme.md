# PC5
## PARTE 1
Una vez descargado el archivo vamos a visualizar si todo corre con normalidad despues de ejecutar primero `bundle install` y posteriormente `rails server`. A continaucion nos aparecera lo siguiente. 

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini0.png)

Este problema indica que aun no se ha inicialido la tabla `movie` por lo que procederemos a crearlo con el siguiente comnado `rake db:migrate RAILS_ENV=development`.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini1.png)

Vemos que no se ha insertado ningun dato a la tabla por lo que ingresaremos el comando `rake db:seed`.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini3.png)

ahora vemos que se presenta todo con normalidad.

Ahora vamos a modiciar `app/views/movies/index.html.erb` y el `BDD-Cucumber/app/controllers/movies_controller.rb` para que nos aparezca un mensaje de error al momento de no encontrar una pelicula.
Para esto tenemos que modificar el controlador.

```ruby
---
  def show
    id = params[:id] # retrieve movie ID from URI route
    @movie = Movie.find_by(id: id) # look up movie by unique ID

    if @movie.nil?
      flash[:alert] = "La pelicula que estas buscando no existe"
      redirect_to movies_path
    end
    # will render app/views/movies/show.<extension> by default
  end
---
```
Aqui nos preguntamos que pasa si `@movie` es `nil` es decir no existe o es nulo, entonces enviamos un mensaje de alerta.
y tambien se modifico el index agregando lo siguiente

```html
<% if flash[:alert] %>
  <div class="alert alert-danger">
    <%= flash[:alert] %>
  </div>
<% end %>
```
el cual hara que se visualice como un mensaje en rojo (danger) en lugar del error predefinido por rails. Al ejecutar una ruta erronea como `http://localhost:3000/movies/0912309` para que nos aparezca lo siguiente

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini4.png)


## PARTE 2

## PARTE 3
