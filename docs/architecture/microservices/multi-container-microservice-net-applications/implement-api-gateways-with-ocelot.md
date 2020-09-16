---
title: Ocelot ile API Ağ Geçitlerini uygulama
description: Ocelot ile API ağ geçitleri uygulamayı ve kapsayıcı tabanlı bir ortamda Ocelot 'yi kullanmayı öğrenin.
ms.date: 03/02/2020
ms.openlocfilehash: cd776b2fa31a630d9b58530605966ed2431912a2
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539560"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="b5112-103">Ocelot ile API ağ geçitleri uygulama</span><span class="sxs-lookup"><span data-stu-id="b5112-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b5112-104">Başvuru mikro hizmet uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) Şu anda, önceki başvurulan [OCELOT](https://github.com/ThreeMammals/Ocelot)yerine API ağ geçidini uygulamak üzere [Envoy](https://www.envoyproxy.io/) tarafından sunulan özellikleri kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="b5112-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="b5112-105">Bu tasarımı, eShopOnContainers 'da uygulanan yeni gRPC Hizmetleri arası iletişimler için gerekli olan WebSocket protokolüne yönelik yerleşik destek nedeniyle, bu tasarımın seçimi yaptık.</span><span class="sxs-lookup"><span data-stu-id="b5112-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="b5112-106">Ancak, bu bölümü kılavuzda tutduk, böylece üretim sınıfı senaryolar için uygun olan basit, yetenekli ve hafif bir API ağ geçidi olarak Ocelot 'yi düşünebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>
> <span data-ttu-id="b5112-107">Ayrıca, en son Ocelot sürümü JSON şemasında bir son değişiklik içerir.</span><span class="sxs-lookup"><span data-stu-id="b5112-107">Also, latest Ocelot version contains a breaking change on its json schema.</span></span> <span data-ttu-id="b5112-108">Ocelot < v 16.0.0 kullanmayı düşünün veya ReRoutes yerine anahtar yollarını kullanın.</span><span class="sxs-lookup"><span data-stu-id="b5112-108">Consider using Ocelot < v16.0.0, or use the key Routes instead of ReRoutes.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="b5112-109">API ağ geçitlerini mimarinizi ve tasarlama</span><span class="sxs-lookup"><span data-stu-id="b5112-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="b5112-110">Aşağıdaki mimari diyagramda, API ağ geçitlerinin eShopOnContainers 'da Ocelot ile nasıl uygulandığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5112-110">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![EShopOnContainers mimarisini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="b5112-112">**Şekil 6-28**.</span><span class="sxs-lookup"><span data-stu-id="b5112-112">**Figure 6-28**.</span></span> <span data-ttu-id="b5112-113">API ağ geçitleri ile eShopOnContainers mimarisi</span><span class="sxs-lookup"><span data-stu-id="b5112-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="b5112-114">Bu diyagramda tüm uygulamanın, "Docker for Windows" veya "Docker for Mac" ile tek bir Docker konağına veya geliştirme BILGISAYARıNA nasıl dağıtıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b5112-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="b5112-115">Ancak, herhangi bir Orchestrator 'a dağıtım benzerdir, ancak Diyagramdaki herhangi bir kapsayıcı Orchestrator 'da genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-115">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="b5112-116">Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıklarının, Orchestrator 'dan boşaltılabilmesi ve Azure SQL veritabanı, Azure Cosmos DB, Azure redin, Azure Service Bus veya şirket içinde herhangi bir HA kümeleme çözümü gibi altyapıda yüksek kullanılabilir sistemlere dağıtılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5112-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="b5112-117">Diyagramda da fark edebilirsiniz. birçok API ağ geçidine sahip olmak, mikro hizmetlerinin yanı sıra kendi ilgili API ağ geçitlerinin geliştirilmesi ve dağıtılmasında birden çok geliştirme ekibinin otonom olmasına (Bu durumda pazarlama özellikleri ve alışveriş özellikleri) izin verir.</span><span class="sxs-lookup"><span data-stu-id="b5112-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="b5112-118">Çeşitli geliştirme ekipleri tarafından güncelleştirilebilecek tek bir tek nokta olan tek bir tek bir API ağ geçidiniz varsa, tüm mikro hizmetlere uygulamanın tek bir bölümüyle de neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="b5112-119">Tasarımda çok daha fazla şey varsa, bazen ayrıntılı bir API ağ geçidi, seçilen mimariye bağlı olarak tek bir iş mikro hizmeti ile de sınırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="b5112-120">API ağ geçidinin iş veya etki alanı tarafından dikte edilen sınırlarının olması, daha iyi bir tasarım almanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="b5112-120">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="b5112-121">Örneğin, gelişmiş bir API Gateway kavramı bir UI bileşim hizmetine benzer olduğundan, API ağ geçidi katmanında ince ayrıntı düzeyi özellikle mikro hizmetleri temel alan daha gelişmiş bileşik UI uygulamaları için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="b5112-122">Önceki bölümde, [mikro hizmetlere dayalı bileşik Kullanıcı arabirimi oluşturma hakkında](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)daha fazla ayrıntı inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="b5112-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="b5112-123">Anahtar kullanımı, çok sayıda Orta ve büyük ölçekli uygulamalar için, özel olarak oluşturulmuş bir API ağ geçidi ürünü kullanmak genellikle iyi bir yaklaşımdır, ancak tek bir monoparçalı toplayıcı veya benzersiz bir merkezi özel API ağ geçidi değil, bu API Gateway, özerk mikro hizmetler oluşturan çeşitli geliştirme ekipleri için birden çok bağımsız yapılandırma alanına izin vermez.</span><span class="sxs-lookup"><span data-stu-id="b5112-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="b5112-124">API ağ geçitleri aracılığıyla yeniden yönlendirme için örnek mikro hizmetler/kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="b5112-124">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="b5112-125">Örnek olarak, eShopOnContainers, aşağıdaki görüntüde gösterildiği gibi, API ağ geçitleri aracılığıyla yayımlanması gereken altı adet iç mikro hizmet türü içerir.</span><span class="sxs-lookup"><span data-stu-id="b5112-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Alt klasörlerini gösteren hizmetler klasörünün ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="b5112-127">**Şekil 6-29**.</span><span class="sxs-lookup"><span data-stu-id="b5112-127">**Figure 6-29**.</span></span> <span data-ttu-id="b5112-128">Visual Studio 'da eShopOnContainers çözümünde mikro hizmet klasörleri</span><span class="sxs-lookup"><span data-stu-id="b5112-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="b5112-129">Kimlik hizmeti hakkında, tasarımda tek bir çapraz kesme sorunu olduğundan, bu, yönetim ağ geçidi yönlendirmesinde kalmadı, ancak bu da yeniden yönlendirme listelerinin bir parçası olarak dahil olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="b5112-130">Koddan bildirebilmeniz için, bu hizmetlerin tümü şu anda ASP.NET Core Web API hizmeti olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="b5112-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="b5112-131">Kataloğun mikro hizmet kodu gibi mikro hizmetlerden birine odaklanalım.</span><span class="sxs-lookup"><span data-stu-id="b5112-131">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![Catalog. API proje içeriğini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="b5112-133">**Şekil 6-30**.</span><span class="sxs-lookup"><span data-stu-id="b5112-133">**Figure 6-30**.</span></span> <span data-ttu-id="b5112-134">Örnek Web API mikro hizmeti (Katalog mikro hizmeti)</span><span class="sxs-lookup"><span data-stu-id="b5112-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="b5112-135">Catalog mikro hizmet 'in, aşağıdaki kodda olduğu gibi çeşitli denetleyiciler ve yöntemlerle tipik bir ASP.NET Core Web API projesi olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="b5112-136">HTTP isteği, mikro hizmet veritabanına ve gerekli ek eylemlere erişen bu tür C# kodunu çalıştırmaya sona acaktır.</span><span class="sxs-lookup"><span data-stu-id="b5112-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="b5112-137">Mikro hizmet URL 'SI ile ilgili olan kapsayıcılar yerel geliştirme PC 'nizde (yerel Docker ana bilgisayarı) dağıtıldığında, her mikro hizmet kapsayıcısı, aşağıdaki dockerfile içinde olduğu gibi, dockerfile içinde her zaman bir iç bağlantı noktasına (genellikle bağlantı noktası 80) sahiptir:</span><span class="sxs-lookup"><span data-stu-id="b5112-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container always has an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="b5112-138">Kodda gösterilen bağlantı noktası 80, Docker ana bilgisayarı dahilinde olduğundan istemci uygulamaları tarafından ulaşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="b5112-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="b5112-139">İstemci uygulamaları, ile dağıtım sırasında yayımlanan dış bağlantı noktalarına (varsa) erişebilir `docker-compose` .</span><span class="sxs-lookup"><span data-stu-id="b5112-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="b5112-140">Bu dış bağlantı noktaları, bir üretim ortamına dağıtıldığında yayımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="b5112-141">Bu, istemci uygulamaları ve mikro hizmetler arasındaki doğrudan iletişimin önüne geçmek için API ağ geçidini kullanmak istediğinizden kesinlikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="b5112-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="b5112-142">Ancak geliştirme sırasında, mikro hizmet/kapsayıcıya doğrudan erişmek ve Swagger aracılığıyla çalıştırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="b5112-143">EShopOnContainers 'da bu nedenle, dış bağlantı noktaları API Gateway veya istemci uygulamaları tarafından kullanılmayabilse bile hala belirtilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-143">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="b5112-144">`docker-compose.override.yml`Katalog mikro hizmetinin dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b5112-144">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

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

<span data-ttu-id="b5112-145">Docker-Compose. override. yıml yapılandırmasında Katalog kapsayıcısının iç bağlantı noktası 80 olup olmadığını görebilirsiniz, ancak dış erişim bağlantı noktası 5101 ' dir.</span><span class="sxs-lookup"><span data-stu-id="b5112-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="b5112-146">Ancak bu bağlantı noktası, yalnızca katalog mikro hizmetini yalnızca hata ayıklama, çalıştırma ve test etme amacıyla bir API ağ geçidi kullanırken uygulama tarafından kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-146">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="b5112-147">Genellikle, mikro hizmetler için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir Orchestrator olduğundan, bir üretim ortamına Docker-Compose ile dağıtım yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="b5112-147">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="b5112-148">Bu ortamlara dağıtım yaparken, mikro hizmetler için doğrudan herhangi bir harici bağlantı noktasını yayımlayamayacağınız farklı yapılandırma dosyalarını kullanırsınız, ancak her zaman ters proxy 'yi API Gateway 'den kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="b5112-148">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="b5112-149">Katalog mikro hizmetini yerel Docker ana bilgisayarınızda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="b5112-149">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="b5112-150">Visual Studio 'dan tam eShopOnContainers çözümünü çalıştırın (Docker-Compose dosyalarındaki tüm hizmetleri çalıştırır) ya da Katalog mikro hizmetini CMD veya PowerShell 'deki aşağıdaki Docker-Compose komutuyla `docker-compose.yml` ve ' nin yerleştirildiği klasörde konumlandırılmış şekilde başlatın `docker-compose.override.yml` .</span><span class="sxs-lookup"><span data-stu-id="b5112-150">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="b5112-151">Bu komut yalnızca Catalog-API hizmet kapsayıcısını ve Docker-Compose. yıml içinde belirtilen bağımlılıkları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="b5112-151">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="b5112-152">Bu durumda, SQL Server Container ve Kbbitmq kapsayıcısı.</span><span class="sxs-lookup"><span data-stu-id="b5112-152">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="b5112-153">Daha sonra, Katalog mikro hizmetine doğrudan erişebilir ve bu durumda "dış" bağlantı noktasından doğrudan bu bağlantı noktası üzerinden erişim için Swagger Kullanıcı arabirimi aracılığıyla yöntemlerini görebilirsiniz `http://localhost:5101/swagger` :</span><span class="sxs-lookup"><span data-stu-id="b5112-153">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Catalog. API REST API gösteren Swagger Kullanıcı arabiriminin ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="b5112-155">**Şekil 6-31**.</span><span class="sxs-lookup"><span data-stu-id="b5112-155">**Figure 6-31**.</span></span> <span data-ttu-id="b5112-156">Katalog mikro hizmetini Swagger Kullanıcı arabirimiyle test etme</span><span class="sxs-lookup"><span data-stu-id="b5112-156">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="b5112-157">Bu noktada, Visual Studio 'da C# kodunda bir kesme noktası ayarlayabilir, mikro hizmeti Swagger Kullanıcı arabiriminde kullanıma sunulan yöntemlerle test edebilirsiniz ve son olarak komutla her şeyi temizleyebilirsiniz `docker-compose down` .</span><span class="sxs-lookup"><span data-stu-id="b5112-157">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="b5112-158">Ancak, bu durumda 5101 dış bağlantı noktası aracılığıyla mikro hizmetle doğrudan erişim iletişimi, uygulamanızda kaçınmak istediğiniz kadar kesin bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="b5112-158">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="b5112-159">API ağ geçidinin ek yöneltme düzeyini (Bu durumda Ocelot) ayarlayarak bundan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-159">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="b5112-160">Bu şekilde, istemci uygulaması mikro hizmete doğrudan erişemez.</span><span class="sxs-lookup"><span data-stu-id="b5112-160">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="b5112-161">API ağ geçitlerini Ocelot ile uygulama</span><span class="sxs-lookup"><span data-stu-id="b5112-161">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="b5112-162">Ocelot, temel olarak belirli bir sırada uygulayabileceğiniz bir middlewares kümesidir.</span><span class="sxs-lookup"><span data-stu-id="b5112-162">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="b5112-163">Ocelot yalnızca ASP.NET Core çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="b5112-163">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="b5112-164">Paketin en son sürümü hedefler `.NETCoreApp 3.1` ve bu nedenle .NET Framework uygulamalar için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="b5112-164">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="b5112-165">Ocelot 'yi ve onun bağımlılıklarını, Visual Studio 'dan [Ocelot 'Nin NuGet paketiyle](https://www.nuget.org/packages/Ocelot/)ASP.NET Core projenize yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-165">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="b5112-166">EShopOnContainers 'da, API Gateway uygulamasının basit bir ASP.NET Core WebHost projesi ve Ocelot 'nin ara yazılımı, aşağıdaki görüntüde gösterildiği gibi tüm API ağ geçidi özelliklerini işler:</span><span class="sxs-lookup"><span data-stu-id="b5112-166">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![Ocelot API Gateway projesini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="b5112-168">**Şekil 6-32**.</span><span class="sxs-lookup"><span data-stu-id="b5112-168">**Figure 6-32**.</span></span> <span data-ttu-id="b5112-169">EShopOnContainers 'da OcelotApiGw temel projesi</span><span class="sxs-lookup"><span data-stu-id="b5112-169">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="b5112-170">Bu ASP.NET Core WebHost projesi temel olarak iki basit dosya ile oluşturulmuştur:  `Program.cs` ve `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="b5112-170">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="b5112-171">Program.cs yalnızca, BuildWebHost ASP.NET Core oluşturmak ve yapılandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="b5112-171">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="b5112-172">Ocelot için buradaki önemli nokta, `configuration.json` Oluşturucu yöntemi aracılığıyla sağlamanız gereken dosyadır `AddJsonFile()` .</span><span class="sxs-lookup"><span data-stu-id="b5112-172">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="b5112-173">Diğer bir deyişle, `configuration.json` genellikle farklı bağlantı noktaları kullanan belirli bağlantı noktaları ve bağıntılı iç uç noktalar içeren dış uç noktalar olan tüm API ağ geçidi ReRoutes belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-173">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="b5112-174">Yapılandırmanın iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="b5112-174">There are two sections to the configuration.</span></span> <span data-ttu-id="b5112-175">Bir ReRoutes dizisi ve bir GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="b5112-175">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="b5112-176">ReRoutes, bir yukarı akış isteğini nasıl ele alacaklarını belirten nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="b5112-176">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="b5112-177">Genel yapılandırma, belirli ayarları yeniden yönlendirme için geçersiz kılmalara izin verir.</span><span class="sxs-lookup"><span data-stu-id="b5112-177">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="b5112-178">Çok sayıda yeniden yönlendirme için belirli ayarları yönetmek istemiyorsanız yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-178">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="b5112-179">Aşağıda, eShopOnContainers 'dan API ağ geçitlerinden birinden [yapılandırma dosyası yeniden yönlendirme](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) için basitleştirilmiş bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b5112-179">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

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

<span data-ttu-id="b5112-180">Bir Ocelot API ağ geçidinin ana işlevselliği, gelen HTTP isteklerini almak ve şu anda başka bir HTTP isteği olarak bir aşağı akış hizmetine iletmektir.</span><span class="sxs-lookup"><span data-stu-id="b5112-180">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="b5112-181">Ocelot, bir isteğin bir yeniden yönlendirme olarak diğerine yönlendirilmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b5112-181">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="b5112-182">Örneğin, sepet mikro hizmeti yapılandırması, yukarıdaki configuration.jsüzerinde bulunan ReRoutes birine odaklanalım.</span><span class="sxs-lookup"><span data-stu-id="b5112-182">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

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

<span data-ttu-id="b5112-183">DownstreamPathTemplate, düzen ve Downstreamhostandport, bu isteğin iletileceği iç mikro hizmet URL 'sini yapar.</span><span class="sxs-lookup"><span data-stu-id="b5112-183">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="b5112-184">Bağlantı noktası, hizmet tarafından kullanılan iç bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-184">The port is the internal port used by the service.</span></span> <span data-ttu-id="b5112-185">Kapsayıcılar kullanılırken dockerfile 'da belirtilen bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="b5112-185">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="b5112-186">, `Host` Kullanmakta olduğunuz hizmet adı çözümlemesine bağlı olan bir hizmet adıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-186">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="b5112-187">Docker-Compose kullanırken, hizmet adları Docker ana bilgisayarı tarafından sağlanır ve bu, Docker-Compose dosyalarında belirtilen hizmet adlarını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b5112-187">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="b5112-188">Kubernetes veya Service Fabric gibi bir Orchestrator kullanılıyorsa, bu ad her Orchestrator tarafından sağlanmış olan DNS veya ad çözümlemesi tarafından çözümlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="b5112-188">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="b5112-189">Downstreamhostandport, istekleri iletmek istediğiniz herhangi bir aşağı akış hizmetinin ana bilgisayar ve bağlantı noktasını içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="b5112-189">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="b5112-190">Genellikle bu yalnızca bir giriş içerir, ancak bazen aşağı akış hizmetlerinize yük dengelemesi yapmak isteyebilirsiniz ve Ocelot, birden fazla giriş eklemenizi ve sonra bir yük dengeleyici seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="b5112-190">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="b5112-191">Ancak Azure ve herhangi bir Orchestrator kullanılıyorsa, bulut ve Orchestrator altyapısıyla yük dengelemesi daha iyi bir fikir olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-191">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="b5112-192">UpstreamPathTemplate, istemci tarafından verilen bir istek için kullanılacak olan DownstreamPathTemplate 'i tanımlamak için kullanılan URL 'dir.</span><span class="sxs-lookup"><span data-stu-id="b5112-192">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="b5112-193">Son olarak, UpstreamHttpMethod kullanılır. bu nedenle, Ocelot, farklı istekleri (GET, POST, PUT) aynı URL 'ye ayırabilirler.</span><span class="sxs-lookup"><span data-stu-id="b5112-193">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="b5112-194">Bu noktada, dosyalarda bir veya [birden çok birleştirilmiş configuration.js](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) kullanarak tek bir Ocelot API ağ geçidine (ASP.NET Core Webhost) sahip olabilirsiniz veya [yapılandırmayı BIR tüketil kV deposunda](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)da saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-194">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="b5112-195">Ancak, mimari ve tasarım bölümlerinde tanıtıldıkça, gerçekten otonom mikro hizmetlere sahip olmak istiyorsanız, bu tek monoparçalı API ağ geçidini birden çok API ağ geçidine ve/veya BFF (ön uç için arka uç) olarak bölmek daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-195">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="b5112-196">Bu amaçla, bu yaklaşımı Docker kapsayıcılarıyla nasıl uygulayacağınızı görelim.</span><span class="sxs-lookup"><span data-stu-id="b5112-196">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="b5112-197">Birden çok farklı API Gateway/BFF kapsayıcı türü çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanma</span><span class="sxs-lookup"><span data-stu-id="b5112-197">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="b5112-198">EShopOnContainers 'da, Ocelot API ağ geçidiyle tek bir Docker kapsayıcı görüntüsü kullanıyoruz, ancak çalışma zamanında, her bir hizmet için farklı bir BILGISAYAR klasörüne erişmek üzere bir Docker birimi kullanarak her bir API-Gateway/Bconfiguration.jsff türü için farklı hizmetler/kapsayıcılar oluşturacağız.</span><span class="sxs-lookup"><span data-stu-id="b5112-198">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Tüm API ağ geçitleri için tek bir Ocelot Gateway Docker görüntüsünün diyagramı.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="b5112-200">**Şekil 6-33**.</span><span class="sxs-lookup"><span data-stu-id="b5112-200">**Figure 6-33**.</span></span> <span data-ttu-id="b5112-201">Birden çok API ağ geçidi türü genelinde tek bir Ocelot Docker görüntüsünü yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="b5112-201">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="b5112-202">EShopOnContainers 'da, "genel Ocelot API Gateway Docker Image", Docker-Compose. yml dosyasında belirtilen ' OcelotApiGw ' adlı projeyle ve "eShop/ocelotapigw" görüntü adına oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="b5112-202">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="b5112-203">Daha sonra, Docker 'a dağıtım yaparken, Docker-Compose. yıml dosyasında aşağıdaki ayıklama bölümünde gösterildiği gibi, aynı Docker görüntüsünden oluşturulan dört API-Gateway kapsayıcısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5112-203">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

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

<span data-ttu-id="b5112-204">Ayrıca, aşağıdaki Docker-Compose. override. yıml dosyasında görebileceğiniz gibi, bu API ağ geçidi kapsayıcıları arasındaki tek fark, her bir hizmet kapsayıcısı için farklı olan ve bir Docker birimi aracılığıyla çalışma zamanında belirtilen Ocelot yapılandırma dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-204">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

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

<span data-ttu-id="b5112-205">Bu önceki kod nedeniyle ve aşağıdaki Visual Studio Gezgini 'nde gösterildiği gibi, her bir iş/BFF API ağ geçidini tanımlamak için gereken tek dosya yalnızca bir configuration.jsdosyası olur, çünkü dört API ağ geçidi aynı Docker görüntüsüne dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-205">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Dosyalar üzerinde configuration.jstüm API ağ geçitlerini gösteren ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="b5112-207">**Şekil 6-34**.</span><span class="sxs-lookup"><span data-stu-id="b5112-207">**Figure 6-34**.</span></span> <span data-ttu-id="b5112-208">Her API ağ geçidini/BFF 'yi Ocelot ile tanımlamak için gereken tek dosya bir yapılandırma dosyasıdır</span><span class="sxs-lookup"><span data-stu-id="b5112-208">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="b5112-209">API ağ geçidini birden çok API ağ geçidine bölerek, mikro hizmetlerin farklı alt kümelerine odaklanan farklı geliştirme takımları, bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitlerini yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-209">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="b5112-210">Ayrıca, aynı anda aynı Ocelot Docker görüntüsünü yeniden kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-210">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="b5112-211">Artık, API ağ geçitleri ile eShopOnContainers çalıştırırsanız (eShopOnContainers-ServicesAndWebApps. sln çözümü açılırken veya "Docker-Compose up" çalıştırıyorsanız), aşağıdaki örnek yollar gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-211">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="b5112-212">Örneğin, `http://localhost:5202/api/v1/c/catalog/items/2/` webshoppingapigw API Gateway tarafından sunulan yukarı AKıŞ URL 'sini ziyaret ederken, `http://catalog-api/api/v1/2` Docker ana bilgisayarı Içindeki Iç aşağı akış URL 'sinden aşağıdaki tarayıcıda olduğu gibi aynı sonucu elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-212">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![API Gateway üzerinden yanıt gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="b5112-214">**Şekil 6-35**.</span><span class="sxs-lookup"><span data-stu-id="b5112-214">**Figure 6-35**.</span></span> <span data-ttu-id="b5112-215">API ağ geçidi tarafından sunulan bir URL aracılığıyla mikro hizmete erişme</span><span class="sxs-lookup"><span data-stu-id="b5112-215">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="b5112-216">Test veya hata ayıklama nedenlerinden dolayı, API Gateway 'e geçmeden doğrudan Katalog Docker kapsayıcısına (yalnızca geliştirme ortamında) erişmek isterseniz, ' Catalog-API ', Docker ana bilgisayarına (Docker-Compose hizmet adları tarafından işlenen hizmet bulma) iç bir DNS çözümünden, kapsayıcıya doğrudan erişmenin tek yolu, yalnızca aşağıdaki tarayıcıda olduğu gibi geliştirme testleri için sağlanmış olan Docker-Compose. override. yıml içinde Yayınlanan dış bağlantı noktasıdır `http://localhost:5101/api/v1/Catalog/items/1` .</span><span class="sxs-lookup"><span data-stu-id="b5112-216">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Catalog. API 'ye doğrudan yanıt gösteren tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="b5112-218">**Şekil 6-36**.</span><span class="sxs-lookup"><span data-stu-id="b5112-218">**Figure 6-36**.</span></span> <span data-ttu-id="b5112-219">Sınama amacıyla bir mikro hizmete doğrudan erişim</span><span class="sxs-lookup"><span data-stu-id="b5112-219">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="b5112-220">Ancak uygulama, doğrudan bağlantı noktasında "kısayollar" değil, tüm mikro hizmetlere API ağ geçitleri üzerinden erişmesi için yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b5112-220">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="b5112-221">EShopOnContainers 'daki ağ geçidi toplama deseninin</span><span class="sxs-lookup"><span data-stu-id="b5112-221">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="b5112-222">Daha önce sunulmuş olduğu gibi, istek toplamayı uygulamak için esnek bir yol, koda göre özel hizmetlerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="b5112-222">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="b5112-223">Ayrıca, [Ocelot Içindeki Istek toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)ile istek toplamayı da uygulayabilirsiniz, ancak ihtiyacınız olduğu kadar esnek olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-223">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="b5112-224">Bu nedenle, eShopOnContainers 'da toplamayı uygulamak için seçilen yol, her toplayıcı için açık bir ASP.NET Core Web API hizmeti kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="b5112-224">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="b5112-225">Bu yaklaşıma göre, API ağ geçidi bileşim diyagramı, daha önce gösterilen Basitleştirilmiş küresel mimari diyagramında görünmeyen toplayıcı Hizmetleri düşünüldüğünde çok daha fazla uzatılmış bir bittir.</span><span class="sxs-lookup"><span data-stu-id="b5112-225">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="b5112-226">Aşağıdaki diyagramda, toplayıcı Hizmetleri 'nin ilgili API ağ geçitleriyle nasıl çalıştığını da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-226">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Toplayıcı hizmetlerini gösteren eShopOnContainers mimarisinin diyagramı.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="b5112-228">**Şekil 6-37**.</span><span class="sxs-lookup"><span data-stu-id="b5112-228">**Figure 6-37**.</span></span> <span data-ttu-id="b5112-229">Toplayıcı Hizmetleri ile eShopOnContainers mimarisi</span><span class="sxs-lookup"><span data-stu-id="b5112-229">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="b5112-230">Daha fazla yakınlaştırma, aşağıdaki görüntüde "alışveriş" iş alanında, API ağ geçitlerinde toplayıcı Hizmetleri kullanılırken istemci uygulamaları ve mikro hizmetler arasındaki azaltmaya azaldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-230">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![EShopOnContainers mimarisi yakınlaştırmasını gösteren diyagram.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="b5112-232">**Şekil 6-38**.</span><span class="sxs-lookup"><span data-stu-id="b5112-232">**Figure 6-38**.</span></span> <span data-ttu-id="b5112-233">Toplayıcı hizmetlerini yakından yakınlaştırın</span><span class="sxs-lookup"><span data-stu-id="b5112-233">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="b5112-234">Diyagramda, karmaşık alabileceğiniz API ağ geçitlerinden gelen olası istekleri nasıl gösterdiğinin fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-234">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="b5112-235">Mavi renkli okların nasıl basitleştiğini, bir istemci uygulamalar perspektifinden, iletişim azaltmaya ve gecikme süresini azaltarak, uzak uygulamalar (mobil ve SPA uygulamaları) için Kullanıcı deneyimini önemli ölçüde geliştirerek, özellikle.</span><span class="sxs-lookup"><span data-stu-id="b5112-235">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="b5112-236">"Pazarlama" iş alanı ve mikro hizmetler söz konusu olduğunda, bu basit bir kullanım durumdur, bu nedenle aggregators 'ı kullanmaya gerek yoktur, ancak gerekirse bu da mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-236">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="b5112-237">Ocelot API ağ geçitlerinde kimlik doğrulama ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="b5112-237">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="b5112-238">Bir Ocelot API ağ geçidinde, kimlik doğrulama belirtecini veya API ağ geçidinin içinden veya içinden kimlik doğrulama [belirtecini sağlayan bir](https://identityserver.io/) ASP.NET Core Web API hizmeti gibi, kimlik doğrulama hizmetine oturtyükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b5112-238">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="b5112-239">EShopOnContainers, BFF ve iş alanlarını temel alan sınırların bulunduğu birden çok API ağ geçidi kullandığından, kimlik/kimlik doğrulama hizmeti, aşağıdaki diyagramda sarı renkle vurgulanmış şekilde API ağ geçitlerinden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="b5112-239">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![API ağ geçidinin altındaki kimlik mikro hizmetini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="b5112-241">**Şekil 6-39**.</span><span class="sxs-lookup"><span data-stu-id="b5112-241">**Figure 6-39**.</span></span> <span data-ttu-id="b5112-242">EShopOnContainers 'da kimlik hizmetinin konumu</span><span class="sxs-lookup"><span data-stu-id="b5112-242">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="b5112-243">Ancak, Ocelot Ayrıca, bu diğer diyagramda olduğu gibi, API Gateway sınırının içinde kimlik/auth mikro hizmetini de destekler.</span><span class="sxs-lookup"><span data-stu-id="b5112-243">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Bir Ocelot API ağ geçidinde kimlik doğrulamasını gösteren diyagram.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="b5112-245">**Şekil 6-40**.</span><span class="sxs-lookup"><span data-stu-id="b5112-245">**Figure 6-40**.</span></span> <span data-ttu-id="b5112-246">Ocelot 'de kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="b5112-246">Authentication in Ocelot</span></span>

<span data-ttu-id="b5112-247">Önceki diyagramda gösterildiği gibi, kimlik mikro hizmeti, API ağ geçidinin (AG) altında olduğunda, 1) AG, kimlik mikro hizmetinden bir kimlik doğrulama belirteci ister 2) kimlik doğrulama belirtecini kullanarak mikro hizmetlerden gelen bir kimlik doğrulaması belirteci 3-4 döndürür.</span><span class="sxs-lookup"><span data-stu-id="b5112-247">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="b5112-248">EShopOnContainers uygulaması, API ağ geçidini birden çok BFF (ön uç için arka uç) ve iş alanları API ağ geçitleri 'ne böldüğü için, çapraz kesme sorunları için ek bir API ağ geçidi oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5112-248">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="b5112-249">Bu seçenek, birden çok çapraz kesme sorunları olan mikro hizmetlere sahip daha karmaşık bir mikro hizmet tabanlı mimaride yer alan bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="b5112-249">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="b5112-250">EShopOnContainers 'da yalnızca bir çapraz kesme sorunu olduğundan, basitlik 'in sake 'SI için API ağ geçidi bölgesinden yalnızca güvenlik hizmetini işlemeye karar verdi.</span><span class="sxs-lookup"><span data-stu-id="b5112-250">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="b5112-251">Herhangi bir durumda, uygulama API ağ geçidi düzeyinde güvenli hale getirildiğinden, güvenli mikro hizmeti kullanmaya çalışırken Ocelot API ağ geçidinin kimlik doğrulama modülü ilk olarak ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-251">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="b5112-252">Bu, access_token ile korunan hizmetleri ziyaret edebilmeniz için erişim belirtecini almak üzere kimliği veya auth mikro hizmetini ziyaret etmek üzere HTTP isteğini yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="b5112-252">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="b5112-253">API ağ geçidi düzeyinde herhangi bir hizmette kimlik doğrulama ile güvenli hale getirmenin yolu, üzerinde configuration.jsilgili ayarlarındaki AuthenticationProviderKey ' i ayarlamadır.</span><span class="sxs-lookup"><span data-stu-id="b5112-253">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

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

<span data-ttu-id="b5112-254">Ocelot çalıştırıldığında, ReRoutes AuthenticationOptions. AuthenticationProviderKey öğesine bakar ve verilen anahtara kayıtlı bir kimlik doğrulama sağlayıcısı olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="b5112-254">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="b5112-255">Yoksa, Ocelot başlamacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5112-255">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="b5112-256">Varsa, yeniden yönlendirme bu sağlayıcıyı çalıştırıldığında kullanır.</span><span class="sxs-lookup"><span data-stu-id="b5112-256">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="b5112-257">Ocelot WebHost ile yapılandırıldığı için `authenticationProviderKey = "IdentityApiKey"` , bu hizmet kimlik doğrulama belirteci olmadan herhangi bir istek olduğunda kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="b5112-257">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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

<span data-ttu-id="b5112-258">Daha sonra, aşağıdaki sepet mikro hizmet denetleyicisi gibi mikro hizmetler gibi erişilecek herhangi bir kaynaktaki [Yetkilendir] özniteliğiyle yetkilendirmeyi de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="b5112-258">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="b5112-259">"Sepet" gibi Validaudide, `AddJwtBearer()` aşağıdaki kodda olduğu gibi başlangıç sınıfının ConfigureServices () ile birlikte her bir mikro hizmette tanımlanan hedef kitlelerle bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="b5112-259">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="b5112-260">Benzer bir API ağ geçidine dayanan bir yeniden yönlendirme URL 'SI olan sepet mikro hizmeti gibi, güvenli mikro hizmetlere erişmeyi denerseniz `http://localhost:5202/api/v1/b/basket/1` , geçerli bir belirteç sağlamadığınız takdirde bir 401 yetkisi alırsınız.</span><span class="sxs-lookup"><span data-stu-id="b5112-260">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="b5112-261">Öte yandan, bir yeniden yönlendirme URL 'SI doğrulandıysa, Ocelot kendisiyle ilişkili bir aşağı akış şemasını (iç mikro hizmet URL 'SI) çağırır.</span><span class="sxs-lookup"><span data-stu-id="b5112-261">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="b5112-262">**Ocelot 'nin ReRoutes katmanında yetkilendirme.**</span><span class="sxs-lookup"><span data-stu-id="b5112-262">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="b5112-263">Ocelot, kimlik doğrulamasından sonra değerlendirilen talep tabanlı yetkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="b5112-263">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="b5112-264">Yeniden yönlendirme yapılandırmasına aşağıdaki satırları ekleyerek bir rota düzeyinde yetkilendirme ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="b5112-264">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="b5112-265">Bu örnekte, yetkilendirme ara yazılımı çağrıldığında, kullanıcının belirteçte ' UserType ' talep türüne sahip olup olmadığını ve bu talebin değeri ' Employee ' olup olmadığını bulur.</span><span class="sxs-lookup"><span data-stu-id="b5112-265">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="b5112-266">Değilse, Kullanıcı yetkilendirilmez ve yanıt 403 olarak yasaklanmış olur.</span><span class="sxs-lookup"><span data-stu-id="b5112-266">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="b5112-267">Kubernetes ınress ve Ocelot API ağ geçitlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="b5112-267">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="b5112-268">Kubernetes (bir Azure Kubernetes hizmet kümesinde olduğu gibi) kullanılırken, genellikle tüm HTTP isteklerini *NGINX*temelinde [Kubernetes giriş katmanı](https://kubernetes.io/docs/concepts/services-networking/ingress/) üzerinden birleştirmişsinizdir.</span><span class="sxs-lookup"><span data-stu-id="b5112-268">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="b5112-269">Kubernetes 'te herhangi bir giriş yaklaşımı kullanmıyorsanız, hizmetlerinizin ve klarınızın IP 'Leri yalnızca küme ağı tarafından yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-269">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="b5112-270">Ancak, bir giriş yaklaşımı kullanıyorsanız Internet ve hizmetleriniz (API ağ geçitleriniz dahil) arasında bir orta katman ve ters proxy görevi gören bir orta katmanınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="b5112-270">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="b5112-271">Bir tanım olarak, giriş, gelen bağlantılara küme hizmetlerine ulaşmasına izin veren kuralların koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="b5112-271">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="b5112-272">Giriş genellikle hizmetlere dışarıdan erişilebilen URL 'Ler, Yük Dengeleme trafiği, SSL sonlandırma ve daha fazlası sağlamak üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="b5112-272">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="b5112-273">Kullanıcılar giriş kaynağını API sunucusuna naklederek giriş isteği ister.</span><span class="sxs-lookup"><span data-stu-id="b5112-273">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="b5112-274">EShopOnContainers 'da, yerel olarak geliştirilirken ve yalnızca bir geliştirme makinenizi Docker Konağı olarak kullanırken, yalnızca birden fazla API ağ geçidi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="b5112-274">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="b5112-275">Ancak, Kubernetes tabanlı bir "üretim" ortamını hedeflerken eShopOnContainers, API ağ geçitlerinin önünde bir giriş kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="b5112-275">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="b5112-276">Bu şekilde, istemciler yine de aynı temel URL 'YI çağırır, ancak istekler birden fazla API ağ geçidine veya BFF 'ye yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-276">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="b5112-277">API ağ geçitleri ön uçlardır veya façades, genellikle kendi kapsamlarından çıkan Web uygulamalarına değil, yalnızca hizmetlere yönelik olur.</span><span class="sxs-lookup"><span data-stu-id="b5112-277">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="b5112-278">Ayrıca, API ağ geçitleri bazı iç mikro hizmetleri gizleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b5112-278">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="b5112-279">Ancak giriş, HTTP isteklerini yeniden yönlendirse de herhangi bir mikro hizmeti veya Web uygulamasını gizlemeyi denememelidir.</span><span class="sxs-lookup"><span data-stu-id="b5112-279">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="b5112-280">Web uygulamalarının önündeki Kubernetes 'de bir giriş Nginx katmanına sahip olmak ve çeşitli Ocelot API ağ geçitleri/BFF, aşağıdaki diyagramda gösterildiği gibi ideal mimaridir.</span><span class="sxs-lookup"><span data-stu-id="b5112-280">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Bir giriş katmanının AKS ortamına nasıl uyduğunu gösteren bir diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="b5112-282">**Şekil 6-41**.</span><span class="sxs-lookup"><span data-stu-id="b5112-282">**Figure 6-41**.</span></span> <span data-ttu-id="b5112-283">Kubernetes 'e dağıtıldığında eShopOnContainers içindeki giriş katmanı</span><span class="sxs-lookup"><span data-stu-id="b5112-283">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="b5112-284">Kubernetes girişi, genellikle API ağ geçidi kapsamından çıkan Web uygulamaları dahil olmak üzere, uygulamaya yönelik tüm trafik için ters proxy görevi görür.</span><span class="sxs-lookup"><span data-stu-id="b5112-284">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="b5112-285">EShopOnContainers 'ı Kubernetes 'e dağıttığınızda, temel olarak yalnızca birkaç hizmet veya uç _nokta Ile URL_'lerde aşağıdaki postdüzeltmelerin listesini sunar:</span><span class="sxs-lookup"><span data-stu-id="b5112-285">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="b5112-286">`/` istemci SPA Web uygulaması için</span><span class="sxs-lookup"><span data-stu-id="b5112-286">`/` for the client SPA web application</span></span>
- <span data-ttu-id="b5112-287">`/webmvc` istemci MVC web uygulaması için</span><span class="sxs-lookup"><span data-stu-id="b5112-287">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="b5112-288">`/webstatus` durum/healthdenetimleri gösteren istemci Web uygulaması için</span><span class="sxs-lookup"><span data-stu-id="b5112-288">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="b5112-289">`/webshoppingapigw` Web BFF ve alışveriş iş süreçlerini</span><span class="sxs-lookup"><span data-stu-id="b5112-289">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="b5112-290">`/webmarketingapigw` Web BFF ve pazarlama iş işlemlerinde</span><span class="sxs-lookup"><span data-stu-id="b5112-290">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="b5112-291">`/mobileshoppingapigw` Mobil BFF ve alışveriş iş işlemlerinde</span><span class="sxs-lookup"><span data-stu-id="b5112-291">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="b5112-292">`/mobilemarketingapigw` Mobil BFF ve pazarlama iş işlemlerinde</span><span class="sxs-lookup"><span data-stu-id="b5112-292">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="b5112-293">Kubernetes 'e dağıtım yaparken, her Ocelot API ağ geçidi, API ağ geçitlerini çalıştıran her _Pod_ için farklı bir "configuration.json" dosyası kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="b5112-293">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="b5112-294">"configuration.json" dosyaları, ' Ocelot ' adlı bir Kubernetes _yapılandırma eşlemesi_ temel alınarak oluşturulan bir birimi bağlama tarafından sağlanır (başlangıçta deploy.ps1 betiği ile).</span><span class="sxs-lookup"><span data-stu-id="b5112-294">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="b5112-295">Her kapsayıcı, ilişkili yapılandırma dosyasını kapsayıcısının adlı kapsayıcı klasörüne bağlar `/app/configuration` .</span><span class="sxs-lookup"><span data-stu-id="b5112-295">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="b5112-296">EShopOnContainers kaynak kodu dosyalarında, özgün "configuration.json" dosyaları klasör içinde bulunabilir `k8s/ocelot/` .</span><span class="sxs-lookup"><span data-stu-id="b5112-296">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="b5112-297">Her BFF/APIGateway için bir dosya vardır.</span><span class="sxs-lookup"><span data-stu-id="b5112-297">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="b5112-298">Bir Ocelot API ağ geçidinde ek çapraz kesme özellikleri</span><span class="sxs-lookup"><span data-stu-id="b5112-298">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="b5112-299">Aşağıdaki bağlantılarda açıklanan bir Ocelot API ağ geçidi kullanırken araştırmak ve kullanmak için kullanabileceğiniz diğer önemli özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="b5112-299">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="b5112-300">**İstemci tarafında, Cell veya Eureka ile, Ocelot ile tümleştirme** </span><span class="sxs-lookup"><span data-stu-id="b5112-300">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="b5112-301">**API ağ geçidi katmanında önbelleğe alma** </span><span class="sxs-lookup"><span data-stu-id="b5112-301">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="b5112-302">**API ağ geçidi katmanında günlüğe kaydetme** </span><span class="sxs-lookup"><span data-stu-id="b5112-302">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="b5112-303">**API ağ geçidi katmanında hizmet kalitesi (yeniden denemeler ve devre kesiciler)** </span><span class="sxs-lookup"><span data-stu-id="b5112-303">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="b5112-304">**Hız sınırlandırma** </span><span class="sxs-lookup"><span data-stu-id="b5112-304">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="b5112-305">[Önceki](background-tasks-with-ihostedservice.md) 
>  [Sonraki](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="b5112-305">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
