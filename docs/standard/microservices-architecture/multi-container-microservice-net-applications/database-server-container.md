---
title: Bir kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro mimarisi | Bir kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: 8ff6afbe9618df918e0a965fa1202bbb999eee5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578176"
---
# <a name="using-a-database-server-running-as-a-container"></a>Bir kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma

Normal tek başına sunucularda, şirket içi kümeleri veya Azure SQL DB gibi bulutta PaaS Hizmetleri'nde veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) olabilir. Ancak, geliştirme ve test ortamları için çalışan kapsayıcılar veritabanlarınızı sahip uygun herhangi bir dış bağımlılığı olmadığından yalnızca olduğundan ve çalıştığından docker compose'u komut, tüm uygulama başlatır. Veritabanı kapsayıcısında başlatıldı ve testleri daha tahmin edilebilir böylece her zaman aynı örnek verilerle doldurulur kapsayıcı olarak bu veritabanına sahip olmanın da tümleştirme testleri için mükemmeldir.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Mikro hizmet ile ilgili bir veritabanıyla bir kapsayıcı olarak çalışan SQL Server

EShopOnContainers içinde tanımlanan sql.data adlı bir kapsayıcı olduğundan [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) mikro hizmetler için gerekli tüm SQL Server veritabanları ile Linux için SQL Server çalıştıran dosya. (Her veritabanı için bir SQL Server kapsayıcısı sahip olabilir, ancak, Docker için atanan daha fazla bellek gerektirir.) Önemli mikro içinde her mikro hizmet ilgili verileri, bu nedenle ilgili SQL veritabanını bu durumda sahibi olduğu noktasıdır. Ancak veritabanlarını her yerden olabilir.

Örnek uygulama kapsayıcısında aşağıdaki YAML kod çalıştırdığınızda yürütülür docker-compose.yml dosyası ile yapılandırılmış SQL Server docker-kuruluşu ayarlama Yapılandırma bilgilerini genel docker-compose.yml dosyası ve docker compose.override.yml dosyasındaki YAML kod birleştirilmiş unutmayın. (Genellikle SQL Server görüntüsünü ilgili temel veya statik bilgiler ortam ayarlarından ayıracaktır.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5434:1433"
```

Benzer bir şekilde kullanmak yerine, `docker-compose`, aşağıdaki `docker run` komutu, bu kapsayıcı çalıştırabilirsiniz:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

EShopOnContainers gibi birden çok kapsayıcı uygulama dağıtıyorsanız, ancak kullanmak daha kullanışlı olan uygulama için gerekli tüm kapsayıcılar dağıtır böylece komutu docker-oluşturun.

Bu SQL Server kapsayıcı ilk kez başlattığınızda, kapsayıcı verdiğiniz parola ile SQL Server başlatır. SQL Server bir kapsayıcı olarak çalışmaya başladıktan sonra tüm normal SQL bağlantısı gibi SQL Server Management Studio'yu, Visual Studio veya C bağlanarak veritabanı güncelleştirebilirsiniz\# kodu.

EShopOnContainers uygulama her mikro hizmet veritabanı örnek verilerle başlangıçta, verilerle dengeli dağıtarak aşağıdaki bölümde açıklandığı gibi başlatır.

Bir kapsayıcı olarak çalışan SQL Server sahip olduğu SQL Server'ın bir örneğine erişimi olmayabilir demo yalnızca kullanışlı değildir. Böylece kolayca temiz bir SQL Server görüntüden başlangıç tümleştirme testleri çalıştırın ve yeni örnek veriler dengeli dağıtarak veri bilinen belirtildiği gibi aynı zamanda geliştirme ve test ortamları için çok yararlıdır.

#### <a name="additional-resources"></a>Ek kaynaklar

-   **Linux, Mac veya Windows üzerinde SQL Server Docker görüntü çalıştırın**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **Bağlanma ve sqlcmd ile SQL Server Linux üzerinde sorgulama**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Web uygulaması başlangıç test verilerle üretme

Uygulama başlatıldığında veritabanına veri eklemek için Web API projesini başlangıç sınıfının yapılandırma yöntemine kod aşağıdaki gibi ekleyebilirsiniz:

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

Özel CatalogContextSeed sınıfında aşağıdaki kodu verileri doldurur.

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

Tümleştirme testlerini çalıştırdığınızda, tümleştirme testlerinizi ile tutarlı verileri oluşturmak için bir yol olması yararlıdır. Her şeyi bir kapsayıcı üzerinde çalışan SQL Server örneği de dahil olmak üzere sıfırdan oluşturma yetkisi olan test ortamları için mükemmeldir.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF çekirdek Inmemory veritabanı bir kapsayıcı olarak çalışan SQL Server ile karşılaştırması

Testleri çalıştırırken başka bir iyi seçimdir Entity Framework Inmemory veritabanı sağlayıcısı kullanmaktır. Bu yapılandırma, Web API projesinde başlangıç sınıfı ConfigureServices yönteminde belirtebilirsiniz:

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...

}
```

Ancak önemli bir catch yoktur. Bellek içi veritabanı belirli bir veritabanına özgü birçok kısıtlamaları desteklemez. Örneği için benzersiz bir dizin EF çekirdek modelinizde bir sütun ekleyin ve onu yinelenen değer eklemenize izin vermez olduğunu denetlemek için bellek içi veritabanına karşı test yazma. Ancak, bellek içi veritabanı kullanırken, bir sütunda benzersiz dizinler işleyemiyor. Bu nedenle, bellek içi veritabanı tam olarak aynı gerçek bir SQL Server veritabanı olarak davranıyor değildir — veritabanı özgü kısıtlamaları öykünmek değil.

Buna rağmen bir bellek içi veritabanı sınama ve prototipi oluşturulurken için hala yararlıdır. Ancak belirli veritabanı uygulama davranışını dikkate doğru tümleştirme testleri oluşturmak istiyorsanız, SQL Server gibi gerçek bir veritabanını kullanmak gerekir. Bu amaç için SQL Server bir kapsayıcıda seçim ve EF çekirdek Inmemory veritabanı sağlayıcısı daha kesin mükemmel çalışıyor.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Bir kapsayıcıda çalışan bir Redis önbelleği hizmeti kullanma

Redis ve kavram kanıtı senaryoları özellikle geliştirme ve test için bir kapsayıcı çalıştırabilirsiniz. Tüm bağımlılıkları kapsayıcılarında çalıştıran olabileceği için bu senaryo uygundur — değil yalnızca yerel geliştirme makinelerinizi, ancak test ortamınızı CI/CD hatlarınızı.

Ancak, Redis üretimde çalıştırdığınızda, Redis Microsoft PaaS (hizmet olarak Platform) olarak çalışan Azure gibi bir yüksek kullanılabilirlik çözümü arayın en iyisidir. Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.

Redis, Redis Docker görüntüsüyle sağlar. Bu görüntü, Docker hub'a bu URL'de edinilebilir:

<https://hub.docker.com/_/redis/>

Docker Redis bir kapsayıcı, komut isteminde aşağıdaki Docker CLI komutunu yürüterek doğrudan çalıştırabilirsiniz:

```
  docker run --name some-redis -d redis
```

Bu nedenle standart kapsayıcı bağlama otomatik olarak bağlantılı kapsayıcıları kullanabilmesi, Redis görüntü sunmaya: 6379 (Redis tarafından kullanılan bağlantı noktası) içerir.

EShopOnContainers içinde basket.api mikro hizmet kapsayıcı olarak çalışan bir Redis önbelleği kullanır. Bu basket.data kapsayıcı, aşağıdaki örnekte gösterildiği gibi birden çok kapsayıcı docker-compose.yml dosyası bir parçası olarak tanımlanır:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Bu kodu docker-compose.yml redis görüntüyü temel alarak ve bağlantı noktası 6379 dahili olarak, yalnızca Docker ana içinde çalışan diğer kapsayıcılar erişilebilir olacaktır anlamına yayımlama basket.data adlı bir kapsayıcı tanımlar.

Son olarak, docker compose.override.yml dosyasında eShopOnContainers örnek basket.api mikro hizmet bu Redis kapsayıcı için kullanılacak bağlantı dizesini tanımlar:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[Önceki] (çok-container-uygulamalar-docker-compose.md) [sonraki] (tümleştirme-olay-tabanlı-mikro hizmet-communications.md)
