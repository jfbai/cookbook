# jq examples

## Given a list of objects and filter out objects whose keys contains specific keyword

Given a list of objects in file `objects.txt`,

```
[
  {"name": "foo", "age": 12},
  {"name": "foo1", "age": 12},
  {"name": "bar", "age": 12},
  {"name": "bar", "age": 12}
]
```

filter out `name` is `bar`,

```
jq -c '.[] | select(.name | . and contains("bar"))' objects.txt

output:

{"name": "bar", "age": 12}
{"name": "bar", "age": 12}
```

or filter out `name` is **not** `bar`,

```
jq -c '.[] | select(.name | . and contains("bar") | not)' objects.txt

output:

{"name": "foo", "age": 12}
{"name": "foo1", "age": 12}
```

and maps to a new object,

```
jq -c '.[] | select(.name | . and contains("bar") | not) | {new_name: .name} ' objects.txt

output:

{"new_name": "foo"}
{"new_name": "foo1"}

```

then construct a list,

```
jq -c '[ .[] | select(.name | . and contains("bar") | not) ]' objects.txt

output:

[{"name": "foo", "age": 12},{"name": "foo1", "age": 12}]
```
