spring-boot
---

# Gitの情報をActuatorの`/info`で表示する方法

以下プラグインを適用し、ビルド時に`git.properties`がresourcesに生成される。

**maven**

```xml

<build>
  <plugins>
    <plugin>
      <groupId>pl.project13.maven</groupId>
      <artifactId>git-commit-id-plugin</artifactId>
    </plugin>
  </plugins>
</build>
```

**gradle**

```groovy
plugins {
  id "com.gorylenko.gradle-git-properties" version "2.2.4"
}
```

Actuatorが依存に入っていると`/info`で`git.properties`の一部の情報が表示される。

```json
{
  "git": {
    "branch": "main",
    "commit": {
      "id": "2f5d546",
      "time": "2021-09-25T10:17:48Z"
    }
  }
}
```

FYI: https://docs.spring.io/spring-boot/docs/current/reference/htmlsingle/#howto.build.generate-git-info
