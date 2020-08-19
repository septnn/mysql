# [TODO] Glossary

- <span id="Glossary_DML">DML

Data manipulation language, a set of SQL statements for performing INSERT, UPDATE, and DELETE operations. The SELECT statement is sometimes considered as a DML statement, because the SELECT ... FOR UPDATE form is subject to the same considerations for locking as INSERT, UPDATE, and DELETE.

数据操作语言

DML statements for an InnoDB table operate in the context of a transaction, so their effects can be committed or rolled back as a single unit.

Contrast with DDL and DCL.

See Also commit, DCL, DDL, locking, rollback, SQL, transaction.