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
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="baea0-103">Ocelot ile API Ağ Geçitleri Uygulayın</span><span class="sxs-lookup"><span data-stu-id="baea0-103">Implement API Gateways with Ocelot</span></span>

> [!IMPORTANT]
> <span data-ttu-id="baea0-104">Referans microservice uygulaması [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) şu anda elçi [tarafından](https://www.envoyproxy.io/) sunulan özellikleri yerine daha önce başvurulan [Ocelot](https://github.com/ThreeMammals/Ocelot)API Ağ Geçidi uygulamak için kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="baea0-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is currently using features provided by [Envoy](https://www.envoyproxy.io/) to implement the API Gateway instead of the earlier referenced [Ocelot](https://github.com/ThreeMammals/Ocelot).</span></span>
> <span data-ttu-id="baea0-105">Bu tasarım seçimini, Envoy'ın eShopOnContainers'da uygulanan yeni gRPC servisler arası iletişimin gerektirdiği WebSocket protokolüne verdiği yerleşik destek sayesinde yaptık.</span><span class="sxs-lookup"><span data-stu-id="baea0-105">We made this design choice because of Envoy's built-in support for the WebSocket protocol, required by the new gRPC inter-service communications implemented in eShopOnContainers.</span></span>
> <span data-ttu-id="baea0-106">Ancak, ocelot'u üretim sınıfı senaryolar için uygun basit, yetenekli ve hafif bir API Ağ Geçidi olarak düşünebilmeniz için kılavuzda bu bölümü koruduk.</span><span class="sxs-lookup"><span data-stu-id="baea0-106">However, we've retained this section in the guide so you can consider Ocelot as a simple, capable, and lightweight API Gateway suitable for production-grade scenarios.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="baea0-107">API Ağ geçitlerinizi tasarla ve tasarla</span><span class="sxs-lookup"><span data-stu-id="baea0-107">Architect and design your API Gateways</span></span>

<span data-ttu-id="baea0-108">Aşağıdaki mimari diyagram, API Ağ Geçitlerinin eShopOnContainers'da Ocelot ile nasıl uygulandığını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="baea0-108">The following architecture diagram shows how API Gateways were implemented with Ocelot in eShopOnContainers.</span></span>

![eShopOnContainers mimarisini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="baea0-110">**Şekil 6-28**.</span><span class="sxs-lookup"><span data-stu-id="baea0-110">**Figure 6-28**.</span></span> <span data-ttu-id="baea0-111">API Ağ Geçitleri ile eShopOnContainers mimarisi</span><span class="sxs-lookup"><span data-stu-id="baea0-111">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="baea0-112">Bu diyagram, tüm uygulamanın "Docker for Windows" veya "Docker for Mac" ile tek bir Docker ana bilgisayarına veya geliştirme bilgisayarına nasıl dağıtılanını gösterir.</span><span class="sxs-lookup"><span data-stu-id="baea0-112">That diagram shows how the whole application is deployed into a single Docker host or development PC with "Docker for Windows" or "Docker for Mac".</span></span> <span data-ttu-id="baea0-113">Ancak, herhangi bir orkestratöre dağıtmak benzer, ancak diyagramdaki herhangi bir kapsayıcı orkestratörde ölçeklendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-113">However, deploying into any orchestrator would be similar, but any container in the diagram could be scaled out in the orchestrator.</span></span>

<span data-ttu-id="baea0-114">Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıkları orkestratörden boşaltılmalı ve Azure SQL Veritabanı, Azure Cosmos DB, Azure Redis, Azure Hizmet Veri Mes'leri gibi altyapı için kullanılabilir yüksek sistemlere dağıtılmalıdır, veya herhangi bir HA kümeleme çözümü şirket içinde.</span><span class="sxs-lookup"><span data-stu-id="baea0-114">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="baea0-115">Diyagramda da fark edebilirsiniz, birkaç API Ağ Geçidi'ne sahip olmak, mikro hizmetlerini ve kendi ilgili API Ağ geçitlerini geliştirirken ve dağıtırken birden çok geliştirme ekibinin özerk olmasına (bu durumda Pazarlama özellikleri ve Alışveriş özellikleri) izin verir.</span><span class="sxs-lookup"><span data-stu-id="baea0-115">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="baea0-116">Tek bir monolitik API Ağ Geçidi varsa, bu uygulamanın tek bir parçası ile tüm mikro hizmetleri çift olabilir birkaç geliştirme ekipleri tarafından güncellenecek tek bir nokta anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="baea0-116">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="baea0-117">Tasarımda çok daha ileri gitmek, bazen ince taneli API Ağ Geçidi de seçilen mimariye bağlı olarak tek bir iş microservice ile sınırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-117">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="baea0-118">API Ağ Geçidi'nin sınırlarının işletme veya etki alanı tarafından dikte edilmiş olması, daha iyi bir tasarım elde etmenize yardımcı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="baea0-118">Having the API Gateway's boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="baea0-119">Örneğin, API Ağ Geçidi katmanındaki ince parçalılık, mikro hizmetlere dayalı daha gelişmiş kompozit Kullanıcı Arabirimi uygulamaları için özellikle yararlı olabilir, çünkü ince taneli API ağ geçidi kavramı kullanıcı arabirimi kompozisyon hizmetine benzer.</span><span class="sxs-lookup"><span data-stu-id="baea0-119">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="baea0-120">Biz [mikrohizmetlere dayalı kompozit ui oluşturma](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)önceki bölümde daha fazla ayrıntı içine dalmak.</span><span class="sxs-lookup"><span data-stu-id="baea0-120">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="baea0-121">Anahtar paket olarak, birçok orta ve büyük boyutlu uygulamalar için, özel olarak oluşturulmuş BIR API Ağ Geçidi ürünü kullanmak genellikle iyi bir yaklaşımdır, ancak API Ağ Geçidi birden fazla bağımsız izin vermedikçe tek bir monolitik toplayıcı veya benzersiz merkezi özel API Ağ Geçidi olarak değil özerk mikrohizmetler oluşturan çeşitli geliştirme ekipleri için yapılandırma alanları.</span><span class="sxs-lookup"><span data-stu-id="baea0-121">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-reroute-through-the-api-gateways"></a><span data-ttu-id="baea0-122">API Ağ Geçitleri üzerinden yeniden yönlendirmek için örnek mikro hizmetler/kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="baea0-122">Sample microservices/containers to reroute through the API Gateways</span></span>

<span data-ttu-id="baea0-123">Örnek olarak, eShopOnContainers aşağıdaki resimde gösterildiği gibi, API Ağ geçitleri aracılığıyla yayınlanması gereken yaklaşık altı dahili microservice türü vardır.</span><span class="sxs-lookup"><span data-stu-id="baea0-123">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Alt klasörlerini gösteren Hizmetler klasörünün ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="baea0-125">**Şekil 6-29**.</span><span class="sxs-lookup"><span data-stu-id="baea0-125">**Figure 6-29**.</span></span> <span data-ttu-id="baea0-126">Visual Studio'da eShopOnContainers çözümünde microservice klasörleri</span><span class="sxs-lookup"><span data-stu-id="baea0-126">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="baea0-127">Kimlik hizmeti hakkında, tasarımda API Ağ Geçidi yönlendirmesinin dışında bırakılır, çünkü sistemdeki tek çapraz kesme endişesidir, ancak Ocelot ile yeniden yönlendirme listelerinin bir parçası olarak eklemek de mümkündür.</span><span class="sxs-lookup"><span data-stu-id="baea0-127">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="baea0-128">Tüm bu hizmetler şu anda ASP.NET Core Web API hizmetleri olarak uygulanmaktadır, koddan da anlayabileceğiniz gibi.</span><span class="sxs-lookup"><span data-stu-id="baea0-128">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="baea0-129">Katalog mikrohizmet kodu gibi mikro hizmetlerden birine odaklanalım.</span><span class="sxs-lookup"><span data-stu-id="baea0-129">Let's focus on one of the microservices like the Catalog microservice code.</span></span>

![Catalog.API proje içeriğini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="baea0-131">**Şekil 6-30**.</span><span class="sxs-lookup"><span data-stu-id="baea0-131">**Figure 6-30**.</span></span> <span data-ttu-id="baea0-132">Örnek Web API microservice (Katalog microservice)</span><span class="sxs-lookup"><span data-stu-id="baea0-132">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="baea0-133">Katalog microservice'in, aşağıdaki koddaki gibi çeşitli denetleyicileri ve yöntemleri içeren tipik bir ASP.NET Core Web API projesi olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-133">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="baea0-134">HTTP isteği, mikrohizmet veritabanına ve gerekli herhangi bir ek eyleme erişen bu tür C# kodunu çalıştırarak sona erer.</span><span class="sxs-lookup"><span data-stu-id="baea0-134">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="baea0-135">Mikro hizmet URL'si ile ilgili olarak, kapsayıcılar yerel geliştirme pc 'nizde (yerel Docker ana bilgisayar) dağıtıldığında, her microservice konteyner her zaman bir dahili bağlantı noktası (genellikle port 80) dockerfile belirtilen, aşağıdaki dockerfile olduğu gibi:</span><span class="sxs-lookup"><span data-stu-id="baea0-135">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice's container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="baea0-136">Kodda gösterilen bağlantı noktası 80, Docker ana bilgisayar içinde dahili olduğundan, istemci uygulamaları tarafından ulaşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="baea0-136">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="baea0-137">İstemci uygulamaları, `docker-compose`dağıtılırken yalnızca harici bağlantı noktalarına (varsa) erişebilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-137">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="baea0-138">Bu dış bağlantı noktaları, üretim ortamına dağıtılırken yayımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="baea0-138">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="baea0-139">Bu nedenle, istemci uygulamaları ve mikro hizmetler arasındaki doğrudan iletişimi önlemek için API Ağ Geçidi'ni kullanmak istiyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="baea0-139">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="baea0-140">Ancak, geliştirirken, microservice /konteyner doğrudan erişmek ve Swagger üzerinden çalıştırmak istiyorum.</span><span class="sxs-lookup"><span data-stu-id="baea0-140">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="baea0-141">Bu nedenle eShopOnContainers'da, harici bağlantı noktaları API Ağ Geçidi veya istemci uygulamaları tarafından kullanılmayacak olsa bile yine de belirtilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-141">That's why in eShopOnContainers, the external ports are still specified even when they won't be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="baea0-142">Katalog microservice için `docker-compose.override.yml` dosyanın bir örneği aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="baea0-142">Here's an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

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

<span data-ttu-id="baea0-143">Docker-compose.override.yml yapılandırmasında Katalog kapsayıcısının iç bağlantı noktasının bağlantı noktası 80 olduğunu, ancak dış erişim bağlantı noktasının 5101 olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-143">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="baea0-144">Ancak bu bağlantı noktası, bir API Ağ Geçidi kullanırken uygulama tarafından kullanılmamalı, yalnızca hata ayıklamak, çalıştırmak ve yalnızca Katalog mikro hizmetini test etmek için kullanılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="baea0-144">But this port shouldn't be used by the application when using an API Gateway, only to debug, run, and test just the Catalog microservice.</span></span>

<span data-ttu-id="baea0-145">Normalde, mikro hizmetler için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir orkestratör olduğundan, docker-compose ile üretim ortamına dağıtım yapmazsınız.</span><span class="sxs-lookup"><span data-stu-id="baea0-145">Normally, you won't be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="baea0-146">Bu ortamlara dağıtırken, mikro hizmetler için doğrudan herhangi bir dış bağlantı noktası yayımlamayacağınız, ancak API Ağ Geçidi'ndeki ters proxy'yi her zaman kullanacağınız farklı yapılandırma dosyaları kullanırsınız.</span><span class="sxs-lookup"><span data-stu-id="baea0-146">When deploying to those environments you use different configuration files where you won't publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="baea0-147">Katalog microservice'i yerel Docker ana bilgisayarevinizde çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="baea0-147">Run the catalog microservice in your local Docker host.</span></span> <span data-ttu-id="baea0-148">Visual Studio'dan tam eShopOnContainers çözümünü çalıştırın (docker-compose dosyalarındaki tüm hizmetleri çalıştırın) veya cmd veya PowerShell'de yer alan klasörde `docker-compose.override.yml` konumlandırılmış aşağıdaki docker-compose komutuyla Katalog mikrohizmetini başlatın. `docker-compose.yml`</span><span class="sxs-lookup"><span data-stu-id="baea0-148">Either run the full eShopOnContainers solution from Visual Studio (it runs all the services in the docker-compose files), or start the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and `docker-compose.override.yml` are placed.</span></span>

```console
docker-compose run --service-ports catalog-api
```

<span data-ttu-id="baea0-149">Bu komut yalnızca docker-compose.yml'de belirtilen katalog-api hizmet kapsayıcısını ve bağımlılıkları çalıştırUr.</span><span class="sxs-lookup"><span data-stu-id="baea0-149">This command only runs the catalog-api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="baea0-150">Bu durumda, SQL Server kapsayıcı ve RabbitMQ kapsayıcı.</span><span class="sxs-lookup"><span data-stu-id="baea0-150">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="baea0-151">Daha sonra, doğrudan Katalog microservice erişebilir ve Swagger UI üzerinden doğrudan bu "dış" bağlantı `http://localhost:5101/swagger`noktası üzerinden erişen yöntemleri ni görebilirsiniz, bu durumda:</span><span class="sxs-lookup"><span data-stu-id="baea0-151">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that "external" port, in this case `http://localhost:5101/swagger`:</span></span>

![Catalog.API REST API'yi gösteren Swagger UI ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="baea0-153">**Şekil 6-31**.</span><span class="sxs-lookup"><span data-stu-id="baea0-153">**Figure 6-31**.</span></span> <span data-ttu-id="baea0-154">Swagger UI ile Katalog microservice test</span><span class="sxs-lookup"><span data-stu-id="baea0-154">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="baea0-155">Bu noktada Visual Studio'da C# kodunda bir kırılma noktası ayarlayabilir, mikro hizmeti Swagger UI'de açığa `docker-compose down` çıkan yöntemlerle test edebilir ve son olarak komutla her şeyi temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-155">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="baea0-156">Ancak, bu durumda harici bağlantı noktası 5101 üzerinden mikro hizmete doğrudan erişim iletişimi, tam olarak uygulamanızda kaçınmak istediğiniz şeydir.</span><span class="sxs-lookup"><span data-stu-id="baea0-156">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="baea0-157">Ve api ağ geçidi (Ocelot, bu durumda) yönlendirme ek düzeyini ayarlayarak bunu önleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-157">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="baea0-158">Bu şekilde, istemci uygulaması mikro hizmete doğrudan erişmez.</span><span class="sxs-lookup"><span data-stu-id="baea0-158">That way, the client app won't directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="baea0-159">ApI Ağ Geçitlerinizi Ocelot ile uygulama</span><span class="sxs-lookup"><span data-stu-id="baea0-159">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="baea0-160">Ocelot temelde belirli bir sırada uygulayabilirsiniz middlewares bir dizi.</span><span class="sxs-lookup"><span data-stu-id="baea0-160">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="baea0-161">Ocelot sadece ASP.NET Core ile çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="baea0-161">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="baea0-162">Paketin en son sürümü `.NETCoreApp 3.1` hedefler ve bu nedenle .NET Framework uygulamaları için uygun değildir.</span><span class="sxs-lookup"><span data-stu-id="baea0-162">The latest version of the package targets `.NETCoreApp 3.1` and hence it is not suitable for .NET Framework applications.</span></span>

<span data-ttu-id="baea0-163">Ocelot'un NuGet paketi ile Visual [Studio'dan ocelot'u](https://www.nuget.org/packages/Ocelot/)ve bağımlılıklarını ASP.NET Core projenizde yüklüyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="baea0-163">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="baea0-164">eShopOnContainers olarak, onun API Ağ Geçidi uygulaması basit bir ASP.NET Core WebHost proje ve Ocelot's middleware aşağıdaki resimde gösterildiği gibi, tüm API Ağ Geçidi özellikleri işler:</span><span class="sxs-lookup"><span data-stu-id="baea0-164">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middleware handles all the API Gateway features, as shown in the following image:</span></span>

![Ocelot API ağ geçidi projesini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="baea0-166">**Şekil 6-32**.</span><span class="sxs-lookup"><span data-stu-id="baea0-166">**Figure 6-32**.</span></span> <span data-ttu-id="baea0-167">eShopOnContainers OcelotApiGw temel proje</span><span class="sxs-lookup"><span data-stu-id="baea0-167">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="baea0-168">Bu ASP.NET Core WebHost proje temelde iki `Program.cs` `Startup.cs`basit dosyaları ile inşa edilmiştir: ve .</span><span class="sxs-lookup"><span data-stu-id="baea0-168">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="baea0-169">Program.cs sadece oluşturmak ve Core BuildWebHost ASP.NET tipik yapılandırmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="baea0-169">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="baea0-170">Ocelot için burada önemli `configuration.json` `AddJsonFile()` nokta, yöntem aracılığıyla oluşturucuya sağlamanız gereken dosyadır.</span><span class="sxs-lookup"><span data-stu-id="baea0-170">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="baea0-171">Tüm `configuration.json` API Ağ Geçidi Rotalarını, yani belirli bağlantı noktalarına sahip dış uç noktaları ve genellikle farklı bağlantı noktalarını kullanarak ilişkili iç uç noktaları burada belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-171">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="baea0-172">Yapılandırmanın iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="baea0-172">There are two sections to the configuration.</span></span> <span data-ttu-id="baea0-173">Bir dizi ReRoutes ve GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="baea0-173">An array of ReRoutes and a GlobalConfiguration.</span></span> <span data-ttu-id="baea0-174">Rotalar, Ocelot'a bir akış yukarı isteği nasıl ele alsüreceğini söyleyen nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="baea0-174">The ReRoutes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="baea0-175">Global yapılandırma, ReRoute belirli ayarlarının geçersiz kılmasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="baea0-175">The Global configuration allows overrides of ReRoute specific settings.</span></span> <span data-ttu-id="baea0-176">Çok sayıda ReRoute özel ayarını yönetmek istemiyorsanız kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="baea0-176">It's useful if you don't want to manage lots of ReRoute specific settings.</span></span>

<span data-ttu-id="baea0-177">Burada eShopOnContainers gelen API Ağ Geçitleri birinden [ReRoute yapılandırma dosyasıbasitleştirilmiş](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) bir örnek.</span><span class="sxs-lookup"><span data-stu-id="baea0-177">Here's a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

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

<span data-ttu-id="baea0-178">Ocelot API Ağ Geçidi'nin temel işlevi, gelen HTTP isteklerini almak ve bunları şu anda başka bir HTTP isteği olarak bir aşağı hizmete iletmektir.</span><span class="sxs-lookup"><span data-stu-id="baea0-178">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="baea0-179">Ocelot's, bir isteğin diğerine yönlendirildiğini Yeniden Yönlendirme olarak tanımlar.</span><span class="sxs-lookup"><span data-stu-id="baea0-179">Ocelot's describes the routing of one request to another as a ReRoute.</span></span>

<span data-ttu-id="baea0-180">Örneğin, yukarıdan configuration.json'daki ReRoutes'lardan birine odaklanalım, Sepet mikrohizmetinin yapılandırmasına.</span><span class="sxs-lookup"><span data-stu-id="baea0-180">For instance, let's focus on one of the ReRoutes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

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

<span data-ttu-id="baea0-181">DownstreamPathTemplate, Düzeni ve DownstreamHostAndPorts bu istek iletilecek dahili microservice URL olun.</span><span class="sxs-lookup"><span data-stu-id="baea0-181">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="baea0-182">Bağlantı noktası, hizmet tarafından kullanılan iç bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="baea0-182">The port is the internal port used by the service.</span></span> <span data-ttu-id="baea0-183">Kapsayıcılar kullanılırken, bağlantı noktası dockerdosyasında belirtilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-183">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="baea0-184">Bu, `Host` kullanmakta olduğunuz hizmet adı çözümlemesi bağlıdır bir hizmet adıdır.</span><span class="sxs-lookup"><span data-stu-id="baea0-184">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="baea0-185">Docker-compose kullanırken, hizmet adları Docker Host tarafından sağlanır, docker-compose dosyalarında sağlanan hizmet adlarını kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="baea0-185">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="baea0-186">Kubernetes veya Service Fabric gibi bir orkestratör kullanıyorsanız, bu ad dns veya her orchestrator tarafından sağlanan ad çözünürlüğü ile çözülmelidir.</span><span class="sxs-lookup"><span data-stu-id="baea0-186">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="baea0-187">DownstreamHostAndPorts istekleri iletmek istediğiniz herhangi bir downstream hizmetlerin ana bilgisayar ve bağlantı noktası içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="baea0-187">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="baea0-188">Genellikle bu sadece bir giriş içerir, ancak bazen alt akım hizmetleri ve Ocelot birden fazla giriş eklemek ve sonra bir yük dengeleyici seçmenize olanak sağlar bakiye istekleri yüklemek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-188">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="baea0-189">Ancak Azure ve herhangi bir orkestratör kullanıyorsanız, bulut ve orkestratör altyapısıyla dengeyi yüklemek muhtemelen daha iyi bir fikirdir.</span><span class="sxs-lookup"><span data-stu-id="baea0-189">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="baea0-190">UpstreamPathTemplate, Ocelot'un istemciden belirli bir istek için hangi DownstreamPathTemplate'in kullanılacağını belirlemek için kullanacağı URL'dir.</span><span class="sxs-lookup"><span data-stu-id="baea0-190">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="baea0-191">Son olarak, UpstreamHttpMethod, Ocelot'un farklı istekleri (GET, POST, PUT) ile aynı URL'yi ayırt edebilmeleri için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="baea0-191">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="baea0-192">Bu noktada, tek bir Ocelot API Ağ Geçidi (ASP.NET Core WebHost) bir veya [birden çok birleştirilmiş configuration.json dosyaları](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) kullanarak olabilir veya aynı zamanda bir Konsolos [KV deposunda yapılandırma](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-192">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="baea0-193">Ama mimari ve tasarım bölümlerinde tanıtıldı, eğer gerçekten özerk mikro hizmetlere sahip olmak istiyorsanız, birden fazla API Ağ Geçidi ve / veya BFF (Frontend için Backend) içine tek monolitik API Ağ Geçidi bölmek için daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-193">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="baea0-194">Bu amaçla, docker konteynerleri ile bu yaklaşımı nasıl uygulayacağını görelim.</span><span class="sxs-lookup"><span data-stu-id="baea0-194">For that purpose, let's see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="baea0-195">Birden çok farklı API Ağ Geçidi / BFF kapsayıcı türleri çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanma</span><span class="sxs-lookup"><span data-stu-id="baea0-195">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="baea0-196">eShopOnContainers olarak, Ocelot API Ağ Geçidi ile tek bir Docker konteyner görüntü kullanıyoruz ama sonra, çalışma zamanında, her hizmet için farklı bir PC klasörüne erişmek için bir docker hacmi kullanarak, farklı bir configuration.json dosyası sağlayarak API-Gateway/BFF her türü için farklı hizmetler / kapsayıcılar oluşturmak.</span><span class="sxs-lookup"><span data-stu-id="baea0-196">In eShopOnContainers, we're using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Tüm API ağ geçitleri için tek bir Ocelot ağ geçidi Docker görüntüsünün diyagramı.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="baea0-198">**Şekil 6-33**.</span><span class="sxs-lookup"><span data-stu-id="baea0-198">**Figure 6-33**.</span></span> <span data-ttu-id="baea0-199">Birden çok API Ağ Geçidi türünde tek bir Ocelot Docker görüntüsünü yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="baea0-199">Reusing a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="baea0-200">eShopOnContainers olarak, "Generic Ocelot API Gateway Docker Image" proje 'OcelotApiGw' ve görüntü adı "eshop/ ocelotapigw" docker-compose.yml dosyasında belirtilen adlı oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="baea0-200">In eShopOnContainers, the "Generic Ocelot API Gateway Docker Image" is created with the project named 'OcelotApiGw' and the image name "eshop/ocelotapigw" that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="baea0-201">Daha sonra, Docker'a dağıtılırken, docker-compose.yml dosyasından aşağıdaki ekstrede gösterildiği gibi, aynı Docker görüntüsünden oluşturulan dört API-Ağ Geçidi kapsayıcısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="baea0-201">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

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

<span data-ttu-id="baea0-202">Ayrıca, aşağıdaki docker-compose.override.yml dosyasında da görebileceğiniz gibi, bu API Ağ Geçidi kapsayıcıları arasındaki tek fark, her hizmet kapsayıcısı için farklı olan Ocelot yapılandırma dosyasıdır ve çalışma zamanında Docker hacmi.</span><span class="sxs-lookup"><span data-stu-id="baea0-202">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

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

<span data-ttu-id="baea0-203">Bu önceki kod nedeniyle ve aşağıdaki Visual Studio Explorer'da gösterildiği gibi, her bir iş /BFF API Ağ Geçidi tanımlamak için gereken tek dosya yalnızca bir configuration.json dosyasıdır, çünkü dört API Ağ Geçidi aynı Docker görüntüsünü temel alır.</span><span class="sxs-lookup"><span data-stu-id="baea0-203">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Configuration.json dosyalarıyla tüm API ağ geçitlerini gösteren ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="baea0-205">**Şekil 6-34**.</span><span class="sxs-lookup"><span data-stu-id="baea0-205">**Figure 6-34**.</span></span> <span data-ttu-id="baea0-206">Ocelot ile her API Ağ Geçidi / BFF tanımlamak için gerekli tek dosya bir yapılandırma dosyasıdır</span><span class="sxs-lookup"><span data-stu-id="baea0-206">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="baea0-207">API Ağ Geçidi'ni birden çok API Ağ Geçidine bölerek, farklı mikro hizmetler alt kümelerine odaklanan farklı geliştirme ekipleri, bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitlerini yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-207">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="baea0-208">Ayrıca, aynı zamanda aynı Ocelot Docker görüntüsünü yeniden kullanabilirler.</span><span class="sxs-lookup"><span data-stu-id="baea0-208">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="baea0-209">Şimdi, API Ağ geçitleri ile eShopOnContainers çalıştırırsanız (eShopOnContainers-ServicesAndWebApps.sln çözüm açarken veya çalışan "docker-compose" vs varsayılan olarak dahil), aşağıdaki örnek yolları gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-209">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running "docker-compose up"), the following sample routes will be performed.</span></span>

<span data-ttu-id="baea0-210">Örneğin, webshoppingapigw `http://localhost:5202/api/v1/c/catalog/items/2/` API Ağ Geçidi tarafından sunulan akış yukarı URL'yi ziyaret ettiğinizde, `http://catalog-api/api/v1/2` aynı sonucu aşağıdaki tarayıcıda olduğu gibi Docker ana bilgisayar içindeki dahili Downstream URL'sinden alırsınız.</span><span class="sxs-lookup"><span data-stu-id="baea0-210">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog-api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![API ağ geçidinden geçen bir yanıtı gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="baea0-212">**Şekil 6-35**.</span><span class="sxs-lookup"><span data-stu-id="baea0-212">**Figure 6-35**.</span></span> <span data-ttu-id="baea0-213">API Ağ Geçidi tarafından sağlanan bir URL üzerinden bir mikro hizmete erişme</span><span class="sxs-lookup"><span data-stu-id="baea0-213">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="baea0-214">Test veya hata ayıklama nedenleriyle, API Ağ Geçidi'nden geçmeden Katalog Docker kapsayıcısına (yalnızca geliştirme ortamında) doğrudan erişmek istiyorsanız, 'catalog-api' Docker ana bilgisayara dahil olan bir DNS çözünürlüğü olduğundan (docker-compose servis adlarıyla işlenen hizmet keşfi), konteynere doğrudan erişmenin `http://localhost:5101/api/v1/Catalog/items/1` tek yolu docker-compose.override.yml'de yayınlanan ve yalnızca geliştirme testleri için sağlanan dış bağlantı noktasından geçer.</span><span class="sxs-lookup"><span data-stu-id="baea0-214">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog-api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Catalog.api'ye doğrudan yanıt gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="baea0-216">**Şekil 6-36**.</span><span class="sxs-lookup"><span data-stu-id="baea0-216">**Figure 6-36**.</span></span> <span data-ttu-id="baea0-217">Test amacıyla bir mikro hizmete doğrudan erişim</span><span class="sxs-lookup"><span data-stu-id="baea0-217">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="baea0-218">Ancak uygulama, doğrudan bağlantı noktası "kısayollar" olsa da, API Ağ geçitleri üzerinden tüm mikro hizmetlere erişebilmek için yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="baea0-218">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port "shortcuts".</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="baea0-219">eShopOnContainers ağ geçidi toplama deseni</span><span class="sxs-lookup"><span data-stu-id="baea0-219">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="baea0-220">Daha önce de tanıtıldığı gibi, istekleri toplama uygulamak için esnek bir yol, kod, özel hizmetler ile.</span><span class="sxs-lookup"><span data-stu-id="baea0-220">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="baea0-221">[Ayrıca Ocelot İstek Toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)ile istek toplama uygulayabilirsiniz , ancak ihtiyacınız kadar esnek olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-221">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="baea0-222">Bu nedenle, eShopOnContainers toplama uygulamak için seçilen yolu her toplayıcı için açık bir ASP.NET Core Web API hizmeti ile.</span><span class="sxs-lookup"><span data-stu-id="baea0-222">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API service for each aggregator.</span></span>

<span data-ttu-id="baea0-223">Bu yaklaşıma göre, API Ağ Geçidi kompozisyon diyagramı, daha önce gösterilen basitleştirilmiş küresel mimari diyagramında gösterilmeyen toplayıcı hizmetleri göz önüne alındığında gerçekte biraz daha genişletilmiştir.</span><span class="sxs-lookup"><span data-stu-id="baea0-223">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="baea0-224">Aşağıdaki diyagramda, toplayıcı hizmetlerin ilgili API Ağ geçitleriyle nasıl çalıştığını da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-224">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Toplayıcı hizmetlerini gösteren eShopOnContainers mimarisinin diyagramı.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="baea0-226">**Şekil 6-37**.</span><span class="sxs-lookup"><span data-stu-id="baea0-226">**Figure 6-37**.</span></span> <span data-ttu-id="baea0-227">toplayıcı hizmetleri ile eShopOnContainers mimarisi</span><span class="sxs-lookup"><span data-stu-id="baea0-227">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="baea0-228">Daha fazla yakınlaştırma, aşağıdaki resimde "Alışveriş" iş alanında, istemci uygulamaları ve mikro hizmetler arasındaki gevezelik API Ağ Geçitleri'nde toplayıcı hizmetleri kullanırken azalır görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-228">Zooming in further, on the "Shopping" business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![eShopOnContainers mimarisini gösteren diyagram yakınlaştırın.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="baea0-230">**Şekil 6-38**.</span><span class="sxs-lookup"><span data-stu-id="baea0-230">**Figure 6-38**.</span></span> <span data-ttu-id="baea0-231">Toplayıcı hizmetlerinin vizyonunu yakınlaştırın</span><span class="sxs-lookup"><span data-stu-id="baea0-231">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="baea0-232">Diyagram, API Ağ Geçitlerinden gelen olası istekleri gösterdiğinde karmaşık hale nasıl geldiğini fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-232">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get complex.</span></span> <span data-ttu-id="baea0-233">Mavi okların, istemci uygulamaları açısından nasıl basitleştirileceğini görebilseniz de, iletişimdeki gevezeliği ve gecikmeyi azaltarak toplayıcı deseni kullanırken, sonuçta uzak uygulamalar için kullanıcı deneyimini önemli ölçüde geliştirebilirsiniz ( mobil ve SPA uygulamaları), özellikle.</span><span class="sxs-lookup"><span data-stu-id="baea0-233">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="baea0-234">"Pazarlama" iş alanı ve mikrohizmetler söz konusu olduğunda, basit bir kullanım örneğidir, bu nedenle toplayıcılar kullanmaya gerek yoktur, ancak gerekirse da mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-234">In the case of the "Marketing" business area and microservices, it is a simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="baea0-235">Ocelot API Ağ Geçitlerinde kimlik doğrulama ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="baea0-235">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="baea0-236">Ocelot API Ağ Geçidi'nde, API Ağ Geçidi'nin dışında veya içinde auth belirteci sağlayan [IdentityServer'ı](https://identityserver.io/) kullanarak ASP.NET Core Web API hizmeti gibi kimlik doğrulama hizmetini oturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-236">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="baea0-237">eShopOnContainers BFF ve iş alanlarına dayalı sınırları olan birden fazla API Ağ Geçidi kullandığından, Kimlik/Auth hizmeti aşağıdaki diyagramda sarı renkte vurgulandığı gibi API Ağ Geçitlerinin dışında bırakılır.</span><span class="sxs-lookup"><span data-stu-id="baea0-237">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![API ağ geçidinin altındaki Kimlik mikro hizmetini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="baea0-239">**Şekil 6-39**.</span><span class="sxs-lookup"><span data-stu-id="baea0-239">**Figure 6-39**.</span></span> <span data-ttu-id="baea0-240">eShopOnContainers kimlik hizmetinin konumu</span><span class="sxs-lookup"><span data-stu-id="baea0-240">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="baea0-241">Ancak, Ocelot da API Ağ Geçidi sınırı içinde Kimlik / Auth microservice oturan destekler, bu diğer diyagramda olduğu gibi.</span><span class="sxs-lookup"><span data-stu-id="baea0-241">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Ocelot API Ağ Geçidi'nde kimlik doğrulamayı gösteren diyagram.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="baea0-243">**Şekil 6-40.**</span><span class="sxs-lookup"><span data-stu-id="baea0-243">**Figure 6-40**.</span></span> <span data-ttu-id="baea0-244">Ocelot'ta kimlik doğrulama</span><span class="sxs-lookup"><span data-stu-id="baea0-244">Authentication in Ocelot</span></span>

<span data-ttu-id="baea0-245">Önceki diyagramda görüldüğü gibi, Kimlik microservice API ağ geçidi (AG) altında olduğunda: 1) AG kimlik microservice bir auth belirteç istekleri, 2) Kimlik microservice ag, 3-4) AG isteklerini auth belirteci kullanarak microservices döner.</span><span class="sxs-lookup"><span data-stu-id="baea0-245">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="baea0-246">eShopOnContainers uygulaması birden fazla BFF (Frontend için Backend) ve iş alanları API Ağ Geçitleri içine API Ağ Geçidi bölünmüş olduğundan, başka bir seçenek çapraz kesme endişeleri için ek bir API Ağ Geçidi oluşturmak olurdu.</span><span class="sxs-lookup"><span data-stu-id="baea0-246">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would have been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="baea0-247">Bu seçim, birden fazla çapraz kesme endişeleri microservices ile daha karmaşık bir microservice tabanlı mimari adil olacaktır.</span><span class="sxs-lookup"><span data-stu-id="baea0-247">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="baea0-248">eShopOnContainers sadece bir çapraz kesme endişe olduğundan, sadece api Gateway bölge dışında güvenlik hizmeti işlemek için karar verildi, basitlik uğruna.</span><span class="sxs-lookup"><span data-stu-id="baea0-248">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity's sake.</span></span>

<span data-ttu-id="baea0-249">Her durumda, uygulama API Ağ Geçidi düzeyinde güvenli ise, güvenli bir microservice kullanmaya çalışırken ilk başta Ocelot API Ağ Geçidi kimlik doğrulama modülü ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-249">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="baea0-250">Bu, access_token ile korunan hizmetleri ziyaret edebilirsiniz böylece erişim belirteci almak için Kimlik veya auth microservice ziyaret etmek için HTTP isteği yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="baea0-250">That redirects the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="baea0-251">API Ağ Geçidi düzeyindeki herhangi bir hizmeti kimlik doğrulamayla güvence altına almanın yolu, AuthenticationProviderKey'i configuration.json'daki ilgili ayarlarında ayarlayarak elde edilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-251">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

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

<span data-ttu-id="baea0-252">Ocelot çalıştığında, ReRoutes AuthenticationOptions.AuthenticationProviderKey'e bakar ve verilen anahtara kayıtlı bir Kimlik Doğrulama Sağlayıcısı olup olmadığını denetler.</span><span class="sxs-lookup"><span data-stu-id="baea0-252">When Ocelot runs, it will look at the ReRoutes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="baea0-253">Eğer yoksa, Ocelot başlamaz.</span><span class="sxs-lookup"><span data-stu-id="baea0-253">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="baea0-254">Varsa, Yeniden Yönlendirme bu sağlayıcıyı çalıştırdığında kullanır.</span><span class="sxs-lookup"><span data-stu-id="baea0-254">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="baea0-255">Çünkü Ocelot WebHost ile yapılandırılır `authenticationProviderKey = "IdentityApiKey"`, bu hizmet herhangi bir auth belirteç olmadan herhangi bir istek olduğunda kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="baea0-255">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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

<span data-ttu-id="baea0-256">Ardından, aşağıdaki Sepet mikro hizmet denetleyicisi gibi mikro hizmetler gibi erişilecek herhangi bir kaynağa [Authorize] özniteliği ile yetkilendirme ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="baea0-256">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="baea0-257">"Sepet" gibi Geçerli Hedef Kitleler, aşağıdaki kodda olduğu `AddJwtBearer()` gibi Başlangıç sınıfının ConfigureServices() adresindeki her bir mikro hizmette tanımlanan hedef kitleyle ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="baea0-257">The ValidAudiences such as "basket" are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="baea0-258">API Ağ Geçidi'ne dayalı bir ReRoute URL'si olan Sepet mikrohizmeti `http://localhost:5202/api/v1/b/basket/1`gibi güvenli bir mikro hizmete erişmeye çalışırsanız, geçerli bir belirteç sağlamadığınız sürece 401 Yetkisiz alırsınız.</span><span class="sxs-lookup"><span data-stu-id="baea0-258">If you try to access any secured microservice, like the Basket microservice with a ReRoute URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you'll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="baea0-259">Diğer taraftan, bir ReRoute URL'si kimlik doğrulanırsa, Ocelot onunla ilişkili ne olursa olsun aşağı akış düzenini (dahili microservice URL'si) çağırır.</span><span class="sxs-lookup"><span data-stu-id="baea0-259">On the other hand, if a ReRoute URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="baea0-260">**Ocelot'un Rotalar katmanında yetkilendirme.**</span><span class="sxs-lookup"><span data-stu-id="baea0-260">**Authorization at Ocelot's ReRoutes tier.**</span></span>  <span data-ttu-id="baea0-261">Ocelot, kimlik doğrulamadan sonra değerlendirilen taleplere dayalı yetkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="baea0-261">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="baea0-262">ReRoute yapılandırmasına aşağıdaki satırları ekleyerek yetkilendirmeyi rota düzeyinde ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="baea0-262">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="baea0-263">Bu örnekte, yetkilendirme ara ware çağrıldığında, Ocelot kullanıcının belirteci 'UserType' talep türüne sahip olup olmadığını ve bu talebin değerinin 'çalışan' olup olmadığını bulur.</span><span class="sxs-lookup"><span data-stu-id="baea0-263">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="baea0-264">Değilse, kullanıcı yetkilendirilmeyecek ve yanıt 403 yasak olacaktır.</span><span class="sxs-lookup"><span data-stu-id="baea0-264">If it isn't, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="baea0-265">Kubernetes Ingress artı Ocelot API Ağ Geçitlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="baea0-265">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="baea0-266">Kubernetes kullanırken (Azure Kubernetes Hizmet kümesinde olduğu gibi), genellikle Tüm HTTP isteklerini *Nginx'e*dayalı [Kubernetes Ingress katmanı](https://kubernetes.io/docs/concepts/services-networking/ingress/) üzerinden biraraya bilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-266">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="baea0-267">Kubernetes'te, herhangi bir giriş yaklaşımı kullanmıyorsanız, hizmetleriniz ve bölmelerinizde yalnızca küme ağı tarafından epi'ler vardır.</span><span class="sxs-lookup"><span data-stu-id="baea0-267">In Kubernetes, if you don't use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="baea0-268">Ancak giriş yaklaşımı kullanırsanız, Internet ve hizmetleriniz (API Ağ geçitleriniz dahil) arasında bir orta katman alabilirsiniz ve ters proxy olarak hareket elabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="baea0-268">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="baea0-269">Tanım olarak, Giriş, gelen bağlantıların küme hizmetlerine erişmesine izin veren kurallar topluluğudur.</span><span class="sxs-lookup"><span data-stu-id="baea0-269">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="baea0-270">Giriş genellikle harici olarak erişilebilen URL'ler, yük dengesi trafiği, SSL sonlandırma ve daha fazlasını sağlayacak şekilde yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="baea0-270">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="baea0-271">Kullanıcılar Giriş kaynağını API sunucusuna göndererek giriş isteğinde bulunarak.</span><span class="sxs-lookup"><span data-stu-id="baea0-271">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="baea0-272">eShopOnContainers, yerel olarak gelişmekte ve Docker ana bilgisayar olarak sadece geliştirme makinesi kullanırken, herhangi bir giriş değil, sadece birden fazla API Ağ Geçitleri kullanıyorsunuz.</span><span class="sxs-lookup"><span data-stu-id="baea0-272">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="baea0-273">Ancak, Kubernetes dayalı bir "üretim" ortamı hedeflenirken, eShopOnContainers API ağ geçitleri önünde bir giriş kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="baea0-273">However, when targeting a "production" environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="baea0-274">Bu şekilde, istemciler hala aynı temel URL'yi arar, ancak istekler birden çok API Ağ Geçidi'ne veya BFF'ye yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-274">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="baea0-275">API Ağ geçitleri, yalnızca hizmetleri yüzeye çıkaran ön uçlar veya cephelerdir, ancak genellikle kapsam dışında olan web uygulamaları değildir.</span><span class="sxs-lookup"><span data-stu-id="baea0-275">API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="baea0-276">Buna ek olarak, API Ağ Geçitleri bazı dahili mikro hizmetleri gizleyebilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-276">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="baea0-277">Giriş, ancak, sadece HTTP isteklerini yönlendirme ama herhangi bir microservice veya web uygulaması gizlemek için çalışıyor değil.</span><span class="sxs-lookup"><span data-stu-id="baea0-277">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="baea0-278">Web uygulamaları artı birkaç Ocelot API Ağ Geçitleri / BFF önünde Kubernetes bir giriş Nginx katmanı olması ideal bir mimari, aşağıdaki diyagramda gösterildiği gibi.</span><span class="sxs-lookup"><span data-stu-id="baea0-278">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Giriş katmanının AKS ortamına nasıl uyduğunu gösteren bir diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="baea0-280">**Şekil 6-41**.</span><span class="sxs-lookup"><span data-stu-id="baea0-280">**Figure 6-41**.</span></span> <span data-ttu-id="baea0-281">Kubernetes'e dağıtıldığında eShopOnContainers'daki giriş katmanı</span><span class="sxs-lookup"><span data-stu-id="baea0-281">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="baea0-282">Bir Kubernetes Ingress genellikle Api ağ geçidi kapsamı dışında web uygulamaları da dahil olmak üzere uygulamaya tüm trafik için ters proxy olarak görür.</span><span class="sxs-lookup"><span data-stu-id="baea0-282">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="baea0-283">EShopOnContainers'ı Kubernetes'e dağıttığınızda, _giriş_yoluyla sadece birkaç hizmet veya uç noktayı ortaya çıkarır , temelde URL'lerde aşağıdaki düzeltmeler listesi:</span><span class="sxs-lookup"><span data-stu-id="baea0-283">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="baea0-284">`/`istemci SPA web uygulaması için</span><span class="sxs-lookup"><span data-stu-id="baea0-284">`/` for the client SPA web application</span></span>
- <span data-ttu-id="baea0-285">`/webmvc`istemci MVC web uygulaması için</span><span class="sxs-lookup"><span data-stu-id="baea0-285">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="baea0-286">`/webstatus`durumu/sağlık kontrollerini gösteren istemci web uygulaması için</span><span class="sxs-lookup"><span data-stu-id="baea0-286">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="baea0-287">`/webshoppingapigw`web BFF ve alışveriş iş süreçleri için</span><span class="sxs-lookup"><span data-stu-id="baea0-287">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="baea0-288">`/webmarketingapigw`web BFF ve pazarlama iş süreçleri için</span><span class="sxs-lookup"><span data-stu-id="baea0-288">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="baea0-289">`/mobileshoppingapigw`mobil BFF ve alışveriş iş süreçleri için</span><span class="sxs-lookup"><span data-stu-id="baea0-289">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="baea0-290">`/mobilemarketingapigw`mobil BFF ve pazarlama iş süreçleri için</span><span class="sxs-lookup"><span data-stu-id="baea0-290">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="baea0-291">Kubernetes'e dağıtılırken, her Ocelot API Ağ Geçidi, API Ağ Geçitlerini çalıştıran her _pod_ için farklı bir "configuration.json" dosyası kullanır.</span><span class="sxs-lookup"><span data-stu-id="baea0-291">When deploying to Kubernetes, each Ocelot API Gateway is using a different "configuration.json" file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="baea0-292">Bu "configuration.json" dosyaları ,'ocelot' adlı bir Kubernetes _config haritasına_ dayalı olarak oluşturulan bir ses düzeyine (başlangıçta deploy.ps1 komut dosyasıyla) monte edilerek sağlanır.</span><span class="sxs-lookup"><span data-stu-id="baea0-292">Those "configuration.json" files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot'.</span></span> <span data-ttu-id="baea0-293">Her kapsayıcı, ilgili yapılandırma dosyasını kapsayıcının `/app/configuration`klasörüne bağlar.</span><span class="sxs-lookup"><span data-stu-id="baea0-293">Each container mounts its related configuration file in the container's folder named `/app/configuration`.</span></span>

<span data-ttu-id="baea0-294">eShopOnContainers kaynak kod dosyalarında, orijinal "configuration.json" dosyaları `k8s/ocelot/` klasör içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="baea0-294">In the source code files of eShopOnContainers, the original "configuration.json" files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="baea0-295">Her BFF/APIGateway için bir dosya vardır.</span><span class="sxs-lookup"><span data-stu-id="baea0-295">There's one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="baea0-296">Ocelot API Ağ Geçidi'ndeki ek çapraz kesme özellikleri</span><span class="sxs-lookup"><span data-stu-id="baea0-296">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="baea0-297">Araştırma ve kullanım için diğer önemli özellikleri vardır, bir Ocelot API Ağ Geçidi kullanırken, aşağıdaki bağlantılarda açıklanan.</span><span class="sxs-lookup"><span data-stu-id="baea0-297">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="baea0-298">**Ocelot'u Konsolos veya Eureka ile entegre eden müşteri tarafında hizmet keşfi** </span><span class="sxs-lookup"><span data-stu-id="baea0-298">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="baea0-299">**API Ağ Geçidi katmanında önbelleğe alma** </span><span class="sxs-lookup"><span data-stu-id="baea0-299">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="baea0-300">**API Ağ Geçidi katmanında günlüğe kaydetme** </span><span class="sxs-lookup"><span data-stu-id="baea0-300">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="baea0-301">**API Ağ Geçidi katmanında Hizmet Kalitesi (Yeniden Denemeler ve Devre kesiciler)** </span><span class="sxs-lookup"><span data-stu-id="baea0-301">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="baea0-302">**Hız sınırlaması** </span><span class="sxs-lookup"><span data-stu-id="baea0-302">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="baea0-303">[Önceki](background-tasks-with-ihostedservice.md)
> [Sonraki](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="baea0-303">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
