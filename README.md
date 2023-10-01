# Services em angular
__Camada do Angular responsável pela parte lógica da aplicação__  
* o mesmo arquivo.ts pode servir a mais de um `component`, muda o jeito de eles consumirem os dados
* Usar service evita de sobrecarregar a camada do `component`
* Não tem jeito certo ou errado mas, crie `services` por tipos de serviços, já que a proposta do angular é ser leve e de fácil manutenção ex.: service que é especialista em acessar a api

_note que não temos o .html do app.component já que usamos o `template` ao inves de `templateUrl`, assim podemos passar uma tag diretamente dentro do arquivo .ts

# O projeto será um card de pokémon
* Usando pokeAPI
* [PokeAPI](https://pokeapi.co/)  

## Services -> aquivo provedor de dados
* Para deixar o component limpo, usamos os services para consumir e tratar os dados da [API](https://pokeapi.co/api/v2/)
* Importar em enviroments.ts -> é o arquivo que vai importar a API
~~~
export const environment = {
  production: false,
  pokeApi: 'https://pokeapi.co/api/v2/pokemon/'
};
~~~
* criando o service `ng g s services/pokemon` -> no terminal.
### Entendendo a anatomia de um service
~~~
import { Injectable } from '@angular/core';

@Injectable({
  providedIn: 'root'
})
export class PokemonServiceService {

  constructor() { }
}
~~~
* `import { Injectable } from '@angular/core';`-> Import do conteudo injetável, pode passar esse conteúdo como dependência de outra classe, como uma vacina
* `@injectable({...})`-> onde pode ser injetado, no arquivo em questão é em tudo que está em root, pasta raiz, todos os componentes podem consumir/injetar esse arquivo, colocamos eles no providers, no arquivo app.module.ts
* `export class` -> classe normal de .ts
### Injetando o service em um component
* no `constructor(){}` do component
~~~
  constructor(
    private service:PokemonService
    ) { }
~~~
* Importando a url da variavel no enviroment `import { environment } from 'src/environments/environment'` 
## Requisições http
* em app.module.ts -> `imports: [...]` -> declarar `HttpClientModule` -> pacote que lida com a parte de requisições
* em pokemon.service.ts -> nos parâmetros do `constructor(...){}` -> `private http:HttpClient`
~~~
export class PokemonService {
  private baseURL:string = ''
  private pokeData:any

  constructor(
    private http:HttpClient
  ) {
    this.baseURL = environment.pokeApi
  }

  getPokemon(pokemonName:string){
    this.pokeData = this.http.get(`${this.baseURL}${pokemonName}`)
    console.log(this.pokeData)
  }
}
~~~
* Usar o observable no lugar das promisses -> lemnra um pouco as promisses
* Para trabalhar com formularios precusa importar o `FormsModule` em app.module.ts
