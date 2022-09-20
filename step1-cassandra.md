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
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 1 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step2-cassandra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">DataStax Bulk Loader</div>

DataStax Bulk Loader (DSBulk) is an efficient, flexible, easy-to-use and free command-line utility for Apache Cassandra™ 
that excels at loading, unloading and counting data. You should use DSBulk to:

- Load data from CSV or JSON files into the database
- Unload data stored in the database into CSV or JSON files
- Quickly count the number of rows in a given table

DSBulk is a good choice for small, medium and large datasets. It gets data in and out of the database 
significantly faster than individual `INSERT`s, the `COPY` command or other community tools. Only for very large datasets 
that reside in a distributed file system, a potentially faster alternative to DSBulk 
could be data loading with Apache Spark.

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"intro"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step2-cassandra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
