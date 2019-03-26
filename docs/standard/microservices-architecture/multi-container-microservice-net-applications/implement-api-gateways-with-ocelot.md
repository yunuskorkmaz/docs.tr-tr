---
title: API ağ geçitleri Ocelot ile uygulama
description: API ağ geçitleri ile Ocelot uygular ve kapsayıcı tabanlı bir ortamda Ocelot kullanmayı öğrenin.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: b7ef0e7a172337f32f625bd65261b6577decd223
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2019
ms.locfileid: "58464547"
---
# <a name="implement-api-gateways-with-ocelot"></a>API ağ geçitleri ile Ocelot uygular

Mikro hizmet başvurusu [hizmetine](https://github.com/dotnet-architecture/eShopOnContainers) kullanıyor [Ocelot](https://github.com/ThreeMammals/Ocelot), basit ve basit API dağıtabileceğiniz herhangi bir yere, mikro hizmetler/kapsayıcılar ile birlikte olduğu gibi ağ geçidi herhangi bir hizmetine tarafından kullanılan aşağıdaki ortamları.

- Docker konağı, yerel geliştirme PC, şirket içinde veya bulutta.
- Kubernetes kümenizi şirket içinde veya Azure Kubernetes Service (AKS) gibi yönetilen bulut.
- Service Fabric kümesi, şirket içi veya bulutta.
- Azure PaaS/sunucusuz olarak Service Fabric kafes.

## <a name="architect-and-design-your-api-gateways"></a>Mimari ve tasarım, API ağ geçitleri

Aşağıdaki Mimari diyagram, API ağ geçitleri ile Ocelot hizmetine içinde nasıl uygulandığını gösterir.

![istemci uygulamaları, mikro hizmetler ve API ağ geçitleri arasında gösteren hizmetine mimarisi diyagramı](./media/image28.png)

**Şekil 6-28**. API ağ geçitleri ile hizmetine mimarisi

Bu diyagram, tek bir Docker konağı ya da geliştirme PC "Windows için Docker" veya "Docker için Mac" tüm uygulamayı nasıl dağıtılacağını gösterir. Tüm orchestrator dağıtma oldukça benzer olacaktır ancak diyagramında herhangi bir kapsayıcı orchestrator'da genişletilmiş.

Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıkları orchestrator'dan boşaltılmamalıdır ve Azure Service Bus, Azure SQL veritabanı, Azure Cosmos DB, Azure Redis, altyapısı için yüksek kullanılabilir sistemleri içine dağıtılan, ya da şirket içi çözüm kümeleme herhangi bir HA.

Diyagramda da olduğunu fark edebilirsiniz gibi birkaç API ağ geçidine sahip birden çok geliştirme takımları (Bu durumda özellikleri vs pazarlama. otonom olmasını sağlar Özellikleri alışveriş) geliştirme ve kendi mikro hizmetlerin yanı sıra kendi ilgili API ağ geçitleri dağıtma.

Tek bir uygulamanın parçası tüm mikro hizmetler halinde birleştirebilir birkaç geliştirme takımı tarafından güncelleştirilmesi için tek bir nokta açardı bir tek tek parça API Gateway tablonuz varsa.

Çok daha tasarımında giderek, bazı durumlarda ayrıntılı bir API ağ geçidi de bir tek iş mikro hizmet seçilen mimarisine bağlı olarak sınırlı olabilir. API ağ geçidinin sınırları iş veya etki alanı tarafından dikte sahip daha iyi bir tasarım elde etmenize yardımcı olur.

Örneğin, kavramı ayrıntılı bir API ağ geçidi, bir kullanıcı Arabirimi oluşturma hizmetine benzer olduğundan ince ayrıntılı olmasını API ağ geçidi katmanındaki üzerinde mikro hizmetler, alan daha gelişmiş bileşik kullanıcı Arabirimi uygulamalar için özellikle kullanışlı olabilir.

Biz önceki bölümde daha fazla ayrıntıya delve [üzerinde mikro hizmet tabanlı bileşik kullanıcı Arabirimi oluşturma](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).

Güvenebileceğinizdir özel olarak geliştirilmiş bir API ağ geçidi kullanarak birçok Orta ve büyük-ölçekli uygulamalar için genellikle iyi bir yaklaşım olduğu gibi ancak tek tek parça toplayıcısı veya benzersiz merkezi özel API ağ geçidi olarak değil, API ağ geçidi, birden çok bağımsız izin vermesi dışında otonom mikro hizmetler oluşturma birkaç geliştirme ekipleri için yapılandırma alanları.

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a>Örnek mikro hizmetler / API ağ geçitleri yeniden yönlendirmek için kapsayıcılar

Örneğin, hizmetine yaklaşık altı iç mikro hizmet-API ağ geçitleri yayımlanmasını aşağıdaki görüntüde gösterildiği gibi sahip türleri vardır.

![Yalnızca sepet, katalog, konum, pazarlama, sıralama ve ödeme mikro hizmetler API ağ geçidi üzerinden yayımlanır.](./media/image29.png)

**Şekil 6-29**. Mikro hizmet klasörlerinde hizmetine çözümünü Visual Studio'da

Kimlik hizmeti hakkında tasarımında, API ile Ocelot da rerouting listeleri bir parçası olarak dahil etmek mümkündür ancak, çapraz önemli bir sistemde olduğundan yönlendirme ağ geçidi dışında bırakılır.

Koddan söyleyebilirsiniz gibi bu hizmetler şu anda ASP.NET Core Web API Hizmetleri olarak uygulanır. Bir mikro hizmet Kataloğu mikro hizmet kodu gibi odaklanalım.

![Çözüm Gezgini görünümü Catalog.API proje.](./media/image30.png)

**Şekil 6-30**. Örnek Web API'si mikro hizmet (katalog mikro hizmet)

Tipik bir ASP.NET Core Web API'si projesi birkaç denetleyicileriyle Kataloğu mikro hizmetidir ve yöntemleri aşağıdaki kodda ister görebilirsiniz.

```csharp
[HttpGet]
[Route("items/{id:int}")]
[ProducesResponseType((int)HttpStatusCode.BadRequest)]
[ProducesResponseType((int)HttpStatusCode.NotFound)]
[ProducesResponseType(typeof(CatalogItem),(int)HttpStatusCode.OK)]
public async Task<IActionResult> GetItemById(int id)
{
    if (id <= 0)
    {
        return BadRequest();
    }
    var item = await _catalogContext.CatalogItems.
                                          SingleOrDefaultAsync(ci => ci.Id == id);
    //…

    if (item != null)
    {
        return Ok(item);
    }
    return NotFound();
}
```
HTTP isteği, tür çalışan sona erecek C# kod mikro hizmet veritabanı ve gerekli herhangi bir ek eylem erişme.

Mikro hizmet URL'si ile ilgili kapsayıcıları, yerel geliştirme bilgisayar (yerel Docker konağı) dağıtıldığında, her bir mikro hizmetin ait kapsayıcı her zaman dahili bir bağlantı vardır. (genellikle, bağlantı noktası 80) aşağıdaki dockerfile olduğu gibi ilgili dockerfile içinde belirtilen:

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

Bağlantı noktası 80 kodda gösterildiği bir Docker konağı içinde iç olduğundan istemci uygulamalar tarafından erişilemiyor.

İstemci uygulamaları ile dağıtım yaparken yayımlanan yalnızca dış bağlantı noktaları (varsa) erişim `docker-compose`.

Dış bağlantı noktalarından bir üretim ortamına dağıtma yaparken yayımlanması gerekir. API ağ geçidi istemci uygulamalar ve mikro hizmetler arasında doğrudan iletişim önlemek için kullanmak istediğiniz neden tam olarak budur.

Ancak, geliştirirken, mikro hizmet/kapsayıcı doğrudan erişim Swagger çalıştırmak istediğiniz. İşte bu nedenle hizmetine, bile bunlar API ağ geçidi veya istemci uygulamalar tarafından kullanılmayacak, dış bağlantı noktaları hala belirtilir.

İşte bir örnek `docker-compose.override.yml` Kataloğu mikro hizmet dosyası:

```yml
catalog.api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

Docker-compose.override.yml yapılandırmada Kataloğu kapsayıcı iç bağlantı noktası 80 numaralı bağlantı noktasını nasıl olduğunu görebilirsiniz, ancak 5101 dış erişim için bağlantı noktasıdır. Ancak, bu bağlantı noktası uygulama tarafından bir API ağ geçidi yalnızca hata ayıklama, çalıştırma ve test yalnızca katalog mikro hizmet kullanırken kullanılmamalıdır.

Normalde, olmayacaktır ile dağıtma docker-compose bir üretim ortamına mikro Hizmetleri için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir orchestrator olduğundan. Bu ortamlar için dağıtım yaparken burada herhangi bir dış bağlantı işlemi mikro hizmetlere yönelik doğrudan yayınlama olmaz ancak API ağ geçidi ters Ara sunucuya her zaman kullanacağınız farklı yapılandırma dosyalarını kullanın.

Katalog mikro hizmet, yerel bir Docker konağı tam hizmetine çözüm Visual Studio'da çalıştırarak ya da Çalıştır (docker'da tüm hizmetleri çalıştıracaksınız-compose dosyası) veya yeni katalog mikro hizmet aşağıdaki docker ile başlayan-compose CMD ya da klasör konumlandırılmış PowerShell komutunu burada `docker-compose.yml` ve docker-compose.override.yml yerleştirilir.

```console
docker-compose run --service-ports catalog.api
```

Bu komut yalnızca catalog.api hizmet kapsayıcı yanı sıra docker-compose.yml belirtilen bağımlılıkları çalıştırır. Bu durumda SQL Server kapsayıcı ve RabbitMQ kapsayıcı.

Ardından, doğrudan Kataloğu mikro hizmet erişebilir ve kendi yöntemlerini doğrudan aracılığıyla "dış", bu durumda numaralı bağlantı noktasını erişme Swagger UI aracılığıyla görmek `http://localhost:5101/swagger`:

![Catalog.API REST API için Swagger kullanıcı arabirimini yaşında tarayıcı görünümü.](./media/image31.png)

**Şekil 6-31**. Katalog mikro hizmet kendi Swagger kullanıcı Arabirimi ile test etme

Bu noktada, Visual Studio'da C# kod bir kesme noktası ayarlayın, mikro hizmet Swagger kullanıcı Arabiriminde kullanıma sunulan yöntemleri test ve son olan her şeyi Temizleme `docker-compose down` komutu.

Ancak, doğrudan erişim mikro hizmet için bu durumda harici bağlantı noktası üzerinden 5101 tam olarak uygulamanızda önlemek istediğiniz iletişimdir. Ve ek API ağ geçidinin (Bu durumda, Ocelot) yöneltme düzeyi ayarlayarak, önleyebilirsiniz. Bu şekilde, istemci uygulaması doğrudan mikro hizmet erişimi olmaz.

## <a name="implementing-your-api-gateways-with-ocelot"></a>API ağ Geçitlerinizi Ocelot ile uygulama

Ocelot temel olarak, belirli bir sırayla uygulayabileceğiniz middlewares kümesidir.

Ocelot, yalnızca ASP.NET Core ile çalışacak şekilde tasarlanmıştır. Bu nedenle, .NET Standard 2.0 desteklenir, .NET Core 2.0 çalışma zamanı ve .NET Framework 4.6.1 çalışma zamanı dahil her yerde kullanılabilir ve yedekleme netstandard2.0 hedefler.

ASP.NET Core projenizdeki Ocelot ve bağımlılıklarını yüklemek [Ocelot'ın NuGet paketini](https://www.nuget.org/packages/Ocelot/), Visual Studio'dan.

```powershell
Install-Package Ocelot
```

Hizmetine, basit bir ASP.NET Core Web barındırma proje kendi API ağ geçidi uygulamasıdır ve Ocelot'ın middlewares API ağ geçidi özellikleri aşağıdaki görüntüde gösterildiği gibi işleme:

![Çözüm Gezgini görünümü Ocelot API ağ geçidi proje.](./media/image32.png)

**Şekil 6-32**. Hizmetine OcelotApiGw temel proje

Bu ASP.NET Core Web barındırma proje temelde iki basit dosyalarıyla oluşturulmuştur: `Program.cs` ve `Startup.cs`.

Program.cs yalnızca oluşturulup tipik ASP.NET Core BuildWebHost yapılandırılması gerekir.

```csharp
namespace OcelotApiGw
{
    public class Program
    {
        public static void Main(string[] args)
        {
            BuildWebHost(args).Run();
        }

        public static IWebHost BuildWebHost(string[] args)
        {
            var builder = WebHost.CreateDefaultBuilder(args);

            builder.ConfigureServices(s => s.AddSingleton(builder))
                    .ConfigureAppConfiguration(
                          ic => ic.AddJsonFile(Path.Combine("configuration",
                                                            "configuration.json")))
                    .UseStartup<Startup>();
            var host = builder.Build();
            return host;
        }
    }
}
```

Önemli nokta burada Ocelot için `configuration.json` Oluşturucu sağlaması gereken dosya `AddJsonFile()` yöntemi. Olduğunu `configuration.json` , tüm API ağ geçidi belirli bağlantı noktaları ile dış uç noktaları ve ilişkili iç uç nokta yani genellikle farklı bağlantı noktalarını kullanarak ReRoutes, belirttiğiniz yerdir.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Yapılandırma için iki bölümü vardır. Yeniden yönlendirir ve bir GlobalConfiguration dizisi. Yeniden yönlendiren bir Yukarı Akış isteği işlemek nasıl Ocelot bildiren nesneleridir. Genel yapılandırma geçersiz kılmalarına yönelik özel ayarları yeniden yönlendirme sağlar. Yeniden yönlendirme belirli ayarları çok sayıda yönetmek istemiyorsanız yararlıdır.

İşte basit bir örnek [yöneltme yapılandırma dosyası](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) hizmetine API Gateway'lerinden birinin.

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/c/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ]
    },
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }

  ],
    "GlobalConfiguration": {
      "RequestIdKey": "OcRequestId",
      "AdministrationPath": "/administration"
    }
  }
```

Bir Ocelot API ağ geçidi ana işlevlerini olan gelen HTTP isteklerini almak ve bunları bir aşağı akış hizmeti açın iletebilir, şu anda başka bir HTTP isteği. Ocelot'ın başka bir yeniden yönlendirmek için bir istek yönlendirme açıklar.

Örneğin, şimdi yeniden yönlendirir, yukarıdaki, sepet mikro hizmet yapılandırmasını configuration.json birini odaklanır.

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [ "POST", "PUT", "GET" ],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
}
```

Bu istek için iletilir iç mikro hizmet URL'si DownstreamPathTemplate, şema ve DownstreamHostAndPorts olun.

Bağlantı, hizmet tarafından kullanılan iç bağlantı noktasıdır. Kapsayıcıları kullanarak, bağlantı noktası ilgili dockerfile belirtilmiş.

`Host` Kullandığınız hizmet adı çözünürlüğüne bağlıdır hizmet adıdır. Kullanarak docker-compose adları docker'da sağlanan hizmet adları kullanarak Docker konağı tarafından sağlanan hizmetleri-compose dosyası. Kubernetes veya Service Fabric gibi bir orchestrator kullanıyorsanız, bu ad DNS ile çözümlenip ya da her orchestrator tarafından sağlanan ad çözümlemesi.

DownstreamHostAndPorts isteklerini iletmek istediğiniz herhangi bir aşağı akış hizmetleriyle bağlantı noktası ve ana bilgisayar içeren bir dizidir. Genellikle bu yalnızca bir giriş içerir, ancak bazen Yük Dengeleme isteklerini, aşağı akış hizmetleriyle isteyebilirsiniz ve Ocelot birden fazla giriş ekleyin ve ardından Yük Dengeleyici seçmenizi sağlar. Ancak, Azure ve tüm orchestrator kullanıyorsanız, Bulut ve orchestrator altyapısıyla dengelemek için çok iyi bir fikir olabilir.

UpstreamPathTemplate Ocelot istemciden gelen belirli bir istek için kullanmak için hangi DownstreamPathTemplate tanımlamak için kullanacağı URL'dir. Son olarak, Ocelot farklı isteklerini aynı URL'yi (POST, Al koy) arasında ayrım yapabilme kolaylığı için UpstreamHttpMethod kullanılır.

Bu noktada, tek bir Ocelot API'sini kullanarak ağ geçidi (ASP.NET Core Web barındırma) sahip olabilir veya [birden çok birleştirilmiş configuration.json dosyaları](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) ya da depolayabilirsiniz [yapılandırma Consul KV deposundaki](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).

Ancak gerçekten otonom mikro hizmetler olmasını istiyorsanız, mimari ve tasarım bölümlerinde sunulan gibi birden çok API ağ geçitleri ve/veya BFF (ön uç için arka uç), tek tek parça API ağ geçidi bölün daha iyi olabilir. Bu amaçla, Docker kapsayıcıları ile bu yaklaşımı uygulamak nasıl bir bakalım.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Birden çok farklı API ağ geçidi'ni çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanarak / BFF kapsayıcı türleri

Hizmetine içinde tek bir Docker kapsayıcı görüntüsü Ocelot API ağ geçidi ile kullanıyoruz ancak ardından, çalışma zamanında farklı Hizmetleri/kapsayıcılar API-ağ geçidi/BFF her tür için bir farklı configuration.json dosyası sağlayarak kullanarak bir docker birime oluştururuz Her hizmet için farklı bir bilgisayar klasöre erişin.

![İçin dört tüm API ağ geçitleri Ocelot API ağ geçidi için tek bir Docker görüntüsü kullanılır](./media/image33.png)

**Şekil 6-33**. Birden çok API ağ geçidi türleri arasında yeniden tek Ocelot Docker görüntüsü kullanma

Hizmetine "Genel Ocelot API ağ geçidi Docker görüntüsünü" 'OcelotApiGw' adlı proje ile oluşturulur ve görüntünün adı "Elektronik Mağaza/ocelotapigw" yani docker-compose.yml dosyası içinde belirtilen. Ardından, Docker için dağıtırken, olacaktır o aynı Docker görüntüden oluşturulan dört API ağ geçidi kapsayıcılar aşağıdaki docker-compose.yml dosyasını ayıklayın de gösterildiği gibi.

```yml
  mobileshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  mobilemarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webshoppingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile

  webmarketingapigw:
    image: eshop/ocelotapigw:${TAG:-latest}
    build:
      context: .
      dockerfile: src/ApiGateways/ApiGw-Base/Dockerfile
```

Ayrıca, aşağıdaki docker-compose.override.yml dosya görebileceğiniz gibi her bir hizmet kapsayıcısı için farklı Ocelot yapılandırma dosyası API ağ geçidi kapsayıcıların arasındaki tek fark, ve çalışma zamanında belirtilen bir Docker birim.

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity.api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

Dört API ağ geçitleri üzerindeki aynı Docker görüntüsü tabanlı olduğundan dolayı önceki kod ve Visual Studio Gezgini her belirli iş/BFF tanımlamak için gerekli tek dosya aşağıda gösterildiği gibi API ağ geçidi yalnızca bir configuration.json dosyasıdır.

![Tüm API ağ geçitleri arasındaki tek fark, her birinde bir configuration.json dosyasıdır.](./media/image34.png)

**Şekil 6-34**. Her API ağ geçidi tanımlamak için gerekli tek dosya / BFF Ocelot ile bir yapılandırma dosyası

API ağ geçidi ile birden çok API ağ geçitleri arasında bölünmesi sayesinde mikro hizmetler farklı alt kümelerinde üzerinde odaklanarak farklı geliştirme ekipleri bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitleri yönetebilirsiniz. Ayrıca, aynı anda aynı Ocelot Docker görüntüsünü yeniden kullanabilirsiniz.

Şimdi, (varsayılan olarak VS hizmetine ServicesAndWebApps.sln solution açarken veya çalışıyor "docker compose up ise" dahil) API ağ geçitleri ile hizmetine çalıştırırsanız, aşağıdaki örnek yolları gerçekleştirilir.

Örneğin, Yukarı Akış URL'sini ziyaret `http://localhost:5202/api/v1/c/catalog/items/2/` webshoppingapigw API ağ geçidi tarafından sunulan, aynı sonucu iç akış URL'den aldığınız `http://catalog.api/api/v1/2` aşağıdaki tarayıcı olduğu gibi bir Docker konağı içinde.

![Bir API ağ geçidi üzerinden giderek Catalog.api yanıt tarayıcı görünümü.](./media/image35.png)

**Şekil 6-35**. API ağ geçidi tarafından sağlanan URL ile bir mikro hizmet erişme

Test veya API 'catalog.api' Docker Konağı (hizmet dahili bir DNS çözümlemesi olduğundan ağ geçidi üzerinden geçirmeden Kataloğu Docker kapsayıcısı (yalnızca, geliştirme ortamı) doğrudan erişmek isterseniz nedeniyle, hata ayıklama nedeniyle tarafından işlenen bulma docker-compose hizmet adları), docker-yalnızca geliştirme testleri için gibi sağlanan compose.override.yml içinde yayımlanan dış bağlantı noktası üzerinden doğrudan kapsayıcısına erişmek için tek yolu olduğundan `http://localhost:5101/api/v1/Catalog/items/1` aşağıdaki Tarayıcı.

![Tarayıcı Görünümü Catalog.api Catalog.api özdeş bir API ağ geçidi aracılığıyla doğrudan gidip bir yanıt.](./media/image36.png)

**Şekil 6-36**. Sınama amacıyla bir mikro hizmet doğrudan erişim

Ancak, uygulamanın tüm mikro Hizmetleri API ağ geçitleri değil ancak doğrudan bağlantı noktası "kısayolları" eriştiği şekilde yapılandırılır.

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>Hizmetine ağ geçidi toplama düzeni

Daha önce sunulan, istekleri toplama uygulamak için esnek bir şekilde kod tarafından özel hizmetler ile aynıdır. Ayrıca istek toplama uygulayabileceğine [Ocelot istek toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), ancak gereksinim duyduğunuz kadar esnek olmayabilir. Bu nedenle, toplama içinde hizmetine uygulamak için seçilen her toplayıcı için açık bir ASP.NET Core Web API'si hizmetleriyle yoludur.

Bu yaklaşım göre biraz daha Basitleştirilmiş genel mimari diyagramında daha önce gösterilen gösterilmez toplayıcısı Hizmetleri değerlendirirken genişletilmiş gerçeklik API ağ geçidi oluşturma diyagram bileşenidir.

Aşağıdaki diyagramda, toplayıcısı Hizmetleri kendi ilgili API ağ geçitleri ile nasıl çalıştığını görebilirsiniz.

![toplayıcısı hizmetlerini gösteren hizmetine mimari.](./media/image37.png)

**Şekil 6-37**. toplayıcısı Hizmetleri ile hizmetine mimarisi

Aşağıdaki görüntüde, "Alışveriş" iş alanının üzerinde daha fazla yakınlaştırma toplayıcısı Hizmetleri API ağ geçitleri kullanırken istemci uygulamalar ve mikro hizmetler arasındaki iletişim yoğunluğunu azaltılır görebilirsiniz.

!["" son istemcisi ile iletişim yoğunluğunu azaltmak için birçok mikro hizmetler yanıttan birleştirme"yanıt çeviren" içinde toplayıcısı hizmetlerini gösteren hizmetine mimarisi yakınlaştırma.](./media/image38.png)

**Şekil 6-38**. Görüntü toplayıcısı Hizmetleri içinde Yakınlaştır

API ağ geçitleri gelen olası istekleri diyagramda gösterilmektedir, nasıl oldukça karmaşık elde edeceğinizi olduğunu fark edebilirsiniz. Nasıl mavi ok, istemci uygulamalar açısından bakıldığında, Toplayıcı düzeni iletişim yoğunluğu ve iletişimde gecikme süresini azaltarak kullanırken Basitleştirilmiş görebilir, ancak sonuç olarak önemli ölçüde kullanıcı geliştirme deneyimi için Uzak uygulamalara ( uygulamalarını ve mobil uygulamaları SPA), özellikle.

"Pazarlama" iş alan ve mikro hizmetler söz konusu olduğunda, toplayıcılardan verileri kullanılmasına gerek yoktu, ancak aynı zamanda gerekirse mümkün olabilir çok basit bir kullanım durumu gösterir.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Kimlik doğrulama ve yetkilendirme Ocelot API ağ geçitleri

Bir Ocelot API ağ geçidi kullanarak bir ASP.NET Core Web API'si hizmeti gibi kimlik doğrulama hizmeti yerleştirilebilir [IdentityServer](https://identityserver.io/) ölçeği genişletin veya içinde API Ağ Geçidi kimlik doğrulama belirteci sağlama.

Hizmetine olduğundan BFF üzerinde birden çok API ağ geçitleri ile sınırlarını kullanarak alan ve işletme alanlarına, kimlik/kimlik doğrulama hizmeti, aşağıdaki diyagramda sarı renkle vurgulandığı API ağ geçitleri dışında bırakılır.

![API ağ geçidi altındaki kimlik mikro hizmet gösteren hizmetine mimarisi diyagramı.](./media/image39.png)

**Şekil 6-39**. Hizmetine kimlik service konumu

Ancak, Ocelot ayrıca kimlik/Auth mikro hizmet, bu diğer diyagram olduğu gibi bir API ağ geçidi sınırında oturan destekler.

![API ağ geçidi (ağ) altındaki kimlik mikro hizmet ile kimlik doğrulaması: (1) AG kimlik mikro hizmet bir kimlik doğrulama belirteci isteklerini, 2) kimlik mikro hizmet toke AG, kimlik doğrulaması belirtecini kullanarak mikro hizmetler gelen ağ istekleri 3 - 4) döndürür.](./media/image40.png)

**Şekil 6-40**. Ocelot kimlik doğrulaması

Birden çok BFF (ön uç için arka uç) içinde API ağ geçidi hizmetine uygulama bölündü ve işletme alanlarına API ağ geçitleri, başka bir seçenek gerekir çünkü geniş kapsamlı kritik konular için ek bir API ağ geçidi oluşturmak için eklenmiştir. Seçim daha karmaşık bir mikro hizmet adil İmparatoru birden çok geniş kapsamlı kritik konular mikro hizmet mimarisiyle temel. Hizmetine içinde yalnızca bir çapraz önemli olduğundan, yalnızca güvenlik hizmeti API ağ geçidi bölgesi dışında Basitlik'ın çok işlemek için karar verilmiştir.

Uygulama API ağ geçidi düzeyinde güvenli hale getirilmişse, herhangi bir durumda, kimlik doğrulama modülü Ocelot API ağ geçidinin ilk başta güvenli bir mikro hizmet kullanmaya çalışırken ziyaret edilen. HTTP isteği access_token ile korunan hizmetlerini ziyaret ettiğiniz için erişim belirteci almak için kimliği veya kimlik doğrulama mikro hizmet ziyaret etmek için yeniden yönlendirir.

Herhangi bir hizmeti API ağ geçidi düzeyinde kimlik doğrulama ile güvenli, ilgili ayarlarının configuration.json AuthenticationProviderKey ayarlayarak yoludur.

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket.api",
          "Port": 80
        }
      ],
      "UpstreamPathTemplate": "/api/{version}/b/{everything}",
      "UpstreamHttpMethod": [],
      "AuthenticationOptions": {
        "AuthenticationProviderKey": "IdentityApiKey",
        "AllowedScopes": []
      }
    }
```

Ocelot çalıştığında, yeniden yönlendiren AuthenticationOptions.AuthenticationProviderKey bakın ve verilen anahtarla bir kimlik doğrulama sağlayıcısı kayıtlı olup olmadığını denetleyin. Yoksa, ardından Ocelot başlatılamaz. Ardından varsa, yürütüldüğünde yöneltme bu sağlayıcı kullanacaktır.

Ocelot WebHost ile yapılandırıldığından `authenticationProviderKey = "IdentityApiKey"`, ilgili hizmete tüm istekleri herhangi bir kimlik doğrulama belirteci olmadan olduğunda kimlik doğrulama gerekebilir.

```csharp
namespace OcelotApiGw
{
    public class Startup
    {
        private readonly IConfiguration _cfg;

        public Startup(IConfiguration configuration) => _cfg = configuration;

        public void ConfigureServices(IServiceCollection services)
        {
            var identityUrl = _cfg.GetValue<string>("IdentityUrl");
            var authenticationProviderKey = "IdentityApiKey";
                         //…
            services.AddAuthentication()
                .AddJwtBearer(authenticationProviderKey, x =>
                {
                    x.Authority = identityUrl;
                    x.RequireHttpsMetadata = false;
                    x.TokenValidationParameters = new Microsoft.IdentityModel.Tokens.TokenValidationParameters()
                    {
                        ValidAudiences = new[] { "orders", "basket", "locations", "marketing", "mobileshoppingagg", "webshoppingagg" }
                    };
                });
            //...
        }
    }
}
```

Ardından, ayrıca yetkilendirme [Authorize] özniteliği ile mikro hizmetler gibi sepet mikro hizmet denetleyicisi gibi erişilecek herhangi bir kaynak üzerinde ayarlamanız gerekir.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class BasketController : Controller
    {
      //...
    }
}
```

Her bir mikro hizmet içinde tanımlanan hedef kitle ile "sepet" gibi ValidAudiences bağıntılı `AddJwtBearer()` ConfigureServices() başlangıç sınıfın, aşağıdaki kod gibi.

```csharp
// prevent from mapping "sub" claim to nameidentifier.
JwtSecurityTokenHandler.DefaultInboundClaimTypeMap.Clear();

var identityUrl = Configuration.GetValue<string>("IdentityUrl");

services.AddAuthentication(options =>
{
    options.DefaultAuthenticateScheme = JwtBearerDefaults.AuthenticationScheme;
    options.DefaultChallengeScheme = JwtBearerDefaults.AuthenticationScheme;

}).AddJwtBearer(options =>
{
    options.Authority = identityUrl;
    options.RequireHttpsMetadata = false;
    options.Audience = "basket";
});
```

Güvenli bir mikro hizmet erişmeye çalışırsanız, sepet gibi API ağ geçidi gibi bir yeniden yönlendirme URL'si ile mikro hizmet tabanlı `http://localhost:5202/api/v1/b/basket/1`, sonra da geçerli bir belirteç sağladığınız sürece bir 401 Yetkisiz elde edersiniz. Öte yandan, bir yeniden yönlendirme URL'si doğrulanırsa Ocelot herhangi bir aşağı akış düzeni onunla (iç mikro hizmet URL'si) ilişkilendirilen çağırın.

**Yetkilendirme Ocelot'ın ReRoutes katmanında.**  Beyana dayalı yetkilendirme kimlik doğrulamasından sonra hesaplanan ocelot destekler. Bir rota düzeyinde yetkilendirme için yöneltme yapılandırma aşağıdaki satırı ekleyerek ayarlayın.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

Yetkilendirme ara yazılımı çağrıldığında, bu örnekte, kullanıcının belirtecinde talep türü 'UserType' varsa ve bu talebi değerini 'çalışanı' ise Ocelot bulabilirsiniz. Aksi takdirde kullanıcı yetkilendirilmemiş ve yanıt 403 Yasak olacaktır.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Kubernetes giriş artı Ocelot API ağ geçidi kullanma

Kubernetes (like Azure Kubernetes Service kümesinde) kullanırken, tüm HTTP isteklerini genellikle birleştirin [Kubernetes giriş katmanı](https://kubernetes.io/docs/concepts/services-networking/ingress/) göre *Ngınx*.

Herhangi bir giriş yaklaşım kullanmazsanız Kubernetes'te, ardından hizmet ve pod'ların yalnızca yönlendirilebilir IP'leri tarafından küme ağı var.

Ancak, bir giriş yaklaşımı kullanırsanız, bir ters proxy olarak görev yapan Internet ve hizmetlerinizi (API ağ Geçitlerinizi dahil) arasında bir orta katman sahip olacaksınız.

Bir tanım, bir giriş küme hizmetlere erişmek gelen bağlantılara izin veren kuralları koleksiyonudur. Bir giriş genellikle harici olarak erişilebilen URL'leri sağlamak için trafiğin yükünü dengelemenizi, SSL sonlandırma ve daha fazlasını yüklemek için yapılandırılır. Kullanıcılar, API sunucusu giriş kaynağa göndererek giriş ister.

Docker konağı olarak yalnızca geliştirme makinenizde yerel olarak geliştirme ve kullanırken hizmetine, tüm giriş ancak yalnızca birden çok API ağ geçitleri kullanmıyorsunuz.

Ancak, azure'da Kubernetes göre bir "üretim" ortam hedeflenirken hizmetine API ağ geçitleri önünde bir giriş kullanıyor. Bu şekilde, istemciler hala aynı temel URL'yi çağrı ancak istekleri birden çok API ağ geçitleri veya BFF yönlendirilir.

API ağ geçitleri ön uç veya yalnızca Hizmetleri ancak genellikle kendi kapsamı dışında olan web uygulamaları görünmesini façades olduğunu unutmayın. Ayrıca, API ağ geçitleri belirli iç mikro hizmetler gizlemek.

Giriş, ancak yalnızca HTTP isteklerini yönlendirerek, ancak herhangi bir mikro hizmet veya web uygulamasının gizlemek çalışıyor değil.

Web uygulamalarının yanı sıra birkaç Ocelot API ağ geçitleri önünde bir giriş Ngınx katmanı Kubernetes'te sahip / BFF ideal mimarisi, aşağıdaki diyagramda gösterildiği gibi.

![Kubernetes giriş, giden tüm trafik, genellikle API ağ geçidi kapsam dışına web uygulamaları da dahil olmak üzere, uygulama için ters Ara sunucu görevi görür.](./media/image41.png)

**Şekil 6-41**. Kubernetes dağıtıldığında hizmetine giriş katmanı

Kubernetes hizmetine dağıtın, yalnızca birkaç hizmet veya uç noktaları aracılığıyla kullanıma sunduğu _giriş_, temelde aşağıdaki listede yer alan postfixes URL'leri üzerinde:

- `/` SPA istemci için web uygulaması
- `/webmvc` MVC web uygulaması istemci için
- `/webstatus` İstemci web uygulaması için durum/healthchecks gösteriliyor
- `/webshoppingapigw` alışveriş iş süreçleri ve web BFF için
- `/webmarketingapigw` Pazarlama iş süreçleri ve web BFF için
- `/mobileshoppingapigw` Mobil BFF ve iş süreçlerini alışveriş için
- `/mobilemarketingapigw` Mobil BFF ve iş süreçlerini pazarlama için

Kubernetes için dağıtırken her Ocelot API ağ geçidi farklı "configuration.json" dosya her biri için kullanan _pod_ API ağ geçitleri çalışıyor. Bu "configuration.json" dosyaları (başlangıçta deploy.ps1 betikle) azure'da bir Kubernetes göre oluşturulan birim bağlama tarafından sağlanan _yapılandırma eşlemesi_ 'ocelot' adlı. Her kapsayıcı, ilgili yapılandırma dosyası adlı kapsayıcının klasör içinde bağlar `/app/configuration`.

İçinde özgün "configuration.json" dosyaları hizmetine, kaynak kodu dosyalarında bulunabilir `k8s/ocelot/` klasör. Her BFF/APIGateway için bir dosya yok.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Bir Ocelot API ağ geçidi ek çapraz özellikleri

Araştırma ve aşağıdaki bağlantıları açıklanan bir Ocelot API Gateway kullanırken, diğer önemli özellikleri vardır.

- **Ocelot Consul veya Eureka tümleştirmek istemci tarafı hizmet bulmayı** \
  [https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html](https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html)

- **API ağ geçidi katmanında önbelleğe alma** \
  [https://ocelot.readthedocs.io/en/latest/features/caching.html](https://ocelot.readthedocs.io/en/latest/features/caching.html)

- **API ağ geçidi katmanında günlüğe kaydetme** \
  [https://ocelot.readthedocs.io/en/latest/features/logging.html](https://ocelot.readthedocs.io/en/latest/features/logging.html)

- **API ağ geçidi katmanında (yeniden denemeler ve devre Kesiciler) hizmet kalitesi** \
  [https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html](https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html)

- **Oran sınırlandırma** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Önceki](background-tasks-with-ihostedservice.md)
> [İleri](../microservice-ddd-cqrs-patterns/index.md)
