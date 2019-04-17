---
title: Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmet mimarisi | Bir kapsayıcı olarak çalışan bir veritabanı sunucusu mi kullanıyorsunuz? yalnızca geliştirme için! Nedenini anlamak.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: c993f962d84ca3fc859ab704489300192536ee74
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611282"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="9cec0-104">Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="9cec0-104">Using a database server running as a container</span></span>

<span data-ttu-id="9cec0-105">Normal bir tek başına sunucular, şirket içi kümelerle ya da Azure SQL DB gibi bir bulut PaaS Hizmetleri, veritabanları (SQL Server, PostgreSQL, MySQL vb.) olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="9cec0-106">Ancak, geliştirme ve test ortamları için kapsayıcı olarak kullanışlı, herhangi bir dış bağımlılık olmadığı için çalışan ve yalnızca çalışan veritabanlarınızı sahip `docker-compose up` komut tüm uygulamayı başlatır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="9cec0-107">Veritabanı kapsayıcısında başlatıldı ve testler daha öngörülebilir olabilir. Bu nedenle her zaman aynı örnek verilerle doldurulur kapsayıcıları olarak bu veritabanına sahip olmanın da tümleştirme testleri için harika olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="9cec0-108">Mikro hizmet ile ilgili bir veritabanıyla bir kapsayıcı çalışan SQL Server</span><span class="sxs-lookup"><span data-stu-id="9cec0-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="9cec0-109">Hizmetine içinde tanımlanan sql.data adlı bir kapsayıcı olduğundan [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) mikro hizmetler için gerekli olan tüm SQL Server veritabanları ile Linux için SQL Server çalıştıran bir dosya.</span><span class="sxs-lookup"><span data-stu-id="9cec0-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="9cec0-110">(Her veritabanı için bir SQL Server kapsayıcı da olabilir, ancak, Docker için atanan daha fazla bellek gerektirir.) Mikro hizmetlerde en önemli nokta, her bir mikro hizmet kendi ilgili verileri bu nedenle, ilgili SQL veritabanı bu durumda sahip olduğunu ' dir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="9cec0-111">Ancak herhangi bir veritabanı olabilir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="9cec0-112">Örnek uygulamada bulunan SQL Server kapsayıcı çalıştırdığınızda, yürütülen docker-compose.yml dosyasında aşağıdaki YAML koduna yapılandırılmış `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="9cec0-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="9cec0-113">YAML koduna genel docker-compose.yml dosyasını ve docker-compose.override.yml dosyasını yapılandırma bilgilerini birleştirilmiş olmadığını unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9cec0-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="9cec0-114">(Genellikle SQL Server görüntüsünü ilgili temel veya statik bilgi ortam ayarları ayıracaktır.)</span><span class="sxs-lookup"><span data-stu-id="9cec0-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="9cec0-115">Benzer bir şekilde kullanmak yerine, `docker-compose`, aşağıdaki `docker run` komutu o kapsayıcı çalıştırın:</span><span class="sxs-lookup"><span data-stu-id="9cec0-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="9cec0-116">Hizmetine gibi çok kapsayıcılı bir uygulama dağıtıyorsanız, ancak kullanmak daha kullanışlı olan `docker-compose up` komut, böylece uygulama için gerekli tüm kapsayıcıları dağıtır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="9cec0-117">Bu SQL Server kapsayıcı ilk kez başlattığınızda, kapsayıcı sağladığınız parola ile SQL Server başlatır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="9cec0-118">Bir kapsayıcı SQL Server çalıştırıldıktan sonra normal bir SQL bağlantısı gibi SQL Server Management Studio, Visual Studio ve C bağlanarak veritabanı güncelleştirebilirsiniz\# kod.</span><span class="sxs-lookup"><span data-stu-id="9cec0-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="9cec0-119">Hizmetine uygulama örnek verilerle her bir mikro hizmet veritabanı verilerle başlangıçta temel olarak aşağıdaki bölümde açıklandığı gibi başlatır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="9cec0-120">Bir kapsayıcı çalışan SQL Server sahip olduğu SQL Server örneğine erişimi olmayabilir demo yalnızca kullanışlı değildir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="9cec0-121">Böylece kolayca temiz bir SQL Server görüntüsünü başlatma tümleştirme testleri çalıştırmak ve verileri yeni örnek veri üretme tarafından bilinen belirtildiği gibi ayrıca geliştirme ve test ortamları için harika bir hizmettir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="9cec0-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="9cec0-122">Additional resources</span></span>

- <span data-ttu-id="9cec0-123">**Linux, Mac veya Windows üzerinde SQL Server Docker görüntüsünü çalıştırma** \\</span><span class="sxs-lookup"><span data-stu-id="9cec0-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** \\</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="9cec0-124">**Bağlanma ve Linux'ta SQL Server sqlcmd ile sorgulama** \\</span><span class="sxs-lookup"><span data-stu-id="9cec0-124">**Connect and query SQL Server on Linux with sqlcmd** \\</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="9cec0-125">Web uygulama başlatma verileriyle test üretme</span><span class="sxs-lookup"><span data-stu-id="9cec0-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="9cec0-126">Uygulama başlatıldığında verileri veritabanına eklemek için yapılandırma yöntemine Web API projesi başlangıç sınıfına aşağıdaki gibi kod ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9cec0-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="9cec0-127">Aşağıdaki kodda özel CatalogContextSeed sınıf veri doldurur.</span><span class="sxs-lookup"><span data-stu-id="9cec0-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="9cec0-128">Tümleştirme testleri çalıştırdığınızda, tümleştirme testleri ile tutarlı verileri oluşturabileceği bir yol olan yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="9cec0-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="9cec0-129">Her şeyi bir kapsayıcı üzerinde çalışan SQL Server örneğini dahil olmak üzere sıfırdan oluşturmak için test ortamları için harika bir yoldur.</span><span class="sxs-lookup"><span data-stu-id="9cec0-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="9cec0-130">EF Core Inmemory veritabanı bir kapsayıcı çalışan SQL Server ile karşılaştırması</span><span class="sxs-lookup"><span data-stu-id="9cec0-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="9cec0-131">Testler çalışırken başka bir iyi seçim, Entity Framework Inmemory veritabanı sağlayıcısı kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="9cec0-132">Bu yapılandırma, Web API projesinde başlangıç sınıfı Createservicereplicalisteners() yönteminde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9cec0-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="9cec0-133">Ancak önemli bir catch yoktur.</span><span class="sxs-lookup"><span data-stu-id="9cec0-133">There is an important catch, though.</span></span> <span data-ttu-id="9cec0-134">Bellek içi veritabanı, belirli bir veritabanına belirli birçok kısıtlama desteklemez.</span><span class="sxs-lookup"><span data-stu-id="9cec0-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="9cec0-135">Örneği için benzersiz bir dizin EF Core modelinizde bir sütun ekleyin ve bunu bir yinelenen değer eklemenize izin vermez, denetlenecek bellek içi veritabanınızda bir test yazın.</span><span class="sxs-lookup"><span data-stu-id="9cec0-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="9cec0-136">Ancak, bellek içi veritabanına kullanırken bir sütunun benzersiz dizinler işleyemiyor.</span><span class="sxs-lookup"><span data-stu-id="9cec0-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="9cec0-137">Bu nedenle, bellek içi veritabanı ile aynı gerçek bir SQL Server veritabanı şekilde davranmaz — veritabanı özgü kısıtlamaları öykünmek değil.</span><span class="sxs-lookup"><span data-stu-id="9cec0-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="9cec0-138">Buna rağmen bir bellek içi veritabanına test ve prototip oluşturma için hala faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="9cec0-139">Ancak, belirli bir veritabanı uygulama davranışını dikkate doğru tümleştirme testleri oluşturmak istiyorsanız, SQL Server gibi gerçek bir veritabanı kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="9cec0-140">Bu amaç için SQL Server çalıştıran bir kapsayıcıda, harika bir seçim ve EF Core Inmemory veritabanı sağlayıcısı daha doğru olduğu.</span><span class="sxs-lookup"><span data-stu-id="9cec0-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="9cec0-141">Bir kapsayıcı içinde çalışan bir Redis cache hizmeti kullanma</span><span class="sxs-lookup"><span data-stu-id="9cec0-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="9cec0-142">Redis, kavram kanıtı senaryoları ve geliştirme ve test için özellikle kapsayıcısı üzerinde çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9cec0-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="9cec0-143">Tüm bağımlılıklarınızı kapsayıcılarında çalıştırılan olabilir çünkü bu senaryo uygundur: yalnızca değil yerel geliştirme makineleriniz için test ortamlarınızda CI/CD işlem hatlarınızı için.</span><span class="sxs-lookup"><span data-stu-id="9cec0-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="9cec0-144">Ancak, üretim ortamında Redis çalıştırdığınızda, Redis Microsoft bir PaaS (hizmet olarak Platform) olarak çalışan Azure gibi bir yüksek kullanılabilirlik çözümü arayın daha iyi olur.</span><span class="sxs-lookup"><span data-stu-id="9cec0-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="9cec0-145">Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="9cec0-146">Redis, Redis ile bir Docker görüntüsü sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cec0-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="9cec0-147">Bu görüntüyü Docker hub'dan bu URL'de kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="9cec0-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/\_/redis/>

<span data-ttu-id="9cec0-148">Doğrudan komut isteminde aşağıdaki Docker CLI komutunu yürüterek bir Redis Docker kapsayıcısı çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9cec0-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="9cec0-149">Bu nedenle standart kapsayıcı bağlama, otomatik olarak bağlı kapsayıcılara kullandıracağınız, Redis görüntüsünü'ı kullanıma sunar: 6379 (Redis tarafından kullanılan bağlantı noktası) içerir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="9cec0-150">Hizmetine basket.api mikro hizmet kapsayıcı olarak çalışan bir Redis önbelleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="9cec0-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="9cec0-151">Bu basket.data kapsayıcı çok kapsayıcılı docker-compose.yml dosyasını bir parçası olarak, aşağıdaki örnekte gösterildiği gibi tanımlanır:</span><span class="sxs-lookup"><span data-stu-id="9cec0-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="9cec0-152">Docker-compose.yml bu kodda, redis görüntüye göre ve 6379 bağlantı dahili olarak, yani yalnızca Docker konağı içinde çalışan diğer kapsayıcılar erişilebilir olacağını yayımlama basket.data adlı bir kapsayıcı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9cec0-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="9cec0-153">Son olarak, docker-compose.override.yml dosyasında basket.api mikro hizmetine örnek için Redis kapsayıcı için kullanılacak bağlantı dizesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="9cec0-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="9cec0-154">Daha önce belirtildiği gibi "basket.data" mikro hizmet adını docker'ın iç ağ DNS tarafından çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="9cec0-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9cec0-155">[Önceki](multi-container-applications-docker-compose.md)
>[İleri](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="9cec0-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
