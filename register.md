## eureka-server
### 服务注册
- 1.ApplicationResource.addInstance()
![image](./images/register/register01.png)
- 2.PeerAwareInstanceRegistryImpl.register()
![image](./images/register/register02.png)
- 3.AbstractInstanceRegistry.register()
![image](./images/register/register03.png)
- 4.AbstractInstanceRegistry.register()，服务注册保存到本地内存，即变量registry
![image](./images/register/register04.png)
- 5.AbstractInstanceRegistry.register()，清除缓存
![image](./images/register/register05.png)
- 6.AbstractInstanceRegistry.invalidateCache()
![image](./images/register/register06.png)
- 7.ResponseCacheImpl.invalidate()
![image](./images/register/register07.png)
- 8.ResponseCacheImpl.invalidate()，readWriteCacheMap用的是guava的LoadingCache
![image](./images/register/register08.png)
### 三级缓存的失效与更新
- 1-1.AbstractInstanceRegistry.EvictionTask.run()，每隔60s，清理超过90s未续约的节点
![image](./images/register/register09.png)
- 1-2.AbstractInstanceRegistry.evict()，遍历服务实例是否过期
![image](./images/register/register10.png)
- 1-3.AbstractInstanceRegistry.evict()
![image](./images/register/register11.png)
- 1-4.AbstractInstanceRegistry.internalCancel()，删除过期的服务实例，即删除变量registry对应节点
![image](./images/register/register12.png)
- 1-5.AbstractInstanceRegistry.internalCancel()，清除缓存，同上
![image](./images/register/register13.png)
***
- 2.ResponseCacheImpl.getCacheUpdateTask().new TimerTask.run()，每隔30s，将readWriteCacheMap同步到readOnlyCacheMap
![image](./images/register/register14.png)
