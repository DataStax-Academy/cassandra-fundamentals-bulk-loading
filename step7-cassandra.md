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
 <a href='command:katapod.loadPage?[{"step":"step6-cassandra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 7 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"finish-cassandra"}]'
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Unloading and counting</div>

Finally, take a look at how commands `unload` and `count` can be used to 
export data from Cassandra and compute simple row counts. 

✅ Unload all rows from table `ratings_by_movie`:
```
dsbulk unload -url all_ratings    \
              -k ks_bulk_loading  \
              -t ratings_by_movie \
              -header true        \
              -logDir /tmp/logs 
```

✅ Unload rows from table `ratings_by_movie` using a query:
```
dsbulk unload -url m267_ratings   \
              -k ks_bulk_loading  \
              -query "            \
SELECT *                          \
FROM ratings_by_movie             \
WHERE movie_id = 'm267'"          \
              -header true        \
              -logDir /tmp/logs 
```

✅ Check the resulting CSV files:
```
head -n 5 all_ratings/*
head -n 5 m267_ratings/*
```

✅ Count all rows in table `ratings_by_movie`:
```
dsbulk count  -k ks_bulk_loading  \
              -t ratings_by_movie \
              -logDir /tmp/logs 
```

✅ Count rows in table `ratings_by_movie` using a query:
```
dsbulk count  -k ks_bulk_loading  \
              -query "            \
SELECT *                          \
FROM ratings_by_movie             \
WHERE movie_id = 'm267'"          \
              -logDir /tmp/logs 
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step6-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"finish-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>

