---
title: Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
description: Yalnızca geliştirme için kapsayıcı olarak çalışan bir veritabanı sunucusu kullanmanın önemini anlayın. Üretim için asla.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628533"
---
# <a name="use-a-database-server-running-as-a-container"></a>Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma

Veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) normal bağımsız sunucularda, şirket içi kümelerde veya Azure SQL DB gibi bulutta PaaS hizmetlerinde alabilirsiniz. Ancak, geliştirme ve test ortamları için veritabanlarınızın kapsayıcı olarak çalıştırılması uygundur, çünkü herhangi bir `docker-compose up` dış bağımlılığınız yoktur ve yalnızca komutu çalıştırmak tüm uygulamayı başlatır. Veritabanı kapsayıcıda başlatılır ve her zaman aynı örnek verilerle doldurulur, bu nedenle testler daha öngörülebilir olabilir, çünkü kapsayıcı olarak bu veritabanları olması da tümleştirme testleri için harika.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Microservice ile ilgili veritabanına sahip bir kapsayıcı olarak çalışan SQL Server

eShopOnContainers'da `sqldata` [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) dosyasında tanımlandığı üzere, linux için bir SQL Server örneği, ihtiyaç duyan tüm mikro hizmetler için SQL veritabanlarını çalıştıran bir kapsayıcı vardır.

Mikro hizmetlerde önemli bir nokta, her microservice kendi ilgili veri sahibi olmasıdır, bu yüzden kendi veritabanı olmalıdır. Ancak, veritabanları her yerde olabilir. Bu durumda, Docker bellek gereksinimlerini mümkün olduğunca düşük tutmak için hepsi aynı kapsayıcıdadır. Bunun geliştirme ve belki de test etmek için yeterli olan bir çözüm olduğunu ancak üretim için olmadığını unutmayın.

Örnek uygulamadaki SQL Server kapsayıcısı, çalıştırdığınızda `docker-compose up`çalıştırılan docker-compose.yml dosyasında aşağıdaki YAML koduyla yapılandırılır. YAML kodunun genel docker-compose.yml dosyasından ve docker-compose.override.yml dosyasından yapılandırma bilgilerini birleştirdiğini unutmayın. (Genellikle ortam ayarlarını SQL Server görüntüsüyle ilgili temel veya statik bilgilerden ayırırsınız.)

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Benzer bir şekilde, kullanmak `docker-compose`yerine, `docker run` aşağıdaki komut bu kapsayıcı çalıştırabilirsiniz:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Ancak, eShopOnContainers gibi bir çok kapsayıcı uygulaması dağıtıyorsanız, uygulama `docker-compose up` için gerekli tüm kapsayıcıları dağıtmak için komutu kullanmak daha uygundur.

Bu SQL Server kapsayıcısını ilk kez başlattığınızda, kapsayıcı, sağladığınız parolayla SQL Server'ı başlatir. SQL Server kapsayıcı olarak çalıştırdıktan sonra, SQL Server Management Studio, Visual Studio veya C\# kodu gibi normal SQL bağlantısı üzerinden bağlanarak veritabanını güncelleştirebilirsiniz.

eShopOnContainers uygulaması, aşağıdaki bölümde açıklandığı gibi, başlangıç verileri ile tohumlama tarafından örnek verileri ile her mikrohizmet veritabanı nı başlatir.

SQL Server'ın kapsayıcı olarak çalışması, yalnızca SQL Server'ın bir örneğine erişemeyemeyeceğiniz bir demo için yararlı değildir. Belirtildiği gibi, yeni örnek verileri tohumlayarak temiz bir SQL Server görüntüsünden ve bilinen verilerden başlayarak entegrasyon testlerini kolayca çalıştırabilmeniz için geliştirme ve test ortamları için de idealdir.

### <a name="additional-resources"></a>Ek kaynaklar

- **LINUX, Mac veya Windows'da SQL Server Docker görüntüsünü çalıştırma** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **SQLCMD ile Linux'ta SQL Server'ı bağlayın ve sorgulayın** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Web uygulaması başlatma test verileri ile tohumlama

Uygulama başlatıldığında veritabanına veri eklemek için, Web API projesinin `Main` `Program` sınıfındaki yönteme aşağıdaki gibi kod ekleyebilirsiniz:

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

Geçişleri uygularken ve konteyner başlatma sırasında bir veritabanı tohumlama önemli bir uyarı var. Veritabanı sunucusu her ne sebeple olursa olsun kullanılamayabileceğinden, sunucunun kullanılabilir olmasını beklerken yeniden denemeleri işlemeniz gerekir. Bu yeniden deneme mantığı, `MigrateDbContext()` aşağıdaki kodda gösterildiği gibi uzantı yöntemi yle işlenir:

```cs
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

Özel CatalogContextSeed sınıfındaaşağıdaki kod verileri doldurur.

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

Tümleştirme testlerini çalıştırdığınızda, tümleştirme testlerinizle tutarlı veriler oluşturmanın bir yolunun olması yararlıdır. Bir kapsayıcı üzerinde çalışan SQL Server örneği de dahil olmak üzere sıfırdan her şeyi oluşturabilmek, test ortamları için idealdir.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory veritabanı karşı SQL Server kapsayıcı olarak çalışan

Testleri çalıştırırken başka bir iyi seçenek, Entity Framework InMemory veritabanı sağlayıcısını kullanmaktır. Web API projenizde Başlangıç sınıfının Yapılandırma Hizmetleri yönteminde yapılandırmayı belirtebilirsiniz:

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

Yine de önemli bir sorun var. Bellek veritabanı, belirli bir veritabanına özgü birçok kısıtlamayı desteklemez. Örneğin, EF Core modelinizdeki bir sütuna benzersiz bir dizin ekleyebilir ve yinelenen bir değer eklemenize izin vermeyeceğini denetlemek için bellek veritabanınıza karşı bir test yazabilirsiniz. Ancak bellek veritabanını kullanırken, bir sütundaki benzersiz dizinleri işleyemezsiniz. Bu nedenle, bellek içi veritabanı gerçek bir SQL Server veritabanı ile tam olarak aynı şekilde davranmıyor-veritabanına özgü kısıtlamaları taklit etmez.

Yine de, bellek içi veritabanı test ve prototip oluşturma için hala yararlıdır. Ancak, belirli bir veritabanı uygulamasının davranışını dikkate alan doğru tümleştirme testleri oluşturmak istiyorsanız, SQL Server gibi gerçek bir veritabanı kullanmanız gerekir. Bu amaçla, SQL Server'ı bir kapsayıcıda çalıştırmak, EF Core InMemory veritabanı sağlayıcısından harika bir seçim dir.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Kapsayıcıda çalışan redis önbellek hizmetini kullanma

Redis'i özellikle geliştirme ve sınama ve kavram kanıtı senaryoları için bir kapsayıcıüzerinde çalıştırabilirsiniz. Bu senaryo kullanışlıdır, çünkü tüm bağımlılıklarınızın yalnızca yerel geliştirme makineleriniz için değil, CI/CD ardışık hatlarınızdaki test ortamlarınız için de kapsayıcılarda çalıştırılabilir.

Ancak, Redis'i üretimde çalıştırdığınızda, PaaS (Hizmet Olarak Platform) olarak çalışan Redis Microsoft Azure gibi yüksek kullanılabilirlikli bir çözüm aramak daha iyidir. Kodunuzda, bağlantı dizelerinizi değiştirmeniz gerekir.

Redis, Redis ile Docker görüntüsü sağlar. Bu resim Docker Hub'dan şu URL'de edinilebilir:

<https://hub.docker.com/_/redis/>

Komut isteminizde aşağıdaki Docker CLI komutunu çalıştırarak doğrudan bir Docker Redis kapsayıcısı çalıştırabilirsiniz:

```console
docker run --name some-redis -d redis
```

Redis görüntü expose:6379 (Redis tarafından kullanılan bağlantı noktası) içerir, böylece standart konteyner bağlantı bağlantılı kapsayıcılar için otomatik olarak kullanılabilir hale getirecek.

`basket-api` eShopOnContainers'da, microservice kapsayıcı olarak çalışan bir Redis önbelleği kullanır. Bu `basketdata` kapsayıcı, aşağıdaki örnekte gösterildiği gibi, çok kapsayıcı *docker-compose.yml* dosyasının bir parçası olarak tanımlanır:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Docker-compose.yml'deki bu kod, redis görüntüsüne dayalı olarak adlandırılan `basketdata` bir kapsayıcıyı tanımlar ve 6379 bağlantı noktasını dahili olarak yayımlar. Bu, yalnızca Docker ana bilgisayar içinde çalışan diğer kaplardan erişilebildiği anlamına gelir.

Son olarak, *docker-compose.override.yml* dosyasında, eShopOnContainers örneği için `basket-api` microservice bu Redis kapsayıcı için kullanılacak bağlantı dizesini tanımlar:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Daha önce de belirtildiği gibi, `basketdata` microservice adı Docker iç ağ DNS tarafından çözülür.

>[!div class="step-by-step"]
>[Önceki](multi-container-applications-docker-compose.md)
>[Sonraki](integration-event-based-microservice-communications.md)
