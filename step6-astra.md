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
 <a href='command:katapod.loadPage?[{"step":"step5-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 6 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step7-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Loading ratings</div>

Let's load movie ratings from file `ratings.csv` 
into tables `ratings_by_user` and `ratings_by_movie`. 

✅ Output the first five lines from the file:
```
head -n 5 assets/ratings.csv
```

✅ Verify that the tables are empty:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  TRUNCATE TABLE movies;
  SELECT * FROM ratings_by_user LIMIT 5;"
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  TRUNCATE TABLE movies;
  SELECT * FROM ratings_by_movie LIMIT 5;"
```

Notice that the file field names and the table column names match. We do not 
need to provide an explicit mapping this time.

✅ Load data into table `ratings_by_user`:
```
astra db load cassandra-fundamentals        \
            -url assets/ratings.csv         \
            -k ks_bulk_loading              \
            -t ratings_by_user              \
            -header true                    \
            -logDir /tmp/logs
```

✅ Load data into table `ratings_by_movie`:
<details>
  <summary>Solution</summary>

```
astra db load cassandra-fundamentals        \
            -url assets/ratings.csv         \
            -k ks_bulk_loading              \
            -t ratings_by_movie             \
            -header true                    \
            -logDir /tmp/logs
```

</details>

<br/>

✅ Output five rows from each table:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  SELECT * FROM ratings_by_user LIMIT 5;"
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  SELECT * FROM ratings_by_movie LIMIT 5;"
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step5-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step7-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

