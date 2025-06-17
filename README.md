# API de Controle de Sessões de Votação

## Descrição

Projeto desenvolvido em Java com Spring Boot que implementa uma API REST para gerenciar sessões de votação em uma assembleia. A API mantém os dados **em memória**, sem uso de banco de dados, e aplica regras de negócio para criação de pautas, abertura de sessões, registro de votos e consulta de resultados.

---

## Funcionalidades

* Criar uma pauta de votação (`POST /pauta`)
* Abrir uma sessão de votação para uma pauta com duração configurável (`POST /sessao`)
* Registrar votos para pautas (`POST /voto`)
* Consultar o resultado da votação de uma pauta após o encerramento da sessão (`GET /resultado/{pautaId}`)

---

## Tecnologias utilizadas

* Java 17+
* Spring Boot 3+
* Maven
* JUnit 5 para testes unitários
* Armazenamento em memória (Map, List)

---

## Como rodar o projeto

1. Clone o repositório:

   ```bash
   git clone https://github.com/seu-usuario/seu-repositorio.git
   cd seu-repositorio
   ```

2. Execute a aplicação:

   ```bash
   ./mvnw spring-boot:run
   ```

3. Acesse a API em: `http://localhost:8080`

---

## Endpoints principais

| Método | Endpoint             | Descrição                      |
| ------ | -------------------- | ------------------------------ |
| POST   | /pauta               | Criar nova pauta               |
| POST   | /sessao              | Abrir sessão para uma pauta    |
| POST   | /voto                | Registrar voto para uma pauta  |
| GET    | /resultado/{pautaId} | Consultar resultado da votação |

---

## Exemplos de requisição (JSON)

### Criar pauta

```json
{
  "titulo": "Revisão das metas do trimestre"
}
```

### Abrir sessão

```json
{
  "pautaId": 1,
  "duracaoEmMinutos": 2
}
```

### Registrar voto

```json
{
  "pautaId": 1,
  "cpfAssociado": "12345678900",
  "voto": "SIM"
}
```

### Consultar resultado

`GET /resultado/1`

Resposta:

```json
{
  "pauta": "Revisão das metas do trimestre",
  "totalVotos": 5,
  "votosSim": 3,
  "votosNao": 2,
  "resultado": "APROVADA"
}
```

---

## Testes

Para rodar os testes unitários:

```bash
./mvnw test
```

---

## Considerações finais

Este projeto é uma aplicação simples, focada em regras de negócio e arquitetura limpa, ideal para aprendizado e prática de Spring Boot sem banco de dados.

Contribuições, issues e pull requests são bem-vindos!
