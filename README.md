## With Docker

For development:
```
docker run --rm --name slate -p 4567:4567 -v $(pwd)/source:/srv/slate/source slatedocs/slate serve
```

For building:
```
docker run --rm --name slate -v $(pwd)/build:/srv/slate/build -v $(pwd)/source:/srv/slate/source slatedocs/slate build
```

## Without Docker

https://github.com/slatedocs/slate/wiki/Using-Slate-Natively
