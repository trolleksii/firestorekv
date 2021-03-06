# FirestoreKV

Small CLI tool to store/retrieve key/value pairs in GCP Firestore(in Datastore mode).

## How to use it

Accessing the Firestore will require the Service Account with 'Cloud Datastore User' Role granted. Download the Service Account key file and store it as `credentials.json`.

```SH
export GOOGLE_APPLICATION_CREDENTIALS="credentials.json"
export GOOGLE_PROJECT_ID="my_project123"
```

There are 3 commands implemented: `get`, `put`, and `clean`.

### Storing values

The syntax is following:

```SH
./firestorekv put <KIND> <KEY> <VALUE>
```

For example:

```SH
./firestorekv put numbers the_number 42
```

### Retrieving values

The syntax is following:

```SH
./firestorekv get <KIND> <KEY>
```

For example:

```SH
./firestorekv get numbers the_number
```

### Cleanup old key/value pairs

All key/value pairs get timestamp field during creation/update. This allows to cleanup old entities.

The syntax is following:

```SH
./firestorekv clean <TIMESTAMP>
```

For example:

```SH
week_ago=$(date --date="7 days ago" +%s)
./firestorekv clean passwords $week_ago
```
