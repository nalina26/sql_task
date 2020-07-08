### sql_task

## 1. DB overview (conventions, charset, logging)
##### The database in question contains a few components that could be found in a classic bank system database, meaning that it has tables regarding users(customers), bank accounts, transactions, access(for login purpose) and identification ids data. 
##### The schema is called `bank_cgf` and it is built in `MySQL Workbench`. 
##### The `character set` is set to `utf8` and `collation` is set to `default`.
##### As for the conventions, the db is built taking into consideration a `naming conventions`: each identifier is in `lowercase` (e.g: address, expiry); words are separated with `underscores` (e.g: first_name, last_name); contains only a few abbreviations; tables, for example, have `singular names`(e.g: account, transaction) to easily establish relations; `table prefix` is used for ids(e.g: account_id, transaction_id); constraints have also descriptive names.

		
