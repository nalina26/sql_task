### sql_task
## 1. DB overview (conventions, charset, logging)
##### The database in question contains a few components that could be found in a classic bank system database, meaning that it has tables regarding users(customers), bank accounts, transactions, access(for login purpose) and identification ids data. 
##### The schema is called `bank_cgf` and it is built in `MySQL Workbench`. 
##### The `character set` is set to `utf8` and `collation` is set to `default`.
##### As for the conventions, the db is built taking into consideration `naming conventions`: each identifier is in `lowercase` (e.g: address, expiry); words are separated with `underscores` (e.g: first_name, last_name); contains only a few abbreviations; tables, for example, have `singular names`(e.g: account, transaction) to easily establish relations; `table prefix` is used for ids(e.g: account_id, transaction_id); constraints have also descriptive names. (see EER_diagram)

## 2. Tables
##### Tables structure:
		customer(user_id - pk, act_id - fk, first_name, last_name, gender, phone_no, CNP, occupation, dob, email)
		access(access_id - pk, user_id - fk, user, pass, last_login)
		act(act_id - pk, act_number, address, expiry)
		account(account_id - pk, user_id - fk, account_no, currency, IBAN, SWIFT)
		transaction(transaction_id - pk, account_id - fk, IBAN_s, IBAN_d, amount, currency, tr_date)
##### Relations
		customer -- 1:1 -- access
		customer -- 1:1 -- act
		customer -- 1:m -- account
		account -- 1:m -- transaction
##### The relations are set within logic context.		

## 3. Constraints, values and data types
