A cheat sheet for Splunk, covering essential commands and techniques for analyzing data. This guide should be helpful for quick reference:

### Splunk Basics

- **Login URL**: `http://<hostname>:8000`
- **Search Bar**: Where you enter search queries.
- **Time Picker**: Located at the top right to set the time range for searches.
- **Data Sources**: Inputs from various log files, directories, scripts, etc.

### Basic Search Commands

- **Simple Search**:
  - `error`: Finds events containing the keyword "error".
  - `host="server1"`: Finds events from the specified host.

- **Search with Time Range**:
  - `index=main error earliest=-1h`: Finds events with "error" in the last hour.

- **Field Filtering**:
  - `source="/var/log/syslog"`: Filters events from a specific source file.

### Commonly Used Commands

- **stats**: Provides statistical results.
  - `stats count by status`: Counts events grouped by the `status` field.

- **table**: Formats search results into a table.
  - `table _time, host, status`: Displays a table with `_time`, `host`, and `status` fields.

- **top**: Returns the most frequent values of a field.
  - `top status`: Displays the top values for the `status` field.

- **rex**: Extracts fields using regular expressions.
  - `rex field=_raw "user=(?<user>\w+)"`: Extracts `user` field from raw events.

### Advanced Search Techniques

- **Transforming Commands**:
  - `timechart`: Creates a time-based chart.
    - `timechart count by host`: Plots event counts by host over time.
  - `chart`: Creates a chart from search results.
    - `chart avg(response_time) by uri`: Charts average response time by URI.

- **Eval**: Evaluates an expression and creates a new field.
  - `eval response_time_ms=response_time*1000`: Converts response time to milliseconds.

- **Transaction**: Groups related events.
  - `transaction startswith="login" endswith="logout" maxspan=30m`: Groups login and logout events into a transaction with a maximum span of 30 minutes.

### Alerting and Reporting

- **Creating Alerts**:
  - Define a search query.
  - Set trigger conditions (number of results, custom condition).
  - Configure actions (email, script, etc.).

- **Scheduled Reports**:
  - `Settings > Searches, reports, and alerts > New Report`
  - Define search and schedule frequency.

### Dashboard and Visualization

- **Creating Dashboards**:
  - `Dashboard > Create New Dashboard`
  - Add panels with search queries.

- **Visualization Types**:
  - `Line Chart`: Best for time-based data.
  - `Bar Chart`: Good for categorical data comparison.
  - `Pie Chart`: Useful for showing proportions.
  - `Table`: Displays raw or aggregated data in tabular form.

### Splunk Search Language (SPL) Basics

- **Search Pipelines**: Use `|` to pipe results from one command to another.
  - `index=main | stats count by status`

- **Subsearches**: Nested searches within parentheses.
  - `index=main [search index=secondary error | fields session_id]`

- **Lookup**: Enriches events with external data.
  - `lookup user_details user_id OUTPUT user_name`

### Useful Shortcuts

- **Quickly Access Search History**: Use the up and down arrow keys in the search bar.
- **Save Search as Report**: Click on `Save As` > `Report`.
- **Save Search as Alert**: Click on `Save As` > `Alert`.

### Example Queries

- **Failed Login Attempts**:
  - `index=main sourcetype=auth action=failure | stats count by user`

- **HTTP Error Codes**:
  - `index=web sourcetype=access_combined status>=400 | stats count by status`

- **Top 10 IPs by Bandwidth**:
  - `index=netflow | stats sum(bytes) as total_bytes by src_ip | sort -total_bytes | head 10`

### Additional Resources

- **Splunk Documentation**: Comprehensive guides and tutorials [here](https://docs.splunk.com/Documentation/Splunk/latest/SearchTutorial/WelcometotheSearchTutorial).
- **Splunk Answers**: Community-driven Q&A for troubleshooting and tips [here](https://community.splunk.com/).



