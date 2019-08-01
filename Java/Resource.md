# jar에서 File 참조시 FileNotFoundException 발생

스프링부트 환경에서 리소스를 사용할 때 다음 에러가 발생했다.

```
java.io.FileNotFoundException: class path resource [test.xxx] cannot be resolved to absolute file path because it does not reside in the file system
```

[여기](https://sonegy.wordpress.com/2015/07/23/spring-boot-executable-jar에서-file-resource-처리)에서 해결책을 찾음

* Resource -> ClassPathResource
* getFile() -> getInputStream()