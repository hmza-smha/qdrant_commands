✅ 1. List all collections



```curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/collections```

✅ 2. Get collection info (metadata & config)



```curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/collections/your_collection_name```

✅ 3. List points in a collection (first 10)



```curl -X POST http://localhost:6335/collections/your_collection_name/points/scroll \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{"limit": 10}'
```
✅ 4. Get a specific point by ID



```curl http://localhost:6335/collections/your_collection_name/points/1 \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2"
```
✅ 5. Search similar vectors


```
curl -X POST http://localhost:6335/collections/your_collection_name/points/search \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{
    "vector": [0.1, 0.2, 0.3],
    "top": 5
}'
```
✅ 6. Count points in a collection


```
curl -X POST http://localhost:6335/collections/your_collection_name/points/count \
  -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" \
  -H "Content-Type: application/json" \
  -d '{"exact": true}'
```
✅ 7. Check collection aliases


```
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/aliases
```
✅ 8. List cluster info / health


```
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/cluster
```
✅ 9. Get service info


```

curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335
```
✅ 10. Get collection field schema (indexed fields)


```
curl -H "api-key: 9f8e7d6c5b4a392817f0e1d2c3b4a5f6g7h8i9j0k1l2m3n4o5p6q7r8s9t0u1v2" http://localhost:6335/collections/your_collection_name/index
```
