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
 <a href='command:katapod.loadPage?[{"step":"step2-astra"}]' 
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 3 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step4-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">Connect to Astra DB and create a database</div>

✅ Create an application token with the *Database Administrator* role to access Astra DB. Skip this step is you already have a token.

<ul>
  <li>Sign in (or sign up) to your Astra account at <a href="https://astra.datastax.com" target="_blank">astra.datastax.com</a></li>
  <li>Create an application token with the <i>Database Administrator</i> role by following <a href="https://awesome-astra.github.io/docs/pages/astra/create-token/" target="_blank">these instructions</a></li>
</ul>

You can reuse the same token in our other labs, too.

✅ Setup Astra CLI by providing your application token:
```
astra setup
```

✅ List your existing Astra DB databases:
```
astra db list
```

✅ Create database `cassandra-fundamentals` and keyspace `ks_bulk_loading` if they do not exist:
```
astra db create cassandra-fundamentals -k ks_bulk_loading --if-not-exist --wait
```

This operation may take a bit longer when creating a new database or resuming an existing hibernated database.

✅ Verify that database `cassandra-fundamentals` is `ACTIVE` and keyspace `ks_bulk_loading` exists:
```
astra db get cassandra-fundamentals
```

✅ Create the tables:
```
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "

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
astra db cqlsh cassandra-fundamentals -k ks_bulk_loading -e "DESCRIBE TABLES;"
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step2-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step4-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
