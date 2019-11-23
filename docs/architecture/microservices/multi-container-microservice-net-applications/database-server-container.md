---
title: Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Kapsayıcı olarak çalışan bir veritabanı sunucusu mı kullanıyorsunuz? yalnızca geliştirme için! Nedenini anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: a508ba734525b24e2f3f00408e2c59c8c00f1898
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291309"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="63f14-104">Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma</span><span class="sxs-lookup"><span data-stu-id="63f14-104">Using a database server running as a container</span></span>

<span data-ttu-id="63f14-105">Veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) normal tek başına sunucularda, şirket içi kümelerde veya Azure SQL VERITABANı gibi buluttaki PaaS hizmetlerinde bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63f14-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="63f14-106">Ancak, geliştirme ve test ortamları için, herhangi bir dış bağımlılığı olmadığından ve yalnızca `docker-compose up` komutu uygulamanın tamamını başlattığında, veritabanlarının kapsayıcılar olarak çalışmasını sağlamak uygun olur.</span><span class="sxs-lookup"><span data-stu-id="63f14-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="63f14-107">Veritabanı kapsayıcıda başlatıldığı ve her zaman aynı örnek verilerle doldurulduğu için, bu veritabanlarının kapsayıcı olarak kullanılması da çok önemlidir. bu nedenle, testler daha öngörülebilir hale getirebilir.</span><span class="sxs-lookup"><span data-stu-id="63f14-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="63f14-108">Mikro hizmetle ilgili bir veritabanıyla kapsayıcı olarak çalışan SQL Server</span><span class="sxs-lookup"><span data-stu-id="63f14-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="63f14-109">EShopOnContainers 'da, mikro hizmetler için gereken tüm SQL Server veritabanlarına sahip Linux için SQL Server çalıştıran [Docker-Compose. yıml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) dosyasında tanımlanan SQL. Data adlı bir kapsayıcı vardır.</span><span class="sxs-lookup"><span data-stu-id="63f14-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="63f14-110">(Her veritabanı için bir SQL Server kapsayıcısına da sahip olabilirsiniz, ancak bu, Docker 'a daha fazla bellek atanmasını gerektirir.) Mikro hizmetlerdeki önemli nokta, her bir mikro hizmetin ilgili verilerin sahibi olması, dolayısıyla ilgili SQL veritabanının bu durumda olması.</span><span class="sxs-lookup"><span data-stu-id="63f14-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="63f14-111">Ancak veritabanları herhangi bir yerde olabilir.</span><span class="sxs-lookup"><span data-stu-id="63f14-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="63f14-112">Örnek uygulamadaki SQL Server kapsayıcısı, `docker-compose up`çalıştırdığınızda yürütülen Docker-Compose. yıml dosyasında aşağıdaki YAML kodu ile yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="63f14-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="63f14-113">YAML kodunun genel Docker-Compose. yıml dosyasından ve Docker-Compose. override. yıml dosyasından birleştirilmiş yapılandırma bilgilerine sahip olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="63f14-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="63f14-114">(Genellikle, ortam ayarlarını SQL Server görüntüyle ilgili temel veya statik bilgilerden ayırabilirsiniz.)</span><span class="sxs-lookup"><span data-stu-id="63f14-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="63f14-115">Benzer bir şekilde, `docker-compose`kullanmak yerine aşağıdaki `docker run` komutu bu kapsayıcıyı çalıştırabilir:</span><span class="sxs-lookup"><span data-stu-id="63f14-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="63f14-116">Ancak, eShopOnContainers gibi çok kapsayıcılı bir uygulama dağıtıyorsanız, uygulamanın tüm gerekli kapsayıcılarını dağıtması için `docker-compose up` komutunu kullanmak daha uygundur.</span><span class="sxs-lookup"><span data-stu-id="63f14-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="63f14-117">Bu SQL Server kapsayıcısını ilk kez başlattığınızda, kapsayıcı, sağladığınız parolayla SQL Server başlatır.</span><span class="sxs-lookup"><span data-stu-id="63f14-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="63f14-118">SQL Server bir kapsayıcı olarak çalışmaya başladıktan sonra, SQL Server Management Studio, Visual Studio veya C\# kodu gibi herhangi bir normal SQL bağlantısı üzerinden bağlanarak veritabanını güncelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63f14-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="63f14-119">EShopOnContainers uygulaması, aşağıdaki bölümde açıklandığı gibi, her mikro hizmet veritabanını başlangıçtaki verilerle dengeli hale getirerek örnek verilerle başlatır.</span><span class="sxs-lookup"><span data-stu-id="63f14-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="63f14-120">Bir kapsayıcı olarak çalışan SQL Server olması yalnızca bir SQL Server örneğine erişiminizin olmadığı bir demo için yararlı değildir.</span><span class="sxs-lookup"><span data-stu-id="63f14-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="63f14-121">Belirtildiği gibi, geliştirme ve test ortamları için de harika olduğundan, yeni örnek verileri dengeli hale getirerek bir temiz SQL Server görüntüsünden ve bilinen verilerden itibaren tümleştirme testlerini kolayca çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63f14-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="63f14-122">Ek kaynaklar</span><span class="sxs-lookup"><span data-stu-id="63f14-122">Additional resources</span></span>

- <span data-ttu-id="63f14-123">**Linux, Mac veya Windows \ SQL Server Docker görüntüsünü çalıştırın**</span><span class="sxs-lookup"><span data-stu-id="63f14-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** \</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="63f14-124">**Sqlcmd \ ile Linux üzerinde SQL Server bağlama ve sorgulama**</span><span class="sxs-lookup"><span data-stu-id="63f14-124">**Connect and query SQL Server on Linux with sqlcmd** \</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="63f14-125">Web uygulaması başlangıcında test verileriyle dengeli dağıtım</span><span class="sxs-lookup"><span data-stu-id="63f14-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="63f14-126">Uygulama başlatıldığında veritabanına veri eklemek için, Web API projesinin başlangıç sınıfındaki yapılandırma yöntemine aşağıdakine benzer bir kod ekleyebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63f14-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="63f14-127">Özel CatalogContextSeed sınıfında bulunan aşağıdaki kod, verileri doldurur.</span><span class="sxs-lookup"><span data-stu-id="63f14-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="63f14-128">Tümleştirme testlerini çalıştırdığınızda, tümleştirme testleriniz ile tutarlı veri oluşturmak için bir yol olması yararlı olur.</span><span class="sxs-lookup"><span data-stu-id="63f14-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="63f14-129">Kapsayıcıda çalışan bir SQL Server örneği de dahil olmak üzere sıfırdan her şeyi oluşturabilmek, test ortamları için harika bir şeydir.</span><span class="sxs-lookup"><span data-stu-id="63f14-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="63f14-130">EF Core InMemory veritabanı, kapsayıcı olarak çalışan SQL Server karşı</span><span class="sxs-lookup"><span data-stu-id="63f14-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="63f14-131">Testleri çalıştırırken bir diğer iyi seçenek de Entity Framework InMemory veritabanı sağlayıcısını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="63f14-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="63f14-132">Bu yapılandırmayı, Web API projenizdeki başlangıç sınıfının ConfigureServices yönteminde belirtebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63f14-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="63f14-133">Ancak önemli bir catch vardır.</span><span class="sxs-lookup"><span data-stu-id="63f14-133">There is an important catch, though.</span></span> <span data-ttu-id="63f14-134">Bellek içi veritabanı, belirli bir veritabanına özgü birçok kısıtlamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="63f14-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="63f14-135">Örneğin, EF Core modelinizdeki bir sütuna benzersiz bir dizin ekleyebilir ve bir yinelenen değer eklemenize izin vermediğinden emin olmak için bellek içi veritabanınıza bir test yazabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63f14-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="63f14-136">Ancak bellek içi veritabanını kullanırken, bir sütundaki benzersiz dizinleri işleyemez.</span><span class="sxs-lookup"><span data-stu-id="63f14-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="63f14-137">Bu nedenle, bellek içi veritabanı gerçek bir SQL Server veritabanıyla tamamen aynı şekilde davranmaz; veritabanına özgü kısıtlamalara benzemez.</span><span class="sxs-lookup"><span data-stu-id="63f14-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="63f14-138">Bu nedenle, bir bellek içi veritabanı, test ve prototip oluşturma için hala yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="63f14-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="63f14-139">Ancak belirli bir veritabanı uygulamasının davranışını dikkate alan doğru tümleştirme testleri oluşturmak isterseniz, SQL Server gibi gerçek bir veritabanını kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="63f14-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="63f14-140">Bu amaçla, bir kapsayıcıda SQL Server çalıştırmak, EF Core InMemory veritabanı sağlayıcısından çok iyi bir seçimdir ve daha doğru bir seçenektir.</span><span class="sxs-lookup"><span data-stu-id="63f14-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="63f14-141">Kapsayıcıda çalışan Redsıs önbelleği hizmetini kullanma</span><span class="sxs-lookup"><span data-stu-id="63f14-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="63f14-142">Özellikle geliştirme ve test için ve kavram kanıtı olabilecek senaryolar için Redsıs 'yi bir kapsayıcıda çalıştırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="63f14-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="63f14-143">Bu senaryo, yalnızca yerel Geliştirme makinelerinizde değil, ancak CI/CD işlem hatlarınızdaki sınama ortamlarınız için değil, kapsayıcılarda çalışan tüm bağımlılıklarınızı sunabileceğinden kullanışlı bir yöntemdir.</span><span class="sxs-lookup"><span data-stu-id="63f14-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="63f14-144">Ancak, Redsıs 'yi üretimde çalıştırdığınızda, PaaS Microsoft Azure gibi (hizmet olarak platform) olarak çalışan yüksek kullanılabilirliğe sahip bir çözüm aramak daha iyidir.</span><span class="sxs-lookup"><span data-stu-id="63f14-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="63f14-145">Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.</span><span class="sxs-lookup"><span data-stu-id="63f14-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="63f14-146">Redsıs, redin ile bir Docker görüntüsü sağlar.</span><span class="sxs-lookup"><span data-stu-id="63f14-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="63f14-147">Bu URL 'de Docker Hub 'dan bu görüntü kullanılabilir:</span><span class="sxs-lookup"><span data-stu-id="63f14-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/\_/redis/>

<span data-ttu-id="63f14-148">Komut istemindeki aşağıdaki Docker CLı komutunu yürüterek bir Docker Redsıs kapsayıcısını doğrudan çalıştırabilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="63f14-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="63f14-149">Redsıs görüntüsü şunları içerir: 6379 (Redsıs tarafından kullanılan bağlantı noktası), bu nedenle standart kapsayıcı bağlama bunu otomatik olarak bağlantılı kapsayıcılar için kullanılabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="63f14-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="63f14-150">EShopOnContainers 'da sepet. API mikro hizmeti kapsayıcı olarak çalışan bir Redsıs önbelleği kullanır.</span><span class="sxs-lookup"><span data-stu-id="63f14-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="63f14-151">Bu sepet. veri kapsayıcısı, aşağıdaki örnekte gösterildiği gibi çok Kapsayıcılı Docker-Compose. yml dosyasının bir parçası olarak tanımlanmıştır:</span><span class="sxs-lookup"><span data-stu-id="63f14-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="63f14-152">Docker-Compose. yıml içindeki bu kod, redsıs görüntüsünü temel alan basket. Data adlı bir kapsayıcı tanımlar ve 6379 numaralı bağlantı noktasını dahili olarak yayımlayarak yalnızca Docker ana bilgisayarı içinde çalışan diğer kapsayıcılardan erişilebilir olacaktır.</span><span class="sxs-lookup"><span data-stu-id="63f14-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="63f14-153">Son olarak, Docker-Compose. override. yml dosyasında eShopOnContainers örneği için basket. API mikro hizmeti, o Redsıs kapsayıcısı için kullanılacak bağlantı dizesini tanımlar:</span><span class="sxs-lookup"><span data-stu-id="63f14-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="63f14-154">Daha önce bahsedildiği gibi, mikro hizmetin "sepet. Data" adı Docker 'ın iç ağ DNS 'i tarafından çözümlenir.</span><span class="sxs-lookup"><span data-stu-id="63f14-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="63f14-155">[Önceki](multi-container-applications-docker-compose.md)
>[İleri](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="63f14-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
