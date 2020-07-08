### sql_task
## 1. DB overview (conventions, charset, logging)
#####  A database is an organized collection of structured information or data. The database in question contains a few components that could be found in a classic bank system database, meaning that it has tables regarding users(customers), bank accounts, transactions, access(for login purpose) and identification ids data. 
##### The schema is called `bank_cgf` and it is built in `MySQL Workbench`. 
##### The `character set` is set to `utf8` and `collation` is set to `default`.
##### As for the conventions, the db is built taking into consideration `naming conventions`: each identifier is in `lowercase` (e.g: address, expiry); words are separated with `underscores` (e.g: first_name, last_name); contains only a few abbreviations; tables, for example, have `singular names`(e.g: account, transaction) to easily establish relations; `table prefix` is used for ids(e.g: account_id, transaction_id); foreign keys have also descriptive names to easily identify the refference table. (see EER_diagram)

## 2. Tables
##### Tables structure:
		customer(user_id as pk, act_id as fk, first_name, last_name, gender, phone_no, CNP, occupation, dob, email)
		access(access_id as pk, user_id as fk, user, pass, last_login)
		act(act_id as pk, act_number, address, expiry)
		account(account_id as pk, user_id as fk, account_no, currency, IBAN, SWIFT)
		transaction(transaction_id as pk, account_id as fk, IBAN_s, IBAN_d, amount, currency, tr_date)
##### Relations:
		customer -- 1:1 -- access
		customer -- 1:1 -- act
		customer -- 1:m -- account
		account -- 1:m -- transaction
##### The relations are set taking into consideration the logical flow.		

## 3. Constraints, values and data types
##### Constraints are used to specify rules for data in a table. Usually, when it comes to a bank database, `NOT NULL` constraint is frequently encountered to ensure that a column cannot have a NULL value (e.g: IBAN, account_no), `PRIMARY KEY` and `FOREIGN KEY` are used for id attributes to also establish unicity and to link tables.
##### Usage of correct data types and character length is also important especially in this case when it comes to storing values in a standardized format(e.g: IBAN, account_no, SWIFT, CNP).
##### There is a particular data type that also required a function, in this case `TIMESTAMP` columns can be automatically initialized and updated to the current date and time (that is, the current timestamp). For example, `last_login` with both `DEFAULT CURRENT_TIMESTAMP` and `ON UPDATE CURRENT_TIMESTAMP`, the column has the current timestamp for its default value and is automatically updated to the current timestamp. 
##### As for values, it is worth mentioning that in the `pass`(user password) column, storing passwords should be done by hashing.

## 4. Optimization
##### IBAN can be parsed to extract country code, bank code (usually for Ro) and account number.
##### CNP can be checked if valid or correctly stored by comparing with dob (date of birth) and viceversa.
##### Values stored in `user_id` column, for example, should be generated as a combination of alphanumeric characters, let's say, first 2 characters of `user_id` to match first 2 characters of `user` (username) or other identification attribute. Same rule could also be applied to other `id` attributes.
