## eureka-server
### 服务注册
- 1.ApplicationResource.addInstance()
![image](./images/register/register01.png)
- 2.PeerAwareInstanceRegistryImpl.register()
![image](./images/register/register02.png)
- 3.AbstractInstanceRegistry.register()
![image](./images/register/register03.png)
- 4.AbstractInstanceRegistry.register()，服务注册保存到本地内存
![image](./images/register/register04.png)
- 5.AbstractInstanceRegistry.register()，清除缓存
![image](./images/register/register05.png)
- 6.AbstractInstanceRegistry.invalidateCache()
![image](./images/register/register06.png)
- 7.ResponseCacheImpl.invalidate()
![image](./images/register/register07.png)
- 8.ResponseCacheImpl.invalidate()，readWriteCacheMap用的是guava的LoadingCache
![image](./images/register/register08.png)
