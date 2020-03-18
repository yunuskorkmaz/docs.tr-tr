---
title: Ocelot ile API Ağ Geçitlerini uygulama
description: Ocelot ile API Ağ Geçitlerini nasıl uygulayacağınızı ve Ocelot'u konteyner tabanlı bir ortamda nasıl kullanacağınızı öğrenin.
ms.date: 03/02/2020
ms.openlocfilehash: 28b9ca22d232baf3545d71b876cecf72fea05c92
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846952"
---
# <a name="implement-api-gateways-with-ocelot"></a>Ocelot ile API Ağ Geçitleri Uygulayın

> [!IMPORTANT]
> Referans microservice uygulaması [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) şu anda elçi [tarafından](https://www.envoyproxy.io/) sunulan özellikleri yerine daha önce başvurulan [Ocelot](https://github.com/ThreeMammals/Ocelot)API Ağ Geçidi uygulamak için kullanıyor.
> Bu tasarım seçimini, Envoy'ın eShopOnContainers'da uygulanan yeni gRPC servisler arası iletişimin gerektirdiği WebSocket protokolüne verdiği yerleşik destek sayesinde yaptık.
> Ancak, ocelot'u üretim sınıfı senaryolar için uygun basit, yetenekli ve hafif bir API Ağ Geçidi olarak düşünebilmeniz için kılavuzda bu bölümü koruduk.

## <a name="architect-and-design-your-api-gateways"></a>API Ağ geçitlerinizi tasarla ve tasarla

Aşağıdaki mimari diyagram, API Ağ Geçitlerinin eShopOnContainers'da Ocelot ile nasıl uygulandığını göstermektedir.

![eShopOnContainers mimarisini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**Şekil 6-28**. API Ağ Geçitleri ile eShopOnContainers mimarisi

Bu diyagram, tüm uygulamanın "Docker for Windows" veya "Docker for Mac" ile tek bir Docker ana bilgisayarına veya geliştirme bilgisayarına nasıl dağıtılanını gösterir. Ancak, herhangi bir orkestratöre dağıtmak benzer, ancak diyagramdaki herhangi bir kapsayıcı orkestratörde ölçeklendirilebilir.

Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıkları orkestratörden boşaltılmalı ve Azure SQL Veritabanı, Azure Cosmos DB, Azure Redis, Azure Hizmet Veri Mes'leri gibi altyapı için kullanılabilir yüksek sistemlere dağıtılmalıdır, veya herhangi bir HA kümeleme çözümü şirket içinde.

Diyagramda da fark edebilirsiniz, birkaç API Ağ Geçidi'ne sahip olmak, mikro hizmetlerini ve kendi ilgili API Ağ geçitlerini geliştirirken ve dağıtırken birden çok geliştirme ekibinin özerk olmasına (bu durumda Pazarlama özellikleri ve Alışveriş özellikleri) izin verir.

Tek bir monolitik API Ağ Geçidi varsa, bu uygulamanın tek bir parçası ile tüm mikro hizmetleri çift olabilir birkaç geliştirme ekipleri tarafından güncellenecek tek bir nokta anlamına gelir.

Tasarımda çok daha ileri gitmek, bazen ince taneli API Ağ Geçidi de seçilen mimariye bağlı olarak tek bir iş microservice ile sınırlı olabilir. API Ağ Geçidi'nin sınırlarının işletme veya etki alanı tarafından dikte edilmiş olması, daha iyi bir tasarım elde etmenize yardımcı olacaktır.

Örneğin, API Ağ Geçidi katmanındaki ince parçalılık, mikro hizmetlere dayalı daha gelişmiş kompozit Kullanıcı Arabirimi uygulamaları için özellikle yararlı olabilir, çünkü ince taneli API ağ geçidi kavramı kullanıcı arabirimi kompozisyon hizmetine benzer.

Biz [mikrohizmetlere dayalı kompozit ui oluşturma](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)önceki bölümde daha fazla ayrıntı içine dalmak.

Anahtar paket olarak, birçok orta ve büyük boyutlu uygulamalar için, özel olarak oluşturulmuş BIR API Ağ Geçidi ürünü kullanmak genellikle iyi bir yaklaşımdır, ancak API Ağ Geçidi birden fazla bağımsız izin vermedikçe tek bir monolitik toplayıcı veya benzersiz merkezi özel API Ağ Geçidi olarak değil özerk mikrohizmetler oluşturan çeşitli geliştirme ekipleri için yapılandırma alanları.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>API Ağ Geçitleri üzerinden yeniden yönlendirmek için örnek mikro hizmetler/kapsayıcılar

Örnek olarak, eShopOnContainers aşağıdaki resimde gösterildiği gibi, API Ağ geçitleri aracılığıyla yayınlanması gereken yaklaşık altı dahili microservice türü vardır.

![Alt klasörlerini gösteren Hizmetler klasörünün ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**Şekil 6-29**. Visual Studio'da eShopOnContainers çözümünde microservice klasörleri

Kimlik hizmeti hakkında, tasarımda API Ağ Geçidi yönlendirmesinin dışında bırakılır, çünkü sistemdeki tek çapraz kesme endişesidir, ancak Ocelot ile yeniden yönlendirme listelerinin bir parçası olarak eklemek de mümkündür.

Tüm bu hizmetler şu anda ASP.NET Core Web API hizmetleri olarak uygulanmaktadır, koddan da anlayabileceğiniz gibi. Katalog mikrohizmet kodu gibi mikro hizmetlerden birine odaklanalım.

![Catalog.API proje içeriğini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

**Şekil 6-30**. Örnek Web API microservice (Katalog microservice)

Katalog microservice'in, aşağıdaki koddaki gibi çeşitli denetleyicileri ve yöntemleri içeren tipik bir ASP.NET Core Web API projesi olduğunu görebilirsiniz.

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

HTTP isteği, mikrohizmet veritabanına ve gerekli herhangi bir ek eyleme erişen bu tür C# kodunu çalıştırarak sona erer.

Mikro hizmet URL'si ile ilgili olarak, kapsayıcılar yerel geliştirme pc 'nizde (yerel Docker ana bilgisayar) dağıtıldığında, her microservice konteyner her zaman bir dahili bağlantı noktası (genellikle port 80) dockerfile belirtilen, aşağıdaki dockerfile olduğu gibi:

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

Kodda gösterilen bağlantı noktası 80, Docker ana bilgisayar içinde dahili olduğundan, istemci uygulamaları tarafından ulaşılamıyor.

İstemci uygulamaları, `docker-compose`dağıtılırken yalnızca harici bağlantı noktalarına (varsa) erişebilir.

Bu dış bağlantı noktaları, üretim ortamına dağıtılırken yayımlanmamalıdır. Bu nedenle, istemci uygulamaları ve mikro hizmetler arasındaki doğrudan iletişimi önlemek için API Ağ Geçidi'ni kullanmak istiyorsunuz.

Ancak, geliştirirken, microservice /konteyner doğrudan erişmek ve Swagger üzerinden çalıştırmak istiyorum. Bu nedenle eShopOnContainers'da, harici bağlantı noktaları API Ağ Geçidi veya istemci uygulamaları tarafından kullanılmayacak olsa bile yine de belirtilir.

Katalog microservice için `docker-compose.override.yml` dosyanın bir örneği aşağıda verilmiştir:

```yml
catalog-api:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - ASPNETCORE_URLS=http://0.0.0.0:80
    - ConnectionString=YOUR_VALUE
    - ... Other Environment Variables
  ports:
    - "5101:80"   # Important: In a production environment you should remove the external port (5101) kept here for microservice debugging purposes.
                  # The API Gateway redirects and access through the internal port (80).
```

Docker-compose.override.yml yapılandırmasında Katalog kapsayıcısının iç bağlantı noktasının bağlantı noktası 80 olduğunu, ancak dış erişim bağlantı noktasının 5101 olduğunu görebilirsiniz. Ancak bu bağlantı noktası, bir API Ağ Geçidi kullanırken uygulama tarafından kullanılmamalı, yalnızca hata ayıklamak, çalıştırmak ve yalnızca Katalog mikro hizmetini test etmek için kullanılmalıdır.

Normalde, mikro hizmetler için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir orkestratör olduğundan, docker-compose ile üretim ortamına dağıtım yapmazsınız. Bu ortamlara dağıtırken, mikro hizmetler için doğrudan herhangi bir dış bağlantı noktası yayımlamayacağınız, ancak API Ağ Geçidi'ndeki ters proxy'yi her zaman kullanacağınız farklı yapılandırma dosyaları kullanırsınız.

Katalog microservice'i yerel Docker ana bilgisayarevinizde çalıştırın. Visual Studio'dan tam eShopOnContainers çözümünü çalıştırın (docker-compose dosyalarındaki tüm hizmetleri çalıştırın) veya cmd veya PowerShell'de yer alan klasörde `docker-compose.override.yml` konumlandırılmış aşağıdaki docker-compose komutuyla Katalog mikrohizmetini başlatın. `docker-compose.yml`

```console
docker-compose run --service-ports catalog-api
```

Bu komut yalnızca docker-compose.yml'de belirtilen katalog-api hizmet kapsayıcısını ve bağımlılıkları çalıştırUr. Bu durumda, SQL Server kapsayıcı ve RabbitMQ kapsayıcı.

Daha sonra, doğrudan Katalog microservice erişebilir ve Swagger UI üzerinden doğrudan bu "dış" bağlantı `http://localhost:5101/swagger`noktası üzerinden erişen yöntemleri ni görebilirsiniz, bu durumda:

![Catalog.API REST API'yi gösteren Swagger UI ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**Şekil 6-31**. Swagger UI ile Katalog microservice test

Bu noktada Visual Studio'da C# kodunda bir kırılma noktası ayarlayabilir, mikro hizmeti Swagger UI'de açığa `docker-compose down` çıkan yöntemlerle test edebilir ve son olarak komutla her şeyi temizleyebilirsiniz.

Ancak, bu durumda harici bağlantı noktası 5101 üzerinden mikro hizmete doğrudan erişim iletişimi, tam olarak uygulamanızda kaçınmak istediğiniz şeydir. Ve api ağ geçidi (Ocelot, bu durumda) yönlendirme ek düzeyini ayarlayarak bunu önleyebilirsiniz. Bu şekilde, istemci uygulaması mikro hizmete doğrudan erişmez.

## <a name="implementing-your-api-gateways-with-ocelot"></a>ApI Ağ Geçitlerinizi Ocelot ile uygulama

Ocelot temelde belirli bir sırada uygulayabilirsiniz middlewares bir dizi.

Ocelot sadece ASP.NET Core ile çalışmak üzere tasarlanmıştır. Paketin en son sürümü `.NETCoreApp 3.1` hedefler ve bu nedenle .NET Framework uygulamaları için uygun değildir.

Ocelot'un NuGet paketi ile Visual [Studio'dan ocelot'u](https://www.nuget.org/packages/Ocelot/)ve bağımlılıklarını ASP.NET Core projenizde yüklüyorsunuz.

```powershell
Install-Package Ocelot
```

eShopOnContainers olarak, onun API Ağ Geçidi uygulaması basit bir ASP.NET Core WebHost proje ve Ocelot's middleware aşağıdaki resimde gösterildiği gibi, tüm API Ağ Geçidi özellikleri işler:

![Ocelot API ağ geçidi projesini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**Şekil 6-32**. eShopOnContainers OcelotApiGw temel proje

Bu ASP.NET Core WebHost proje temelde iki `Program.cs` `Startup.cs`basit dosyaları ile inşa edilmiştir: ve .

Program.cs sadece oluşturmak ve Core BuildWebHost ASP.NET tipik yapılandırmak gerekir.

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

Ocelot için burada önemli `configuration.json` `AddJsonFile()` nokta, yöntem aracılığıyla oluşturucuya sağlamanız gereken dosyadır. Tüm `configuration.json` API Ağ Geçidi Rotalarını, yani belirli bağlantı noktalarına sahip dış uç noktaları ve genellikle farklı bağlantı noktalarını kullanarak ilişkili iç uç noktaları burada belirtirsiniz.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Yapılandırmanın iki bölümü vardır. Bir dizi ReRoutes ve GlobalConfiguration. Rotalar, Ocelot'a bir akış yukarı isteği nasıl ele alsüreceğini söyleyen nesnelerdir. Global yapılandırma, ReRoute belirli ayarlarının geçersiz kılmasına izin verir. Çok sayıda ReRoute özel ayarını yönetmek istemiyorsanız kullanışlıdır.

Burada eShopOnContainers gelen API Ağ Geçitleri birinden [ReRoute yapılandırma dosyasıbasitleştirilmiş](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) bir örnek.

```json
{
  "ReRoutes": [
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "catalog-api",
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
          "Host": "basket-api",
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

Ocelot API Ağ Geçidi'nin temel işlevi, gelen HTTP isteklerini almak ve bunları şu anda başka bir HTTP isteği olarak bir aşağı hizmete iletmektir. Ocelot's, bir isteğin diğerine yönlendirildiğini Yeniden Yönlendirme olarak tanımlar.

Örneğin, yukarıdan configuration.json'daki ReRoutes'lardan birine odaklanalım, Sepet mikrohizmetinin yapılandırmasına.

```json
{
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

DownstreamPathTemplate, Düzeni ve DownstreamHostAndPorts bu istek iletilecek dahili microservice URL olun.

Bağlantı noktası, hizmet tarafından kullanılan iç bağlantı noktasıdır. Kapsayıcılar kullanılırken, bağlantı noktası dockerdosyasında belirtilir.

Bu, `Host` kullanmakta olduğunuz hizmet adı çözümlemesi bağlıdır bir hizmet adıdır. Docker-compose kullanırken, hizmet adları Docker Host tarafından sağlanır, docker-compose dosyalarında sağlanan hizmet adlarını kullanıyor. Kubernetes veya Service Fabric gibi bir orkestratör kullanıyorsanız, bu ad dns veya her orchestrator tarafından sağlanan ad çözünürlüğü ile çözülmelidir.

DownstreamHostAndPorts istekleri iletmek istediğiniz herhangi bir downstream hizmetlerin ana bilgisayar ve bağlantı noktası içeren bir dizidir. Genellikle bu sadece bir giriş içerir, ancak bazen alt akım hizmetleri ve Ocelot birden fazla giriş eklemek ve sonra bir yük dengeleyici seçmenize olanak sağlar bakiye istekleri yüklemek isteyebilirsiniz. Ancak Azure ve herhangi bir orkestratör kullanıyorsanız, bulut ve orkestratör altyapısıyla dengeyi yüklemek muhtemelen daha iyi bir fikirdir.

UpstreamPathTemplate, Ocelot'un istemciden belirli bir istek için hangi DownstreamPathTemplate'in kullanılacağını belirlemek için kullanacağı URL'dir. Son olarak, UpstreamHttpMethod, Ocelot'un farklı istekleri (GET, POST, PUT) ile aynı URL'yi ayırt edebilmeleri için kullanılır.

Bu noktada, tek bir Ocelot API Ağ Geçidi (ASP.NET Core WebHost) bir veya [birden çok birleştirilmiş configuration.json dosyaları](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) kullanarak olabilir veya aynı zamanda bir Konsolos [KV deposunda yapılandırma](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)saklayabilirsiniz.

Ama mimari ve tasarım bölümlerinde tanıtıldı, eğer gerçekten özerk mikro hizmetlere sahip olmak istiyorsanız, birden fazla API Ağ Geçidi ve / veya BFF (Frontend için Backend) içine tek monolitik API Ağ Geçidi bölmek için daha iyi olabilir. Bu amaçla, docker konteynerleri ile bu yaklaşımı nasıl uygulayacağını görelim.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Birden çok farklı API Ağ Geçidi / BFF kapsayıcı türleri çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanma

eShopOnContainers olarak, Ocelot API Ağ Geçidi ile tek bir Docker konteyner görüntü kullanıyoruz ama sonra, çalışma zamanında, her hizmet için farklı bir PC klasörüne erişmek için bir docker hacmi kullanarak, farklı bir configuration.json dosyası sağlayarak API-Gateway/BFF her türü için farklı hizmetler / kapsayıcılar oluşturmak.

![Tüm API ağ geçitleri için tek bir Ocelot ağ geçidi Docker görüntüsünün diyagramı.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

**Şekil 6-33**. Birden çok API Ağ Geçidi türünde tek bir Ocelot Docker görüntüsünü yeniden kullanma

eShopOnContainers olarak, "Generic Ocelot API Gateway Docker Image" proje 'OcelotApiGw' ve görüntü adı "eshop/ ocelotapigw" docker-compose.yml dosyasında belirtilen adlı oluşturulur. Daha sonra, Docker'a dağıtılırken, docker-compose.yml dosyasından aşağıdaki ekstrede gösterildiği gibi, aynı Docker görüntüsünden oluşturulan dört API-Ağ Geçidi kapsayıcısı olacaktır.

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

Ayrıca, aşağıdaki docker-compose.override.yml dosyasında da görebileceğiniz gibi, bu API Ağ Geçidi kapsayıcıları arasındaki tek fark, her hizmet kapsayıcısı için farklı olan Ocelot yapılandırma dosyasıdır ve çalışma zamanında Docker hacmi.

```yml
mobileshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5200:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Shopping/apigw:/app/configuration

mobilemarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5201:80"
  volumes:
    - ./src/ApiGateways/Mobile.Bff.Marketing/apigw:/app/configuration

webshoppingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5202:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Shopping/apigw:/app/configuration

webmarketingapigw:
  environment:
    - ASPNETCORE_ENVIRONMENT=Development
    - IdentityUrl=http://identity-api
  ports:
    - "5203:80"
  volumes:
    - ./src/ApiGateways/Web.Bff.Marketing/apigw:/app/configuration
```

Bu önceki kod nedeniyle ve aşağıdaki Visual Studio Explorer'da gösterildiği gibi, her bir iş /BFF API Ağ Geçidi tanımlamak için gereken tek dosya yalnızca bir configuration.json dosyasıdır, çünkü dört API Ağ Geçidi aynı Docker görüntüsünü temel alır.

![Configuration.json dosyalarıyla tüm API ağ geçitlerini gösteren ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**Şekil 6-34**. Ocelot ile her API Ağ Geçidi / BFF tanımlamak için gerekli tek dosya bir yapılandırma dosyasıdır

API Ağ Geçidi'ni birden çok API Ağ Geçidine bölerek, farklı mikro hizmetler alt kümelerine odaklanan farklı geliştirme ekipleri, bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitlerini yönetebilir. Ayrıca, aynı zamanda aynı Ocelot Docker görüntüsünü yeniden kullanabilirler.

Şimdi, API Ağ geçitleri ile eShopOnContainers çalıştırırsanız (eShopOnContainers-ServicesAndWebApps.sln çözüm açarken veya çalışan "docker-compose" vs varsayılan olarak dahil), aşağıdaki örnek yolları gerçekleştirilir.

Örneğin, webshoppingapigw `http://localhost:5202/api/v1/c/catalog/items/2/` API Ağ Geçidi tarafından sunulan akış yukarı URL'yi ziyaret ettiğinizde, `http://catalog-api/api/v1/2` aynı sonucu aşağıdaki tarayıcıda olduğu gibi Docker ana bilgisayar içindeki dahili Downstream URL'sinden alırsınız.

![API ağ geçidinden geçen bir yanıtı gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**Şekil 6-35**. API Ağ Geçidi tarafından sağlanan bir URL üzerinden bir mikro hizmete erişme

Test veya hata ayıklama nedenleriyle, API Ağ Geçidi'nden geçmeden Katalog Docker kapsayıcısına (yalnızca geliştirme ortamında) doğrudan erişmek istiyorsanız, 'catalog-api' Docker ana bilgisayara dahil olan bir DNS çözünürlüğü olduğundan (docker-compose servis adlarıyla işlenen hizmet keşfi), konteynere doğrudan erişmenin `http://localhost:5101/api/v1/Catalog/items/1` tek yolu docker-compose.override.yml'de yayınlanan ve yalnızca geliştirme testleri için sağlanan dış bağlantı noktasından geçer.

![Catalog.api'ye doğrudan yanıt gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**Şekil 6-36**. Test amacıyla bir mikro hizmete doğrudan erişim

Ancak uygulama, doğrudan bağlantı noktası "kısayollar" olsa da, API Ağ geçitleri üzerinden tüm mikro hizmetlere erişebilmek için yapılandırılır.

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>eShopOnContainers ağ geçidi toplama deseni

Daha önce de tanıtıldığı gibi, istekleri toplama uygulamak için esnek bir yol, kod, özel hizmetler ile. [Ayrıca Ocelot İstek Toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)ile istek toplama uygulayabilirsiniz , ancak ihtiyacınız kadar esnek olmayabilir. Bu nedenle, eShopOnContainers toplama uygulamak için seçilen yolu her toplayıcı için açık bir ASP.NET Core Web API hizmeti ile.

Bu yaklaşıma göre, API Ağ Geçidi kompozisyon diyagramı, daha önce gösterilen basitleştirilmiş küresel mimari diyagramında gösterilmeyen toplayıcı hizmetleri göz önüne alındığında gerçekte biraz daha genişletilmiştir.

Aşağıdaki diyagramda, toplayıcı hizmetlerin ilgili API Ağ geçitleriyle nasıl çalıştığını da görebilirsiniz.

![Toplayıcı hizmetlerini gösteren eShopOnContainers mimarisinin diyagramı.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**Şekil 6-37**. toplayıcı hizmetleri ile eShopOnContainers mimarisi

Daha fazla yakınlaştırma, aşağıdaki resimde "Alışveriş" iş alanında, istemci uygulamaları ve mikro hizmetler arasındaki gevezelik API Ağ Geçitleri'nde toplayıcı hizmetleri kullanırken azalır görebilirsiniz.

![eShopOnContainers mimarisini gösteren diyagram yakınlaştırın.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**Şekil 6-38**. Toplayıcı hizmetlerinin vizyonunu yakınlaştırın

Diyagram, API Ağ Geçitlerinden gelen olası istekleri gösterdiğinde karmaşık hale nasıl geldiğini fark edebilirsiniz. Mavi okların, istemci uygulamaları açısından nasıl basitleştirileceğini görebilseniz de, iletişimdeki gevezeliği ve gecikmeyi azaltarak toplayıcı deseni kullanırken, sonuçta uzak uygulamalar için kullanıcı deneyimini önemli ölçüde geliştirebilirsiniz ( mobil ve SPA uygulamaları), özellikle.

"Pazarlama" iş alanı ve mikrohizmetler söz konusu olduğunda, basit bir kullanım örneğidir, bu nedenle toplayıcılar kullanmaya gerek yoktur, ancak gerekirse da mümkün olabilir.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ocelot API Ağ Geçitlerinde kimlik doğrulama ve yetkilendirme

Ocelot API Ağ Geçidi'nde, API Ağ Geçidi'nin dışında veya içinde auth belirteci sağlayan [IdentityServer'ı](https://identityserver.io/) kullanarak ASP.NET Core Web API hizmeti gibi kimlik doğrulama hizmetini oturabilirsiniz.

eShopOnContainers BFF ve iş alanlarına dayalı sınırları olan birden fazla API Ağ Geçidi kullandığından, Kimlik/Auth hizmeti aşağıdaki diyagramda sarı renkte vurgulandığı gibi API Ağ Geçitlerinin dışında bırakılır.

![API ağ geçidinin altındaki Kimlik mikro hizmetini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**Şekil 6-39**. eShopOnContainers kimlik hizmetinin konumu

Ancak, Ocelot da API Ağ Geçidi sınırı içinde Kimlik / Auth microservice oturan destekler, bu diğer diyagramda olduğu gibi.

![Ocelot API Ağ Geçidi'nde kimlik doğrulamayı gösteren diyagram.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**Şekil 6-40.** Ocelot'ta kimlik doğrulama

Önceki diyagramda görüldüğü gibi, Kimlik microservice API ağ geçidi (AG) altında olduğunda: 1) AG kimlik microservice bir auth belirteç istekleri, 2) Kimlik microservice ag, 3-4) AG isteklerini auth belirteci kullanarak microservices döner. eShopOnContainers uygulaması birden fazla BFF (Frontend için Backend) ve iş alanları API Ağ Geçitleri içine API Ağ Geçidi bölünmüş olduğundan, başka bir seçenek çapraz kesme endişeleri için ek bir API Ağ Geçidi oluşturmak olurdu. Bu seçim, birden fazla çapraz kesme endişeleri microservices ile daha karmaşık bir microservice tabanlı mimari adil olacaktır. eShopOnContainers sadece bir çapraz kesme endişe olduğundan, sadece api Gateway bölge dışında güvenlik hizmeti işlemek için karar verildi, basitlik uğruna.

Her durumda, uygulama API Ağ Geçidi düzeyinde güvenli ise, güvenli bir microservice kullanmaya çalışırken ilk başta Ocelot API Ağ Geçidi kimlik doğrulama modülü ziyaret edilir. Bu, access_token ile korunan hizmetleri ziyaret edebilirsiniz böylece erişim belirteci almak için Kimlik veya auth microservice ziyaret etmek için HTTP isteği yönlendirir.

API Ağ Geçidi düzeyindeki herhangi bir hizmeti kimlik doğrulamayla güvence altına almanın yolu, AuthenticationProviderKey'i configuration.json'daki ilgili ayarlarında ayarlayarak elde edilir.

```json
    {
      "DownstreamPathTemplate": "/api/{version}/{everything}",
      "DownstreamScheme": "http",
      "DownstreamHostAndPorts": [
        {
          "Host": "basket-api",
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

Ocelot çalıştığında, ReRoutes AuthenticationOptions.AuthenticationProviderKey'e bakar ve verilen anahtara kayıtlı bir Kimlik Doğrulama Sağlayıcısı olup olmadığını denetler. Eğer yoksa, Ocelot başlamaz. Varsa, Yeniden Yönlendirme bu sağlayıcıyı çalıştırdığında kullanır.

Çünkü Ocelot WebHost ile yapılandırılır `authenticationProviderKey = "IdentityApiKey"`, bu hizmet herhangi bir auth belirteç olmadan herhangi bir istek olduğunda kimlik doğrulaması gerektirir.

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

Ardından, aşağıdaki Sepet mikro hizmet denetleyicisi gibi mikro hizmetler gibi erişilecek herhangi bir kaynağa [Authorize] özniteliği ile yetkilendirme ayarlamanız gerekir.

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

"Sepet" gibi Geçerli Hedef Kitleler, aşağıdaki kodda olduğu `AddJwtBearer()` gibi Başlangıç sınıfının ConfigureServices() adresindeki her bir mikro hizmette tanımlanan hedef kitleyle ilişkilidir.

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

API Ağ Geçidi'ne dayalı bir ReRoute URL'si olan Sepet mikrohizmeti `http://localhost:5202/api/v1/b/basket/1`gibi güvenli bir mikro hizmete erişmeye çalışırsanız, geçerli bir belirteç sağlamadığınız sürece 401 Yetkisiz alırsınız. Diğer taraftan, bir ReRoute URL'si kimlik doğrulanırsa, Ocelot onunla ilişkili ne olursa olsun aşağı akış düzenini (dahili microservice URL'si) çağırır.

**Ocelot'un Rotalar katmanında yetkilendirme.**  Ocelot, kimlik doğrulamadan sonra değerlendirilen taleplere dayalı yetkilendirmeyi destekler. ReRoute yapılandırmasına aşağıdaki satırları ekleyerek yetkilendirmeyi rota düzeyinde ayarlarsınız.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

Bu örnekte, yetkilendirme ara ware çağrıldığında, Ocelot kullanıcının belirteci 'UserType' talep türüne sahip olup olmadığını ve bu talebin değerinin 'çalışan' olup olmadığını bulur. Değilse, kullanıcı yetkilendirilmeyecek ve yanıt 403 yasak olacaktır.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Kubernetes Ingress artı Ocelot API Ağ Geçitlerini Kullanma

Kubernetes kullanırken (Azure Kubernetes Hizmet kümesinde olduğu gibi), genellikle Tüm HTTP isteklerini *Nginx'e*dayalı [Kubernetes Ingress katmanı](https://kubernetes.io/docs/concepts/services-networking/ingress/) üzerinden biraraya bilirsiniz.

Kubernetes'te, herhangi bir giriş yaklaşımı kullanmıyorsanız, hizmetleriniz ve bölmelerinizde yalnızca küme ağı tarafından epi'ler vardır.

Ancak giriş yaklaşımı kullanırsanız, Internet ve hizmetleriniz (API Ağ geçitleriniz dahil) arasında bir orta katman alabilirsiniz ve ters proxy olarak hareket elabilirsiniz.

Tanım olarak, Giriş, gelen bağlantıların küme hizmetlerine erişmesine izin veren kurallar topluluğudur. Giriş genellikle harici olarak erişilebilen URL'ler, yük dengesi trafiği, SSL sonlandırma ve daha fazlasını sağlayacak şekilde yapılandırılır. Kullanıcılar Giriş kaynağını API sunucusuna göndererek giriş isteğinde bulunarak.

eShopOnContainers, yerel olarak gelişmekte ve Docker ana bilgisayar olarak sadece geliştirme makinesi kullanırken, herhangi bir giriş değil, sadece birden fazla API Ağ Geçitleri kullanıyorsunuz.

Ancak, Kubernetes dayalı bir "üretim" ortamı hedeflenirken, eShopOnContainers API ağ geçitleri önünde bir giriş kullanıyor. Bu şekilde, istemciler hala aynı temel URL'yi arar, ancak istekler birden çok API Ağ Geçidi'ne veya BFF'ye yönlendirilir.

API Ağ geçitleri, yalnızca hizmetleri yüzeye çıkaran ön uçlar veya cephelerdir, ancak genellikle kapsam dışında olan web uygulamaları değildir. Buna ek olarak, API Ağ Geçitleri bazı dahili mikro hizmetleri gizleyebilir.

Giriş, ancak, sadece HTTP isteklerini yönlendirme ama herhangi bir microservice veya web uygulaması gizlemek için çalışıyor değil.

Web uygulamaları artı birkaç Ocelot API Ağ Geçitleri / BFF önünde Kubernetes bir giriş Nginx katmanı olması ideal bir mimari, aşağıdaki diyagramda gösterildiği gibi.

![Giriş katmanının AKS ortamına nasıl uyduğunu gösteren bir diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**Şekil 6-41**. Kubernetes'e dağıtıldığında eShopOnContainers'daki giriş katmanı

Bir Kubernetes Ingress genellikle Api ağ geçidi kapsamı dışında web uygulamaları da dahil olmak üzere uygulamaya tüm trafik için ters proxy olarak görür. EShopOnContainers'ı Kubernetes'e dağıttığınızda, _giriş_yoluyla sadece birkaç hizmet veya uç noktayı ortaya çıkarır , temelde URL'lerde aşağıdaki düzeltmeler listesi:

- `/`istemci SPA web uygulaması için
- `/webmvc`istemci MVC web uygulaması için
- `/webstatus`durumu/sağlık kontrollerini gösteren istemci web uygulaması için
- `/webshoppingapigw`web BFF ve alışveriş iş süreçleri için
- `/webmarketingapigw`web BFF ve pazarlama iş süreçleri için
- `/mobileshoppingapigw`mobil BFF ve alışveriş iş süreçleri için
- `/mobilemarketingapigw`mobil BFF ve pazarlama iş süreçleri için

Kubernetes'e dağıtılırken, her Ocelot API Ağ Geçidi, API Ağ Geçitlerini çalıştıran her _pod_ için farklı bir "configuration.json" dosyası kullanır. Bu "configuration.json" dosyaları ,'ocelot' adlı bir Kubernetes _config haritasına_ dayalı olarak oluşturulan bir ses düzeyine (başlangıçta deploy.ps1 komut dosyasıyla) monte edilerek sağlanır. Her kapsayıcı, ilgili yapılandırma dosyasını kapsayıcının `/app/configuration`klasörüne bağlar.

eShopOnContainers kaynak kod dosyalarında, orijinal "configuration.json" dosyaları `k8s/ocelot/` klasör içinde bulunabilir. Her BFF/APIGateway için bir dosya vardır.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Ocelot API Ağ Geçidi'ndeki ek çapraz kesme özellikleri

Araştırma ve kullanım için diğer önemli özellikleri vardır, bir Ocelot API Ağ Geçidi kullanırken, aşağıdaki bağlantılarda açıklanan.

- **Ocelot'u Konsolos veya Eureka ile entegre eden müşteri tarafında hizmet keşfi** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **API Ağ Geçidi katmanında önbelleğe alma** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **API Ağ Geçidi katmanında günlüğe kaydetme** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **API Ağ Geçidi katmanında Hizmet Kalitesi (Yeniden Denemeler ve Devre kesiciler)** \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Hız sınırlaması** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Önceki](background-tasks-with-ihostedservice.md)
> [Sonraki](../microservice-ddd-cqrs-patterns/index.md)
