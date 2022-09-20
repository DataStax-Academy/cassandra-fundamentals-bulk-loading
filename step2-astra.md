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
 <a href='command:katapod.loadPage?[{"step":"step1-astra"}]'
   class="btn btn-dark navigation-top-left">⬅️ Back
 </a>
<span class="step-count"> Step 2 of 7</span>
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]' 
    class="btn btn-dark navigation-top-right">Next ➡️
  </a>
</div>

<!-- CONTENT -->

<div class="step-title">DSBulk commands and options</div>

DSBulk usage:
<pre class="non-executable-code">
dsbulk <command> [options]
</pre>

DSBulk supports the following three commands:

| Command  | Description |
|----------|-------------|
| `load`   | Load data from external files into Apache Cassandra™   |
| `unload` | Unload data from Apache Cassandra™ into files | 
| `count`  | Compute statistics about a Cassandra table, such as the total number of rows and other metrics |

DSBulk has dozens of options. Here are some of the most common ones:

| Option        | Description |
|---------------|-------------|
| `url`         | URL or path of the resource(s) to read from or write to |
| `k`           | Keyspace used for loading/unloading/counting    |
| `t`           | Table used for loading/unloading/counting  | 
| `m`           | Mapping from file fields to table columns  |
| `cl`          | Consistency level to use for reading or writing (`LOCAL_ONE` is the default) |
| `header`      | Enable or disable whether the files to read or write begin with a header line |
| `logDir`      | Directory for logs (current directory is the default) |
| `query`       | CQL statement to use for loading/unloading/counting |
| `skipRecords` | Number of non-header lines to skip when reading a file |

You can learn more about these and other options from the help page:
```
dsbulk help
```

<!-- NAVIGATION -->
<div id="navigation-bottom" class="navigation-bottom">
 <a href='command:katapod.loadPage?[{"step":"step1-astra"}]'
   class="btn btn-dark navigation-bottom-left">⬅️ Back
 </a>
 <a href='command:katapod.loadPage?[{"step":"step3-astra"}]'
    class="btn btn-dark navigation-bottom-right">Next ➡️
  </a>
</div>
