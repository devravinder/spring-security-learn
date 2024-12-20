1. Generating Private & Public Keys
   ```shell
    openssl genrsa -out private.key 2048
    openssl rsa -in private.key -pubout -out public.key
   ```
     or
    ```shell
    openssl genpkey -algorithm RSA -out private.key -pkeyopt rsa_keygen_bits:4096
    openssl rsa -pubout -in private.key -out public.key
    ```
   

2. In this project we are using both authentications  
   - jwt & http basic , so both works
   so:  
     1. to get the token, 
        - call api '/token' with http basic credentials ( username:password )
        ```shell
         curl -u user:password http://localhost:8080/token
        ```  
        or
        ```shell
         curl -u user:password -X POST http://localhost:8080/token
        ```
     2. use the token for other requests
        ```shell
         curl -H "Authorization: Bearer <token>" http://localhost:8080/secure
        ```