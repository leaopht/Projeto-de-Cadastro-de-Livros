# Projeto-de-Cadastro-de-Livros
Sistema de Cadastro de Livros – Versão
Expandida
1. Tema
Sistema de Cadastro e Gerenciamento de Livros com controle de editoras e
empréstimos.

3. Descrição
Problema a ser resolvido:
Muitas bibliotecas, livrarias e instituições de ensino ainda realizam
o controle de seus acervos de livros de forma manual ou
desorganizada, utilizando planilhas ou registros em papel. Isso
gera dificuldades como perda de informações, duplicidade de
registros, dificuldade em localizar títulos específicos e lentidão nos
processos de consulta e atualização de dados. Além disso, não
existe controle sobre a origem dos livros (editora) nem sobre os
empréstimos feitos a usuários.

Justificativa:
Um sistema informatizado permite centralizar todas as informações
em um banco de dados, tornando o gerenciamento mais rápido,
preciso e seguro. A inclusão de tabelas de editoras e empréstimos
possibilita controlar a origem dos livros e monitorar o histórico de
empréstimos, evitando perdas e melhorando a organização.

Objetivos:
• Desenvolver um sistema em Java integrado a um banco de
dados MySQL para cadastrar e gerenciar livros, editoras e
empréstimos.
• Permitir as operações CRUD (Criar, Ler, Atualizar e Excluir)
sobre os registros.
• Garantir segurança e integridade dos dados armazenados no
banco.
• Facilitar a consulta e atualização das informações de cada
livro, editora e empréstimo.
• Proporcionar uma interface simples (via console) para
interação do usuário com o sistema.
Potenciais clientes/usuários:
• Bibliotecas públicas e privadas — para controle de acervo e
empréstimos.
• Livrarias — para organização de estoque e consulta de títulos.
• Escolas e universidades — para catalogar livros didáticos e
registrar empréstimos.
• Colecionadores e leitores — para gerenciamento pessoal de
coleções.

5. Diagrama de Caso de Uso (UC)
Atores:
• Usuário → Cadastra, lista, atualiza e exclui livros, editoras e
empréstimos.
• Sistema → Armazena, processa e recupera as informações no banco
de dados.
Principais casos de uso:
• Cadastrar novo livro, editora ou empréstimo
• Consultar lista de livros, editoras ou empréstimos
• Atualizar informações de um livro, editora ou empréstimo
• Excluir registros do sistema
Descrição textual do diagrama:
O ator Usuário interage com o Sistema de Cadastro de Livros por
meio de um menu no console. Ele pode cadastrar livros, editoras e
empréstimos, listar registros, atualizar informações ou excluir
registros. O Sistema valida as informações e realiza as operações
no banco de dados MySQL através da camada DAO.
Representação esquemática (UC):
+----------------------------+
| Usuário |
|----------------------------|
| - Cadastrar livro |
| - Cadastrar editora |
| - Cadastrar empréstimo |
| - Listar registros |
| - Atualizar registros |
| - Excluir registros |
+------------|---------------+
 |
 v
+----------------------------+
| Sistema de Cadastro de |
| Livros (Java + MySQL) |
+----------------------------+

4. DER (Diagrama Entidade-Relacionamento)
O sistema agora possui 3 entidades principais: Livro, Editora e Empréstimo.
Entidade: Livro
• id (PK, int, auto_increment)
• titulo (varchar(100), not null)
• autor (varchar(100), not null)
• ano_publicacao (int)
• genero (varchar(50))
• preco (decimal(10,2))
• id_editora (FK, int) → referencia a Editora

Entidade: Editora
• id (PK, int, auto_increment)
• nome (varchar(100), not null)
• endereco (varchar(200))
• telefone (varchar(20))

Entidade: Empréstimo
• id (PK, int, auto_increment)
• id_livro (FK, int) → referencia a Livro
• nome_usuario (varchar(100), not null)
• data_emprestimo (date)
• data_devolucao (date)
• status (varchar(20)) → ex: "Emprestado", "Devolvido"
Relacionamentos:
• Um livro pertence a uma editora.
• Um livro pode ter múltiplos empréstimos, mas cada
empréstimo refere-se a apenas um livro.

Representação do DER (texto):
+-----------------------------+
| LIVRO |
+-----------------------------+
| id (PK) |
| titulo |
| autor |
| ano_publicacao |
| genero |
| preco |
| id_editora (FK) |
+-----------------------------+

+-----------------------------+
| EDITORA |
+-----------------------------+
| id (PK) |
| nome |
| endereco |
| telefone |
+-----------------------------+

| EMPRÉSTIMO |
+-----------------------------+
| id (PK) |
| id_livro (FK) |
| nome_usuario |
| data_emprestimo |
| data_devolucao |
| status |
+-----------------------------+

6. Resumo Geral do Sistema
Item Descrição
Linguagem Java
Banco de Dados MySQL
Interface Console
Entidades
principais Livro, Editora, Empréstimo
Operações Inserir, Listar, Atualizar, Excluir
Camadas Modelo (Livro, Editora, Emprestimo), DAO, Banco (ConexaoBD), Aplicação
(Principal)
Público-alvo Bibliotecas, livrarias, instituições de ensino e leitores em geral
