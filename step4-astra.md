<!-- TOP -->
<div class="top">
  <img class="scenario-academy-logo" src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-2023.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Bulk Loading Large Datasets into Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 4 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step5-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Loading users</div>

Our first task is to load user data from file `users.csv` with header fields `user_id`, `gender` and `age` 
into table `users` with columns `id`, `gender` and `age`. 

✅ Output the first five lines from the file:
```
head -n 5 assets/users.csv
```

✅ Verify that the table is empty:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  TRUNCATE TABLE users;
  SELECT * FROM users LIMIT 5;"
```

Since the file field names and the table column names do no match exactly, 
we have to map fields to columns explicitly. There 
are many ways to do this as we demonstrate in the following examples.

✅ Load data (name-to-name mapping):
```
astra db load cassandra-fundamentals        \
            -url assets/users.csv           \
            -k ks_bulk_loading              \
            -t users                        \
            -header true                    \
            -m "user_id=id,                 \
                gender=gender,              \
                age=age"                    \
            -logDir /tmp/logs
```

✅ Load data (position-to-name mapping): 
```
astra db load cassandra-fundamentals        \
            -url assets/users.csv           \
            -k ks_bulk_loading              \
            -t users                        \
            -header true                    \
            -m "0=id,                       \
                1=gender,                   \
                2=age"                      \
            -logDir /tmp/logs
```

✅ Load data (skip the file header and specify the column names): 
```
astra db load cassandra-fundamentals        \
            -url assets/users.csv           \
            -k ks_bulk_loading              \
            -t users                        \
            -header false                   \
            -skipRecords 1                  \
            -m "id, gender, age"            \
            -logDir /tmp/logs
```

✅ Output five rows from the table:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  SELECT * FROM users LIMIT 5;"
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step5-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

