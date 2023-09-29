# Services em angular
__Camada do Angular responsável pela parte lógica da aplicação__  
* o mesmo arquivo.ts pode servir a mais de um `component`, muda o jeito de eles consumirem os dados
* Usar service evita de sobrecarregar a camada do `component`
* Não tem jeito certo ou errado mas, crie `services` por tipos de serviços, já que a proposta do angular é ser leve e de fácil manutenção ex.: service que é especialista em acessar a api

_note que não temos o .html do app.component já que usamos o `template` ao inves de `templateUrl`, assim podemos passar uma tag diretamente dentro do arquivo .ts

# O projeto será um card de pokémon
