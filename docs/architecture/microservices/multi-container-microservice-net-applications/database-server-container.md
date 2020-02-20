---
title: Kapsayıcı olarak çalışan bir veritabanı sunucusunu kullanma
description: Yalnızca geliştirme için bir kapsayıcı olarak çalışan bir veritabanı sunucusunu kullanmanın önemini anlayın. Üretim için hiçbir şekilde.
ms.date: 01/30/2020
ms.openlocfilehash: 816ac196636f78a368a9f20e8eedcc6a22567fa7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502283"
---
# <a name="use-a-database-server-running-as-a-container"></a>Kapsayıcı olarak çalışan bir veritabanı sunucusunu kullanma

Veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) normal tek başına sunucularda, şirket içi kümelerde veya Azure SQL VERITABANı gibi buluttaki PaaS hizmetlerinde bulabilirsiniz. Ancak, geliştirme ve test ortamları için, herhangi bir dış bağımlılığı olmadığından ve yalnızca `docker-compose up` komutu uygulamanın tamamını başlattığında, veritabanlarının kapsayıcılar olarak çalışmasını sağlamak uygun olur. Veritabanı kapsayıcıda başlatıldığı ve her zaman aynı örnek verilerle doldurulduğu için, bu veritabanlarının kapsayıcı olarak kullanılması da çok önemlidir. bu nedenle, testler daha öngörülebilir hale getirebilir.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Mikro hizmetle ilgili bir veritabanıyla kapsayıcı olarak çalışan SQL Server

EShopOnContainers 'da, [Docker-Compose. yıml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) dosyasında tanımlanan `sqldata`adlı bir kapsayıcı vardır. Bu, bir Linux örneği için, bir tane olması gereken tüm mikro HIZMETLER için SQL veritabanlarına sahip bir SQL Server çalıştırır.

Mikro hizmetlerde bir anahtar noktası, her mikro hizmetin ilgili verilerinin sahibi olduğu için kendi veritabanına sahip olması gerekir. Ancak veritabanları her yerde olabilir. Bu durumda, Docker bellek gereksinimlerini mümkün olduğunca düşük tutmak için aynı kapsayıcıda bulunur. Bu, geliştirme ve, belki de test için yeterli bir çözüm olduğunu ve üretime yönelik olmayan bir çözüm olduğunu göz önünde bulundurun.

Örnek uygulamadaki SQL Server kapsayıcısı, `docker-compose up`çalıştırdığınızda yürütülen Docker-Compose. yıml dosyasında aşağıdaki YAML kodu ile yapılandırılır. YAML kodunun genel Docker-Compose. yıml dosyasından ve Docker-Compose. override. yıml dosyasından birleştirilmiş yapılandırma bilgilerine sahip olduğunu unutmayın. (Genellikle, ortam ayarlarını SQL Server görüntüyle ilgili temel veya statik bilgilerden ayırabilirsiniz.)

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Benzer bir şekilde, `docker-compose`kullanmak yerine aşağıdaki `docker run` komutu bu kapsayıcıyı çalıştırabilir:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Ancak, eShopOnContainers gibi çok kapsayıcılı bir uygulama dağıtıyorsanız, uygulamanın tüm gerekli kapsayıcılarını dağıtması için `docker-compose up` komutunu kullanmak daha uygundur.

Bu SQL Server kapsayıcısını ilk kez başlattığınızda, kapsayıcı, sağladığınız parolayla SQL Server başlatır. SQL Server bir kapsayıcı olarak çalışmaya başladıktan sonra, SQL Server Management Studio, Visual Studio veya C\# kodu gibi herhangi bir normal SQL bağlantısı üzerinden bağlanarak veritabanını güncelleştirebilirsiniz.

EShopOnContainers uygulaması, aşağıdaki bölümde açıklandığı gibi, her mikro hizmet veritabanını başlangıçtaki verilerle dengeli hale getirerek örnek verilerle başlatır.

Bir kapsayıcı olarak çalışan SQL Server olması yalnızca bir SQL Server örneğine erişiminizin olmadığı bir demo için yararlı değildir. Belirtildiği gibi, geliştirme ve test ortamları için de harika olduğundan, yeni örnek verileri dengeli hale getirerek bir temiz SQL Server görüntüsünden ve bilinen verilerden itibaren tümleştirme testlerini kolayca çalıştırabilirsiniz.

### <a name="additional-resources"></a>Ek kaynaklar

- **Linux, Mac veya Windows \ SQL Server Docker görüntüsünü çalıştırın**
    <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Sqlcmd \ ile Linux üzerinde SQL Server bağlama ve sorgulama**
    <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Web uygulaması başlangıcında test verileriyle dengeli dağıtım

Uygulama başlatıldığında veritabanına veri eklemek için, Web API projesinin `Program` sınıfındaki `Main` yöntemine aşağıdakine benzer bir kod ekleyebilirsiniz:

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

Kapsayıcı başlangıcında bir veritabanının dağıtımı ve dağıtımı uygulanırken önemli bir desteklenmediği uyarısıyla vardır. Veritabanı sunucusu herhangi bir nedenle kullanılamadığından, sunucunun kullanılabilir olması beklenirken yeniden denemeleri işlemeniz gerekir. Bu yeniden deneme mantığı, aşağıdaki kodda gösterildiği gibi `MigrateDbContext()` uzantısı yöntemi tarafından işlenir:

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

Özel CatalogContextSeed sınıfında bulunan aşağıdaki kod, verileri doldurur.

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

Tümleştirme testlerini çalıştırdığınızda, tümleştirme testleriniz ile tutarlı veri oluşturmak için bir yol olması yararlı olur. Kapsayıcıda çalışan bir SQL Server örneği de dahil olmak üzere sıfırdan her şeyi oluşturabilmek, test ortamları için harika bir şeydir.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory veritabanı, kapsayıcı olarak çalışan SQL Server karşı

Testleri çalıştırırken bir diğer iyi seçenek de Entity Framework InMemory veritabanı sağlayıcısını kullanmaktır. Bu yapılandırmayı, Web API projenizdeki başlangıç sınıfının ConfigureServices yönteminde belirtebilirsiniz:

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

Ancak önemli bir catch vardır. Bellek içi veritabanı, belirli bir veritabanına özgü birçok kısıtlamayı desteklemez. Örneğin, EF Core modelinizdeki bir sütuna benzersiz bir dizin ekleyebilir ve bir yinelenen değer eklemenize izin vermediğinden emin olmak için bellek içi veritabanınıza bir test yazabilirsiniz. Ancak bellek içi veritabanını kullanırken, bir sütundaki benzersiz dizinleri işleyemez. Bu nedenle, bellek içi veritabanı gerçek bir SQL Server veritabanıyla tamamen aynı şekilde davranmaz; veritabanına özgü kısıtlamalara benzemez.

Bu nedenle, bir bellek içi veritabanı, test ve prototip oluşturma için hala yararlıdır. Ancak belirli bir veritabanı uygulamasının davranışını dikkate alan doğru tümleştirme testleri oluşturmak isterseniz, SQL Server gibi gerçek bir veritabanını kullanmanız gerekir. Bu amaçla, bir kapsayıcıda SQL Server çalıştırmak, EF Core InMemory veritabanı sağlayıcısından çok iyi bir seçimdir ve daha doğru bir seçenektir.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Kapsayıcıda çalışan Redsıs önbelleği hizmetini kullanma

Özellikle geliştirme ve test için ve kavram kanıtı olabilecek senaryolar için Redsıs 'yi bir kapsayıcıda çalıştırabilirsiniz. Bu senaryo, yalnızca yerel Geliştirme makinelerinizde değil, ancak CI/CD işlem hatlarınızdaki sınama ortamlarınız için değil, kapsayıcılarda çalışan tüm bağımlılıklarınızı sunabileceğinden kullanışlı bir yöntemdir.

Ancak, Redsıs 'yi üretimde çalıştırdığınızda, PaaS Microsoft Azure gibi (hizmet olarak platform) olarak çalışan yüksek kullanılabilirliğe sahip bir çözüm aramak daha iyidir. Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.

Redsıs, redin ile bir Docker görüntüsü sağlar. Bu URL 'de Docker Hub 'dan bu görüntü kullanılabilir:

<https://hub.docker.com/_/redis/>

Komut istemindeki aşağıdaki Docker CLı komutunu yürüterek bir Docker Redsıs kapsayıcısını doğrudan çalıştırabilirsiniz:

```console
docker run --name some-redis -d redis
```

Redsıs görüntüsü şunları içerir: 6379 (Redsıs tarafından kullanılan bağlantı noktası), bu nedenle standart kapsayıcı bağlama bunu otomatik olarak bağlantılı kapsayıcılar için kullanılabilir hale getirir.

EShopOnContainers 'da, `basket-api` mikro hizmeti kapsayıcı olarak çalışan bir Redsıs önbelleği kullanır. Bu `basketdata` kapsayıcı, aşağıdaki örnekte gösterildiği gibi çok Kapsayıcılı *Docker-Compose. yml* dosyasının bir parçası olarak tanımlanmıştır:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Docker-Compose. yıml içindeki bu kod, redsıs görüntüsüne göre `basketdata` adlı bir kapsayıcı tanımlar ve 6379 numaralı bağlantı noktasını dahili olarak yayımlarız. Bu, yalnızca Docker ana bilgisayarı içinde çalışan diğer kapsayıcılardan erişilebileceği anlamına gelir.

Son olarak, *Docker-Compose. override. yml* dosyasında eShopOnContainers örneği için `basket-api` mikro hizmeti, o redsıs kapsayıcısı için kullanılacak bağlantı dizesini tanımlar:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Daha önce belirtildiği gibi, mikro hizmet `basketdata` adı Docker 'ın iç ağ DNS tarafından çözümlenir.

>[!div class="step-by-step"]
>[Önceki](multi-container-applications-docker-compose.md)
>[İleri](integration-event-based-microservice-communications.md)
