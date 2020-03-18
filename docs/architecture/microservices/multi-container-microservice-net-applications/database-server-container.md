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
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="dc99f-104">Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="dc99f-104">Use a database server running as a container</span></span>

<span data-ttu-id="dc99f-105">Veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) normal bağımsız sunucularda, şirket içi kümelerde veya Azure SQL DB gibi bulutta PaaS hizmetlerinde alabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc99f-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="dc99f-106">Ancak, geliştirme ve test ortamları için veritabanlarınızın kapsayıcı olarak çalıştırılması uygundur, çünkü herhangi bir `docker-compose up` dış bağımlılığınız yoktur ve yalnızca komutu çalıştırmak tüm uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="dc99f-107">Veritabanı kapsayıcıda başlatılır ve her zaman aynı örnek verilerle doldurulur, bu nedenle testler daha öngörülebilir olabilir, çünkü kapsayıcı olarak bu veritabanları olması da tümleştirme testleri için harika.</span><span class="sxs-lookup"><span data-stu-id="dc99f-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="dc99f-108">Microservice ile ilgili veritabanına sahip bir kapsayıcı olarak çalışan SQL Server</span><span class="sxs-lookup"><span data-stu-id="dc99f-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="dc99f-109">eShopOnContainers'da `sqldata` [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) dosyasında tanımlandığı üzere, linux için bir SQL Server örneği, ihtiyaç duyan tüm mikro hizmetler için SQL veritabanlarını çalıştıran bir kapsayıcı vardır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="dc99f-110">Mikro hizmetlerde önemli bir nokta, her microservice kendi ilgili veri sahibi olmasıdır, bu yüzden kendi veritabanı olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="dc99f-111">Ancak, veritabanları her yerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="dc99f-112">Bu durumda, Docker bellek gereksinimlerini mümkün olduğunca düşük tutmak için hepsi aynı kapsayıcıdadır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="dc99f-113">Bunun geliştirme ve belki de test etmek için yeterli olan bir çözüm olduğunu ancak üretim için olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dc99f-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="dc99f-114">Örnek uygulamadaki SQL Server kapsayıcısı, çalıştırdığınızda `docker-compose up`çalıştırılan docker-compose.yml dosyasında aşağıdaki YAML koduyla yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="dc99f-115">YAML kodunun genel docker-compose.yml dosyasından ve docker-compose.override.yml dosyasından yapılandırma bilgilerini birleştirdiğini unutmayın.</span><span class="sxs-lookup"><span data-stu-id="dc99f-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="dc99f-116">(Genellikle ortam ayarlarını SQL Server görüntüsüyle ilgili temel veya statik bilgilerden ayırırsınız.)</span><span class="sxs-lookup"><span data-stu-id="dc99f-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="dc99f-117">Benzer bir şekilde, kullanmak `docker-compose`yerine, `docker run` aşağıdaki komut bu kapsayıcı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc99f-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="dc99f-118">Ancak, eShopOnContainers gibi bir çok kapsayıcı uygulaması dağıtıyorsanız, uygulama `docker-compose up` için gerekli tüm kapsayıcıları dağıtmak için komutu kullanmak daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="dc99f-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="dc99f-119">Bu SQL Server kapsayıcısını ilk kez başlattığınızda, kapsayıcı, sağladığınız parolayla SQL Server'ı başlatir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="dc99f-120">SQL Server kapsayıcı olarak çalıştırdıktan sonra, SQL Server Management Studio, Visual Studio veya C\# kodu gibi normal SQL bağlantısı üzerinden bağlanarak veritabanını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc99f-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="dc99f-121">eShopOnContainers uygulaması, aşağıdaki bölümde açıklandığı gibi, başlangıç verileri ile tohumlama tarafından örnek verileri ile her mikrohizmet veritabanı nı başlatir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="dc99f-122">SQL Server'ın kapsayıcı olarak çalışması, yalnızca SQL Server'ın bir örneğine erişemeyemeyeceğiniz bir demo için yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="dc99f-123">Belirtildiği gibi, yeni örnek verileri tohumlayarak temiz bir SQL Server görüntüsünden ve bilinen verilerden başlayarak entegrasyon testlerini kolayca çalıştırabilmeniz için geliştirme ve test ortamları için de idealdir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dc99f-124">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="dc99f-124">Additional resources</span></span>

- <span data-ttu-id="dc99f-125">**LINUX, Mac veya Windows'da SQL Server Docker görüntüsünü çalıştırma** </span><span class="sxs-lookup"><span data-stu-id="dc99f-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="dc99f-126">**SQLCMD ile Linux'ta SQL Server'ı bağlayın ve sorgulayın** </span><span class="sxs-lookup"><span data-stu-id="dc99f-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="dc99f-127">Web uygulaması başlatma test verileri ile tohumlama</span><span class="sxs-lookup"><span data-stu-id="dc99f-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="dc99f-128">Uygulama başlatıldığında veritabanına veri eklemek için, Web API projesinin `Main` `Program` sınıfındaki yönteme aşağıdaki gibi kod ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc99f-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

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

<span data-ttu-id="dc99f-129">Geçişleri uygularken ve konteyner başlatma sırasında bir veritabanı tohumlama önemli bir uyarı var.</span><span class="sxs-lookup"><span data-stu-id="dc99f-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="dc99f-130">Veritabanı sunucusu her ne sebeple olursa olsun kullanılamayabileceğinden, sunucunun kullanılabilir olmasını beklerken yeniden denemeleri işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="dc99f-131">Bu yeniden deneme mantığı, `MigrateDbContext()` aşağıdaki kodda gösterildiği gibi uzantı yöntemi yle işlenir:</span><span class="sxs-lookup"><span data-stu-id="dc99f-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

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

<span data-ttu-id="dc99f-132">Özel CatalogContextSeed sınıfındaaşağıdaki kod verileri doldurur.</span><span class="sxs-lookup"><span data-stu-id="dc99f-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="dc99f-133">Tümleştirme testlerini çalıştırdığınızda, tümleştirme testlerinizle tutarlı veriler oluşturmanın bir yolunun olması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="dc99f-134">Bir kapsayıcı üzerinde çalışan SQL Server örneği de dahil olmak üzere sıfırdan her şeyi oluşturabilmek, test ortamları için idealdir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="dc99f-135">EF Core InMemory veritabanı karşı SQL Server kapsayıcı olarak çalışan</span><span class="sxs-lookup"><span data-stu-id="dc99f-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="dc99f-136">Testleri çalıştırırken başka bir iyi seçenek, Entity Framework InMemory veritabanı sağlayıcısını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="dc99f-137">Web API projenizde Başlangıç sınıfının Yapılandırma Hizmetleri yönteminde yapılandırmayı belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc99f-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="dc99f-138">Yine de önemli bir sorun var.</span><span class="sxs-lookup"><span data-stu-id="dc99f-138">There is an important catch, though.</span></span> <span data-ttu-id="dc99f-139">Bellek veritabanı, belirli bir veritabanına özgü birçok kısıtlamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="dc99f-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="dc99f-140">Örneğin, EF Core modelinizdeki bir sütuna benzersiz bir dizin ekleyebilir ve yinelenen bir değer eklemenize izin vermeyeceğini denetlemek için bellek veritabanınıza karşı bir test yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc99f-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="dc99f-141">Ancak bellek veritabanını kullanırken, bir sütundaki benzersiz dizinleri işleyemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc99f-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="dc99f-142">Bu nedenle, bellek içi veritabanı gerçek bir SQL Server veritabanı ile tam olarak aynı şekilde davranmıyor-veritabanına özgü kısıtlamaları taklit etmez.</span><span class="sxs-lookup"><span data-stu-id="dc99f-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="dc99f-143">Yine de, bellek içi veritabanı test ve prototip oluşturma için hala yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="dc99f-144">Ancak, belirli bir veritabanı uygulamasının davranışını dikkate alan doğru tümleştirme testleri oluşturmak istiyorsanız, SQL Server gibi gerçek bir veritabanı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="dc99f-145">Bu amaçla, SQL Server'ı bir kapsayıcıda çalıştırmak, EF Core InMemory veritabanı sağlayıcısından harika bir seçim dir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="dc99f-146">Kapsayıcıda çalışan redis önbellek hizmetini kullanma</span><span class="sxs-lookup"><span data-stu-id="dc99f-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="dc99f-147">Redis'i özellikle geliştirme ve sınama ve kavram kanıtı senaryoları için bir kapsayıcıüzerinde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc99f-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="dc99f-148">Bu senaryo kullanışlıdır, çünkü tüm bağımlılıklarınızın yalnızca yerel geliştirme makineleriniz için değil, CI/CD ardışık hatlarınızdaki test ortamlarınız için de kapsayıcılarda çalıştırılabilir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="dc99f-149">Ancak, Redis'i üretimde çalıştırdığınızda, PaaS (Hizmet Olarak Platform) olarak çalışan Redis Microsoft Azure gibi yüksek kullanılabilirlikli bir çözüm aramak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="dc99f-150">Kodunuzda, bağlantı dizelerinizi değiştirmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="dc99f-151">Redis, Redis ile Docker görüntüsü sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc99f-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="dc99f-152">Bu resim Docker Hub'dan şu URL'de edinilebilir:</span><span class="sxs-lookup"><span data-stu-id="dc99f-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="dc99f-153">Komut isteminizde aşağıdaki Docker CLI komutunu çalıştırarak doğrudan bir Docker Redis kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="dc99f-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="dc99f-154">Redis görüntü expose:6379 (Redis tarafından kullanılan bağlantı noktası) içerir, böylece standart konteyner bağlantı bağlantılı kapsayıcılar için otomatik olarak kullanılabilir hale getirecek.</span><span class="sxs-lookup"><span data-stu-id="dc99f-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="dc99f-155">`basket-api` eShopOnContainers'da, microservice kapsayıcı olarak çalışan bir Redis önbelleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="dc99f-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="dc99f-156">Bu `basketdata` kapsayıcı, aşağıdaki örnekte gösterildiği gibi, çok kapsayıcı *docker-compose.yml* dosyasının bir parçası olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="dc99f-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="dc99f-157">Docker-compose.yml'deki bu kod, redis görüntüsüne dayalı olarak adlandırılan `basketdata` bir kapsayıcıyı tanımlar ve 6379 bağlantı noktasını dahili olarak yayımlar.</span><span class="sxs-lookup"><span data-stu-id="dc99f-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="dc99f-158">Bu, yalnızca Docker ana bilgisayar içinde çalışan diğer kaplardan erişilebildiği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="dc99f-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="dc99f-159">Son olarak, *docker-compose.override.yml* dosyasında, eShopOnContainers örneği için `basket-api` microservice bu Redis kapsayıcı için kullanılacak bağlantı dizesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="dc99f-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="dc99f-160">Daha önce de belirtildiği gibi, `basketdata` microservice adı Docker iç ağ DNS tarafından çözülür.</span><span class="sxs-lookup"><span data-stu-id="dc99f-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dc99f-161">[Önceki](multi-container-applications-docker-compose.md)
>[Sonraki](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="dc99f-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
