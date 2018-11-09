Sobre o banco de dados "classicmodels", indique as queries para obter as seguintes informações:

- Quantos registros há na tabela "customers"?
select count(*) from customers;
122

- Na tabela "customers", quantos clientes ("customerName") têm nome iniciado pela letra "M"?
select count(*) from customers where customerName like "M%";
14

- Na tabela "customers", crie uma saída que concatene nomes e sobrenomes em uma única coluna.
select concat(contactFirstName, ' ' , contactLastName) as saida_nome from customers;

- Agora repita a query acima, mas com todas as letras em maiúsculo, e ordene pelo sobrenome.
select upper(concat(contactFirstName, ' ' , contactLastName)) as saida_nome from customers order by contactLastName;

- Na tabela "payments", selecione os registros ordenados por volume ("amount") e data de pagamento ("paymentDate")
select * from payments order by amount;order by paymentDate;

- Na tabela "employees", indique quantos nomes de cargos ("jobTitle") únicos existem? 
select count(distinct(jobTitle)) from employees;

- Qual destes cargos ("jobTitle") possuem mais funcionários?
Sales Rep

select distinct(jobTitle) from employees;
select count(jobTitle) from employees where jobTitle = 'President' ;
1
select count(jobTitle) from employees where jobTitle = 'VP Sales' ;
1
select count(jobTitle) from employees where jobTitle = 'VP Marketing' ;
1
select count(jobTitle) from employees where jobTitle = 'Sales Manager (APAC)' ;
1
select count(jobTitle) from employees where jobTitle = 'Sale Manager (EMEA)' ;
1
select count(jobTitle) from employees where jobTitle = 'Sales Manager (NA)' ;
1
select count(jobTitle) from employees where jobTitle = 'Sales Rep' ;
17

select jobTitle, count(jobTitle) from employees group by jobTitle;
select max(primeira.soma) as resultado from (select jobTitle, count(jobTitle) as soma from employees group by jobTitle) as primeira;