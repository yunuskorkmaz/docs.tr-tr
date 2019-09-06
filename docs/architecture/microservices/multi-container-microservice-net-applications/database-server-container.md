---
title: Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma
description: Kapsayıcılı .NET uygulamaları için .NET mikro hizmetleri mimarisi | Kapsayıcı olarak çalışan bir veritabanı sunucusu mı kullanıyorsunuz? yalnızca geliştirme için! Nedenini anlayın.
ms.date: 10/02/2018
ms.openlocfilehash: 312f986b5aa710fe51c7c3488776395194526e51
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70296886"
---
# <a name="using-a-database-server-running-as-a-container"></a>Kapsayıcı olarak çalışan bir veritabanı sunucusu kullanma

Veritabanlarınızı (SQL Server, PostgreSQL, MySQL, vb.) normal tek başına sunucularda, şirket içi kümelerde veya Azure SQL VERITABANı gibi buluttaki PaaS hizmetlerinde bulabilirsiniz. Ancak, geliştirme ve test ortamları için, herhangi bir dış bağımlılığı olmadığından ve yalnızca `docker-compose up` komutu çalıştırmak uygulamanın tamamını başlattığında, veritabanlarının kapsayıcılar olarak çalışmasını sağlamak uygun olur. Veritabanı kapsayıcıda başlatıldığı ve her zaman aynı örnek verilerle doldurulduğu için, bu veritabanlarının kapsayıcı olarak kullanılması da çok önemlidir. bu nedenle, testler daha öngörülebilir hale getirebilir.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>Mikro hizmetle ilgili bir veritabanıyla kapsayıcı olarak çalışan SQL Server

EShopOnContainers 'da, mikro hizmetler için gereken tüm SQL Server veritabanlarına sahip Linux için SQL Server çalıştıran [Docker-Compose. yıml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) dosyasında tanımlanan SQL. Data adlı bir kapsayıcı vardır. (Her veritabanı için bir SQL Server kapsayıcısına da sahip olabilirsiniz, ancak bu, Docker 'a daha fazla bellek atanmasını gerektirir.) Mikro hizmetlerdeki önemli nokta, her bir mikro hizmetin ilgili verilerin sahibi olması, dolayısıyla ilgili SQL veritabanının bu durumda olması. Ancak veritabanları herhangi bir yerde olabilir.

Örnek uygulamadaki SQL Server kapsayıcısı, çalıştırdığınızda `docker-compose up`yürütülen Docker-Compose. yıml dosyasında aşağıdaki YAML kodu ile yapılandırılır. YAML kodunun genel Docker-Compose. yıml dosyasından ve Docker-Compose. override. yıml dosyasından birleştirilmiş yapılandırma bilgilerine sahip olduğunu unutmayın. (Genellikle, ortam ayarlarını SQL Server görüntüyle ilgili temel veya statik bilgilerden ayırabilirsiniz.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Kullanmak `docker-compose`yerine benzer bir şekilde, aşağıdaki `docker run` komut bu kapsayıcıyı çalıştırabilir:

```console
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Ancak, eshoponcontainers gibi çok kapsayıcılı bir uygulama dağıtıyorsanız, uygulamanın tüm gerekli kapsayıcıları dağıtması için `docker-compose up` komutunu kullanmak daha uygundur.

Bu SQL Server kapsayıcısını ilk kez başlattığınızda, kapsayıcı, sağladığınız parolayla SQL Server başlatır. SQL Server bir kapsayıcı olarak çalışmaya başladıktan sonra, SQL Server Management Studio, Visual Studio veya C\# kodu gibi herhangi bir normal SQL bağlantısı üzerinden bağlanarak veritabanını güncelleştirebilirsiniz.

EShopOnContainers uygulaması, aşağıdaki bölümde açıklandığı gibi, her mikro hizmet veritabanını başlangıçtaki verilerle dengeli hale getirerek örnek verilerle başlatır.

Bir kapsayıcı olarak çalışan SQL Server olması yalnızca bir SQL Server örneğine erişiminizin olmadığı bir demo için yararlı değildir. Belirtildiği gibi, geliştirme ve test ortamları için de harika olduğundan, yeni örnek verileri dengeli hale getirerek bir temiz SQL Server görüntüsünden ve bilinen verilerden itibaren tümleştirme testlerini kolayca çalıştırabilirsiniz.

#### <a name="additional-resources"></a>Ek kaynaklar

- **Linux, Mac veya Windows üzerinde SQL Server Docker görüntüsünü çalıştırma** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Sqlcmd ile Linux üzerinde SQL Server bağlama ve sorgulama** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Web uygulaması başlangıcında test verileriyle dengeli dağıtım

Uygulama başlatıldığında veritabanına veri eklemek için, Web API projesinin başlangıç sınıfındaki yapılandırma yöntemine aşağıdakine benzer bir kod ekleyebilirsiniz:

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

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory veritabanı, kapsayıcı olarak çalışan SQL Server karşı

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

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Kapsayıcıda çalışan Redsıs önbelleği hizmetini kullanma

Özellikle geliştirme ve test için ve kavram kanıtı olabilecek senaryolar için Redsıs 'yi bir kapsayıcıda çalıştırabilirsiniz. Bu senaryo, yalnızca yerel Geliştirme makinelerinizde değil, ancak CI/CD işlem hatlarınızdaki sınama ortamlarınız için değil, kapsayıcılarda çalışan tüm bağımlılıklarınızı sunabileceğinden kullanışlı bir yöntemdir.

Ancak, Redsıs 'yi üretimde çalıştırdığınızda, PaaS Microsoft Azure gibi (hizmet olarak platform) olarak çalışan yüksek kullanılabilirliğe sahip bir çözüm aramak daha iyidir. Kodunuzda bağlantı dizelerinizi değiştirmeniz yeterlidir.

Redsıs, redin ile bir Docker görüntüsü sağlar. Bu URL 'de Docker Hub 'dan bu görüntü kullanılabilir:

<https://hub.docker.com/\_/redis/>

Komut istemindeki aşağıdaki Docker CLı komutunu yürüterek bir Docker Redsıs kapsayıcısını doğrudan çalıştırabilirsiniz:

```console
  docker run --name some-redis -d redis
```

Redsıs görüntüsü şunları içerir: 6379 (Redsıs tarafından kullanılan bağlantı noktası), bu nedenle standart kapsayıcı bağlama bunu otomatik olarak bağlantılı kapsayıcılar için kullanılabilir hale getirir.

EShopOnContainers 'da sepet. API mikro hizmeti kapsayıcı olarak çalışan bir Redsıs önbelleği kullanır. Bu sepet. veri kapsayıcısı, aşağıdaki örnekte gösterildiği gibi çok Kapsayıcılı Docker-Compose. yml dosyasının bir parçası olarak tanımlanmıştır:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Docker-Compose. yıml içindeki bu kod, redsıs görüntüsünü temel alan basket. Data adlı bir kapsayıcı tanımlar ve 6379 numaralı bağlantı noktasını dahili olarak yayımlayarak yalnızca Docker ana bilgisayarı içinde çalışan diğer kapsayıcılardan erişilebilir olacaktır.

Son olarak, Docker-Compose. override. yml dosyasında eShopOnContainers örneği için basket. API mikro hizmeti, o Redsıs kapsayıcısı için kullanılacak bağlantı dizesini tanımlar:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Daha önce bahsedildiği gibi, mikro hizmetin "sepet. Data" adı Docker 'ın iç ağ DNS 'i tarafından çözümlenir.

>[!div class="step-by-step"]
>[Önceki](multi-container-applications-docker-compose.md)İleri
>[](integration-event-based-microservice-communications.md)
