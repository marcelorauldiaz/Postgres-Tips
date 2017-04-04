
## The Statistics Collector

# View activity

```
SELECT pid, client_addr,query FROM pg_stat_activity 
```

PID|HOST|QUERY 
---|---|------
13102|	132.147.176.223	| select * from blabla
13369|	127.0.0.1	|select * from long_table where blablab
13358|	127.0.0.1	|select my_preocedure()
13359|	127.0.0.1	|select * from stuff
13360|	127.0.0.1	|select currval('seq_serie')
13522|	132.147.176.223| SELECT pid, client_addr,query FROM pg_stat_activity


#Cancel a backend's current query

```
pg_cancel_backend( PID )
```

===================================================================================
## Backup & Restore

# Restore specific table

```
pg_restore -a -Fc -d databasename --schema="some_schema" --table="my_table" /temp/file_dump.dmp
 ``` 

file_dump previously was create with pg_dump

 ```
 pg_dump -U postgres -Fc -f  /temp/file_dump.dmp
 ```
===================================================================================

## Array to String

# Query return more than one tuple.

 ```
select project_id from companies where id=1
 ```
 project_id |
 -----------|
 1|
 2|
 
 The above sometimes it's not useful, then to view it in one cell, just do:
 
 ```
select array_to_string( array(select project_id from companies where id=1), ', ') as  projects
 ```
projects   |
-----------|
1,2|
 












