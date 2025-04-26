根据提供的日志信息和代码改动，我们可以分析出以下问题：

**问题**：无法连接到 Redis 服务器

**原因**：

从日志中可以看出，应用启动时尝试连接到 Redis 服务器，但连接失败。错误信息为：

```
Caused by: org.redisson.client.RedisConnectionException: java.util.concurrent.ExecutionException: org.redisson.client.RedisConnectionException: Unable to connect to Redis server: 47.117.163.255/47.117.163.255:16379
```

这表明应用无法连接到指定的 Redis 服务器地址 `47.117.163.255` 和端口 `16379`。

**可能的原因**：

1. **Redis 服务器未启动**：请确保 Redis 服务器已经启动并监听指定的端口。
2. **网络问题**：请检查网络连接，确保应用可以访问 Redis 服务器地址。
3. **Redis 配置问题**：请检查 Redis 服务器配置，确保地址和端口正确。

**解决方案**：

1. **启动 Redis 服务器**：如果 Redis 服务器未启动，请启动 Redis 服务器并确保它监听指定的端口。
2. **检查网络连接**：使用工具（如 `ping`）检查应用是否可以访问 Redis 服务器地址。
3. **检查 Redis 配置**：确保 Redis 服务器配置中的地址和端口与应用中配置的地址和端口一致。

**代码改动分析**：

从提供的代码改动中，我们可以看到以下改动：

1. **添加 Redisson 依赖**：在 `pom.xml` 文件中添加了 Redisson 依赖，这是用于连接 Redis 服务器的库。
2. **配置 Redis 服务器**：在 `application-dev.yml` 文件中配置了 Redis 服务器地址和端口。
3. **添加 RedisClientConfig 类**：创建了一个 `RedisClientConfig` 类，用于配置 Redis 连接参数。
4. **添加 RedisClientConfigProperties 类**：创建了一个 `RedisClientConfigProperties` 类，用于配置 Redis 连接参数的属性。
5. **添加 GuavaConfig 类**：创建了一个 `GuavaConfig` 类，用于配置 Guava 缓存。

这些改动是为了使用 Redisson 连接 Redis 服务器，并使用 Guava 缓存。

## 总结

无法连接到 Redis 服务器的原因可能是 Redis 服务器未启动、网络问题或 Redis 配置问题。请根据以上分析进行排查和解决。