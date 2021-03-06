---
layout: api-command
language: JavaScript
permalink: api/javascript/table_create/
command: tableCreate
io:
    -   - db
        - table
related_commands:
    tableList: table_list/
    tableDrop: table_drop/
---

# Command syntax #

{% apibody %}
db.tableCreate(tableName[, options]) &rarr; object
{% endapibody %}

# Description #

<img src="/assets/images/docs/api_illustrations/table_create_javascript.png" class="api_command_illustration" />

Create a table. A RethinkDB table is a collection of JSON documents.

If successful, the operation returns an object: `{created: 1}`. If a table with the same
name already exists, the operation throws `RqlRuntimeError`.

Note: that you can only use alphanumeric characters and underscores for the table name.


When creating a table you can specify the following options:

- `primaryKey`: the name of the primary key. The default primary key is id;
- `durability`: if set to `'soft'`, this enables _soft durability_ on this table:
writes will be acknowledged by the server immediately and flushed to disk in the
background. Default is `'hard'` (acknowledgement of writes happens after data has been
written to disk);
- `datacenter`: the name of the datacenter this table should be assigned to.



__Example:__ Create a table named 'dc_universe' with the default settings.

```js
r.db('test').tableCreate('dc_universe').run(conn, callback)
```

__Example:__ Create a table named 'dc_universe' using the field 'name' as primary key.

```js
r.db('test').tableCreate('dc_universe', {primaryKey: 'name'}).run(conn, callback)
```

__Example:__ Create a table to log the very fast actions of the heroes.

```js
r.db('test').tableCreate('dc_universe', {durability: 'soft'}).run(conn, callback)
```

