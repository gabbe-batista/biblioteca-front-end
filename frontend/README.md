# Front-end da Biblioteca

Interface em React, JavaScript e CSS, sem kit de UI. O back-end ASP.NET Core original não foi alterado.

## Rodar localmente

Requisitos: SDK do .NET 8 e Node.js 20.19+ (linha 20) ou 22.12+.

No primeiro terminal, na raiz do repositório:

```sh
dotnet run --urls http://127.0.0.1:5000
```

No segundo terminal:

```sh
cd frontend
npm ci
npm run dev
```

Abra **http://localhost:5173**. Vite encaminha `/api` para o back-end sem precisar alterar CORS. Para mudar a porta do back-end, copie `.env.example` para `.env.local` e ajuste `API_TARGET`.

## Validação e publicação

- `npm test` valida os métodos e formatos do cliente HTTP.
- `npm run build` gera os arquivos estáticos em `dist/`; `npm run preview` permite verificá-los localmente com o mesmo proxy.
- Em hospedagem, sirva `dist/` e encaminhe `/api/*` no mesmo domínio à API, removendo o prefixo `/api`. Se usar `VITE_API_URL` com outra origem, o servidor que atende a API precisa permitir CORS. A variável é aplicada ao gerar a build, não é segredo.
- A API de exemplo não oferece autenticação; restrinja seu acesso antes de disponibilizar o sistema com dados reais.

## Cobertura

- **Acervo:** listar, consultar por ID, cadastrar, editar, excluir e consultar o acervo disponível.
- **Leitores:** listar, consultar por ID e cadastrar. A API não expõe edição nem exclusão de leitores.
- **Circulação:** listar o histórico, cadastrar empréstimos e registrar devoluções. A API não expõe consulta individual de empréstimo. A página inicial da UI não usa o redirecionamento de `/` da API; o Swagger continua em `http://127.0.0.1:5000/swagger`.
