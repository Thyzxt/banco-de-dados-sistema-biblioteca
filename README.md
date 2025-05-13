<strong> Ferramentas utilizadas: </strong> MySQL, SQL

<br> 

## SISTEMA DE GERENCIAMENTO DE BIBLIOTECA PÚBLICA

<br>

Projeto desenvolvido para a disciplina de Banco de Dados, com o objetivo de criar um sistema para gerenciar o acervo de livros de uma biblioteca pública, o cadastro de autores, categorias literárias, membros associados e o controle de empréstimos de obras. Utilizou-se o MySQL para o desenvolvimento do projeto, um sistema de gerenciamento de banco de dados relacional (SGBD).

<br>

### Ações:

1. Criação da base de dados e estruturação.

2. Inserção de dados nas tabelas "Categoria", "Autor", "Livro", "Membro" e "Emprestimo".
   
3. Listagem de todos os autores cujo nome inicia com a letra ‘A’.
   
4. Listagem de todos os livros cujo título contenha a palavra ‘sistema’.
   
5. Listagem da chave primária e da data de publicação dos livros publicados há mais de 5 anos.
   
6. Listagem dos livros com menos de 5 exemplares disponíveis, ordenados por título.
  
7. Listagem dos livros que nunca foram emprestados.
   
8. Listagem do título do livro e nome do autor de todos os livros cadastrados.

9. Listagem da data de empréstimo, nome do membro e título do livro de empréstimos feitos no último ano.

10. Listagem do nome da categoria e título de todos os livros.

11. Listagem do título do livro, data de empréstimo e devolução de todos os livros.

12. Listagem completa dos empréstimos com nome do membro, título, categoria e autor.

13. Contagem total de livros cadastrados.

14. Contagem de empréstimos feitos no ano anterior.

15. Listagem da quantidade de livros por categoria.

16. Listagem dos livros emprestados na semana atual, com nome do membro e data.

17. Total de livros emprestados no ano atual por mês (mês por extenso).

18. Atualização da data de devolução de todos os empréstimos para a data atual.

19. Exclusão dos membros que nunca fizeram empréstimo.

<br>

### Tópicos:

- Manipulação de dados

```sql
UPDATE Emprestimo
SET DtaDevolucao = CURDATE();
```

<br>

- Agregação de informações 

```sql
SELECT C.Genero, COUNT(L.Id) AS QtdLivros
FROM Categoria C 
INNER JOIN Livro L 
ON C.Id = L.Categoria
GROUP BY C.Id;
```

<br>

- Filtragem de dados

```sql
SELECT Titulo
FROM Livro
WHERE Id NOT IN (SELECT LivroId FROM Emprestimo);
```

<br>

- Junção entre tabelas

```sql
SELECT DtaEmprestimo, DtaDevolucao, M.Nome, L.Titulo, C.Genero, A.Nome
FROM Emprestimo E
INNER JOIN Membro M 
ON E.MembroId = M.Id
INNER JOIN Livro L 
ON E.LivroId = L.Id
INNER JOIN Categoria C 
ON L.Categoria = C.Id
INNER JOIN Autor A 
ON L.AutorId = A.Id;
```

<br> <br>

