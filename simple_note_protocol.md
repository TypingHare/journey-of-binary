## I/O Model

```c++
"Http request string"
	-> Server.parse(_ -> "Http request object")
    -> Server.extract_url(_ -> "Http request object; URL")
    -> Server.match_route(_ -> "Http request object; controller method")
    -> Server.execute(_ -> "Http response object")
    -> Server.encode(_, "Http response string")
    -> Server.send(_, Client)
```



```c++
// NOTE: Nginx is a backend application
// Situation 1: dispatch to a service (final-act)
"Http request string"
    -> Nginx.extract_url(_ -> "URL")
    -> Nginx.match(_ -> "new location")
    -> Nginx.dispatch(_ -> CorrespondingService)
    -> Nginx.get_response(_ -> "HTTP response string")
    -> Nginx.send(_, Client)
    
// Situation 2: static resources (final-act-site)
"Http request string"
    -> Nginx.extract_url(_ -> "URL")
    -> Nginx.match(_ -> "new location")
    -> Nginx.find_file(_ -> "file content")
    -> Nginx.create_response(_ -> "HTTP response string")
    -> Nginx.send(_, Client)
```





```c++
// mbedtls_ssl_write model
_ -> encrypt("buffer" -> "encrypted buffer")
  -> package("encrypted buffer" -> "TSL records")
  -> transfer("TSL records" -> Counterpart)
  -> receive(Counterpart -> "response")
```



```c++
"command string"
  	-> Burrow.extract_chamber_name(_ -> "chamber name; rest of command")
  	-> Burrow.build_burrow(_ -> "burrow; rest of command")
    -> Burrow.create_context(_ -> "context; rest of command")
  	-> Burrow.create_picocli_command(_ -> "picocli command injected context")
```

