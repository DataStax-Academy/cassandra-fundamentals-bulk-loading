<!-- TOP -->
<div class="top">
  <img src="https://datastax-academy.github.io/katapod-shared-assets/images/ds-academy-logo.svg" />
  <div class="scenario-title-section">
    <span class="scenario-title">Bulk Loading Large Datasets into Apache Cassandra®</span>
    <span class="scenario-subtitle">ℹ️ For technical support, please contact us via <a href="mailto:aleksandr.volochnev@datastax.com">email</a> or <a href="https://dtsx.io/aleks">LinkedIn</a>.</span>
  </div>
</div>

<!-- NAVIGATION -->
<div id="navigation-top" class="navigation-top">
 <a href='command:katapod.loadPage?[{"step":"step4-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 5 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step6-astra"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Loading movies</div>

Next, load movie data from file `movies.csv` 
into table `movies`. 

✅ Output the first five lines from the file:
```
head -n 5 assets/movies.csv
```

✅ Verify that the table is empty:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  TRUNCATE TABLE movies;
  SELECT * FROM movies LIMIT 5;"
```

✅ Load data:
<details>
  <summary>Solution</summary>

```
astra db load cassandra-fundamentals        \
            -url assets/movies.csv          \
            -k ks_bulk_loading              \
            -t movies                       \
            -header true                    \
            -m "movie_id=id,                \
                title=title,                \
                year=year,                  \
                duration=duration,          \
                country=country"            \
            -logDir /tmp/logs
```

</details>

<br/>

✅ Output five rows from the table:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "
  SELECT * FROM movies LIMIT 5;"
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step4-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step6-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

