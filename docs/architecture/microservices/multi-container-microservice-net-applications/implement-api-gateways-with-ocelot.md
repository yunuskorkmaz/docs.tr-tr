---
title: Ocelot ile API Ağ Geçitlerini uygulama
description: Ocelot ile API ağ geçitleri uygulamayı ve kapsayıcı tabanlı bir ortamda Ocelot 'yi kullanmayı öğrenin.
ms.date: 10/02/2018
ms.openlocfilehash: c0bcd240b6bd190dd02266c7faaf9fd668eb23bb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777301"
---
# <a name="implement-api-gateways-with-ocelot"></a>Ocelot ile API ağ geçitleri uygulama

Başvuru mikro hizmet uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) , eshoponcontainers tarafından kullanılan aşağıdaki ortamların herhangi birinde olduğu gibi, mikro hizmetlerinize/kapsayıcılarınızla birlikte dağıtabileceğiniz basit ve hafıf bir API ağ geçidi olan [Ocelot](https://github.com/ThreeMammals/Ocelot)'yi kullanıyor:

- Docker ana bilgisayarı, yerel geliştirme bilgisayarınızda, şirket içinde veya bulutta.
- Kubernetes kümesi, şirket içi veya Azure Kubernetes hizmeti (AKS) gibi yönetilen bulutta.
- Küme, şirket içinde veya bulutta Service Fabric.
- Azure 'da PaaS/sunucusuz olarak Service Fabric mesh.

## <a name="architect-and-design-your-api-gateways"></a>API ağ geçitlerini mimarinizi ve tasarlama

Aşağıdaki mimari diyagramda, API ağ geçitlerinin eShopOnContainers 'da Ocelot ile nasıl uygulandığı gösterilmektedir.

![EShopOnContainers mimarisini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

**Şekil 6-28**. API ağ geçitleri ile eShopOnContainers mimarisi

Bu diyagramda tüm uygulamanın, "Docker for Windows" veya "Docker for Mac" ile tek bir Docker konağına veya geliştirme BILGISAYARıNA nasıl dağıtıldığı gösterilmektedir. Ancak, herhangi bir Orchestrator 'a dağıtım benzerdir, ancak Diyagramdaki herhangi bir kapsayıcı Orchestrator 'da genişletilebilir.

Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıklarının, Orchestrator 'dan boşaltılabilmesi ve Azure SQL veritabanı, Azure Cosmos DB, Azure Redu, Azure Service Bus gibi altyapıda yüksek kullanılabilir sistemlere dağıtılması gerekir. ya da herhangi bir HA kümeleme çözümünü şirket içinde.

Diyagramda da fark edebilirsiniz. birçok API ağ geçidine sahip olmak, mikro hizmetlerinin yanı sıra kendi ilgili API ağ geçitlerinin geliştirilmesi ve dağıtılmasında birden çok geliştirme ekibinin otonom olmasına (Bu durumda pazarlama özellikleri ve alışveriş özellikleri) izin verir.

Çeşitli geliştirme ekipleri tarafından güncelleştirilebilecek tek bir tek nokta olan tek bir tek bir API ağ geçidiniz varsa, tüm mikro hizmetlere uygulamanın tek bir bölümüyle de neden olabilir.

Tasarımda çok daha fazla şey varsa, bazen ayrıntılı bir API ağ geçidi, seçilen mimariye bağlı olarak tek bir iş mikro hizmeti ile de sınırlı olabilir. API ağ geçidinin iş veya etki alanı tarafından dikte edilen sınırlarının olması, daha iyi bir tasarım almanıza yardımcı olur.

Örneğin, gelişmiş bir API Gateway kavramı bir UI bileşim hizmetine benzer olduğundan, API ağ geçidi katmanında ince ayrıntı düzeyi özellikle mikro hizmetleri temel alan daha gelişmiş bileşik UI uygulamaları için yararlı olabilir.

Önceki bölümde, [mikro hizmetlere dayalı bileşik Kullanıcı arabirimi oluşturma hakkında](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)daha fazla ayrıntı inceleyeceğiz.

Anahtar kullanımı, birçok orta ve büyük ölçekli uygulamalar için, özel olarak oluşturulmuş bir API ağ geçidi ürünü kullanmanın genellikle iyi bir yaklaşım vardır, ancak tek bir monoparçalı toplayıcı veya benzersiz bir merkezi özel API ağ geçidi, API ağ geçidi birden çok bağımsız izin vermez otonom mikro hizmetler oluşturan çeşitli geliştirme ekipleri için yapılandırma alanı.

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a>API ağ geçitleri aracılığıyla yeniden yönlendirme için örnek mikro hizmetler/kapsayıcılar

Örnek olarak, eShopOnContainers, aşağıdaki görüntüde gösterildiği gibi, API ağ geçitleri aracılığıyla yayımlanması gereken altı adet iç mikro hizmet türü içerir.

![Alt klasörlerini gösteren hizmetler klasörünün ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

**Şekil 6-29**. Visual Studio 'da eShopOnContainers çözümünde mikro hizmet klasörleri

Kimlik hizmeti hakkında, tasarımda tek bir çapraz kesme sorunu olduğundan, bu, yönetim ağ geçidi yönlendirmesinde kalmadı, ancak bu da yeniden yönlendirme listelerinin bir parçası olarak dahil olabilir.

Koddan bildirebilmeniz için, bu hizmetlerin tümü şu anda ASP.NET Core Web API hizmeti olarak uygulanır. Kataloğun mikro hizmet kodu gibi mikro hizmetlerden birine odaklanalım.

![Catalog. API proje içeriğini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

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

İstemci uygulamaları, `docker-compose`ile dağıtım sırasında yayımlanan dış bağlantı noktalarına (varsa) erişebilir.

Bu dış bağlantı noktaları, bir üretim ortamına dağıtıldığında yayımlanmamalıdır. Bu, istemci uygulamaları ve mikro hizmetler arasındaki doğrudan iletişimin önüne geçmek için API ağ geçidini kullanmak istediğinizden kesinlikle önemlidir.

Ancak geliştirme sırasında, mikro hizmet/kapsayıcıya doğrudan erişmek ve Swagger aracılığıyla çalıştırmak istersiniz. EShopOnContainers 'da bu nedenle, dış bağlantı noktaları API Gateway veya istemci uygulamaları tarafından kullanılmayabilse bile hala belirtilir.

Katalog mikro hizmeti için `docker-compose.override.yml` dosyasına bir örnek aşağıda verilmiştir:

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

Docker-Compose. override. yıml yapılandırmasında Katalog kapsayıcısının iç bağlantı noktası 80 olup olmadığını görebilirsiniz, ancak dış erişim bağlantı noktası 5101 ' dir. Ancak bu bağlantı noktası, yalnızca katalog mikro hizmetini yalnızca hata ayıklama, çalıştırma ve test etme amacıyla bir API ağ geçidi kullanırken uygulama tarafından kullanılmamalıdır.

Genellikle, mikro hizmetler için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir Orchestrator olduğundan, bir üretim ortamına Docker-Compose ile dağıtım yapmanız gerekmez. Bu ortamlara dağıtım yaparken, mikro hizmetler için doğrudan herhangi bir harici bağlantı noktasını yayımlayamayacağınız farklı yapılandırma dosyalarını kullanırsınız, ancak her zaman ters proxy 'yi API Gateway 'den kullanacaksınız.

Katalog mikro hizmetini yerel Docker ana bilgisayarınızda çalıştırın. Visual Studio 'dan tam eShopOnContainers çözümünü çalıştırın (Docker-Compose dosyalarındaki tüm hizmetleri çalıştırır) ya da Katalog mikro hizmetini, `docker-compose.yml` ve `docker-compose.override.yml` yerleştirildiği klasörde konumlandırılmış olan CMD veya PowerShell 'de aşağıdaki Docker-Compose komutuyla başlatın.

```console
docker-compose run --service-ports catalog.api
```

Bu komut yalnızca Catalog. API hizmet kapsayıcısını ve Docker-Compose. yıml içinde belirtilen bağımlılıkları çalıştırır. Bu durumda, SQL Server Container ve Kbbitmq kapsayıcısı.

Daha sonra, Katalog mikro hizmetine doğrudan erişebilir ve bu durumda, bu örnekte bu bağlantı noktasından doğrudan bu bağlantı noktası üzerinden erişim için Swagger Kullanıcı arabirimi aracılığıyla yöntemleri görebilirsiniz `http://localhost:5101/swagger`:

![Catalog. API REST API gösteren Swagger Kullanıcı arabiriminin ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

**Şekil 6-31**. Katalog mikro hizmetini Swagger Kullanıcı arabirimiyle test etme

Bu noktada, Visual Studio 'da C# kodda bir kesme noktası ayarlayabilir, mikro hizmeti Swagger Kullanıcı arabiriminde sunulan yöntemlerle test edebilirsiniz ve son olarak `docker-compose down` komutuyla her şeyi temizleyebilirsiniz.

Ancak, bu durumda 5101 dış bağlantı noktası aracılığıyla mikro hizmetle doğrudan erişim iletişimi, uygulamanızda kaçınmak istediğiniz kadar kesin bir durumdur. API ağ geçidinin ek yöneltme düzeyini (Bu durumda Ocelot) ayarlayarak bundan kaçınabilirsiniz. Bu şekilde, istemci uygulaması mikro hizmete doğrudan erişemez.

## <a name="implementing-your-api-gateways-with-ocelot"></a>API ağ geçitlerini Ocelot ile uygulama

Ocelot, temel olarak belirli bir sırada uygulayabileceğiniz bir middlewares kümesidir.

Ocelot yalnızca ASP.NET Core çalışmak üzere tasarlanmıştır. .NET Core 2,0 çalışma zamanı ve .NET Framework 4.6.1 çalışma zamanı ve ' de dahil olmak üzere 2,0 .NET Standard her yerde kullanılabilmesi için Netstandard 2.0 'ı hedefliyordu.

Ocelot 'yi ve onun bağımlılıklarını, Visual Studio 'dan [Ocelot 'Nin NuGet paketiyle](https://www.nuget.org/packages/Ocelot/)ASP.NET Core projenize yüklersiniz.

```powershell
Install-Package Ocelot
```

EShopOnContainers 'da, API Gateway uygulamasının basit bir ASP.NET Core WebHost projesi ve Ocelot 'nin middlewares, aşağıdaki görüntüde gösterildiği gibi tüm API Gateway özelliklerini işlemesi:

![Ocelot API Gateway projesini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

**Şekil 6-32**. EShopOnContainers 'da OcelotApiGw temel projesi

Bu ASP.NET Core WebHost projesi temel olarak iki basit dosya ile oluşturulmuştur: `Program.cs` ve `Startup.cs`.

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

Ocelot için buradaki önemli nokta, `AddJsonFile()` yöntemi aracılığıyla oluşturucuya sağlamanız gereken `configuration.json` dosyasıdır. Bu `configuration.json`, genellikle farklı bağlantı noktaları kullanarak belirli bağlantı noktaları ve bağıntılı iç uç noktalar içeren dış uç noktalar olan tüm API ağ geçidi ReRoutes belirttiğiniz yerdir.

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

Yapılandırmanın iki bölümü vardır. Bir ReRoutes dizisi ve bir GlobalConfiguration. ReRoutes, bir yukarı akış isteğini nasıl ele alacaklarını belirten nesnelerdir. Genel yapılandırma, belirli ayarları yeniden yönlendirme için geçersiz kılmalara izin verir. Çok sayıda yeniden yönlendirme için belirli ayarları yönetmek istemiyorsanız yararlıdır.

Aşağıda, eShopOnContainers 'dan API ağ geçitlerinden birinden [yapılandırma dosyası yeniden yönlendirme](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) için basitleştirilmiş bir örnek verilmiştir.

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

Örneğin, yukarıdaki Configuration. JSON, sepet mikro hizmeti yapılandırması olan ReRoutes birine odaklanalım.

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

`Host`, kullanmakta olduğunuz hizmet adı çözümlemesine bağlı olan bir hizmet adıdır. Docker-Compose kullanırken, hizmet adları Docker ana bilgisayarı tarafından sağlanır ve bu, Docker-Compose dosyalarında belirtilen hizmet adlarını kullanmaktır. Kubernetes veya Service Fabric gibi bir Orchestrator kullanılıyorsa, bu ad her Orchestrator tarafından sağlanmış olan DNS veya ad çözümlemesi tarafından çözümlenmelidir.

Downstreamhostandport, istekleri iletmek istediğiniz herhangi bir aşağı akış hizmetinin ana bilgisayar ve bağlantı noktasını içeren bir dizidir. Genellikle bu yalnızca bir giriş içerir, ancak bazen aşağı akış hizmetlerinize yük dengelemesi yapmak isteyebilirsiniz ve Ocelot, birden fazla giriş eklemenizi ve sonra bir yük dengeleyici seçmenizi sağlar. Ancak Azure ve herhangi bir Orchestrator kullanılıyorsa, bulut ve Orchestrator altyapısıyla yük dengelemesi daha iyi bir fikir olabilir.

UpstreamPathTemplate, istemci tarafından verilen bir istek için kullanılacak olan DownstreamPathTemplate 'i tanımlamak için kullanılan URL 'dir. Son olarak, UpstreamHttpMethod kullanılır. bu nedenle, Ocelot, farklı istekleri (GET, POST, PUT) aynı URL 'ye ayırabilirler.

Bu noktada, bir veya [birden fazla birleştirilmiş Configuration. JSON dosyası](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) kullanarak tek bir Ocelot API Gateway (ASP.NET Core Webhost) olabilir veya [yapılandırmayı BIR tüketil kV deposunda](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)da saklayabilirsiniz.

Ancak, mimari ve tasarım bölümlerinde tanıtıldıkça, gerçekten otonom mikro hizmetlere sahip olmak istiyorsanız, bu tek monoparçalı API ağ geçidini birden çok API ağ geçidine ve/veya BFF (ön uç için arka uç) olarak bölmek daha iyi olabilir. Bu amaçla, bu yaklaşımı Docker kapsayıcılarıyla nasıl uygulayacağınızı görelim.

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a>Birden çok farklı API Gateway/BFF kapsayıcı türü çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanma

EShopOnContainers 'da, Ocelot API ağ geçidiyle tek bir Docker kapsayıcı görüntüsü kullanıyoruz, ancak çalışma zamanında, her bir hizmet için farklı bir BILGISAYAR klasörüne erişmek üzere bir Docker birimi kullanarak, farklı bir Configuration. JSON dosyası sağlayarak her bir API-Gateway/BFF türü için farklı hizmetler/kapsayıcılar oluşturacağız.

![Tüm API ağ geçitleri için tek bir Ocelot Gateway Docker görüntüsünün diyagramı.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

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

![Configuration. JSON dosyaları olan tüm API ağ geçitlerini gösteren ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

**Şekil 6-34**. Her API ağ geçidini/BFF 'yi Ocelot ile tanımlamak için gereken tek dosya bir yapılandırma dosyasıdır

API ağ geçidini birden çok API ağ geçidine bölerek, mikro hizmetlerin farklı alt kümelerine odaklanan farklı geliştirme takımları, bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitlerini yönetebilir. Ayrıca, aynı anda aynı Ocelot Docker görüntüsünü yeniden kullanabilir.

Artık, API ağ geçitleri ile eShopOnContainers çalıştırırsanız (eShopOnContainers-ServicesAndWebApps. sln çözümü açılırken veya "Docker-Compose up" çalıştırıyorsanız), aşağıdaki örnek yollar gerçekleştirilir.

Örneğin, webshoppingapigw API Gateway tarafından sunulan yukarı akış URL 'sini ziyaret `http://localhost:5202/api/v1/c/catalog/items/2/`, aşağıdaki tarayıcıda olduğu gibi, Docker konağının içindeki iç aşağı akış URL 'SI `http://catalog.api/api/v1/2` aynı sonucu elde edersiniz.

![API Gateway üzerinden yanıt gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

**Şekil 6-35**. API ağ geçidi tarafından sunulan bir URL aracılığıyla mikro hizmete erişme

Test veya hata ayıklama nedenlerinden dolayı, API Gateway 'e geçmeden doğrudan Katalog Docker kapsayıcısına (yalnızca geliştirme ortamında) erişmek isterseniz, ' Catalog. API ', Docker ana bilgisayarına (Docker-Compose hizmet adları tarafından işlenen hizmet bulma) iç bir DNS çözümünden, kapsayıcıya doğrudan erişmenin tek yolu, yalnızca aşağıdaki tarayıcıda `http://localhost:5101/api/v1/Catalog/items/1` gibi geliştirme testlerinde sağlanmış olan Docker-Compose. override. yıml içinde Yayınlanan dış bağlantı noktasıdır.

![Catalog. API 'ye doğrudan yanıt gösteren tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

**Şekil 6-36**. Sınama amacıyla bir mikro hizmete doğrudan erişim

Ancak uygulama, doğrudan bağlantı noktasında "kısayollar" değil, tüm mikro hizmetlere API ağ geçitleri üzerinden erişmesi için yapılandırılmıştır.

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a>EShopOnContainers 'daki ağ geçidi toplama deseninin

Daha önce sunulmuş olduğu gibi, istek toplamayı uygulamak için esnek bir yol, koda göre özel hizmetlerle aynıdır. Ayrıca, [Ocelot Içindeki Istek toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)ile istek toplamayı da uygulayabilirsiniz, ancak ihtiyacınız olduğu kadar esnek olmayabilir. Bu nedenle, eShopOnContainers 'da toplamayı uygulamak için seçilen yol, her toplayıcı için açık bir ASP.NET Core Web API hizmeti kullanmaktır.

Bu yaklaşıma göre, API ağ geçidi bileşim diyagramı, daha önce gösterilen Basitleştirilmiş küresel mimari diyagramında görünmeyen toplayıcı Hizmetleri düşünüldüğünde çok daha fazla uzatılmış bir bittir.

Aşağıdaki diyagramda, toplayıcı Hizmetleri 'nin ilgili API ağ geçitleriyle nasıl çalıştığını da görebilirsiniz.

![Toplayıcı hizmetlerini gösteren eShopOnContainers mimarisinin diyagramı.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

**Şekil 6-37**. Toplayıcı Hizmetleri ile eShopOnContainers mimarisi

Daha fazla yakınlaştırma, aşağıdaki görüntüde "alışveriş" iş alanında, API ağ geçitlerinde toplayıcı Hizmetleri kullanılırken istemci uygulamaları ve mikro hizmetler arasındaki azaltmaya azaldığını görebilirsiniz.

![EShopOnContainers mimarisi yakınlaştırmasını gösteren diyagram.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

**Şekil 6-38**. Toplayıcı hizmetlerini yakından yakınlaştırın

Diyagramda, karmaşık alabileceğiniz API ağ geçitlerinden gelen olası istekleri nasıl gösterdiğinin fark edebilirsiniz. Mavi renkli okların nasıl basitleştiğini, bir istemci uygulamalar perspektifinden, iletişim kutusunda azaltmaya ve gecikme süresini azaltarak, uzak uygulamaların kullanıcı deneyimini önemli ölçüde geliştirerek ( Mobil ve SPA uygulamaları), özellikle.

"Pazarlama" iş alanı ve mikro hizmetler söz konusu olduğunda, bu basit bir kullanım durumdur, bu nedenle aggregators 'ı kullanmaya gerek yoktur, ancak gerekirse bu da mümkün olabilir.

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a>Ocelot API ağ geçitlerinde kimlik doğrulama ve yetkilendirme

Bir Ocelot API ağ geçidinde, kimlik doğrulama belirtecini veya API ağ geçidinin içinden veya içinden kimlik doğrulama [belirtecini sağlayan bir](https://identityserver.io/) ASP.NET Core Web API hizmeti gibi, kimlik doğrulama hizmetine oturtyükleyebilirsiniz.

EShopOnContainers, BFF ve iş alanlarını temel alan sınırların bulunduğu birden çok API ağ geçidi kullandığından, kimlik/kimlik doğrulama hizmeti, aşağıdaki diyagramda sarı renkle vurgulanmış şekilde API ağ geçitlerinden bırakılır.

![API ağ geçidinin altındaki kimlik mikro hizmetini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

**Şekil 6-39**. EShopOnContainers 'da kimlik hizmetinin konumu

Ancak, Ocelot Ayrıca, bu diğer diyagramda olduğu gibi, API Gateway sınırının içinde kimlik/auth mikro hizmetini de destekler.

![Bir Ocelot API ağ geçidinde kimlik doğrulamasını gösteren diyagram.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

**Şekil 6-40**. Ocelot 'de kimlik doğrulaması

Önceki diyagramda gösterildiği gibi, kimlik mikro hizmeti, API ağ geçidinin (AG) altında olduğunda, 1) AG, kimlik mikro hizmetinden bir kimlik doğrulama belirteci ister 2) kimlik doğrulama belirtecini kullanarak mikro hizmetlerden gelen bir kimlik doğrulaması belirteci 3-4 döndürür. EShopOnContainers uygulaması, API ağ geçidini birden çok BFF (ön uç için arka uç) ve iş alanları API ağ geçitleri 'ne böldüğü için, çapraz kesme sorunları için ek bir API ağ geçidi oluşturulması gerekir. Bu seçenek, birden çok çapraz kesme sorunları olan mikro hizmetlere sahip daha karmaşık bir mikro hizmet tabanlı mimaride yer alan bir şekilde yapılır. EShopOnContainers 'da yalnızca bir çapraz kesme sorunu olduğundan, basitlik 'in sake 'SI için API ağ geçidi bölgesinden yalnızca güvenlik hizmetini işlemeye karar verdi.

Herhangi bir durumda, uygulama API ağ geçidi düzeyinde güvenli hale getirildiğinden, güvenli mikro hizmeti kullanmaya çalışırken Ocelot API ağ geçidinin kimlik doğrulama modülü ilk olarak ziyaret edilir. Bu, access_token ile korunan hizmetleri ziyaret edebilmeniz için erişim belirtecini almak üzere kimliği veya auth mikro hizmetini ziyaret etmek üzere HTTP isteğini yeniden yönlendirir.

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

Ocelot çalıştırıldığında, ReRoutes AuthenticationOptions. AuthenticationProviderKey öğesine bakar ve verilen anahtara kayıtlı bir kimlik doğrulama sağlayıcısı olup olmadığını kontrol eder. Yoksa, Ocelot başlamacaktır. Varsa, yeniden yönlendirme bu sağlayıcıyı çalıştırıldığında kullanır.

Ocelot WebHost, `authenticationProviderKey = "IdentityApiKey"`ile yapılandırıldığından, bu hizmet kimlik doğrulama belirteci olmayan herhangi bir istek olduğunda kimlik doğrulaması gerektirir.

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

"Sepet" gibi Validaudide, aşağıdaki kodda olduğu gibi, başlangıç sınıfının ConfigureServices () `AddJwtBearer()` ile her bir mikro hizmette tanımlanan hedef kitlelerle bağıntılı.

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

`http://localhost:5202/api/v1/b/basket/1`gibi API ağ geçidine dayanan bir yeniden yönlendirme URL 'SI ile sepet mikro hizmeti gibi güvenli bir mikro hizmete erişmeye çalışırsanız, geçerli bir belirteç sağlamadığınız takdirde 401 yetkisi alırsınız. Öte yandan, bir yeniden yönlendirme URL 'SI doğrulandıysa, Ocelot kendisiyle ilişkili bir aşağı akış şemasını (iç mikro hizmet URL 'SI) çağırır.

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

API ağ geçitleri ön uçlardır veya façades, genellikle kendi kapsamlarından çıkan Web uygulamalarına değil, yalnızca hizmetlere yönelik olur. Ayrıca, API ağ geçitleri bazı iç mikro hizmetleri gizleyebilir.

Ancak giriş, HTTP isteklerini yeniden yönlendirse de herhangi bir mikro hizmeti veya Web uygulamasını gizlemeyi denememelidir.

Web uygulamalarının önündeki Kubernetes 'de bir giriş Nginx katmanına sahip olmak ve çeşitli Ocelot API ağ geçitleri/BFF, aşağıdaki diyagramda gösterildiği gibi ideal mimaridir.

![Bir giriş katmanının AKS ortamına nasıl uyduğunu gösteren bir diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

**Şekil 6-41**. Kubernetes 'e dağıtıldığında eShopOnContainers içindeki giriş katmanı

Kubernetes girişi, genellikle API ağ geçidi kapsamından çıkan Web uygulamaları dahil olmak üzere, uygulamaya yönelik tüm trafik için ters proxy görevi görür. EShopOnContainers 'ı Kubernetes 'e dağıttığınızda, temel olarak yalnızca birkaç hizmet veya uç _nokta Ile URL_'lerde aşağıdaki postdüzeltmelerin listesini sunar:

- istemci SPA Web uygulaması için `/`
- istemci MVC web uygulaması için `/webmvc`
- durum/healthdenetimleri gösteren istemci Web uygulaması için `/webstatus`
- Web BFF ve alışveriş iş işlemlerine yönelik `/webshoppingapigw`
- Web BFF ve pazarlama iş işlemlerine yönelik `/webmarketingapigw`
- Mobil BFF ve alışveriş iş işlemlerine yönelik `/mobileshoppingapigw`
- Mobil BFF ve pazarlama iş işlemlerine yönelik `/mobilemarketingapigw`

Kubernetes 'e dağıtım yaparken, her Ocelot API ağ geçidi, API ağ geçitlerini çalıştıran her _Pod_ için farklı bir "Configuration. JSON" dosyası kullanıyor. Bu "Configuration. JSON" dosyaları, ' Ocelot ' adlı bir Kubernetes _yapılandırma eşlemesi_ temel alınarak oluşturulan bir birimi bağlama tarafından sağlanır (başlangıçta Deploy. ps1 betiği ile). Her kapsayıcı, `/app/configuration`adlı kapsayıcı klasöründe ilgili yapılandırma dosyasını takar.

EShopOnContainers kaynak kodu dosyalarında, özgün "Configuration. JSON" dosyaları `k8s/ocelot/` klasörü içinde bulunabilir. Her BFF/APIGateway için bir dosya vardır.

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a>Bir Ocelot API ağ geçidinde ek çapraz kesme özellikleri

Aşağıdaki bağlantılarda açıklanan bir Ocelot API ağ geçidi kullanırken araştırmak ve kullanmak için kullanabileceğiniz diğer önemli özellikler vardır.

- **İstemci tarafındaki hizmet keşfi, Cell veya Eureka ile tümleştirme** \
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
> [Önceki](background-tasks-with-ihostedservice.md)
> [İleri](../microservice-ddd-cqrs-patterns/index.md)
