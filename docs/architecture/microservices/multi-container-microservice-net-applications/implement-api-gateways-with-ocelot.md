---
title: Ocelot ile API Ağ Geçitlerini uygulama
description: Ocelot ile API ağ geçitleri uygulamayı ve kapsayıcı tabanlı bir ortamda Ocelot 'yi kullanmayı öğrenin.
ms.date: 10/02/2018
ms.openlocfilehash: 2a1c7b0f4baa979864ac32d555f65397531884b8
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296655"
---
# <a name="implement-api-gateways-with-ocelot"></a>Ocelot ile API ağ geçitleri uygulama

Başvuru mikro hizmet uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) , tarafından kullanılan aşağıdaki ortamların herhangi birinde olduğu gibi, mikro hizmetlerinize/kapsayıcılarınızla birlikte dağıtabileceğiniz basit ve hafıf bir API ağ geçidi olan [Ocelot](https://github.com/ThreeMammals/Ocelot)kullanıyor. eShopOnContainers.

- Docker ana bilgisayarı, yerel geliştirme bilgisayarınızda, şirket içinde veya bulutta.
- Kubernetes kümesi, şirket içi veya Azure Kubernetes hizmeti (AKS) gibi yönetilen bulutta.
- Küme, şirket içinde veya bulutta Service Fabric.
- Azure 'da PaaS/sunucusuz olarak Service Fabric mesh.

## <a name="architect-and-design-your-api-gateways"></a>API ağ geçitlerini mimarinizi ve tasarlama

Aşağıdaki mimari diyagramda, API ağ geçitlerinin eShopOnContainers 'da Ocelot ile nasıl uygulandığı gösterilmektedir.

![istemci uygulamalarını, mikro hizmetleri ve between API ağ geçitlerini gösteren eShopOnContainers mimari diyagramı](./media/image28.png)

**Şekil 6-28**. API ağ geçitleri ile eShopOnContainers mimarisi

Bu diyagramda tüm uygulamanın, "Docker for Windows" veya "Docker for Mac" ile tek bir Docker konağına veya geliştirme BILGISAYARıNA nasıl dağıtıldığı gösterilmektedir. Ancak, herhangi bir Orchestrator 'a dağıtmak oldukça benzerdir ancak Diyagramdaki herhangi bir kapsayıcı Orchestrator 'da ölçeklendirilebilir.

Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıklarının, Orchestrator 'dan boşaltılabilmesi ve Azure SQL veritabanı, Azure Cosmos DB, Azure Redu, Azure Service Bus gibi altyapıda yüksek kullanılabilir sistemlere dağıtılması gerekir. ya da herhangi bir HA kümeleme çözümünü şirket içinde.

Diyagramda da fark edebilirsiniz. birçok API ağ geçidinin birden çok geliştirme ekibinin otonom olmasına izin verir (Bu durumda pazarlama özellikleri ile). Alışveriş özellikleri) mikro hizmetlerini geliştirip kendi ilgili API ağ geçitleri.

Çeşitli geliştirme ekipleri tarafından güncelleştirilebilecek tek bir tek nokta olan tek bir tek bir API ağ geçidiniz varsa, tüm mikro hizmetlere uygulamanın tek bir bölümüyle de neden olabilir.

Tasarımda çok daha fazla şey varsa, bazen ayrıntılı bir API ağ geçidi, seçilen mimariye bağlı olarak tek bir iş mikro hizmeti ile de sınırlı olabilir. API ağ geçidinin iş veya etki alanı tarafından dikte edilen sınırlarının olması, daha iyi bir tasarım almanıza yardımcı olur.

Örneğin, gelişmiş bir API Gateway kavramı bir UI bileşim hizmetine benzer olduğundan, API ağ geçidi katmanında ince ayrıntı düzeyi özellikle mikro hizmetleri temel alan daha gelişmiş bileşik UI uygulamaları için yararlı olabilir.

Önceki bölümde, [mikro hizmetlere dayalı bileşik Kullanıcı arabirimi oluşturma hakkında](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)daha fazla ayrıntı inceleyeceğiz.

Anahtar kullanımı, birçok orta ve büyük ölçekli uygulamalar için, özel olarak oluşturulmuş bir API ağ geçidi ürünü kullanmanın genellikle iyi bir yaklaşım vardır, ancak tek bir monoparçalı toplayıcı veya benzersiz bir merkezi özel API ağ geçidi, API ağ geçidi birden çok bağımsız izin vermez otonom mikro hizmetler oluşturan çeşitli geliştirme ekipleri için yapılandırma alanı.

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a>API ağ geçitleri aracılığıyla yeniden yönlendirme için örnek mikro hizmetler/kapsayıcılar

Örnek olarak, eShopOnContainers, aşağıdaki görüntüde gösterildiği gibi, API ağ geçitleri aracılığıyla yayımlanması gereken altı adet iç mikro hizmet türü içerir.

![Yalnızca sepet, katalog, konum, pazarlama, sipariş ve ödeme mikro Hizmetleri API ağ geçidi aracılığıyla yayımlanır.](./media/image29.png)

**Şekil 6-29**. Visual Studio 'da eShopOnContainers çözümünde mikro hizmet klasörleri

Kimlik hizmeti hakkında, tasarımda tek bir çapraz kesme sorunu olduğundan, bu, yönetim ağ geçidi yönlendirmesinde kalmadı, ancak bu da yeniden yönlendirme listelerinin bir parçası olarak dahil olabilir.

Koddan bildirebilmeniz için, bu hizmetlerin tümü şu anda ASP.NET Core Web API hizmeti olarak uygulanır. Kataloğun mikro hizmet kodu gibi mikro hizmetlerden birine odaklanalım.

![Catalog. API projesinin Çözüm Gezgini görünümü.](./media/image30.png)

**Şekil 6-30**. Örnek Web API mikro hizmeti (Katalog mikro hizmeti)

Catalog mikro hizmet 'in, aşağıdaki kodda olduğu gibi çeşitli denetleyiciler ve yöntemlerle tipik bir ASP.NET Core Web API projesi olduğunu görebilirsiniz.

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

HTTP isteği, mikro hizmet veritabanına ve gerekli ek eylemlere C# erişen bu tür bir kodu çalıştırmaya sona acaktır.

Mikro hizmet URL 'SI ile ilgili olan kapsayıcılar yerel geliştirme PC 'nizde (yerel Docker ana bilgisayarı) dağıtıldığında, her mikro hizmet kapsayıcısı, aşağıdaki dockerfile içinde olduğu gibi, dockerfile 'da belirtilen her zaman bir iç bağlantı noktasına (genellikle bağlantı noktası 80) sahiptir:

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

Kodda gösterilen bağlantı noktası 80, Docker ana bilgisayarı dahilinde olduğundan istemci uygulamaları tarafından ulaşılamıyor.

İstemci uygulamaları, ile `docker-compose`dağıtım sırasında yayımlanan dış bağlantı noktalarına (varsa) erişebilir.

Bu dış bağlantı noktaları, bir üretim ortamına dağıtıldığında yayımlanmamalıdır. Bu, istemci uygulamaları ve mikro hizmetler arasındaki doğrudan iletişimin önüne geçmek için API ağ geçidini kullanmak istediğinizden kesinlikle önemlidir.

Ancak geliştirme sırasında, mikro hizmet/kapsayıcıya doğrudan erişmek ve Swagger aracılığıyla çalıştırmak istersiniz. EShopOnContainers 'da bu nedenle, dış bağlantı noktaları API Gateway veya istemci uygulamaları tarafından kullanılmayabilse bile hala belirtilir.

Katalog mikro hizmetinin `docker-compose.override.yml` dosyasına bir örnek aşağıda verilmiştir:

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

Docker-Compose. override. yıml yapılandırmasında Katalog kapsayıcısının iç bağlantı noktası 80 olup olmadığını görebilirsiniz, ancak dış erişim bağlantı noktası 5101 ' dir. Ancak bu bağlantı noktası, yalnızca katalog mikro hizmetini çalıştırmak ve test etmek için bir API ağ geçidi kullanılırken uygulama tarafından kullanılmamalıdır.

Genellikle, mikro hizmetler için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir Orchestrator olduğundan, bir üretim ortamına Docker-Compose ile dağıtım yapmanız gerekmez. Bu ortamlara dağıtım yaparken, mikro hizmetler için doğrudan herhangi bir harici bağlantı noktasını yayımlayamayacağınız farklı yapılandırma dosyalarını kullanırsınız, ancak her zaman ters proxy 'yi API Gateway 'den kullanacaksınız.

Visual Studio 'dan tam eShopOnContainers çözümünü çalıştırarak, Katalog mikro hizmetini yerel Docker ana bilgisayarınızda çalıştırın (Docker-Compose dosyalarındaki tüm hizmetleri çalıştırır) veya yalnızca aşağıdaki Docker-Compose ile katalog mikro hizmeti 'ni kullanmaya başlama CMD veya PowerShell 'de, ve Docker-Compose. override. yıml 'nin `docker-compose.yml` yerleştirildiği klasörde konumlandırılmış olan komut.

```console
docker-compose run --service-ports catalog.api
```

Bu komut yalnızca Catalog. API hizmet kapsayıcısını ve Docker-Compose. yıml içinde belirtilen bağımlılıkları çalıştırır. Bu durumda, SQL Server Container ve Kbbitmq kapsayıcısı.

Daha sonra, Katalog mikro hizmetine doğrudan erişebilir ve bu durumda `http://localhost:5101/swagger`"dış" bağlantı noktasından doğrudan bu bağlantı noktası üzerinden erişim için Swagger Kullanıcı arabirimi aracılığıyla yöntemlerini görebilirsiniz:

![Catalog. API REST API için Swagger Kullanıcı arabirimi yaşı tarayıcı görünümü.](./media/image31.png)

**Şekil 6-31**. Katalog mikro hizmetini Swagger Kullanıcı arabirimiyle test etme

Bu noktada, Visual Studio 'da C# kodda bir kesme noktası ayarlayabilir, mikro hizmeti Swagger Kullanıcı arabiriminde sunulan yöntemlerle test edebilirsiniz ve son olarak `docker-compose down` komutla birlikte her şeyi temizleyebilirsiniz.

Ancak, bu durumda 5101 dış bağlantı noktası aracılığıyla mikro hizmetle doğrudan erişim iletişimi, uygulamanızda kaçınmak istediğiniz kadar kesin bir durumdur. API ağ geçidinin ek yöneltme düzeyini (Bu durumda Ocelot) ayarlayarak bundan kaçınabilirsiniz. Bu şekilde, istemci uygulaması mikro hizmete doğrudan erişemez.

## <a name="implementing-your-api-gateways-with-ocelot"></a>API ağ geçitlerini Ocelot ile uygulama

Ocelot, temel olarak belirli bir sırada uygulayabileceğiniz bir middlewares kümesidir.

Ocelot yalnızca ASP.NET Core çalışmak üzere tasarlanmıştır. .NET Core 2,0 çalışma zamanı ve .NET Framework 4.6.1 çalışma zamanı ve ' de dahil olmak üzere 2,0 .NET Standard her yerde kullanılabilmesi için Netstandard 2.0 'ı hedefliyordu.

Ocelot 'yi ve onun bağımlılıklarını, Visual Studio 'dan [Ocelot 'Nin NuGet paketiyle](https://www.nuget.org/packages/Ocelot/)ASP.NET Core projenize yüklersiniz.

```powershell
Install-Package Ocelot
```

EShopOnContainers 'da, API Gateway uygulamasının basit bir ASP.NET Core WebHost projesi ve Ocelot 'nin middlewares, aşağıdaki görüntüde gösterildiği gibi tüm API Gateway özelliklerini işlemesi:

![Ocelot API Gateway projesinin Çözüm Gezgini görünümü.](./media/image32.png)

**Şekil 6-32**. EShopOnContainers 'da OcelotApiGw temel projesi

Bu ASP.NET Core Webhost projesi temel olarak iki basit dosya ile oluşturulmuştur: `Program.cs` ve `Startup.cs`.

Program.cs yalnızca, BuildWebHost ASP.NET Core oluşturmak ve yapılandırmak için gereklidir.

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

Ocelot `configuration.json` için buradaki önemli nokta, Oluşturucu `AddJsonFile()` yöntemi aracılığıyla sağlamanız gereken dosyadır. Diğer `configuration.json` bir deyişle, genellikle farklı bağlantı noktaları kullanan belirli bağlantı noktaları ve bağıntılı iç uç noktalar içeren dış uç noktalar olan tüm API ağ geçidi ReRoutes belirtirsiniz.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Yapılandırmanın iki bölümü vardır. Bir yeniden yönlendirme dizisi ve bir GlobalConfiguration. Yeniden yönlendirmeler, bir yukarı akış isteğini nasıl değerlendireceği hakkında daha fazla bilgi veren nesnelerdir. Genel yapılandırma, belirli ayarların yeniden yönlendirilmesi için geçersiz kılmalara izin verir. Çok sayıda yeniden yönlendirme, belirli ayarları yönetmek istemiyorsanız yararlıdır.

Aşağıda, eShopOnContainers 'dan API ağ geçitlerinden birinden [yapılandırma dosyası yeniden yönlendirme](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) için basitleştirilmiş bir örnek verilmiştir.

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

Bir Ocelot API ağ geçidinin ana işlevselliği, gelen HTTP isteklerini almak ve şu anda başka bir HTTP isteği olarak bir aşağı akış hizmetine iletmektir. Ocelot, bir isteğin bir yeniden yönlendirme olarak diğerine yönlendirilmesini açıklar.

Örneğin, yukarıdaki Configuration. JSON içindeki yeniden rotalardan birine, sepet mikro hizmeti yapılandırmasına odaklanalım.

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

DownstreamPathTemplate, düzen ve Downstreamhostandport, bu isteğin iletileceği iç mikro hizmet URL 'sini yapar.

Bağlantı noktası, hizmet tarafından kullanılan iç bağlantı noktasıdır. Kapsayıcılar kullanılırken dockerfile 'da belirtilen bağlantı noktası.

, `Host` Kullanmakta olduğunuz hizmet adı çözümlemesine bağlı olan bir hizmet adıdır. Docker-Compose kullanırken, hizmet adları Docker ana bilgisayarı tarafından sağlanır ve bu, Docker-Compose dosyalarında belirtilen hizmet adlarını kullanmaktır. Kubernetes veya Service Fabric gibi bir Orchestrator kullanılıyorsa, bu ad her Orchestrator tarafından sağlanmış olan DNS veya ad çözümlemesi tarafından çözümlenmelidir.

Downstreamhostandport, istekleri iletmek istediğiniz herhangi bir aşağı akış hizmetinin ana bilgisayar ve bağlantı noktasını içeren bir dizidir. Genellikle bu yalnızca bir giriş içerir, ancak bazen aşağı akış hizmetlerinize yük dengelemesi yapmak isteyebilirsiniz ve Ocelot, birden fazla giriş eklemenizi ve sonra bir yük dengeleyici seçmenizi sağlar. Ancak Azure ve herhangi bir Orchestrator kullanılıyorsa, bulut ve Orchestrator altyapısıyla yük dengelemesi daha iyi bir fikir olabilir.

UpstreamPathTemplate, istemci tarafından verilen bir istek için kullanılacak olan DownstreamPathTemplate 'i tanımlamak için kullanılan URL 'dir. Son olarak, UpstreamHttpMethod kullanılır. bu nedenle, Ocelot, farklı istekleri (GET, POST, PUT) aynı URL 'ye ayırabilirler.

Bu noktada, bir veya [birden fazla birleştirilmiş Configuration. JSON dosyası](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) kullanarak tek bir Ocelot API Gateway (ASP.NET Core Webhost) olabilir veya [yapılandırmayı BIR tüketil kV deposunda](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)da saklayabilirsiniz.

Ancak, mimari ve tasarım bölümlerinde tanıtıldıkça, gerçekten otonom mikro hizmetlere sahip olmak istiyorsanız, bu tek monoparçalı API ağ geçidini birden çok API ağ geçidine ve/veya BFF (ön uç için arka uç) olarak bölmek daha iyi olabilir. Bu amaçla, bu yaklaşımı Docker kapsayıcılarıyla nasıl uygulayacağınızı görelim.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Birden çok farklı API Gateway/BFF kapsayıcı türü çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanma

EShopOnContainers 'da, Ocelot API ağ geçidiyle tek bir Docker kapsayıcı görüntüsü kullanıyoruz, ancak çalışma zamanında, farklı bir Configuration. JSON dosyası sağlayarak her bir API-Gateway/BFF türü için bir Docker birimi kullanarak farklı hizmetler/kapsayıcılar oluşturuyoruz Her hizmet için farklı bir BILGISAYAR klasörüne erişin.

![Tüm dört API ağ geçitleri için Ocelot API Gateway için tek bir Docker görüntüsü kullanılır](./media/image33.png)

**Şekil 6-33**. Birden çok API ağ geçidi türü genelinde tek bir Ocelot Docker görüntüsünü yeniden kullanma

EShopOnContainers 'da, "genel Ocelot API Gateway Docker Image", Docker-Compose. yml dosyasında belirtilen ' OcelotApiGw ' adlı projeyle ve "eShop/ocelotapigw" görüntü adına oluşturulur. Daha sonra, Docker 'a dağıtım yaparken, Docker-Compose. yıml dosyasında aşağıdaki ayıklama bölümünde gösterildiği gibi, aynı Docker görüntüsünden oluşturulan dört API-Gateway kapsayıcısı olacaktır.

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

Ayrıca, aşağıdaki Docker-Compose. override. yıml dosyasında görebileceğiniz gibi, bu API ağ geçidi kapsayıcıları arasındaki tek fark, her bir hizmet kapsayıcısı için farklı olan ve çalışma zamanında bir Docker birimi.

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

Bu önceki kod nedeniyle ve aşağıdaki Visual Studio Gezgini 'nde gösterildiği gibi, her bir iş/BFF API ağ geçidini tanımlamak için gereken tek dosya yalnızca bir Configuration. JSON dosyasıdır, çünkü dört API ağ geçitleri aynı Docker görüntüsüne dayalıdır.

![Tüm API ağ geçitleri arasındaki tek fark, her birinde bir Configuration. JSON dosyasıdır.](./media/image34.png)

**Şekil 6-34**. Her API ağ geçidini/BFF 'yi Ocelot ile tanımlamak için gereken tek dosya bir yapılandırma dosyasıdır

API ağ geçidini birden çok API ağ geçidine bölerek, mikro hizmetlerin farklı alt kümelerine odaklanan farklı geliştirme takımları, bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitlerini yönetebilir. Ayrıca, aynı anda aynı Ocelot Docker görüntüsünü yeniden kullanabilir.

Artık, API ağ geçitleri ile eShopOnContainers çalıştırırsanız (eShopOnContainers-ServicesAndWebApps. sln çözümü açılırken veya "Docker-Compose up" çalıştırıyorsanız), aşağıdaki örnek yollar gerçekleştirilir.

Örneğin, webshoppingapigw API `http://localhost:5202/api/v1/c/catalog/items/2/` Gateway tarafından sunulan yukarı akış URL 'sini ziyaret ederken, Docker ana bilgisayarı içindeki iç aşağı akış URL `http://catalog.api/api/v1/2` 'sinden aşağıdaki tarayıcıda olduğu gibi aynı sonucu elde edersiniz.

![Catalog. API ' den gelen bir yanıtın tarayıcı görünümü API ağ geçidiyle devam eteceğiz.](./media/image35.png)

**Şekil 6-35**. API ağ geçidi tarafından sunulan bir URL aracılığıyla mikro hizmete erişme

Test veya hata ayıklama nedenlerinden dolayı, API Gateway 'e geçmeden doğrudan Katalog Docker kapsayıcısına (yalnızca geliştirme ortamında) erişmek isterseniz, ' Catalog. API ', Docker Konağı (hizmeti) iç bir DNS çözümünden dolayı bulma işlemi Docker-Compose hizmeti adları tarafından işlendi), kapsayıcıya doğrudan erişmenin tek yolu, yalnızca geliştirme testleri için sağlanmış olan Docker-Compose. override. yıml içinde Yayınlanan dış bağlantı noktasıdır, örneğin, aşağıdaki gibi `http://localhost:5101/api/v1/Catalog/items/1` Tarayıcı.

![Katalogdan. API ' den gelen bir yanıtın tarayıcı görünümü, API ağ geçidi ile aynı şekilde doğrudan katalog. API 'sine gidiyor.](./media/image36.png)

**Şekil 6-36**. Sınama amacıyla bir mikro hizmete doğrudan erişim

Ancak uygulama, doğrudan bağlantı noktasında "kısayollar" değil, tüm mikro hizmetlere API ağ geçitleri üzerinden erişmesi için yapılandırılmıştır.

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>EShopOnContainers 'daki ağ geçidi toplama deseninin

Daha önce sunulmuş olduğu gibi, istek toplamayı uygulamak için esnek bir yol, koda göre özel hizmetlerle aynıdır. Ayrıca, [Ocelot Içindeki Istek toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)ile istek toplamayı da uygulayabilirsiniz, ancak ihtiyacınız olduğu kadar esnek olmayabilir. Bu nedenle, eShopOnContainers 'da toplamayı uygulamak için seçilen yol, her toplayıcı için açık bir ASP.NET Core Web API hizmetleriyle birlikte bulunur.

Bu yaklaşıma göre, API ağ geçidi bileşim diyagramı, daha önce gösterilen Basitleştirilmiş küresel mimari diyagramında görünmeyen toplayıcı Hizmetleri düşünüldüğünde çok daha fazla uzatılmış bir bittir.

Aşağıdaki diyagramda, toplayıcı Hizmetleri 'nin ilgili API ağ geçitleriyle nasıl çalıştığını da görebilirsiniz.

![Toplayıcı hizmetlerini gösteren eShopOnContainers mimarisi.](./media/image37.png)

**Şekil 6-37**. Toplayıcı Hizmetleri ile eShopOnContainers mimarisi

Daha fazla yakınlaştırma, aşağıdaki görüntüde "alışveriş" iş alanında, API ağ geçitlerinde toplayıcı Hizmetleri kullanılırken istemci uygulamaları ve mikro hizmetler arasındaki azaltmaya azaldığını görebilirsiniz.

![eShopOnContainers mimarisi, toplayıcı Hizmetleri 'ni göstererek, son istemciyle azaltmaya düşürmek için birkaç mikro hizmetten gelen yanıtı "birleştirerek" bir yanıt "ayırır".](./media/image38.png)

**Şekil 6-38**. Toplayıcı hizmetlerini yakından yakınlaştırın

Diyagram, API ağ geçitlerinden gelen olası istekleri nasıl gösterdiğine, oldukça karmaşık bir şekilde sahip olduğunu fark edebilirsiniz. Mavi renkli okların nasıl basitleştiğini, bir istemci uygulamalar perspektifinden, iletişim kutusunda azaltmaya ve gecikme süresini azaltarak, uzak uygulamaların kullanıcı deneyimini önemli ölçüde geliştirerek ( Mobil ve SPA uygulamaları), özellikle.

"Pazarlama" iş alanı ve mikro hizmetler söz konusu olduğunda, aggregators 'ı kullanmaya gerek olmadığı için çok basit bir kullanım durumdur, ancak gerektiğinde de mümkün olabilir.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ocelot API ağ geçitlerinde kimlik doğrulama ve yetkilendirme

Bir Ocelot API ağ geçidinde, kimlik doğrulama belirtecini veya API ağ geçidinin içinden veya içinden kimlik doğrulama [belirtecini sağlayan bir](https://identityserver.io/) ASP.NET Core Web API hizmeti gibi, kimlik doğrulama hizmetine oturtyükleyebilirsiniz.

EShopOnContainers, BFF ve iş alanlarını temel alan sınırların bulunduğu birden çok API ağ geçidi kullandığından, kimlik/kimlik doğrulama hizmeti, aşağıdaki diyagramda sarı renkle vurgulanmış şekilde API ağ geçitlerinden bırakılır.

![eShopOnContainers mimari diyagramı, API ağ geçidinin altındaki kimlik mikro hizmetini gösterir.](./media/image39.png)

**Şekil 6-39**. EShopOnContainers 'da kimlik hizmetinin konumu

Ancak, Ocelot Ayrıca, bu diğer diyagramda olduğu gibi, API Gateway sınırının içinde kimlik/auth mikro hizmetini de destekler.

![API Gateway (AG) altında kimlik mikro hizmeti ile kimlik doğrulaması: 1) AG, kimlik mikro hizmetinden bir kimlik doğrulama belirteci istiyor, 2) kimlik mikro hizmeti, kimlik doğrulama belirtecini kullanarak mikro hizmetlerden gelen AG isteklerini/3-4) AG isteklerini geri döndürüyor.](./media/image40.png)

**Şekil 6-40**. Ocelot 'de kimlik doğrulaması

EShopOnContainers uygulaması, API ağ geçidini birden çok BFF (ön uç için arka uç) ve iş alanları API ağ geçitlerine böldüğü için, çapraz kesme sorunları için ek bir API ağ geçidi oluşturulması gerekir. Bu seçenek, birden çok çapraz kesme sorunları olan mikro hizmetlere sahip daha karmaşık bir mikro hizmet tabanlı mimaride yer alan bir şekilde yapılır. EShopOnContainers 'da yalnızca bir çapraz kesme sorunu olduğundan, basitlik 'in sake 'SI için API ağ geçidi bölgesinden yalnızca güvenlik hizmetini işlemeye karar verdi.

Herhangi bir durumda, uygulama API ağ geçidi düzeyinde güvenli hale getirildiğinden, güvenli mikro hizmeti kullanmaya çalışırken Ocelot API ağ geçidinin kimlik doğrulama modülü ilk olarak ziyaret edilir. Bu, access_token ile korunan hizmetleri ziyaret edebilmeniz için erişim belirtecini almak üzere kimlik veya auth mikro hizmetini ziyaret etmek üzere HTTP isteğini yeniden yönlendirir.

API ağ geçidi düzeyinde herhangi bir hizmette kimlik doğrulama ile güvenli hale getirmenin yolu, AuthenticationProviderKey değerini Configuration. JSON konumundaki ilgili ayarlarında ayarlamadır.

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

Ocelot çalıştırıldığında, AuthenticationOptions. AuthenticationProviderKey yeniden yönlendirmeler ' a bakar ve verilen anahtara kayıtlı bir kimlik doğrulama sağlayıcısı olup olmadığını kontrol eder. Yoksa, Ocelot başlamacaktır. Varsa, yeniden yönlendirme bu sağlayıcıyı çalıştırıldığında kullanır.

Ocelot Webhost ile yapılandırıldığı için `authenticationProviderKey = "IdentityApiKey"`, bu hizmet kimlik doğrulama belirteci olmadan herhangi bir istek olduğunda kimlik doğrulaması gerektirir.

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

Daha sonra, aşağıdaki sepet mikro hizmet denetleyicisi gibi mikro hizmetler gibi erişilecek herhangi bir kaynaktaki [Yetkilendir] özniteliğiyle yetkilendirmeyi de ayarlamanız gerekir.

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

"Sepet" gibi validaudide, aşağıdaki kodda olduğu gibi başlangıç sınıfının ConfigureServices () ile birlikte `AddJwtBearer()` her bir mikro hizmette tanımlanan hedef kitlelerle bağıntılı.

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

Benzer `http://localhost:5202/api/v1/b/basket/1`bir API ağ geçidine dayanan bir yeniden yönlendirme URL 'si ile sepet mikro hizmeti gibi güvenli bir mikro hizmete erişmeye çalışırsanız, geçerli bir belirteç sağlamadığınız takdirde 401 Yetkisiz bir işlem alırsınız. Öte yandan, bir yeniden yönlendirme URL 'SI doğrulandıysa, Ocelot onunla ilişkili olan bir aşağı akış şemasını (iç mikro hizmet URL 'SI) çağırır.

**Ocelot 'nin ReRoutes katmanında yetkilendirme.**  Ocelot, kimlik doğrulamasından sonra değerlendirilen talep tabanlı yetkilendirmeyi destekler. Yeniden yönlendirme yapılandırmasına aşağıdaki satırları ekleyerek bir rota düzeyinde yetkilendirme ayarlarsınız.

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

Bu örnekte, yetkilendirme ara yazılımı çağrıldığında, kullanıcının belirteçte ' UserType ' talep türüne sahip olup olmadığını ve bu talebin değeri ' Employee ' olup olmadığını bulur. Değilse, Kullanıcı yetkilendirilmez ve yanıt 403 olarak yasaklanmış olur.

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a>Kubernetes ınress ve Ocelot API ağ geçitlerini kullanma

Kubernetes (bir Azure Kubernetes hizmet kümesinde olduğu gibi) kullanılırken, genellikle tüm HTTP isteklerini *NGINX*temelinde [Kubernetes giriş katmanı](https://kubernetes.io/docs/concepts/services-networking/ingress/) üzerinden birleştirmişsinizdir.

Kubernetes 'te herhangi bir giriş yaklaşımı kullanmıyorsanız, hizmetlerinizin ve klarınızın IP 'Leri yalnızca küme ağı tarafından yönlendirilebilir.

Ancak, bir giriş yaklaşımı kullanıyorsanız Internet ve hizmetleriniz (API ağ geçitleriniz dahil) arasında bir orta katman ve ters proxy görevi gören bir orta katmanınız olacaktır.

Bir tanım olarak, giriş, gelen bağlantılara küme hizmetlerine ulaşmasına izin veren kuralların koleksiyonudur. Giriş genellikle hizmetlere dışarıdan erişilebilen URL 'Ler, Yük Dengeleme trafiği, SSL sonlandırma ve daha fazlası sağlamak üzere yapılandırılır. Kullanıcılar giriş kaynağını API sunucusuna naklederek giriş isteği ister.

EShopOnContainers 'da, yerel olarak geliştirilirken ve yalnızca bir geliştirme makinenizi Docker Konağı olarak kullanırken, yalnızca birden fazla API ağ geçidi kullanmayın.

Ancak, Kubernetes tabanlı bir "üretim" ortamını hedeflerken eShopOnContainers, API ağ geçitlerinin önünde bir giriş kullanıyor. Bu şekilde, istemciler yine de aynı temel URL 'YI çağırır, ancak istekler birden fazla API ağ geçidine veya BFF 'ye yönlendirilir.

API ağ geçitlerinin ön uçları veya façades, genellikle kapsamlarından çıkan Web uygulamalarına değil, yalnızca hizmetlere yönelik olduğunu unutmayın. Ayrıca, API ağ geçitleri bazı iç mikro hizmetleri gizleyebilir.

Ancak giriş, HTTP isteklerini yeniden yönlendirse de herhangi bir mikro hizmeti veya Web uygulamasını gizlemeyi denememelidir.

Web uygulamalarının önündeki Kubernetes 'de bir giriş Nginx katmanına sahip olmak ve çeşitli Ocelot API ağ geçitleri/BFF, aşağıdaki diyagramda gösterildiği gibi ideal mimaridir.

![Kubernetes girişi, genellikle API ağ geçidi kapsamından çıkan Web uygulamaları dahil olmak üzere, uygulamaya yönelik tüm trafik için ters proxy görevi görür.](./media/image41.png)

**Şekil 6-41**. Kubernetes 'e dağıtıldığında eShopOnContainers içindeki giriş katmanı

EShopOnContainers 'ı Kubernetes 'e dağıttığınızda, temel olarak yalnızca birkaç hizmet veya uç _nokta Ile URL_'lerde aşağıdaki postdüzeltmelerin listesini sunar:

- `/`istemci SPA Web uygulaması için
- `/webmvc`istemci MVC web uygulaması için
- `/webstatus`durum/healthdenetimleri gösteren istemci Web uygulaması için
- `/webshoppingapigw`Web BFF ve alışveriş iş süreçlerini
- `/webmarketingapigw`Web BFF ve pazarlama iş işlemlerinde
- `/mobileshoppingapigw`Mobil BFF ve alışveriş iş işlemlerinde
- `/mobilemarketingapigw`Mobil BFF ve pazarlama iş işlemlerinde

Kubernetes 'e dağıtım yaparken, her Ocelot API ağ geçidi, API ağ geçitlerini çalıştıran her _Pod_ için farklı bir "Configuration. JSON" dosyası kullanıyor. Bu "Configuration. JSON" dosyaları, ' Ocelot ' adlı bir Kubernetes _yapılandırma eşlemesi_ temel alınarak oluşturulan bir birimi bağlama tarafından sağlanır (başlangıçta Deploy. ps1 betiği ile). Her kapsayıcı, ilişkili yapılandırma dosyasını kapsayıcısının adlı `/app/configuration`kapsayıcı klasörüne bağlar.

Eshoponcontainers kaynak kodu dosyalarında, özgün "Configuration. JSON" dosyaları `k8s/ocelot/` klasör içinde bulunabilir. Her BFF/APIGateway için bir dosya vardır.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Bir Ocelot API ağ geçidinde ek çapraz kesme özellikleri

Aşağıdaki bağlantılarda açıklanan bir Ocelot API ağ geçidi kullanırken araştırmak ve kullanmak için kullanabileceğiniz diğer önemli özellikler vardır.

- **İstemci tarafında, Cell veya Eureka ile, Ocelot ile tümleştirme** \
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- **API ağ geçidi katmanında önbelleğe alma** \
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- **API ağ geçidi katmanında günlüğe kaydetme** \
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- **API ağ geçidi katmanında hizmet kalitesi (yeniden denemeler ve devre kesiciler)**  \
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- **Hız sınırlandırma** \
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> [Önceki](background-tasks-with-ihostedservice.md)İleri
> [](../microservice-ddd-cqrs-patterns/index.md)
