# Portal AGV

O Portal AGV é um projeto web educacional que simula um sistema de acesso escolar com diferentes perfis de usuário: aluno, responsável e administrador. O objetivo é aplicar conceitos de autenticação, controle de acesso e integração entre front-end e back-end.

## Tecnologias

O projeto foi desenvolvido utilizando HTML, CSS, JavaScript, Node.js, Express e express-session.

## Objetivo

Praticar conceitos fundamentais de desenvolvimento web como autenticação de usuários, controle de sessão, autorização por perfil, proteção de rotas e comunicação entre front-end e back-end.

## Back-end

Responsável pelo desenvolvimento e ajustes: Nathan (2DS)

## Problema inicial do projeto

O sistema possuía uma tela de login funcional, porém com falhas graves de segurança. Após o login, o usuário era redirecionado para seu painel, mas qualquer outra página podia ser acessada apenas digitando a URL no navegador. Ou seja, mesmo sem login ou com outro perfil, era possível acessar páginas de admin, aluno ou responsável.

## Análise técnica

O problema não estava apenas no login, mas na ausência de controle de acesso nas rotas. O sistema possuía autenticação visual, mas não tinha autorização real no backend.

As principais falhas eram:
- páginas HTML públicas
- ausência de validação de sessão por rota
- ausência de controle por perfil
- segurança baseada apenas no front-end
- inexistência de persistência de login

## Decisão de arquitetura

Foram consideradas algumas abordagens como duplicar páginas, controlar acesso no front-end ou migrar para outras tecnologias, mas todas foram descartadas.

A solução adotada foi implementar autenticação com sessão no backend utilizando Express, express-session e middleware de autenticação e autorização.

## Ajustes implementados

Foi implementada autenticação por sessão, onde após o login o servidor cria uma sessão com os dados do usuário e seu tipo de perfil.

As rotas passaram a ser protegidas no backend, validando se o usuário está autenticado antes de liberar acesso.

Também foi implementado controle de acesso por perfil, restringindo cada tipo de usuário às suas respectivas páginas.

O acesso direto às páginas via URL foi bloqueado e passou a depender da validação do servidor.

Foi adicionado logout para encerramento da sessão e o fluxo do sistema foi ajustado para depender do backend, garantindo controle real de acesso.

## Como rodar o projeto

Para executar o projeto, instale as dependências e inicie o servidor com os comandos abaixo:

npm install
npm start

Depois, acesse no navegador:

http://localhost:3000

## Dados de acesso (teste)

Aluno: aluno@escola / 1234
Admin: admin@escola / 1234
Responsável: responsavel@escola / 1234

## Observações

O projeto não funciona abrindo arquivos HTML diretamente (file://) ou utilizando Live Server. É necessário rodar o backend com Node.js.

Todas as páginas dependem de sessão ativa. Sem login válido, o acesso é bloqueado.

As credenciais são simuladas e não há banco de dados no momento.

Este é um projeto educacional e não está pronto para uso em produção.

## Próximos passos

Integração com banco de dados, uso de bcrypt para senha, criação de cadastro de usuários, validação mais robusta, limitação de tentativas de login e uso de HTTPS.

## Conclusão

O principal problema do projeto era a ausência de proteção das rotas. A solução foi implementar autenticação com sessão, mover a segurança para o backend e controlar o acesso por perfil. Com isso, o sistema passou a ter controle real de autenticação e autorização.
