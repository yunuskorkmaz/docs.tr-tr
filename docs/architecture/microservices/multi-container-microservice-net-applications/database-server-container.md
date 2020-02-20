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
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="9ee03-104">Kapsayıcı olarak çalışan bir veritabanı sunucusunu kullanma</span><span class="sxs-lookup"><span data-stu-id="9ee03-104">Use a database server running as a container</span></span>

<span data-ttu-id="9ee03-105">Veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) normal tek başına sunucularda, şirket içi kümelerde veya Azure SQL VERITABANı gibi buluttaki PaaS hizmetlerinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee03-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="9ee03-106">Ancak, geliştirme ve test ortamları için, herhangi bir dış bağımlılığı olmadığından ve yalnızca `docker-compose up` komutu uygulamanın tamamını başlattığında, veritabanlarının kapsayıcılar olarak çalışmasını sağlamak uygun olur.</span><span class="sxs-lookup"><span data-stu-id="9ee03-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="9ee03-107">Veritabanı kapsayıcıda başlatıldığı ve her zaman aynı örnek verilerle doldurulduğu için, bu veritabanlarının kapsayıcı olarak kullanılması da çok önemlidir. bu nedenle, testler daha öngörülebilir hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="9ee03-108">Mikro hizmetle ilgili bir veritabanıyla kapsayıcı olarak çalışan SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ee03-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="9ee03-109">EShopOnContainers 'da, [Docker-Compose. yıml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) dosyasında tanımlanan `sqldata`adlı bir kapsayıcı vardır. Bu, bir Linux örneği için, bir tane olması gereken tüm mikro HIZMETLER için SQL veritabanlarına sahip bir SQL Server çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="9ee03-110">Mikro hizmetlerde bir anahtar noktası, her mikro hizmetin ilgili verilerinin sahibi olduğu için kendi veritabanına sahip olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="9ee03-111">Ancak veritabanları her yerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="9ee03-112">Bu durumda, Docker bellek gereksinimlerini mümkün olduğunca düşük tutmak için aynı kapsayıcıda bulunur.</span><span class="sxs-lookup"><span data-stu-id="9ee03-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="9ee03-113">Bu, geliştirme ve, belki de test için yeterli bir çözüm olduğunu ve üretime yönelik olmayan bir çözüm olduğunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="9ee03-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="9ee03-114">Örnek uygulamadaki SQL Server kapsayıcısı, `docker-compose up`çalıştırdığınızda yürütülen Docker-Compose. yıml dosyasında aşağıdaki YAML kodu ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="9ee03-115">YAML kodunun genel Docker-Compose. yıml dosyasından ve Docker-Compose. override. yıml dosyasından birleştirilmiş yapılandırma bilgilerine sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9ee03-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="9ee03-116">(Genellikle, ortam ayarlarını SQL Server görüntüyle ilgili temel veya statik bilgilerden ayırabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="9ee03-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="9ee03-117">Benzer bir şekilde, `docker-compose`kullanmak yerine aşağıdaki `docker run` komutu bu kapsayıcıyı çalıştırabilir:</span><span class="sxs-lookup"><span data-stu-id="9ee03-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="9ee03-118">Ancak, eShopOnContainers gibi çok kapsayıcılı bir uygulama dağıtıyorsanız, uygulamanın tüm gerekli kapsayıcılarını dağıtması için `docker-compose up` komutunu kullanmak daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="9ee03-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="9ee03-119">Bu SQL Server kapsayıcısını ilk kez başlattığınızda, kapsayıcı, sağladığınız parolayla SQL Server başlatır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="9ee03-120">SQL Server bir kapsayıcı olarak çalışmaya başladıktan sonra, SQL Server Management Studio, Visual Studio veya C\# kodu gibi herhangi bir normal SQL bağlantısı üzerinden bağlanarak veritabanını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee03-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="9ee03-121">EShopOnContainers uygulaması, aşağıdaki bölümde açıklandığı gibi, her mikro hizmet veritabanını başlangıçtaki verilerle dengeli hale getirerek örnek verilerle başlatır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="9ee03-122">Bir kapsayıcı olarak çalışan SQL Server olması yalnızca bir SQL Server örneğine erişiminizin olmadığı bir demo için yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="9ee03-123">Belirtildiği gibi, geliştirme ve test ortamları için de harika olduğundan, yeni örnek verileri dengeli hale getirerek bir temiz SQL Server görüntüsünden ve bilinen verilerden itibaren tümleştirme testlerini kolayca çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee03-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="9ee03-124">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9ee03-124">Additional resources</span></span>

- <span data-ttu-id="9ee03-125">**Linux, Mac veya Windows \ SQL Server Docker görüntüsünü çalıştırın**</span><span class="sxs-lookup"><span data-stu-id="9ee03-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** \</span></span>
    <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="9ee03-126">**Sqlcmd \ ile Linux üzerinde SQL Server bağlama ve sorgulama**</span><span class="sxs-lookup"><span data-stu-id="9ee03-126">**Connect and query SQL Server on Linux with sqlcmd** \</span></span>
    <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="9ee03-127">Web uygulaması başlangıcında test verileriyle dengeli dağıtım</span><span class="sxs-lookup"><span data-stu-id="9ee03-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="9ee03-128">Uygulama başlatıldığında veritabanına veri eklemek için, Web API projesinin `Program` sınıfındaki `Main` yöntemine aşağıdakine benzer bir kod ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9ee03-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

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

<span data-ttu-id="9ee03-129">Kapsayıcı başlangıcında bir veritabanının dağıtımı ve dağıtımı uygulanırken önemli bir desteklenmediği uyarısıyla vardır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="9ee03-130">Veritabanı sunucusu herhangi bir nedenle kullanılamadığından, sunucunun kullanılabilir olması beklenirken yeniden denemeleri işlemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="9ee03-131">Bu yeniden deneme mantığı, aşağıdaki kodda gösterildiği gibi `MigrateDbContext()` uzantısı yöntemi tarafından işlenir:</span><span class="sxs-lookup"><span data-stu-id="9ee03-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

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

<span data-ttu-id="9ee03-132">Özel CatalogContextSeed sınıfında bulunan aşağıdaki kod, verileri doldurur.</span><span class="sxs-lookup"><span data-stu-id="9ee03-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="9ee03-133">Tümleştirme testlerini çalıştırdığınızda, tümleştirme testleriniz ile tutarlı veri oluşturmak için bir yol olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9ee03-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="9ee03-134">Kapsayıcıda çalışan bir SQL Server örneği de dahil olmak üzere sıfırdan her şeyi oluşturabilmek, test ortamları için harika bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="9ee03-135">EF Core InMemory veritabanı, kapsayıcı olarak çalışan SQL Server karşı</span><span class="sxs-lookup"><span data-stu-id="9ee03-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="9ee03-136">Testleri çalıştırırken bir diğer iyi seçenek de Entity Framework InMemory veritabanı sağlayıcısını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="9ee03-137">Bu yapılandırmayı, Web API projenizdeki başlangıç sınıfının ConfigureServices yönteminde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9ee03-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="9ee03-138">Ancak önemli bir catch vardır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-138">There is an important catch, though.</span></span> <span data-ttu-id="9ee03-139">Bellek içi veritabanı, belirli bir veritabanına özgü birçok kısıtlamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9ee03-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="9ee03-140">Örneğin, EF Core modelinizdeki bir sütuna benzersiz bir dizin ekleyebilir ve bir yinelenen değer eklemenize izin vermediğinden emin olmak için bellek içi veritabanınıza bir test yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee03-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="9ee03-141">Ancak bellek içi veritabanını kullanırken, bir sütundaki benzersiz dizinleri işleyemez.</span><span class="sxs-lookup"><span data-stu-id="9ee03-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="9ee03-142">Bu nedenle, bellek içi veritabanı gerçek bir SQL Server veritabanıyla tamamen aynı şekilde davranmaz; veritabanına özgü kısıtlamalara benzemez.</span><span class="sxs-lookup"><span data-stu-id="9ee03-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="9ee03-143">Bu nedenle, bir bellek içi veritabanı, test ve prototip oluşturma için hala yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="9ee03-144">Ancak belirli bir veritabanı uygulamasının davranışını dikkate alan doğru tümleştirme testleri oluşturmak isterseniz, SQL Server gibi gerçek bir veritabanını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="9ee03-145">Bu amaçla, bir kapsayıcıda SQL Server çalıştırmak, EF Core InMemory veritabanı sağlayıcısından çok iyi bir seçimdir ve daha doğru bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="9ee03-146">Kapsayıcıda çalışan Redsıs önbelleği hizmetini kullanma</span><span class="sxs-lookup"><span data-stu-id="9ee03-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="9ee03-147">Özellikle geliştirme ve test için ve kavram kanıtı olabilecek senaryolar için Redsıs 'yi bir kapsayıcıda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ee03-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="9ee03-148">Bu senaryo, yalnızca yerel Geliştirme makinelerinizde değil, ancak CI/CD işlem hatlarınızdaki sınama ortamlarınız için değil, kapsayıcılarda çalışan tüm bağımlılıklarınızı sunabileceğinden kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="9ee03-149">Ancak, Redsıs 'yi üretimde çalıştırdığınızda, PaaS Microsoft Azure gibi (hizmet olarak platform) olarak çalışan yüksek kullanılabilirliğe sahip bir çözüm aramak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="9ee03-150">Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="9ee03-151">Redsıs, redin ile bir Docker görüntüsü sağlar.</span><span class="sxs-lookup"><span data-stu-id="9ee03-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="9ee03-152">Bu URL 'de Docker Hub 'dan bu görüntü kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9ee03-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="9ee03-153">Komut istemindeki aşağıdaki Docker CLı komutunu yürüterek bir Docker Redsıs kapsayıcısını doğrudan çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9ee03-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="9ee03-154">Redsıs görüntüsü şunları içerir: 6379 (Redsıs tarafından kullanılan bağlantı noktası), bu nedenle standart kapsayıcı bağlama bunu otomatik olarak bağlantılı kapsayıcılar için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="9ee03-155">EShopOnContainers 'da, `basket-api` mikro hizmeti kapsayıcı olarak çalışan bir Redsıs önbelleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ee03-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="9ee03-156">Bu `basketdata` kapsayıcı, aşağıdaki örnekte gösterildiği gibi çok Kapsayıcılı *Docker-Compose. yml* dosyasının bir parçası olarak tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="9ee03-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="9ee03-157">Docker-Compose. yıml içindeki bu kod, redsıs görüntüsüne göre `basketdata` adlı bir kapsayıcı tanımlar ve 6379 numaralı bağlantı noktasını dahili olarak yayımlarız.</span><span class="sxs-lookup"><span data-stu-id="9ee03-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="9ee03-158">Bu, yalnızca Docker ana bilgisayarı içinde çalışan diğer kapsayıcılardan erişilebileceği anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="9ee03-159">Son olarak, *Docker-Compose. override. yml* dosyasında eShopOnContainers örneği için `basket-api` mikro hizmeti, o redsıs kapsayıcısı için kullanılacak bağlantı dizesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="9ee03-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="9ee03-160">Daha önce belirtildiği gibi, mikro hizmet `basketdata` adı Docker 'ın iç ağ DNS tarafından çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9ee03-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9ee03-161">[Önceki](multi-container-applications-docker-compose.md)
>[İleri](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="9ee03-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
