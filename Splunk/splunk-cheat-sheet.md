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





A cheat sheet for using Splunk search queries to discover and filter data, especially when you're unsure about the source, host, index, or sourcetype:

#### Exploring Unknown Data

1. **Search for All Data**:
   ```spl
   index=*
   ```
   Retrieves all events across all indexes.

2. **Identify Source and Sourcetype**:
   ```spl
   index=* | stats count by source sourcetype
   ```
   Provides a count of events grouped by their source and sourcetype.

3. **Identify Host**:
   ```spl
   index=* | stats count by host
   ```
   Lists hosts and the count of events from each host.

4. **Explore Data Fields**:
   ```spl
   index=* | fieldsummary
   ```
   Summarizes all fields in your data, including value distributions.

5. **Refine Searches**:
   ```spl
   index=* sourcetype=<your_sourcetype>
   ```
   Searches data from a specific sourcetype.

6. **Use Metadata Commands**:
   ```spl
   | metadata type=sources index=*      // Lists all sources
   | metadata type=sourcetypes index=*  // Lists all sourcetypes
   | metadata type=hosts index=*        // Lists all hosts
   ```
   Quickly see the different sources, sourcetypes, and hosts in your Splunk instance.

### Filtering Events by Field Value

1. **Exclude Specific Field Value**:
   ```spl
   Source_Country!="United States"
   ```

2. **Basic Search with Exclusion**:
   ```spl
   index=* Source_Country!="United States"
   ```

3. **Search within a Specific Index**:
   ```spl
   index=my_index Source_Country!="United States"
   ```

4. **Adding Additional Conditions**:
   ```spl
   index=my_index sourcetype=my_sourcetype Source_Country!="United States"
   ```

5. **Using Field Filtering in a Table**:
   ```spl
   index=my_index | where Source_Country!="United States" | table _time, Source_Country, other_field
   ```

### Counting Events from All Countries Except One

```spl
index=* Source_Country=* NOT Source_Country="France" | stats count
```
- `index=*`: Searches across all indexes.
- `Source_Country=*`: Considers only events with the `Source_Country` field.
- `NOT Source_Country="France"`: Excludes events where `Source_Country` is "France".
- `| stats count`: Counts the number of events that meet the criteria.

### Counting VPN Events by IP

1. **Basic Search with Known VPN Sourcetype**:
   ```spl
   index=* sourcetype=<vpn_sourcetype> src_ip=107.3.206.58 | stats count
   ```
   Replace `<vpn_sourcetype>` with the actual sourcetype for VPN events.

2. **Basic Search with Known Source**:
   ```spl
   index=* source=<vpn_source> src_ip=107.3.206.58 | stats count
   ```
   Replace `<vpn_source>` with the actual source for VPN events.

3. **Keyword Search**:
   ```spl
   index=* src_ip=107.3.206.58 VPN | stats count
   ```
   Searches for events containing the keyword "VPN".

4. **General Search and Filtering**:
   ```spl
   index=* src_ip=107.3.206.58 | search VPN | stats count
   ```

### Example Search Queries

1. **Find all events from a specific IP address**:
   ```spl
   index=* src_ip="107.3.206.58"
   ```

2. **Count events by source type**:
   ```spl
   index=* | stats count by sourcetype
   ```

3. **Get a table of events with specific fields**:
   ```spl
   index=* | table _time, src_ip, dest_ip, user
   ```

4. **Calculate average response time**:
   ```spl
   index=* sourcetype=access_combined | stats avg(response_time)
   ```

5. **Count VPN events observed by a specific IP**:
   ```spl
   index="vpn_logs" | spath Source_ip | search Source_ip="107.3.206.58" | stats count
   ```

This cheat sheet covers essential Splunk search queries for discovering and analyzing your data. Adjust the examples based on your specific needs and Splunk environment.

### Additional Resources

- **Splunk Documentation**: Comprehensive guides and tutorials [here](https://docs.splunk.com/Documentation/Splunk/latest/SearchTutorial/WelcometotheSearchTutorial).
- **Splunk Answers**: Community-driven Q&A for troubleshooting and tips [here](https://community.splunk.com/).



