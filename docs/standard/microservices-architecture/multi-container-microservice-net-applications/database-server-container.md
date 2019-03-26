---
title: Bir kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Bir kapsayıcı olarak çalışan bir veritabanı sunucusu mi kullanıyorsunuz? yalnızca geliştirme için! Nedenini anlamak.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 2adc58339012095c9dc58d633a9b3815cf7aba3f
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463351"
---
# <a name="using-a-database-server-running-as-a-container"></a>Bir kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma

Normal bir tek başına sunucular, şirket içi kümelerle ya da Azure SQL DB gibi bir bulut PaaS Hizmetleri, veritabanları (SQL Server, PostgreSQL, MySQL vb.) olabilir. Ancak, geliştirme ve test ortamları için kapsayıcı olarak kullanışlı, herhangi bir dış bağımlılık olmadığı için çalışan ve yalnızca çalışan veritabanlarınızı sahip `docker-compose up` komut tüm uygulamayı başlatır. Veritabanı kapsayıcısında başlatıldı ve testler daha öngörülebilir olabilir. Bu nedenle her zaman aynı örnek verilerle doldurulur kapsayıcıları olarak bu veritabanına sahip olmanın da tümleştirme testleri için harika olmasıdır.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Mikro hizmet ile ilgili bir veritabanıyla bir kapsayıcı çalışan SQL Server

Hizmetine içinde tanımlanan sql.data adlı bir kapsayıcı olduğundan [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) mikro hizmetler için gerekli olan tüm SQL Server veritabanları ile Linux için SQL Server çalıştıran bir dosya. (Her veritabanı için bir SQL Server kapsayıcı da olabilir, ancak, Docker için atanan daha fazla bellek gerektirir.) Mikro hizmetlerde en önemli nokta, her bir mikro hizmet kendi ilgili verileri bu nedenle, ilgili SQL veritabanı bu durumda sahip olduğunu ' dir. Ancak herhangi bir veritabanı olabilir.

Örnek uygulamada bulunan SQL Server kapsayıcı çalıştırdığınızda, yürütülen docker-compose.yml dosyasında aşağıdaki YAML koduna yapılandırılmış `docker-compose up`. YAML koduna genel docker-compose.yml dosyasını ve docker-compose.override.yml dosyasını yapılandırma bilgilerini birleştirilmiş olmadığını unutmayın. (Genellikle SQL Server görüntüsünü ilgili temel veya statik bilgi ortam ayarları ayıracaktır.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Benzer bir şekilde kullanmak yerine, `docker-compose`, aşağıdaki `docker run` komutu o kapsayıcı çalıştırın:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Hizmetine gibi çok kapsayıcılı bir uygulama dağıtıyorsanız, ancak kullanmak daha kullanışlı olan `docker-compose up` komut, böylece uygulama için gerekli tüm kapsayıcıları dağıtır.

Bu SQL Server kapsayıcı ilk kez başlattığınızda, kapsayıcı sağladığınız parola ile SQL Server başlatır. Bir kapsayıcı SQL Server çalıştırıldıktan sonra normal bir SQL bağlantısı gibi SQL Server Management Studio, Visual Studio ve C bağlanarak veritabanı güncelleştirebilirsiniz\# kod.

Hizmetine uygulama örnek verilerle her bir mikro hizmet veritabanı verilerle başlangıçta temel olarak aşağıdaki bölümde açıklandığı gibi başlatır.

Bir kapsayıcı çalışan SQL Server sahip olduğu SQL Server örneğine erişimi olmayabilir demo yalnızca kullanışlı değildir. Böylece kolayca temiz bir SQL Server görüntüsünü başlatma tümleştirme testleri çalıştırmak ve verileri yeni örnek veri üretme tarafından bilinen belirtildiği gibi ayrıca geliştirme ve test ortamları için harika bir hizmettir.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Linux, Mac veya Windows üzerinde SQL Server Docker görüntüsünü çalıştırma** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

- **Bağlanma ve Linux'ta SQL Server sqlcmd ile sorgulama** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Web uygulama başlatma verileriyle test üretme

Uygulama başlatıldığında verileri veritabanına eklemek için yapılandırma yöntemine Web API projesi başlangıç sınıfına aşağıdaki gibi kod ekleyebilirsiniz:

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

Aşağıdaki kodda özel CatalogContextSeed sınıf veri doldurur.

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

Tümleştirme testleri çalıştırdığınızda, tümleştirme testleri ile tutarlı verileri oluşturabileceği bir yol olan yararlı olur. Her şeyi bir kapsayıcı üzerinde çalışan SQL Server örneğini dahil olmak üzere sıfırdan oluşturmak için test ortamları için harika bir yoldur.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core Inmemory veritabanı bir kapsayıcı çalışan SQL Server ile karşılaştırması

Testler çalışırken başka bir iyi seçim, Entity Framework Inmemory veritabanı sağlayıcısı kullanmaktır. Bu yapılandırma, Web API projesinde başlangıç sınıfı Createservicereplicalisteners() yönteminde belirtebilirsiniz:

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

Ancak önemli bir catch yoktur. Bellek içi veritabanı, belirli bir veritabanına belirli birçok kısıtlama desteklemez. Örneği için benzersiz bir dizin EF Core modelinizde bir sütun ekleyin ve bunu bir yinelenen değer eklemenize izin vermez, denetlenecek bellek içi veritabanınızda bir test yazın. Ancak, bellek içi veritabanına kullanırken bir sütunun benzersiz dizinler işleyemiyor. Bu nedenle, bellek içi veritabanı ile aynı gerçek bir SQL Server veritabanı şekilde davranmaz — veritabanı özgü kısıtlamaları öykünmek değil.

Buna rağmen bir bellek içi veritabanına test ve prototip oluşturma için hala faydalıdır. Ancak, belirli bir veritabanı uygulama davranışını dikkate doğru tümleştirme testleri oluşturmak istiyorsanız, SQL Server gibi gerçek bir veritabanı kullanmanız gerekir. Bu amaç için SQL Server çalıştıran bir kapsayıcıda, harika bir seçim ve EF Core Inmemory veritabanı sağlayıcısı daha doğru olduğu.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Bir kapsayıcı içinde çalışan bir Redis cache hizmeti kullanma

Redis, kavram kanıtı senaryoları ve geliştirme ve test için özellikle kapsayıcısı üzerinde çalıştırabilirsiniz. Tüm bağımlılıklarınızı kapsayıcılarında çalıştırılan olabilir çünkü bu senaryo uygundur: yalnızca değil yerel geliştirme makineleriniz için test ortamlarınızda CI/CD işlem hatlarınızı için.

Ancak, üretim ortamında Redis çalıştırdığınızda, Redis Microsoft bir PaaS (hizmet olarak Platform) olarak çalışan Azure gibi bir yüksek kullanılabilirlik çözümü arayın daha iyi olur. Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.

Redis, Redis ile bir Docker görüntüsü sağlar. Bu görüntüyü Docker hub'dan bu URL'de kullanılabilir:

[https://hub.docker.com/_/redis/](https://hub.docker.com/_/redis/)

Doğrudan komut isteminde aşağıdaki Docker CLI komutunu yürüterek bir Redis Docker kapsayıcısı çalıştırabilirsiniz:

```
  docker run --name some-redis -d redis
```

Bu nedenle standart kapsayıcı bağlama, otomatik olarak bağlı kapsayıcılara kullandıracağınız, Redis görüntüsünü'ı kullanıma sunar: 6379 (Redis tarafından kullanılan bağlantı noktası) içerir.

Hizmetine basket.api mikro hizmet kapsayıcı olarak çalışan bir Redis önbelleği kullanır. Bu basket.data kapsayıcı çok kapsayıcılı docker-compose.yml dosyasını bir parçası olarak, aşağıdaki örnekte gösterildiği gibi tanımlanır:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Docker-compose.yml bu kodda, redis görüntüye göre ve 6379 bağlantı dahili olarak, yani yalnızca Docker konağı içinde çalışan diğer kapsayıcılar erişilebilir olacağını yayımlama basket.data adlı bir kapsayıcı tanımlar.

Son olarak, docker-compose.override.yml dosyasında basket.api mikro hizmetine örnek için Redis kapsayıcı için kullanılacak bağlantı dizesini tanımlar:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Daha önce belirtildiği gibi "basket.data" mikro hizmet adını docker'ın iç ağ DNS tarafından çözümlenir.

>[!div class="step-by-step"]
>[Önceki](multi-container-applications-docker-compose.md)
>[İleri](integration-event-based-microservice-communications.md)
