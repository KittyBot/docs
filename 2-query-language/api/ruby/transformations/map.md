---
layout: api-command 
language: Ruby
permalink: api/ruby/map/
command: map 
github_doc: https://github.com/rethinkdb/docs/edit/master/2-query-language/api/ruby/transformations/map.md
related_commands:
    concat_map: concat_map/
    reduce: reduce/
---

{% apibody %}
sequence.map(mapping_function) → stream
array.map(mapping_function) → array
{% endapibody %}

Transform each element of the sequence by applying the given mapping function.

__Example:__ Construct a sequence of hero power ratings.

```rb
r.table('marvel').map {|hero|
    hero[:combat_power] + hero[:compassion_power] * 2
}.run(conn)
```

