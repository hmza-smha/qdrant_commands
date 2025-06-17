# Qdrant Commands
---

### ✅ 1. **List all collections**

```bash
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/collections
```

---

### ✅ 2. **Get collection info (metadata & config)**

```bash
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/collections/your_collection_name
```

---

### ✅ 3. **List points in a collection (first 10)**

```bash
curl -X POST http://localhost:6335/collections/your_collection_name/points/scroll \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{"limit": 10}'
```

---

### ✅ 4. **Get a specific point by ID**

```bash
curl http://localhost:6335/collections/your_collection_name/points/1 \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2"
```

---

### ✅ 5. **Search similar vectors**

```bash
curl -X POST http://localhost:6335/collections/your_collection_name/points/search \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{
    "vector": [0.1, 0.2, 0.3],
    "top": 5
}'
```

---

### ✅ 6. **Count points in a collection**

```bash
curl -X POST http://localhost:6335/collections/your_collection_name/points/count \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{"exact": true}'
```

---

### ✅ 7. **Check collection aliases**

```bash
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/aliases
```

---

### ✅ 8. **List cluster info / health**

```bash
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/cluster
```

---

### ✅ 9. **Get service info**

```bash
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335
```

---

### ✅ 10. **Get collection field schema (indexed fields)**

```bash
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/collections/your_collection_name/index
```

---

## Basic Search API (by Vector)

Endpoint:

```
POST /collections/{collection_name}/points/search
```

Full example using your API key and curl:

```
curl -X POST http://localhost:6335/collections/your_collection_name/points/search \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{
    "vector": [0.12, 0.34, 0.56, 0.78], 
    "top": 5
  }'
```

vector: The query vector to search against.

top: Number of nearest neighbors to return.

✅ Search with Metadata Filter

Add "filter" to restrict by payload (e.g. "category": "news"):

```
curl -X POST http://localhost:6335/collections/your_collection_name/points/search \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{
    "vector": [0.12, 0.34, 0.56, 0.78],
    "top": 5,
    "filter": {
      "must": [
        {
          "key": "category",
          "match": { "value": "news" }
        }
      ]
    }
  }'
```

✅ Search by Point ID (Vector of an Existing Point)

If you want to search using the vector of a point that already exists:
```
curl -X POST http://localhost:6335/collections/your_collection_name/points/search \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{
    "id": 42,
    "top": 5
  }'
```
This searches using the vector of point ID 42.

📌 API Reference Docs

The full OpenAPI spec is available here (if enabled on your server):

```
http://localhost:6335/openapi.json
```

Or use their public docs:👉 https://qdrant.tech/documentation/concepts/search/



