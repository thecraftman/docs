<div class="axi-header">
  <h1>Ingesting Data</h1>
</div>

Ingest, transport and fetch data from different sources such as Relational database, web logs, batch data, real-time, application logs, streaming data, etc for later usage using the Axiom API. 

You can also Collect, load, group, move, data from one or more sources to Axiom where it can be stored and further analyzed.

Before ingesting data, you will need an API Token which you can generate from the **Settings->Tokens** page on the Axiom Dashboard. See [API Tokens documentation](/usage/settings#api-tokens).

<br />
 Once you have an ingest token, there are four ways to get your data into Axiom:

1. Using the [Ingest API](#ingest-api)
2. Using a [Data Shipper](#data-shippers) (Logstash, Filebeats, etc)
3. Using an [Integration](#integrations)
4. Using the [Elasticsearch Bulk API](#elasticsearch-bulk-api) that Axiom supports natively

## Ingest API

Axiom exports a simple REST API that can accept any of the following formats:

- `application/json` - single event or json array of events
- `application/nd-json`- structured data processed at a time
- `text/csv` - this should include the header line with field names

=== "cURL"

    ```bash
      curl -X POST \
        -H "Authorization: Bearer <INGEST_TOKEN>" \
        -H "Content-Type: application/x-ndjson" \
        -d '{ "this": "is", "an": "example", "json": 1 }' \
        https://<axiom-url>/api/v1/datasets/<my-dataset>/ingest
    ``` 

If you would like to instead use a language binding, currently our Golang client library is available:

- [axiom-go](https://github.com/axiomhq/axiom-go)

More client libraries are coming very soon!

### Limits

| Kind                      | Limit |
| ------------------------- | ----: |
| Maximum Event Batch Size  |  1000 |
| Maximum Event Fields      |   250 |
| Maximum Array Field Items |   100 |

## Data Shippers

Configure, read, collect, and Send logs to your Axiom deployment using a variety of log shippers. Data shippers are lightweight agents that acquire logs, metrics, and lets you ship data directly into Axiom. 

With the integration of Data shippers to ingest data into Axiom, it is easier for you to create custom built beats for any type of data you would like to send to Axiom. 


<a class="axi-link-button" href="/usage/integrations" title="Learn about integrations">
  <img src="/assets/integrate.svg" width=24 alt="integrations icon" />
  <span>Learn about integrations</span>
  <img src="/assets/chevron-right.svg" width=16 alt="go" />
</a>

## Elasticsearch Bulk API

By default, Axiom supports the ingestion of events by sending them to the [Elastic Bulk API](https://www.elastic.co/guide/en/elasticsearch/reference/6.7/docs-bulk.html) compatible endpoint at **/datasets/:dataset/elastic.** Only the index and create actions are supported, other actions are discarded.
