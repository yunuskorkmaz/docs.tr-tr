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
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="1a364-103">Bir kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="1a364-103">Using a database server running as a container</span></span>

<span data-ttu-id="1a364-104">Normal tek başına sunucularda, şirket içi kümeleri veya Azure SQL DB gibi bulutta PaaS Hizmetleri'nde veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a364-104">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="1a364-105">Ancak, geliştirme ve test ortamları için çalışan kapsayıcılar veritabanlarınızı sahip uygun herhangi bir dış bağımlılığı olmadığından yalnızca olduğundan ve çalıştığından docker compose'u komut, tüm uygulama başlatır.</span><span class="sxs-lookup"><span data-stu-id="1a364-105">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency, and simply running the docker-compose command starts the whole application.</span></span> <span data-ttu-id="1a364-106">Veritabanı kapsayıcısında başlatıldı ve testleri daha tahmin edilebilir böylece her zaman aynı örnek verilerle doldurulur kapsayıcı olarak bu veritabanına sahip olmanın da tümleştirme testleri için mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="1a364-106">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="1a364-107">Mikro hizmet ile ilgili bir veritabanıyla bir kapsayıcı olarak çalışan SQL Server</span><span class="sxs-lookup"><span data-stu-id="1a364-107">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="1a364-108">EShopOnContainers içinde tanımlanan sql.data adlı bir kapsayıcı olduğundan [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) mikro hizmetler için gerekli tüm SQL Server veritabanları ile Linux için SQL Server çalıştıran dosya.</span><span class="sxs-lookup"><span data-stu-id="1a364-108">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="1a364-109">(Her veritabanı için bir SQL Server kapsayıcısı sahip olabilir, ancak, Docker için atanan daha fazla bellek gerektirir.) Önemli mikro içinde her mikro hizmet ilgili verileri, bu nedenle ilgili SQL veritabanını bu durumda sahibi olduğu noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="1a364-109">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="1a364-110">Ancak veritabanlarını her yerden olabilir.</span><span class="sxs-lookup"><span data-stu-id="1a364-110">But the databases can be anywhere.</span></span>

<span data-ttu-id="1a364-111">Örnek uygulama kapsayıcısında aşağıdaki YAML kod çalıştırdığınızda yürütülür docker-compose.yml dosyası ile yapılandırılmış SQL Server docker-kuruluşu ayarlama</span><span class="sxs-lookup"><span data-stu-id="1a364-111">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run docker-compose up.</span></span> <span data-ttu-id="1a364-112">Yapılandırma bilgilerini genel docker-compose.yml dosyası ve docker compose.override.yml dosyasındaki YAML kod birleştirilmiş unutmayın.</span><span class="sxs-lookup"><span data-stu-id="1a364-112">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="1a364-113">(Genellikle SQL Server görüntüsünü ilgili temel veya statik bilgiler ortam ayarlarından ayıracaktır.)</span><span class="sxs-lookup"><span data-stu-id="1a364-113">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

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

<span data-ttu-id="1a364-114">Benzer bir şekilde kullanmak yerine, `docker-compose`, aşağıdaki `docker run` komutu, bu kapsayıcı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a364-114">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

<span data-ttu-id="1a364-115">EShopOnContainers gibi birden çok kapsayıcı uygulama dağıtıyorsanız, ancak kullanmak daha kullanışlı olan uygulama için gerekli tüm kapsayıcılar dağıtır böylece komutu docker-oluşturun.</span><span class="sxs-lookup"><span data-stu-id="1a364-115">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the docker-compose up command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="1a364-116">Bu SQL Server kapsayıcı ilk kez başlattığınızda, kapsayıcı verdiğiniz parola ile SQL Server başlatır.</span><span class="sxs-lookup"><span data-stu-id="1a364-116">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="1a364-117">SQL Server bir kapsayıcı olarak çalışmaya başladıktan sonra tüm normal SQL bağlantısı gibi SQL Server Management Studio'yu, Visual Studio veya C bağlanarak veritabanı güncelleştirebilirsiniz\# kodu.</span><span class="sxs-lookup"><span data-stu-id="1a364-117">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="1a364-118">EShopOnContainers uygulama her mikro hizmet veritabanı örnek verilerle başlangıçta, verilerle dengeli dağıtarak aşağıdaki bölümde açıklandığı gibi başlatır.</span><span class="sxs-lookup"><span data-stu-id="1a364-118">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="1a364-119">Bir kapsayıcı olarak çalışan SQL Server sahip olduğu SQL Server'ın bir örneğine erişimi olmayabilir demo yalnızca kullanışlı değildir.</span><span class="sxs-lookup"><span data-stu-id="1a364-119">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="1a364-120">Böylece kolayca temiz bir SQL Server görüntüden başlangıç tümleştirme testleri çalıştırın ve yeni örnek veriler dengeli dağıtarak veri bilinen belirtildiği gibi aynı zamanda geliştirme ve test ortamları için çok yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a364-120">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1a364-121">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="1a364-121">Additional resources</span></span>

-   <span data-ttu-id="1a364-122">**Linux, Mac veya Windows üzerinde SQL Server Docker görüntü çalıştırın**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span><span class="sxs-lookup"><span data-stu-id="1a364-122">**Run the SQL Server Docker image on Linux, Mac, or Windows**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span></span>

-   <span data-ttu-id="1a364-123">**Bağlanma ve sqlcmd ile SQL Server Linux üzerinde sorgulama**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="1a364-123">**Connect and query SQL Server on Linux with sqlcmd**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span></span>

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="1a364-124">Web uygulaması başlangıç test verilerle üretme</span><span class="sxs-lookup"><span data-stu-id="1a364-124">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="1a364-125">Uygulama başlatıldığında veritabanına veri eklemek için Web API projesini başlangıç sınıfının yapılandırma yöntemine kod aşağıdaki gibi ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a364-125">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="1a364-126">Özel CatalogContextSeed sınıfında aşağıdaki kodu verileri doldurur.</span><span class="sxs-lookup"><span data-stu-id="1a364-126">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="1a364-127">Tümleştirme testlerini çalıştırdığınızda, tümleştirme testlerinizi ile tutarlı verileri oluşturmak için bir yol olması yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a364-127">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="1a364-128">Her şeyi bir kapsayıcı üzerinde çalışan SQL Server örneği de dahil olmak üzere sıfırdan oluşturma yetkisi olan test ortamları için mükemmeldir.</span><span class="sxs-lookup"><span data-stu-id="1a364-128">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="1a364-129">EF çekirdek Inmemory veritabanı bir kapsayıcı olarak çalışan SQL Server ile karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="1a364-129">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="1a364-130">Testleri çalıştırırken başka bir iyi seçimdir Entity Framework Inmemory veritabanı sağlayıcısı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="1a364-130">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="1a364-131">Bu yapılandırma, Web API projesinde başlangıç sınıfı ConfigureServices yönteminde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a364-131">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="1a364-132">Ancak önemli bir catch yoktur.</span><span class="sxs-lookup"><span data-stu-id="1a364-132">There is an important catch, though.</span></span> <span data-ttu-id="1a364-133">Bellek içi veritabanı belirli bir veritabanına özgü birçok kısıtlamaları desteklemez.</span><span class="sxs-lookup"><span data-stu-id="1a364-133">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="1a364-134">Örneği için benzersiz bir dizin EF çekirdek modelinizde bir sütun ekleyin ve onu yinelenen değer eklemenize izin vermez olduğunu denetlemek için bellek içi veritabanına karşı test yazma.</span><span class="sxs-lookup"><span data-stu-id="1a364-134">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="1a364-135">Ancak, bellek içi veritabanı kullanırken, bir sütunda benzersiz dizinler işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="1a364-135">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="1a364-136">Bu nedenle, bellek içi veritabanı tam olarak aynı gerçek bir SQL Server veritabanı olarak davranıyor değildir — veritabanı özgü kısıtlamaları öykünmek değil.</span><span class="sxs-lookup"><span data-stu-id="1a364-136">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="1a364-137">Buna rağmen bir bellek içi veritabanı sınama ve prototipi oluşturulurken için hala yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="1a364-137">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="1a364-138">Ancak belirli veritabanı uygulama davranışını dikkate doğru tümleştirme testleri oluşturmak istiyorsanız, SQL Server gibi gerçek bir veritabanını kullanmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="1a364-138">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="1a364-139">Bu amaç için SQL Server bir kapsayıcıda seçim ve EF çekirdek Inmemory veritabanı sağlayıcısı daha kesin mükemmel çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="1a364-139">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="1a364-140">Bir kapsayıcıda çalışan bir Redis önbelleği hizmeti kullanma</span><span class="sxs-lookup"><span data-stu-id="1a364-140">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="1a364-141">Redis ve kavram kanıtı senaryoları özellikle geliştirme ve test için bir kapsayıcı çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="1a364-141">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="1a364-142">Tüm bağımlılıkları kapsayıcılarında çalıştıran olabileceği için bu senaryo uygundur — değil yalnızca yerel geliştirme makinelerinizi, ancak test ortamınızı CI/CD hatlarınızı.</span><span class="sxs-lookup"><span data-stu-id="1a364-142">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="1a364-143">Ancak, Redis üretimde çalıştırdığınızda, Redis Microsoft PaaS (hizmet olarak Platform) olarak çalışan Azure gibi bir yüksek kullanılabilirlik çözümü arayın en iyisidir.</span><span class="sxs-lookup"><span data-stu-id="1a364-143">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="1a364-144">Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="1a364-144">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="1a364-145">Redis, Redis Docker görüntüsüyle sağlar.</span><span class="sxs-lookup"><span data-stu-id="1a364-145">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="1a364-146">Bu görüntü, Docker hub'a bu URL'de edinilebilir:</span><span class="sxs-lookup"><span data-stu-id="1a364-146">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="1a364-147">Docker Redis bir kapsayıcı, komut isteminde aşağıdaki Docker CLI komutunu yürüterek doğrudan çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="1a364-147">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="1a364-148">Bu nedenle standart kapsayıcı bağlama otomatik olarak bağlantılı kapsayıcıları kullanabilmesi, Redis görüntü sunmaya: 6379 (Redis tarafından kullanılan bağlantı noktası) içerir.</span><span class="sxs-lookup"><span data-stu-id="1a364-148">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="1a364-149">EShopOnContainers içinde basket.api mikro hizmet kapsayıcı olarak çalışan bir Redis önbelleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="1a364-149">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="1a364-150">Bu basket.data kapsayıcı, aşağıdaki örnekte gösterildiği gibi birden çok kapsayıcı docker-compose.yml dosyası bir parçası olarak tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="1a364-150">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="1a364-151">Bu kodu docker-compose.yml redis görüntüyü temel alarak ve bağlantı noktası 6379 dahili olarak, yalnızca Docker ana içinde çalışan diğer kapsayıcılar erişilebilir olacaktır anlamına yayımlama basket.data adlı bir kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="1a364-151">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="1a364-152">Son olarak, docker compose.override.yml dosyasında eShopOnContainers örnek basket.api mikro hizmet bu Redis kapsayıcı için kullanılacak bağlantı dizesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="1a364-152">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
<span data-ttu-id="1a364-153">[Önceki] (çok-container-uygulamalar-docker-compose.md) [sonraki] (tümleştirme-olay-tabanlı-mikro hizmet-communications.md)</span><span class="sxs-lookup"><span data-stu-id="1a364-153">[Previous] (multi-container-applications-docker-compose.md) [Next] (integration-event-based-microservice-communications.md)</span></span>
