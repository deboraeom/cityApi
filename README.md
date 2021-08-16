
   <H3> cityApi</H3>

  Tecnologias utilizadas são:<br>
  <li> SpringBoot <br></li>
  <li> Postegree<br></li>
  <li> Java <br></li>
  <li>  Heroku <br></li>
  <li> Docker <br></li>
  <li> JUnit <br></li>
  <li> JPA/Hibernate <br></li>
 
A api retorna a lista de países,estados, cidades contidos no banco de dados Postegrees acessando da seguinte formas:<br></li>

Acesso local:<br>
localhost:8080/state<br>
localhost:8080/countries<br>
localhost:8080/city<br>


Acesso remoto(heroku):<br>
https://still-crag-58269.herokuapp.com/state<br>
https://still-crag-58269.herokuapp.com/countries
https://still-crag-58269.herokuapp.com/city<br>



<li> Retorna também as distância entre duas cidades, quando se passa por paramentro o id(id1 e id2) das cidades:<br></li>

Para consultar em millhas:<br>

Acesso local local:<br>
localhost:8080/distances/by-points?from=id1&to=id2<br>
Acesso remoto(heroku):<br>
https://still-crag-58269.herokuapp.com/distances/by-points?from=id1&to=id2<br>


Para consultar em metros<br>
Acesso local local:<br>
localhost:8080/distances/by-cube?from=4929&to=4930<br>
Acesso remoto(heroku):<br>
https://still-crag-58269.herokuapp.com/distances/by-cube?from=4929&to=4930<br>


<li> Para configurar o banco localmente é necessário a imagem no docker<br></li>
docker run --name cities-db -d -p 5432:5432 -e POSTGRES_USER=postgres_user_city -e POSTGRES_PASSWORD=super_password -e POSTGRES_DB=cities postgres<br>

<li> Baixar os dados do banco:<br></li>

https://github.com/chinnonsantos/sql-paises-estados-cidades/tree/master/PostgreSQL<br>
 
 

<li> E dentro do diretório(postegree) rodar os seguites comandos:<br></li>

docker run -it --rm --net=host -v $PWD:/tmp postgres /bin/bash<br>

psql -h localhost -U postgres_user_city cities -f /tmp/pais.sql<br>
psql -h localhost -U postgres_user_city cities -f /tmp/estado.sql<br>
psql -h localhost -U postgres_user_city cities -f /tmp/cidade.sql<br>

psql -h localhost -U postgres_user_city cities<br>

CREATE EXTENSION cube; <br>
CREATE EXTENSION earthdistance;<br>

*O servidor do heroku não permanece online, caso você queira usar essa api remotamente, será necessario que você crie e configure o heroku e substitua a configuração em "aplication-heroku.properties" e a url <br>

<li> O projeto original é do professor Andre Gomes: <br></li>
https://github.com/andrelugomes/digital-innovation-one/blob/master/cities-api<br>

<li> Eu o refiz usando Maven, adicionei as classes DTO  de forma que o cliente não tenha acesso direto ao banco, adicionei as classes de serviço, separando as responsabilidades entre service e controller, também fiz os testes unitário.<br></li>
 </ul>   