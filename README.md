### Next.js fetch error

This repo was created to reproduce the error in recent next.js version.

To reproduce:
```shell
docker build -t temp .
export TEMP_CONTAINER_ID=$(docker run --rm -d -p3000:3000 temp)
curl http://localhost:3000
docker logs -f $TEMP_CONTAINER_ID
# you should see something like "TypeError: fetch failed" in the logs ("cause: Error: connect ECONNREFUSED 127.0.0.1:39811")

# cleanup:
docker rm -f $TEMP_CONTAINER_ID
docker image rm temp
```
