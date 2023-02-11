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
 <a href='command:katapod.loadPage?[{"step":"step2-cassandra"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step4-cassandra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Connect to Cassandra and create a keyspace and tables</div>

✅ Start Cassandra:
```
./cassandra
```

✅ Create the keyspace and four tables using the CQL shell:
```
cqlsh -e "

CREATE KEYSPACE IF NOT EXISTS ks_bulk_loading
WITH replication = {
  'class': 'NetworkTopologyStrategy', 
  'DC-Houston': 1 };

USE ks_bulk_loading;

CREATE TABLE IF NOT EXISTS users (
  id TEXT,
  gender TEXT,
  age INT,
  PRIMARY KEY ((id))
);

CREATE TABLE IF NOT EXISTS movies (
  id TEXT,
  title TEXT,
  year INT,
  duration INT,
  country TEXT,
  PRIMARY KEY ((id))
);

CREATE TABLE IF NOT EXISTS ratings_by_user (
  user_id TEXT,
  movie_id TEXT,
  rating INT,
  PRIMARY KEY ((user_id), movie_id)
);

CREATE TABLE IF NOT EXISTS ratings_by_movie (
  movie_id TEXT,
  user_id TEXT,
  rating INT,
  PRIMARY KEY ((movie_id), user_id)
);"
```

✅ Verify that the four tables have been created:
```
cqlsh -k ks_bulk_loading -e "DESCRIBE TABLES;"
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2-cassandra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
