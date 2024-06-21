# Checklist

## Frontend

### Identidade visual única em toda a aplicação (interface)

* Todas as telas possuem mesmo padrão de cores, fontes, imagens e ícones.
* Todas as telas exibem usuário logado (nome, perfil) e opção de logout (Sair).
* Todas as telas permitem algum grau de responsividade.
* Todas as mensagens ao usuário seguem o mesmo padrão da identidade visual da interface, tanto para exibir informação (info), aviso (warning) ou erro (error).

### Validação de Dados (input apenas de dados validados)

* Todas os campos de entrada orientam seu preenchimento.
* Todas os campos de entrada indicam se são ou não obrigatórios.
* Apenas aceita senhas fortes (exige no mínimo 8 caracteres, variedade de letras maiúsculas e minúsculas, números e caractere especial).
* Não permite cadastro de dados únicos duplicados, como CPF, CNPJ, CRM, CREA, e-mail, usuário para login, etc.
* Permite visualizar senha
* Desejável: Permite confirmar senha.
* Desejável: máscara telefone, CPF, CNPJ, CEP, etc.
* Desejável: obtém endereço a partir de CEP válido.

Observação: Consulta CEP - Correios (https://www.correios.com.br/).

## Backend

### Funcionalidades

* Login permite recuperação de usuário e recuperação de senha.
* Desejável: habilitar / desabilitar autenticação em 2 fatores (Two-Factor Authentication - 2FA).

### Persistência

* Senha é criptografada no BD.
* BD geral: entidades fortes são nomeadas como substantivos.
* BD relacional: entidades estão relacionadas (PK x FK).
* BD relacional: diagrama gerado por engenharia reversa (BD implementado).
* Aplicação trata erros de BD: avisa o usuário (BD fora de serviço, dados únicos duplicados, ...).
* DELETE: solicita confirmação antes da exclusão de registro.
* UPDATE: formulários para edição estão preenchidos com os dados persistidos em BD
  * Diferencia dados editáveis (telefone, endereço, ... ) de dados não editáveis (CPF, CNPJ, ...)
* UPDATE de senha: não apresenta a senha criptografada para atualização (campo vazio) 
  * Criptografia de HASH é irreversível, logo a senha criptografada não pode ser revertida / recuperada para edição.
* Desejável: UPDATE de senha em tela exclusiva para trocar senha.
* Desejável: log para auditoria.

### Sessão

* Faz tratamento de restrição de acesso: telas ou funcionalidade são acessíveis apenas a usuários com a devida permissão, ou seja, existe bloqueio de acesso para usuários sem permissão. Nesse caso, o usuário sem permissão é redirecionado à tela apropriada (tela inicial ou tela de login).
* Expira sessão quando não há atividade do usuário logado – existe timeout de inatividade.

---

1. Login (Autenticação e Autorização)
2. CRUD Usuário (User)
3. CRUD Animal de Estimação (Pet)
4. Manter (cadastrar) a agenda de banho e tosa (Cliente)
5. Manter (cadastrar) agenda de consultas veterinárias (Cliente)
6. Manter (cadastrar) serviços ofetados (Admin)
7. Manter (cadastrar) produtos disponíveis (Admin)
8. Manter agendas geral (Admin)
9. Analytics:
   - Filtro por período (data, mês, ano etc.)
   - Total de cancelamentos ao lado do agendamento.
10. Esqueci minha Senha
11. Recuperar senha 
12. Validar campos de entrada em TODOS os cadastros  
   - Tratar nome com 2 letras (os campos nome, endereço, cor, raça devem ter no mínimo 3 caracteres)
   - Identificar os campos obrigatórios (com *)
   - Data de nascimento deve estar no passado, caso esteja no futuro ter uma mensagem para o usuário informando 'Data de agendamento deve estar no passado'
   - Data do agendamento deve estar no futuro, caso esteja no passado ter uma mensagem para o usuário informando 'Data de agendamento deve estar no futuro'
   - Indicar o tipo de erro para cada campo 
   - Idade do Pet: deve retornar a idade calculada do animal, a partir da data de nascimento
13. As implementações devem estar de acordo com as Histórias de Usuário (NOVA entrega do TDE 3)
14. Manutenção do Pet: atualizar e excluir Pet 
15. Fornecer mensagens se ocorrer erro ou se operação for bem sucedida, em TODAS as interações com o usuário
16. Soft delete do usuário deve desabilitar o login
  - Usuário inativo NÃO pode realizar Login.
  - Deve retornar uma mensagem informando 'Usuário inativo ou não cadastrado.'.
17. Agenda deve trazer: tipo de animal, idade
18. Agendamento de consulta deve permitir indicar o veterinário
19. Permitir atualização de agendamento: editar e cancelar agendamento.

