#### 接口状态码的使用

```java
// 使用 @ResponseStatus()注解

@ResponseStatus(HttpStatus.FORBIDDEN) // 注意：HttpStatus.FORBIDDEN 就是状态码 403，由SpringBoot官方提供，可点击HttpStatus查看
public void handleResponseBankException(){
  
}
```

