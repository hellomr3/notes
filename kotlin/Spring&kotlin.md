# spring boot中kotlin获取properties

## Config.kt
``` kotlin
@ConstructorBinding
@ConfigurationProperties(prefix = "config")
data class Config(val isDebug: String)
```
## Application.kt
``` kotlin
@EnableConfigurationProperties(Config::class)
class Application
```
