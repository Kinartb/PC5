# PC5
## PARTE 1
Una vez descargado el archivo vamos a visualizar si todo corre con normalidad despues de ejecutar primero `bundle install` y posteriormente `rails server`. A continaucion nos aparecera lo siguiente. 

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini0.png)

Este problema indica que aun no se ha inicialido la tabla `movie` por lo que procederemos a crearlo con el siguiente comnado `rake db:migrate RAILS_ENV=development`.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini1.png)

Vemos que no se ha insertado ningun dato a la tabla por lo que ingresaremos el comando `rake db:seed`.

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/ini3.png)

ahora vemos que se presenta todo con normalidad.

En las actividades relacionados a la Introducción de Rails los métodos actuales del controlador no son muy robustos: si el usuario introduce de manera manual un URI para ver (Show) una película que no existe (por ejemplo /movies/99999), verás un mensaje de excepción horrible. Modifica el método show del controlador para que, si se pide una película que no existe, el usuario sea redirigido a la vista Index con un mensaje más amigable explicando que no existe ninguna película con ese.

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

_De la actividad relacionada a BDD e historias de usuario crea definiciones de pasos que te permitan escribir los siguientes pasos en un escenario de RottenPotatoes:_

Given the movie "Inception" exists
```cucumber
Given(/^the movie "(.*?)" exists$/) do |movie_title|
  Movie.create(title: movie_title)
end
```
And it has 5 reviews
```cucumber
And(/^it has (\d+) reviews$/) do |review_count|
  movie = Movie.last # ultima película creada
  # agregar reseñas a la película
  review_count.to_i.times { movie.reviews.create }
end
```
And its average review score is 3.5
```cucumber
And(/^its average review score is ([\d.]+)$/) do |average_score|
  movie = Movie.last # última película creada
  # puntuación promedio
  movie.update(average_score: average_score.to_f)
end
```

_De la actividad relacionadas a BDD e historias de usuario, supongamos que en RottenPotatoes, en lugar de utilizar seleccionar la calificación y la fecha de estreno, se opta por rellenar el formulario en blanco. Primero, realiza los cambios apropiados al escenario. Enumera las definiciones de pasos a partir que Cucumber invocaría al pasar las pruebas de estos nuevos pasos. (Recuerda: rails generate cucumber:install)_

_De la actividad relacionadas a BDD e historias de usuario indica una lista de pasos como los de la siguiente figura_

_Para implementar el siguiente paso_

When / I delete the movie: "(.*)"/ do |title|

_Basándose en el siguiente fichero de especificaciones (specfile), ¿a qué métodos deberían responder las instancias de F1 para pasar las pruebas?_
```
require 'f1'
	describe F1 do
                   describe "a new f1" do
                      before :each do ; @f1 = F1.new ; end
                          it "should be a pain in the butt" do
                         @f1.should be_a_pain_in_the_butt
                      end
                it "should be awesome" do
                  @f1.should be_awesome
              end
               it "should not be nil" do
                 @f1.should_not  be_nil
            end
           it "should not be the empty string" do
               @f1.should_not == ""
            end
          end
end
```
## PARTE 2

![](https://github.com/Kinartb/PC5/blob/main/Imagenes/bdd1.png)
![](https://github.com/Kinartb/PC5/blob/main/Imagenes/bdd2.png)
![](https://github.com/Kinartb/PC5/blob/main/Imagenes/bdd3.png)
![](https://github.com/Kinartb/PC5/blob/main/Imagenes/bdd4.png)
![](https://github.com/Kinartb/PC5/blob/main/Imagenes/bdd5.png)
