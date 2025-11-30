# API Jogos (Spring Boot)

API REST para cadastro e gerenciamento de jogos (CRUD) desenvolvida em Java com Spring Boot.

## Visão geral
Esta aplicação expõe endpoints REST para criar, ler, atualizar e excluir registros de jogos. É um projeto simples pensado para estudo, testes e como base para features adicionais (autenticação, paginação, persistência em banco relacional, etc).

Principais tecnologias:
- Java 17 (ou versão compatível definida no pom.xml)
- Spring Boot
- Maven (usando o wrapper mvnw)
- (Opcional) H2 para testes em memória / PostgreSQL ou outro banco para produção

## Estrutura do projeto
- pom.xml — dependências e configuração do Maven
- mvnw, mvnw.cmd — Maven wrapper
- src/main/java — código-fonte da aplicação (controllers, services, models, repositories)
- src/test/java — testes automatizados
- application.properties / application-{profile}.properties — configurações por perfil

> Observação: o README original contém a linha indicando alteração de profile: `spring.profiles.active=test` → `spring.profiles.active=dev`. Ajuste o perfil conforme o ambiente desejado.

## Modelo (exemplo)
Um modelo simples `Game` pode conter:
- id: Long
- title: String
- genre: String
- releaseYear: Integer
- price: BigDecimal

## Endpoints (exemplo)
- GET /games — lista todos os jogos
- GET /games/{id} — obtém jogo por id
- POST /games — cria um novo jogo
- PUT /games/{id} — atualiza um jogo existente
- DELETE /games/{id} — remove um jogo

Exemplo de contrato JSON para criação/atualização:
```json
{
  "title": "Nome do Jogo",
  "genre": "Ação",
  "releaseYear": 2023,
  "price": 99.90
}
```

## Executando localmente
Pré-requisitos: JDK (versão compatível) e git.

1. Clonar o repositório:
   git clone https://github.com/<seu-usuario>/api-jogos-spring.git

2. Entrar no diretório do projeto:
   cd api-jogos-spring

3. Rodar com o Maven wrapper:
   - Linux / macOS:
     ./mvnw spring-boot:run
   - Windows:
     mvnw.cmd spring-boot:run

Por padrão, a aplicação roda em http://localhost:8080. Ajuste o `application.properties` ou defina o profile (`spring.profiles.active`) conforme suas necessidades.

## Executando testes
./mvnw test

## Exemplo de requisições (curl)
- Criar:
  curl -X POST -H "Content-Type: application/json" -d '{"title":"Jogo X","genre":"RPG","releaseYear":2024,"price":59.90}' http://localhost:8080/games

- Listar:
  curl http://localhost:8080/games

- Atualizar:
  curl -X PUT -H "Content-Type: application/json" -d '{"title":"Jogo X Update","genre":"RPG","releaseYear":2024,"price":49.90}' http://localhost:8080/games/1

- Deletar:
  curl -X DELETE http://localhost:8080/games/1

## Boas práticas e próximos passos
- Adicionar validação de entrada com Bean Validation (@Valid)
- Tratar exceções globais com @ControllerAdvice
- Implementar DTOs e mapeamento (ex: MapStruct)
- Adicionar paginação, ordenação e filtros para a listagem
- Configurar persistência com JPA + banco relacional (ex: PostgreSQL)
- Documentar a API com OpenAPI / Swagger

## Contribuição
Sinta-se à vontade para abrir issues e pull requests. Para mudanças significativas, descreva a motivação e os testes realizados.

## Licença
Defina uma licença (ex: MIT) conforme desejar.
