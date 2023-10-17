# postgresql

## begin work. transaction

The `BEGIN WORK` command in psql is used to start a transaction. A transaction is a unit of work that is performed on the database, and it ensures that all of the changes made within the transaction are either committed or rolled back.

To start a transaction in psql, you simply type the `BEGIN WORK` command and then press Enter. You can then execute any SQL statements that you want to include in the transaction. To commit the transaction, type the `COMMIT` command and press Enter. To roll back the transaction, type the `ROLLBACK` command and press Enter.

Here is an example of a simple transaction in psql:

```
BEGIN WORK;

INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
UPDATE users SET name = 'Jane Doe' WHERE id = 1;

COMMIT;
```

This transaction will insert a new user into the `users` table and then update the name of the user with the ID 1 to `Jane Doe`. If either of these statements fails, the entire transaction will be rolled back and the database will be returned to its previous state.

It is important to note that transactions are not enabled by default in psql. To enable transactions, you can add the following line to your `.bashrc` file:

```
export PGOPTIONS="--autocommit=off"
```

Once you have enabled transactions, you will need to start a transaction explicitly using the `BEGIN WORK` command before you can make any changes to the database.

Transactions are useful for ensuring that your database is always in a consistent state. For example, if you are transferring money between two accounts, you would want to use a transaction to ensure that either both transfers are successful or neither of them are successful.

## begin vs begin work

The `BEGIN` and `BEGIN WORK` commands in psql are functionally equivalent. Both commands are used to start a transaction.

The only difference between the two commands is that `BEGIN` is the SQL-standard command, while `BEGIN WORK` is a PostgreSQL extension.

The `BEGIN WORK` command is more commonly used in psql because it is more verbose and easier to remember. The `BEGIN` command is typically used in scripts or when writing SQL code that needs to be compatible with other database systems.

Here is an example of how to use the `BEGIN` and `BEGIN WORK` commands:

```
-- BEGIN
INSERT INTO users (name, email) VALUES ('John Doe', 'john.doe@example.com');
UPDATE users SET name = 'Jane Doe' WHERE id = 1;
COMMIT;

-- BEGIN WORK
INSERT INTO users (name, email) VALUES ('Jane Doe', 'jane.doe@example.com');
UPDATE users SET name = 'John Doe' WHERE id = 1;
COMMIT;
```

Both of these code blocks will produce the same result: two new users will be inserted into the `users` table, and the name of the user with the ID 1 will be updated to `Jane Doe`.

Which command you use to start a transaction is a matter of personal preference. However, I recommend using the `BEGIN WORK` command because it is more verbose and easier to remember.
