Spring Security
---

- [official-reference](https://spring.pleiades.io/spring-security/site/docs/current/reference/html5/)

## SecurityContextHolderのクラス構造

SecurityContextHolder

- SecurityContext
    - Authentication
        - Principal
        - Credentials

SecurityContextHolderはSpringSecurityが認証された人の詳細を格納する場所なので、 SecurityContextHolderを直接設定すると認証されたことになる。

```java
SecurityContext context=SecurityContextHolder.createEmptyContext();
        Authentication authentication=
        new TestingAuthenticationToken("username","password","ROLE_USER");
        context.setAuthentication(authentication);

        SecurityContextHolder.setContext(context);
```

SecurityContextHolderにアクセスすれば認証済みユーザの情報を取得できる SecurityContextHolderはデフォルトではThreadLocalに保存されている。
FilterChainProxyがSecurityContextをクリアする

```java
SecurityContext context=SecurityContextHolder.getContext();
        Authentication authentication=context.getAuthentication();
        String username=authentication.getName();
        Object principal=authentication.getPrincipal();
        Collection<?extends GrantedAuthority> authorities=authentication.getAuthorities();
```
