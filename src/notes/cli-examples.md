# CLI examples

Create a schema
```bash
echo '{"properties": { "title": { "type": "string", "title":"Title" },"body":{"type":"string","title":"Body"}, "topic": { "title":"Topic","type": "array", "items": {"type":"string"}}}}' | node cli -i hello  db put-schema doc

```
