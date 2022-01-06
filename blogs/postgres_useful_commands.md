## **Dump the query results to .csv**

[How do you print the result of a PostgreSQL query in CSV or TSV format from the command line?](https://stackoverflow.com/questions/6521531/how-do-you-print-the-result-of-a-postgresql-query-in-csv-or-tsv-format-from-the)

```sql
psql -d <database_name> -c "<command>" -A -F , -X -o <file_name.csv>
```

```sql
Copy (select * from users) To '/tmp/sample_data.csv' With CSV DELIMITER ',' HEADER;
```

## **Terminate active connections to the database**

[PostgreSQL DROP DATABASE](https://www.postgresqltutorial.com/postgresql-drop-database/)

```sql
SELECT pg_terminate_backend (pg_stat_activity.pid) 
FROM pg_stat_activity 
WHERE pg_stat_activity.datname = 'process_designer';
```

## **Generate a SQL with specified columns not present**

```sql
SELECT 'SELECT ' || string_agg('o' || '.' || c.column_name, ', ') || ' FROM ' || table_name || ' o' As sqlstmt
FROM information_schema.columns As c
WHERE table_name = 'office' AND
      c.column_name NOT IN ('id', 'deleted')
GROUP BY c.table_name;
```

---

## Create a copy of psql database.

```sql
CREATE DATABASE <new_database_name> template <old_database_name>
```

## Updating size of varchar in Postgres column

```sql
alter table <table_name> alter COLUMN <column_name> type varchar(<new_size>);
```

## Get data greater than <n> days

```sql
select * from users where created_at < (CURRENT_DATE - INTERVAL '30 days');
```