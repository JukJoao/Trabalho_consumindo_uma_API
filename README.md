# HTTP.DOG // Jogo da Memória

Aplicação web interativa e educativa desenvolvida para auxiliar no aprendizado e na memorização dos códigos de status HTTP. A ideia é relacionar cada código e seu significado à imagem correspondente fornecida pela API pública `http.dog`.

## Sobre o projeto

O jogo combina elementos visuais, interatividade e estudo técnico para tornar a memorização dos códigos HTTP mais intuitiva e divertida. Cada carta do tabuleiro conecta:

- o código HTTP;
- o nome oficial do status;
- a descrição em português;
- a imagem do cachorro correspondente.

## Funcionalidades

- Associação Código ↔ Imagem: cada par no tabuleiro relaciona uma carta tipográfica ao respectivo cachorro da API.
- Ocultação inteligente de legenda: a faixa inferior da imagem original fica escondida até o par ser encontrado, revelando a imagem completa após o acerto.
- Três níveis de tabuleiro:
  - 6 pares (12 cartas);
  - 8 pares (16 cartas);
  - completo: 16 pares (32 cartas).
- Painel de telemetria HTTP em tempo real: exibe a requisição realizada, o status retornado, o tipo de conteúdo e a explicação do código ao acertar ou ao clicar em um par já encontrado.
- Guia rápido integrado: modal de consulta com os 16 endpoints utilizados na aplicação.

## Comportamento observado na API `http.dog`

Durante os testes técnicos, observou-se que:

- Servidor de arquivos estáticos: o número na URL corresponde apenas ao nome do arquivo JPEG. Independentemente do código solicitado, o servidor retorna `200 OK` com `Content-Type: image/jpeg`.
- Cache via CDN (Cloudflare): as imagens são entregues com o cabeçalho `Cache-Control: public, max-age=31536000, immutable` (cache de 1 ano).
- Métodos HTTP (`GET`, `POST` e `DELETE`): não há diferença observável entre eles, pois o servidor não implementa semântica REST e apenas entrega o arquivo estático.

## Endpoints utilizados

| Endpoint | Categoria | Significado |
|---|---|---|
| `/200.jpg` | 2xx - Sucesso | `200 OK` — Requisição bem-sucedida |
| `/204.jpg` | 2xx - Sucesso | `204 No Content` — Sucesso sem corpo na resposta |
| `/206.jpg` | 2xx - Sucesso | `206 Partial Content` — Entrega parcial do recurso |
| `/300.jpg` | 3xx - Redirecionamento | `300 Multiple Choices` — Múltiplas opções disponíveis |
| `/401.jpg` | 4xx - Erro do Cliente | `401 Unauthorized` — Requer autenticação válida |
| `/404.jpg` | 4xx - Erro do Cliente | `404 Not Found` — Recurso não encontrado |
| `/409.jpg` | 4xx - Erro do Cliente | `409 Conflict` — Conflito com o estado atual do servidor |
| `/418.jpg` | 4xx - Erro do Cliente | `418 I'm a teapot` — Código humorístico (RFC 2324) |
| `/423.jpg` | 4xx - Erro do Cliente | `423 Locked` — Recurso bloqueado (WebDAV) |
| `/425.jpg` | 4xx - Erro do Cliente | `425 Too Early` — Requisição enviada cedo demais |
| `/450.jpg` | 4xx - Erro do Cliente | `450 Blocked by Windows Parental Controls` — Bloqueio parental |
| `/451.jpg` | 4xx - Erro do Cliente | `451 Unavailable For Legal Reasons` — Bloqueio por motivos legais |
| `/507.jpg` | 5xx - Erro do Servidor | `507 Insufficient Storage` — Armazenamento insuficiente |
| `/508.jpg` | 5xx - Erro do Servidor | `508 Loop Detected` — Loop infinito detectado |
| `/530.jpg` | 5xx - Erro do Servidor | `530 Site is frozen / Origin DNS Error` — Erro de origem/DNS |
| `/561.jpg` | 5xx - Erro do Servidor | `561 Unauthorized (AWS ELB)` — Falha de autenticação no balanceador |

## Tecnologias utilizadas

- HTML5
- Tailwind CSS
- JavaScript (ES6+)
- Web Audio API

## Como executar

### Online

Acesse o link publicado na seção de `About` / `Deployments` deste repositório.

### Localmente

Baixe o arquivo `index.html` e abra-o em qualquer navegador moderno.
