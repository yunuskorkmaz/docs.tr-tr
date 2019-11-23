---
title: Ocelot ile API Ağ Geçitlerini uygulama
description: Ocelot ile API ağ geçitleri uygulamayı ve kapsayıcı tabanlı bir ortamda Ocelot 'yi kullanmayı öğrenin.
ms.date: 10/02/2018
ms.openlocfilehash: 6c576a17d784777557bfb8bd99438eb111e8ec2e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737579"
---
# <a name="implement-api-gateways-with-ocelot"></a><span data-ttu-id="ef245-103">Ocelot ile API ağ geçitleri uygulama</span><span class="sxs-lookup"><span data-stu-id="ef245-103">Implement API Gateways with Ocelot</span></span>

<span data-ttu-id="ef245-104">Başvuru mikro hizmet uygulaması [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) , eshoponcontainers tarafından kullanılan aşağıdaki ortamların herhangi birinde olduğu gibi, mikro hizmetlerinize/kapsayıcılarınızla birlikte dağıtabileceğiniz basit ve hafıf bir API ağ geçidi olan [Ocelot](https://github.com/ThreeMammals/Ocelot)'yi kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="ef245-104">The reference microservice application [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) is using [Ocelot](https://github.com/ThreeMammals/Ocelot), a simple and lightweight API Gateway that you can deploy anywhere along with your microservices/containers, such as in any of the following environments used by eShopOnContainers.</span></span>

- <span data-ttu-id="ef245-105">Docker ana bilgisayarı, yerel geliştirme bilgisayarınızda, şirket içinde veya bulutta.</span><span class="sxs-lookup"><span data-stu-id="ef245-105">Docker host, in your local dev PC, on-premises or in the cloud.</span></span>
- <span data-ttu-id="ef245-106">Kubernetes kümesi, şirket içi veya Azure Kubernetes hizmeti (AKS) gibi yönetilen bulutta.</span><span class="sxs-lookup"><span data-stu-id="ef245-106">Kubernetes cluster, on-premises or in managed cloud such as Azure Kubernetes Service (AKS).</span></span>
- <span data-ttu-id="ef245-107">Küme, şirket içinde veya bulutta Service Fabric.</span><span class="sxs-lookup"><span data-stu-id="ef245-107">Service Fabric cluster, on-premises or in the cloud.</span></span>
- <span data-ttu-id="ef245-108">Azure 'da PaaS/sunucusuz olarak Service Fabric mesh.</span><span class="sxs-lookup"><span data-stu-id="ef245-108">Service Fabric mesh, as PaaS/Serverless in Azure.</span></span>

## <a name="architect-and-design-your-api-gateways"></a><span data-ttu-id="ef245-109">API ağ geçitlerini mimarinizi ve tasarlama</span><span class="sxs-lookup"><span data-stu-id="ef245-109">Architect and design your API Gateways</span></span>

<span data-ttu-id="ef245-110">Aşağıdaki mimari diyagramda, API ağ geçitlerinin eShopOnContainers 'da Ocelot ile nasıl uygulandığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef245-110">The following architecture diagram shows how API Gateways are implemented with Ocelot in eShopOnContainers.</span></span>

![EShopOnContainers mimarisini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture.png)

<span data-ttu-id="ef245-112">**Şekil 6-28**.</span><span class="sxs-lookup"><span data-stu-id="ef245-112">**Figure 6-28**.</span></span> <span data-ttu-id="ef245-113">API ağ geçitleri ile eShopOnContainers mimarisi</span><span class="sxs-lookup"><span data-stu-id="ef245-113">eShopOnContainers architecture with API Gateways</span></span>

<span data-ttu-id="ef245-114">Bu diyagramda tüm uygulamanın, "Docker for Windows" veya "Docker for Mac" ile tek bir Docker konağına veya geliştirme BILGISAYARıNA nasıl dağıtıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef245-114">That diagram shows how the whole application is deployed into a single Docker host or development PC with “Docker for Windows” or “Docker for Mac”.</span></span> <span data-ttu-id="ef245-115">Ancak, herhangi bir Orchestrator 'a dağıtmak oldukça benzerdir ancak Diyagramdaki herhangi bir kapsayıcı Orchestrator 'da ölçeklendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-115">However, deploying into any orchestrator would be pretty similar but any container in the diagram could be scaled-out in the orchestrator.</span></span>

<span data-ttu-id="ef245-116">Ayrıca, veritabanları, önbellek ve ileti aracıları gibi altyapı varlıklarının, Orchestrator 'dan boşaltılabilmesi ve Azure SQL veritabanı, Azure Cosmos DB, Azure Redu, Azure Service Bus gibi altyapıda yüksek kullanılabilir sistemlere dağıtılması gerekir. ya da herhangi bir HA kümeleme çözümünü şirket içinde.</span><span class="sxs-lookup"><span data-stu-id="ef245-116">In addition, the infrastructure assets such as databases, cache, and message brokers should be offloaded from the orchestrator and deployed into high available systems for infrastructure, like Azure SQL Database, Azure Cosmos DB, Azure Redis, Azure Service Bus, or any HA clustering solution on-premises.</span></span>

<span data-ttu-id="ef245-117">Diyagramda da fark edebilirsiniz. birçok API ağ geçidine sahip olmak, mikro hizmetlerinin yanı sıra kendi ilgili API ağ geçitlerinin geliştirilmesi ve dağıtılmasında birden çok geliştirme ekibinin otonom olmasına (Bu durumda pazarlama özellikleri ve alışveriş özellikleri) izin verir.</span><span class="sxs-lookup"><span data-stu-id="ef245-117">As you can also notice in the diagram, having several API Gateways allows multiple development teams to be autonomous (in this case Marketing features vs. Shopping features) when developing and deploying their microservices plus their own related API Gateways.</span></span>

<span data-ttu-id="ef245-118">Çeşitli geliştirme ekipleri tarafından güncelleştirilebilecek tek bir tek nokta olan tek bir tek bir API ağ geçidiniz varsa, tüm mikro hizmetlere uygulamanın tek bir bölümüyle de neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-118">If you had a single monolithic API Gateway that would mean a single point to be updated by several development teams, which could couple all the microservices with a single part of the application.</span></span>

<span data-ttu-id="ef245-119">Tasarımda çok daha fazla şey varsa, bazen ayrıntılı bir API ağ geçidi, seçilen mimariye bağlı olarak tek bir iş mikro hizmeti ile de sınırlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-119">Going much further in the design, sometimes a fine-grained API Gateway can also be limited to a single business microservice depending on the chosen architecture.</span></span> <span data-ttu-id="ef245-120">API ağ geçidinin iş veya etki alanı tarafından dikte edilen sınırlarının olması, daha iyi bir tasarım almanıza yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="ef245-120">Having the API Gateway’s boundaries dictated by the business or domain will help you to get a better design.</span></span>

<span data-ttu-id="ef245-121">Örneğin, gelişmiş bir API Gateway kavramı bir UI bileşim hizmetine benzer olduğundan, API ağ geçidi katmanında ince ayrıntı düzeyi özellikle mikro hizmetleri temel alan daha gelişmiş bileşik UI uygulamaları için yararlı olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-121">For instance, fine granularity in the API Gateway tier can be especially useful for more advanced composite UI applications that are based on microservices, because the concept of a fine-grained API Gateway is similar to a UI composition service.</span></span>

<span data-ttu-id="ef245-122">Önceki bölümde, [mikro hizmetlere dayalı bileşik Kullanıcı arabirimi oluşturma hakkında](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md)daha fazla ayrıntı inceleyeceğiz.</span><span class="sxs-lookup"><span data-stu-id="ef245-122">We delve into more details in the previous section [Creating composite UI based on microservices](../architect-microservice-container-applications/microservice-based-composite-ui-shape-layout.md).</span></span>

<span data-ttu-id="ef245-123">Anahtar kullanımı, birçok orta ve büyük ölçekli uygulamalar için, özel olarak oluşturulmuş bir API ağ geçidi ürünü kullanmanın genellikle iyi bir yaklaşım vardır, ancak tek bir monoparçalı toplayıcı veya benzersiz bir merkezi özel API ağ geçidi, API ağ geçidi birden çok bağımsız izin vermez otonom mikro hizmetler oluşturan çeşitli geliştirme ekipleri için yapılandırma alanı.</span><span class="sxs-lookup"><span data-stu-id="ef245-123">As key takeaway, for many medium- and large-size applications, using a custom-built API Gateway product is usually a good approach, but not as a single monolithic aggregator or unique central custom API Gateway unless that API Gateway allows multiple independent configuration areas for the several development teams creating autonomous microservices.</span></span>

### <a name="sample-microservicescontainers-to-re-route-through-the-api-gateways"></a><span data-ttu-id="ef245-124">API ağ geçitleri aracılığıyla yeniden yönlendirme için örnek mikro hizmetler/kapsayıcılar</span><span class="sxs-lookup"><span data-stu-id="ef245-124">Sample microservices/containers to re-route through the API Gateways</span></span>

<span data-ttu-id="ef245-125">Örnek olarak, eShopOnContainers, aşağıdaki görüntüde gösterildiği gibi, API ağ geçitleri aracılığıyla yayımlanması gereken altı adet iç mikro hizmet türü içerir.</span><span class="sxs-lookup"><span data-stu-id="ef245-125">As an example, eShopOnContainers has around six internal microservice-types that have to be published through the API Gateways, as shown in the following image.</span></span>

![Alt klasörlerini gösteren hizmetler klasörünün ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-microservice-folders.png)

<span data-ttu-id="ef245-127">**Şekil 6-29**.</span><span class="sxs-lookup"><span data-stu-id="ef245-127">**Figure 6-29**.</span></span> <span data-ttu-id="ef245-128">Visual Studio 'da eShopOnContainers çözümünde mikro hizmet klasörleri</span><span class="sxs-lookup"><span data-stu-id="ef245-128">Microservice folders in eShopOnContainers solution in Visual Studio</span></span>

<span data-ttu-id="ef245-129">Kimlik hizmeti hakkında, tasarımda tek bir çapraz kesme sorunu olduğundan, bu, yönetim ağ geçidi yönlendirmesinde kalmadı, ancak bu da yeniden yönlendirme listelerinin bir parçası olarak dahil olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-129">About the Identity service, in the design it's left out of the API Gateway routing because it's the only cross-cutting concern in the system, although with Ocelot it's also possible to include it as part of the rerouting lists.</span></span>

<span data-ttu-id="ef245-130">Koddan bildirebilmeniz için, bu hizmetlerin tümü şu anda ASP.NET Core Web API hizmeti olarak uygulanır.</span><span class="sxs-lookup"><span data-stu-id="ef245-130">All those services are currently implemented as ASP.NET Core Web API services, as you can tell from the code.</span></span> <span data-ttu-id="ef245-131">Kataloğun mikro hizmet kodu gibi mikro hizmetlerden birine odaklanalım.</span><span class="sxs-lookup"><span data-stu-id="ef245-131">Let’s focus on one of the microservices like the Catalog microservice code.</span></span>

![Catalog. API proje içeriğini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/catalog-api-microservice-folders.png)

<span data-ttu-id="ef245-133">**Şekil 6-30**.</span><span class="sxs-lookup"><span data-stu-id="ef245-133">**Figure 6-30**.</span></span> <span data-ttu-id="ef245-134">Örnek Web API mikro hizmeti (Katalog mikro hizmeti)</span><span class="sxs-lookup"><span data-stu-id="ef245-134">Sample Web API microservice (Catalog microservice)</span></span>

<span data-ttu-id="ef245-135">Catalog mikro hizmet 'in, aşağıdaki kodda olduğu gibi çeşitli denetleyiciler ve yöntemlerle tipik bir ASP.NET Core Web API projesi olduğunu görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-135">You can see that the Catalog microservice is a typical ASP.NET Core Web API project with several controllers and methods like in the following code.</span></span>

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

<span data-ttu-id="ef245-136">HTTP isteği, mikro hizmet veritabanına ve gerekli ek eylemlere C# erişen bu tür bir kodu çalıştırmaya sona acaktır.</span><span class="sxs-lookup"><span data-stu-id="ef245-136">The HTTP request will end up running that kind of C# code accessing the microservice database and any additional required action.</span></span>

<span data-ttu-id="ef245-137">Mikro hizmet URL 'SI ile ilgili olan kapsayıcılar yerel geliştirme PC 'nizde (yerel Docker ana bilgisayarı) dağıtıldığında, her mikro hizmet kapsayıcısı, aşağıdaki dockerfile içinde olduğu gibi, dockerfile 'da belirtilen her zaman bir iç bağlantı noktasına (genellikle bağlantı noktası 80) sahiptir:</span><span class="sxs-lookup"><span data-stu-id="ef245-137">Regarding the microservice URL, when the containers are deployed in your local development PC (local Docker host), each microservice’s container has always an internal port (usually port 80) specified in its dockerfile, as in the following dockerfile:</span></span>

```Dockerfile
FROM microsoft/aspnetcore:2.0.5 AS base
WORKDIR /app
EXPOSE 80
```

<span data-ttu-id="ef245-138">Kodda gösterilen bağlantı noktası 80, Docker ana bilgisayarı dahilinde olduğundan istemci uygulamaları tarafından ulaşılamıyor.</span><span class="sxs-lookup"><span data-stu-id="ef245-138">The port 80 shown in the code is internal within the Docker host, so it can't be reached by client apps.</span></span>

<span data-ttu-id="ef245-139">İstemci uygulamaları, `docker-compose`ile dağıtım sırasında yayımlanan dış bağlantı noktalarına (varsa) erişebilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-139">Client apps can access only the external ports (if any) published when deploying with `docker-compose`.</span></span>

<span data-ttu-id="ef245-140">Bu dış bağlantı noktaları, bir üretim ortamına dağıtıldığında yayımlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-140">Those external ports shouldn't be published when deploying to a production environment.</span></span> <span data-ttu-id="ef245-141">Bu, istemci uygulamaları ve mikro hizmetler arasındaki doğrudan iletişimin önüne geçmek için API ağ geçidini kullanmak istediğinizden kesinlikle önemlidir.</span><span class="sxs-lookup"><span data-stu-id="ef245-141">This is precisely why you want to use the API Gateway, to avoid the direct communication between the client apps and the microservices.</span></span>

<span data-ttu-id="ef245-142">Ancak geliştirme sırasında, mikro hizmet/kapsayıcıya doğrudan erişmek ve Swagger aracılığıyla çalıştırmak istersiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-142">However, when developing, you want to access the microservice/container directly and run it through Swagger.</span></span> <span data-ttu-id="ef245-143">EShopOnContainers 'da bu nedenle, dış bağlantı noktaları API Gateway veya istemci uygulamaları tarafından kullanılmayabilse bile hala belirtilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-143">That’s why in eShopOnContainers, the external ports are still specified even when they won’t be used by the API Gateway or the client apps.</span></span>

<span data-ttu-id="ef245-144">Katalog mikro hizmeti için `docker-compose.override.yml` dosyasına bir örnek aşağıda verilmiştir:</span><span class="sxs-lookup"><span data-stu-id="ef245-144">Here’s an example of the `docker-compose.override.yml` file for the Catalog microservice:</span></span>

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

<span data-ttu-id="ef245-145">Docker-Compose. override. yıml yapılandırmasında Katalog kapsayıcısının iç bağlantı noktası 80 olup olmadığını görebilirsiniz, ancak dış erişim bağlantı noktası 5101 ' dir.</span><span class="sxs-lookup"><span data-stu-id="ef245-145">You can see how in the docker-compose.override.yml configuration the internal port for the Catalog container is port 80, but the port for external access is 5101.</span></span> <span data-ttu-id="ef245-146">Ancak bu bağlantı noktası, yalnızca katalog mikro hizmetini çalıştırmak ve test etmek için bir API ağ geçidi kullanılırken uygulama tarafından kullanılmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-146">But this port shouldn’t be used by the application when using an API Gateway, only to debug, run and test just the Catalog microservice.</span></span>

<span data-ttu-id="ef245-147">Genellikle, mikro hizmetler için doğru üretim dağıtım ortamı Kubernetes veya Service Fabric gibi bir Orchestrator olduğundan, bir üretim ortamına Docker-Compose ile dağıtım yapmanız gerekmez.</span><span class="sxs-lookup"><span data-stu-id="ef245-147">Normally, you won’t be deploying with docker-compose into a production environment because the right production deployment environment for microservices is an orchestrator like Kubernetes or Service Fabric.</span></span> <span data-ttu-id="ef245-148">Bu ortamlara dağıtım yaparken, mikro hizmetler için doğrudan herhangi bir harici bağlantı noktasını yayımlayamayacağınız farklı yapılandırma dosyalarını kullanırsınız, ancak her zaman ters proxy 'yi API Gateway 'den kullanacaksınız.</span><span class="sxs-lookup"><span data-stu-id="ef245-148">When deploying to those environments you use different configuration files where you won’t publish directly any external port for the microservices but, you'll always use the reverse proxy from the API Gateway.</span></span>

<span data-ttu-id="ef245-149">Katalog mikro hizmetini, Visual Studio 'dan tam eShopOnContainers çözümünü çalıştırarak (Docker-Compose dosyalarındaki tüm hizmetleri çalıştırır) veya katalog mikro hizmetini, `docker-compose.yml` ve Docker-Compose. override. IML dosyasının yerleştirildiği klasörde konumlandırılmış olan CMD veya PowerShell içinde aşağıdaki Docker-Compose komutuyla çalıştırmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-149">Run the catalog microservice in your local Docker host either by running the full eShopOnContainers solution from Visual Studio (it’ll run all the services in the docker-compose files) or just starting the Catalog microservice with the following docker-compose command in CMD or PowerShell positioned at the folder where the `docker-compose.yml` and docker-compose.override.yml are placed.</span></span>

```console
docker-compose run --service-ports catalog.api
```

<span data-ttu-id="ef245-150">Bu komut yalnızca Catalog. API hizmet kapsayıcısını ve Docker-Compose. yıml içinde belirtilen bağımlılıkları çalıştırır.</span><span class="sxs-lookup"><span data-stu-id="ef245-150">This command only runs the catalog.api service container plus dependencies that are specified in the docker-compose.yml.</span></span> <span data-ttu-id="ef245-151">Bu durumda, SQL Server Container ve Kbbitmq kapsayıcısı.</span><span class="sxs-lookup"><span data-stu-id="ef245-151">In this case, the SQL Server container and RabbitMQ container.</span></span>

<span data-ttu-id="ef245-152">Daha sonra, Katalog mikro hizmetine doğrudan erişebilir ve bu durumda, bu örnekte bu bağlantı noktasından doğrudan bu bağlantı noktası üzerinden erişim için Swagger Kullanıcı arabirimi aracılığıyla yöntemleri görebilirsiniz `http://localhost:5101/swagger`:</span><span class="sxs-lookup"><span data-stu-id="ef245-152">Then, you can directly access the Catalog microservice and see its methods through the Swagger UI accessing directly through that “external” port, in this case `http://localhost:5101/swagger`:</span></span>

![Catalog. API REST API gösteren Swagger Kullanıcı arabiriminin ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/test-catalog-microservice.png)

<span data-ttu-id="ef245-154">**Şekil 6-31**.</span><span class="sxs-lookup"><span data-stu-id="ef245-154">**Figure 6-31**.</span></span> <span data-ttu-id="ef245-155">Katalog mikro hizmetini Swagger Kullanıcı arabirimiyle test etme</span><span class="sxs-lookup"><span data-stu-id="ef245-155">Testing the Catalog microservice with its Swagger UI</span></span>

<span data-ttu-id="ef245-156">Bu noktada, Visual Studio 'da C# kodda bir kesme noktası ayarlayabilir, mikro hizmeti Swagger Kullanıcı arabiriminde sunulan yöntemlerle test edebilirsiniz ve son olarak `docker-compose down` komutuyla her şeyi temizleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-156">At this point, you could set a breakpoint in C# code in Visual Studio, test the microservice with the methods exposed in Swagger UI, and finally clean-up everything with the `docker-compose down` command.</span></span>

<span data-ttu-id="ef245-157">Ancak, bu durumda 5101 dış bağlantı noktası aracılığıyla mikro hizmetle doğrudan erişim iletişimi, uygulamanızda kaçınmak istediğiniz kadar kesin bir durumdur.</span><span class="sxs-lookup"><span data-stu-id="ef245-157">However, direct-access communication to the microservice, in this case through the external port 5101, is precisely what you want to avoid in your application.</span></span> <span data-ttu-id="ef245-158">API ağ geçidinin ek yöneltme düzeyini (Bu durumda Ocelot) ayarlayarak bundan kaçınabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-158">And you can avoid that by setting the additional level of indirection of the API Gateway (Ocelot, in this case).</span></span> <span data-ttu-id="ef245-159">Bu şekilde, istemci uygulaması mikro hizmete doğrudan erişemez.</span><span class="sxs-lookup"><span data-stu-id="ef245-159">That way, the client app won’t directly access the microservice.</span></span>

## <a name="implementing-your-api-gateways-with-ocelot"></a><span data-ttu-id="ef245-160">API ağ geçitlerini Ocelot ile uygulama</span><span class="sxs-lookup"><span data-stu-id="ef245-160">Implementing your API Gateways with Ocelot</span></span>

<span data-ttu-id="ef245-161">Ocelot, temel olarak belirli bir sırada uygulayabileceğiniz bir middlewares kümesidir.</span><span class="sxs-lookup"><span data-stu-id="ef245-161">Ocelot is basically a set of middlewares that you can apply in a specific order.</span></span>

<span data-ttu-id="ef245-162">Ocelot yalnızca ASP.NET Core çalışmak üzere tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef245-162">Ocelot is designed to work with ASP.NET Core only.</span></span> <span data-ttu-id="ef245-163">.NET Core 2,0 çalışma zamanı ve .NET Framework 4.6.1 çalışma zamanı ve ' de dahil olmak üzere 2,0 .NET Standard her yerde kullanılabilmesi için Netstandard 2.0 'ı hedefliyordu.</span><span class="sxs-lookup"><span data-stu-id="ef245-163">It targets netstandard2.0 so it can be used anywhere .NET Standard 2.0 is supported, including .NET Core 2.0 runtime and .NET Framework 4.6.1 runtime and up.</span></span>

<span data-ttu-id="ef245-164">Ocelot 'yi ve onun bağımlılıklarını, Visual Studio 'dan [Ocelot 'Nin NuGet paketiyle](https://www.nuget.org/packages/Ocelot/)ASP.NET Core projenize yüklersiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-164">You install Ocelot and its dependencies in your ASP.NET Core project with [Ocelot's NuGet package](https://www.nuget.org/packages/Ocelot/), from Visual Studio.</span></span>

```powershell
Install-Package Ocelot
```

<span data-ttu-id="ef245-165">EShopOnContainers 'da, API Gateway uygulamasının basit bir ASP.NET Core WebHost projesi ve Ocelot 'nin middlewares, aşağıdaki görüntüde gösterildiği gibi tüm API Gateway özelliklerini işlemesi:</span><span class="sxs-lookup"><span data-stu-id="ef245-165">In eShopOnContainers, its API Gateway implementation is a simple ASP.NET Core WebHost project, and Ocelot’s middlewares handle all the API Gateway features, as shown in the following image:</span></span>

![Ocelot API Gateway projesini gösteren Çözüm Gezgini ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelotapigw-base-project.png)

<span data-ttu-id="ef245-167">**Şekil 6-32**.</span><span class="sxs-lookup"><span data-stu-id="ef245-167">**Figure 6-32**.</span></span> <span data-ttu-id="ef245-168">EShopOnContainers 'da OcelotApiGw temel projesi</span><span class="sxs-lookup"><span data-stu-id="ef245-168">The OcelotApiGw base project in eShopOnContainers</span></span>

<span data-ttu-id="ef245-169">Bu ASP.NET Core WebHost projesi temel olarak iki basit dosya ile oluşturulmuştur: `Program.cs` ve `Startup.cs`.</span><span class="sxs-lookup"><span data-stu-id="ef245-169">This ASP.NET Core WebHost project is basically built with two simple files:  `Program.cs` and `Startup.cs`.</span></span>

<span data-ttu-id="ef245-170">Program.cs yalnızca, BuildWebHost ASP.NET Core oluşturmak ve yapılandırmak için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="ef245-170">The Program.cs just needs to create and configure the typical ASP.NET Core BuildWebHost.</span></span>

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

<span data-ttu-id="ef245-171">Ocelot için buradaki önemli nokta, `AddJsonFile()` yöntemi aracılığıyla oluşturucuya sağlamanız gereken `configuration.json` dosyasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-171">The important point here for Ocelot is the `configuration.json` file that you must provide to the builder through the `AddJsonFile()` method.</span></span> <span data-ttu-id="ef245-172">Bu `configuration.json`, genellikle farklı bağlantı noktaları kullanarak belirli bağlantı noktaları ve bağıntılı iç uç noktalar içeren dış uç noktalar olan tüm API ağ geçidi ReRoutes belirttiğiniz yerdir.</span><span class="sxs-lookup"><span data-stu-id="ef245-172">That `configuration.json` is where you specify all the API Gateway ReRoutes, meaning the external endpoints with specific ports and the correlated internal endpoints, usually using different ports.</span></span>

```json
{
    "ReRoutes": [],
    "GlobalConfiguration": {}
}
```

<span data-ttu-id="ef245-173">Yapılandırmanın iki bölümü vardır.</span><span class="sxs-lookup"><span data-stu-id="ef245-173">There are two sections to the configuration.</span></span> <span data-ttu-id="ef245-174">Bir yeniden yönlendirme dizisi ve bir GlobalConfiguration.</span><span class="sxs-lookup"><span data-stu-id="ef245-174">An array of Re-Routes and a GlobalConfiguration.</span></span> <span data-ttu-id="ef245-175">Yeniden yönlendirmeler, bir yukarı akış isteğini nasıl değerlendireceği hakkında daha fazla bilgi veren nesnelerdir.</span><span class="sxs-lookup"><span data-stu-id="ef245-175">The Re-Routes are the objects that tell Ocelot how to treat an upstream request.</span></span> <span data-ttu-id="ef245-176">Genel yapılandırma, belirli ayarların yeniden yönlendirilmesi için geçersiz kılmalara izin verir.</span><span class="sxs-lookup"><span data-stu-id="ef245-176">The Global configuration allows overrides of Re-Route specific settings.</span></span> <span data-ttu-id="ef245-177">Çok sayıda yeniden yönlendirme, belirli ayarları yönetmek istemiyorsanız yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-177">It’s useful if you don’t want to manage lots of Re-Route specific settings.</span></span>

<span data-ttu-id="ef245-178">Aşağıda, eShopOnContainers 'dan API ağ geçitlerinden birinden [yapılandırma dosyası yeniden yönlendirme](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) için basitleştirilmiş bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="ef245-178">Here’s a simplified example of [ReRoute configuration file](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/ApiGateways/Web.Bff.Shopping/apigw/configuration.json) from one of the API Gateways from eShopOnContainers.</span></span>

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

<span data-ttu-id="ef245-179">Bir Ocelot API ağ geçidinin ana işlevselliği, gelen HTTP isteklerini almak ve şu anda başka bir HTTP isteği olarak bir aşağı akış hizmetine iletmektir.</span><span class="sxs-lookup"><span data-stu-id="ef245-179">The main functionality of an Ocelot API Gateway is to take incoming HTTP requests and forward them on to a downstream service, currently as another HTTP request.</span></span> <span data-ttu-id="ef245-180">Ocelot, bir isteğin bir yeniden yönlendirme olarak diğerine yönlendirilmesini açıklar.</span><span class="sxs-lookup"><span data-stu-id="ef245-180">Ocelot’s describes the routing of one request to another as a Re-Route.</span></span>

<span data-ttu-id="ef245-181">Örneğin, yukarıdaki Configuration. JSON içindeki yeniden rotalardan birine, sepet mikro hizmeti yapılandırmasına odaklanalım.</span><span class="sxs-lookup"><span data-stu-id="ef245-181">For instance, let’s focus on one of the Re-Routes in the configuration.json from above, the configuration for the Basket microservice.</span></span>

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

<span data-ttu-id="ef245-182">DownstreamPathTemplate, düzen ve Downstreamhostandport, bu isteğin iletileceği iç mikro hizmet URL 'sini yapar.</span><span class="sxs-lookup"><span data-stu-id="ef245-182">The DownstreamPathTemplate, Scheme, and DownstreamHostAndPorts make the internal microservice URL that this request will be forwarded to.</span></span>

<span data-ttu-id="ef245-183">Bağlantı noktası, hizmet tarafından kullanılan iç bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-183">The port is the internal port used by the service.</span></span> <span data-ttu-id="ef245-184">Kapsayıcılar kullanılırken dockerfile 'da belirtilen bağlantı noktası.</span><span class="sxs-lookup"><span data-stu-id="ef245-184">When using containers, the port specified at its dockerfile.</span></span>

<span data-ttu-id="ef245-185">`Host`, kullanmakta olduğunuz hizmet adı çözümlemesine bağlı olan bir hizmet adıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-185">The `Host` is a service name that depends on the service name resolution you are using.</span></span> <span data-ttu-id="ef245-186">Docker-Compose kullanırken, hizmet adları Docker ana bilgisayarı tarafından sağlanır ve bu, Docker-Compose dosyalarında belirtilen hizmet adlarını kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ef245-186">When using docker-compose, the services names are provided by the Docker Host, which is using the service names provided in the docker-compose files.</span></span> <span data-ttu-id="ef245-187">Kubernetes veya Service Fabric gibi bir Orchestrator kullanılıyorsa, bu ad her Orchestrator tarafından sağlanmış olan DNS veya ad çözümlemesi tarafından çözümlenmelidir.</span><span class="sxs-lookup"><span data-stu-id="ef245-187">If using an orchestrator like Kubernetes or Service Fabric, that name should be resolved by the DNS or name resolution provided by each orchestrator.</span></span>

<span data-ttu-id="ef245-188">Downstreamhostandport, istekleri iletmek istediğiniz herhangi bir aşağı akış hizmetinin ana bilgisayar ve bağlantı noktasını içeren bir dizidir.</span><span class="sxs-lookup"><span data-stu-id="ef245-188">DownstreamHostAndPorts is an array that contains the host and port of any downstream services that you wish to forward requests to.</span></span> <span data-ttu-id="ef245-189">Genellikle bu yalnızca bir giriş içerir, ancak bazen aşağı akış hizmetlerinize yük dengelemesi yapmak isteyebilirsiniz ve Ocelot, birden fazla giriş eklemenizi ve sonra bir yük dengeleyici seçmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="ef245-189">Usually this will just contain one entry but sometimes you might want to load balance requests to your downstream services and Ocelot lets you add more than one entry and then select a load balancer.</span></span> <span data-ttu-id="ef245-190">Ancak Azure ve herhangi bir Orchestrator kullanılıyorsa, bulut ve Orchestrator altyapısıyla yük dengelemesi daha iyi bir fikir olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-190">But if using Azure and any orchestrator it is probably a better idea to load balance with the cloud and orchestrator infrastructure.</span></span>

<span data-ttu-id="ef245-191">UpstreamPathTemplate, istemci tarafından verilen bir istek için kullanılacak olan DownstreamPathTemplate 'i tanımlamak için kullanılan URL 'dir.</span><span class="sxs-lookup"><span data-stu-id="ef245-191">The UpstreamPathTemplate is the URL that Ocelot will use to identify which DownstreamPathTemplate to use for a given request from the client.</span></span> <span data-ttu-id="ef245-192">Son olarak, UpstreamHttpMethod kullanılır. bu nedenle, Ocelot, farklı istekleri (GET, POST, PUT) aynı URL 'ye ayırabilirler.</span><span class="sxs-lookup"><span data-stu-id="ef245-192">Finally, the UpstreamHttpMethod is used so Ocelot can distinguish between different requests (GET, POST, PUT) to the same URL.</span></span>

<span data-ttu-id="ef245-193">Bu noktada, bir veya [birden fazla birleştirilmiş Configuration. JSON dosyası](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) kullanarak tek bir Ocelot API Gateway (ASP.NET Core Webhost) olabilir veya [yapılandırmayı BIR tüketil kV deposunda](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul)da saklayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-193">At this point, you could have a single Ocelot API Gateway (ASP.NET Core WebHost) using one or [multiple merged configuration.json files](https://ocelot.readthedocs.io/en/latest/features/configuration.html#merging-configuration-files) or you can also store the [configuration in a Consul KV store](https://ocelot.readthedocs.io/en/latest/features/configuration.html#store-configuration-in-consul).</span></span>

<span data-ttu-id="ef245-194">Ancak, mimari ve tasarım bölümlerinde tanıtıldıkça, gerçekten otonom mikro hizmetlere sahip olmak istiyorsanız, bu tek monoparçalı API ağ geçidini birden çok API ağ geçidine ve/veya BFF (ön uç için arka uç) olarak bölmek daha iyi olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-194">But as introduced in the architecture and design sections, if you really want to have autonomous microservices, it might be better to split that single monolithic API Gateway into multiple API Gateways and/or BFF (Backend for Frontend).</span></span> <span data-ttu-id="ef245-195">Bu amaçla, bu yaklaşımı Docker kapsayıcılarıyla nasıl uygulayacağınızı görelim.</span><span class="sxs-lookup"><span data-stu-id="ef245-195">For that purpose, let’s see how to implement that approach with Docker containers.</span></span>

### <a name="using-a-single-docker-container-image-to-run-multiple-different-api-gateway--bff-container-types"></a><span data-ttu-id="ef245-196">Birden çok farklı API Gateway/BFF kapsayıcı türü çalıştırmak için tek bir Docker kapsayıcı görüntüsü kullanma</span><span class="sxs-lookup"><span data-stu-id="ef245-196">Using a single Docker container image to run multiple different API Gateway / BFF container types</span></span>

<span data-ttu-id="ef245-197">EShopOnContainers 'da, Ocelot API ağ geçidiyle tek bir Docker kapsayıcı görüntüsü kullanıyoruz, ancak çalışma zamanında, farklı bir Configuration. JSON dosyası sağlayarak her bir API-Gateway/BFF türü için bir Docker birimi kullanarak farklı hizmetler/kapsayıcılar oluşturuyoruz Her hizmet için farklı bir BILGISAYAR klasörüne erişin.</span><span class="sxs-lookup"><span data-stu-id="ef245-197">In eShopOnContainers we’re using a single Docker container image with the Ocelot API Gateway but then, at run time, we create different services/containers for each type of API-Gateway/BFF by providing a different configuration.json file, using a docker volume to access a different PC folder for each service.</span></span>

![Tüm API ağ geçitleri için tek bir Ocelot Gateway Docker görüntüsünün diyagramı.](./media/implement-api-gateways-with-ocelot/reusing-single-ocelot-docker-image.png)

<span data-ttu-id="ef245-199">**Şekil 6-33**.</span><span class="sxs-lookup"><span data-stu-id="ef245-199">**Figure 6-33**.</span></span> <span data-ttu-id="ef245-200">Birden çok API ağ geçidi türü genelinde tek bir Ocelot Docker görüntüsünü yeniden kullanma</span><span class="sxs-lookup"><span data-stu-id="ef245-200">Re-using a single Ocelot Docker image across multiple API Gateway types</span></span>

<span data-ttu-id="ef245-201">EShopOnContainers 'da, "genel Ocelot API Gateway Docker Image", Docker-Compose. yml dosyasında belirtilen ' OcelotApiGw ' adlı projeyle ve "eShop/ocelotapigw" görüntü adına oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="ef245-201">In eShopOnContainers, the “Generic Ocelot API Gateway Docker Image” is created with the project named 'OcelotApiGw' and the image name “eshop/ocelotapigw” that is specified in the docker-compose.yml file.</span></span> <span data-ttu-id="ef245-202">Daha sonra, Docker 'a dağıtım yaparken, Docker-Compose. yıml dosyasında aşağıdaki ayıklama bölümünde gösterildiği gibi, aynı Docker görüntüsünden oluşturulan dört API-Gateway kapsayıcısı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ef245-202">Then, when deploying to Docker, there will be four API-Gateway containers created from that same Docker image, as shown in the following extract from the docker-compose.yml file.</span></span>

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

<span data-ttu-id="ef245-203">Ayrıca, aşağıdaki Docker-Compose. override. yıml dosyasında görebileceğiniz gibi, bu API ağ geçidi kapsayıcıları arasındaki tek fark, her bir hizmet kapsayıcısı için farklı olan ve çalışma zamanında bir Docker birimi.</span><span class="sxs-lookup"><span data-stu-id="ef245-203">Additionally, as you can see in the following docker-compose.override.yml file, the only difference between those API Gateway containers is the Ocelot configuration file, which is different for each service container and it's specified at runtime through a Docker volume.</span></span>

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

<span data-ttu-id="ef245-204">Bu önceki kod nedeniyle ve aşağıdaki Visual Studio Gezgini 'nde gösterildiği gibi, her bir iş/BFF API ağ geçidini tanımlamak için gereken tek dosya yalnızca bir Configuration. JSON dosyasıdır, çünkü dört API ağ geçitleri aynı Docker görüntüsüne dayalıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-204">Because of that previous code, and as shown in the Visual Studio Explorer below, the only file needed to define each specific business/BFF API Gateway is just a configuration.json file, because the four API Gateways are based on the same Docker image.</span></span>

![Configuration. JSON dosyaları olan tüm API ağ geçitlerini gösteren ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/ocelot-configuration-files.png)

<span data-ttu-id="ef245-206">**Şekil 6-34**.</span><span class="sxs-lookup"><span data-stu-id="ef245-206">**Figure 6-34**.</span></span> <span data-ttu-id="ef245-207">Her API ağ geçidini/BFF 'yi Ocelot ile tanımlamak için gereken tek dosya bir yapılandırma dosyasıdır</span><span class="sxs-lookup"><span data-stu-id="ef245-207">The only file needed to define each API Gateway / BFF with Ocelot is a configuration file</span></span>

<span data-ttu-id="ef245-208">API ağ geçidini birden çok API ağ geçidine bölerek, mikro hizmetlerin farklı alt kümelerine odaklanan farklı geliştirme takımları, bağımsız Ocelot yapılandırma dosyalarını kullanarak kendi API ağ geçitlerini yönetebilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-208">By splitting the API Gateway into multiple API Gateways, different development teams focusing on different subsets of microservices can manage their own API Gateways by using independent Ocelot configuration files.</span></span> <span data-ttu-id="ef245-209">Ayrıca, aynı anda aynı Ocelot Docker görüntüsünü yeniden kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-209">Plus, at the same time they can reuse the same Ocelot Docker image.</span></span>

<span data-ttu-id="ef245-210">Artık, API ağ geçitleri ile eShopOnContainers çalıştırırsanız (eShopOnContainers-ServicesAndWebApps. sln çözümü açılırken veya "Docker-Compose up" çalıştırıyorsanız), aşağıdaki örnek yollar gerçekleştirilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-210">Now, if you run eShopOnContainers with the API Gateways (included by default in VS when opening eShopOnContainers-ServicesAndWebApps.sln solution or if running “docker-compose up”), the following sample routes will be performed.</span></span>

<span data-ttu-id="ef245-211">Örneğin, webshoppingapigw API Gateway tarafından sunulan yukarı akış URL 'sini ziyaret `http://localhost:5202/api/v1/c/catalog/items/2/`, aşağıdaki tarayıcıda olduğu gibi, Docker konağının içindeki iç aşağı akış URL 'SI `http://catalog.api/api/v1/2` aynı sonucu elde edersiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-211">For instance, when visiting the upstream URL `http://localhost:5202/api/v1/c/catalog/items/2/` served by the webshoppingapigw API Gateway, you get the same result from the internal Downstream URL `http://catalog.api/api/v1/2` within the Docker host, as in the following browser.</span></span>

![API Gateway üzerinden yanıt gösteren bir tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/access-microservice-through-url.png)

<span data-ttu-id="ef245-213">**Şekil 6-35**.</span><span class="sxs-lookup"><span data-stu-id="ef245-213">**Figure 6-35**.</span></span> <span data-ttu-id="ef245-214">API ağ geçidi tarafından sunulan bir URL aracılığıyla mikro hizmete erişme</span><span class="sxs-lookup"><span data-stu-id="ef245-214">Accessing a microservice through a URL provided by the API Gateway</span></span>

<span data-ttu-id="ef245-215">Test veya hata ayıklama nedenlerinden dolayı, API Gateway 'e geçmeden doğrudan Katalog Docker kapsayıcısına (yalnızca geliştirme ortamında) erişmek isterseniz, ' Catalog. API ', Docker ana bilgisayarına (Docker-Compose hizmet adları tarafından işlenen hizmet bulma) iç bir DNS çözümünden, kapsayıcıya doğrudan erişmenin tek yolu, yalnızca aşağıdaki tarayıcıda `http://localhost:5101/api/v1/Catalog/items/1` gibi geliştirme testlerinde sağlanmış olan Docker-Compose. override. yıml içinde Yayınlanan dış bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-215">Because of testing or debugging reasons, if you wanted to directly access to the Catalog Docker container (only at the development environment) without passing through the API Gateway, since 'catalog.api' is a DNS resolution internal to the Docker host (service discovery handled by docker-compose service names), the only way to directly access the container is through the external port published in the docker-compose.override.yml, which is provided only for development tests, such as `http://localhost:5101/api/v1/Catalog/items/1` in the following browser.</span></span>

![Catalog. API 'ye doğrudan yanıt gösteren tarayıcının ekran görüntüsü.](./media/implement-api-gateways-with-ocelot/direct-access-microservice-testing.png)

<span data-ttu-id="ef245-217">**Şekil 6-36**.</span><span class="sxs-lookup"><span data-stu-id="ef245-217">**Figure 6-36**.</span></span> <span data-ttu-id="ef245-218">Sınama amacıyla bir mikro hizmete doğrudan erişim</span><span class="sxs-lookup"><span data-stu-id="ef245-218">Direct access to a microservice for testing purposes</span></span>

<span data-ttu-id="ef245-219">Ancak uygulama, doğrudan bağlantı noktasında "kısayollar" değil, tüm mikro hizmetlere API ağ geçitleri üzerinden erişmesi için yapılandırılmıştır.</span><span class="sxs-lookup"><span data-stu-id="ef245-219">But the application is configured so it accesses all the microservices through the API Gateways, not though the direct port “shortcuts”.</span></span>

### <a name="the-gateway-aggregation-pattern-in-eshoponcontainers"></a><span data-ttu-id="ef245-220">EShopOnContainers 'daki ağ geçidi toplama deseninin</span><span class="sxs-lookup"><span data-stu-id="ef245-220">The Gateway aggregation pattern in eShopOnContainers</span></span>

<span data-ttu-id="ef245-221">Daha önce sunulmuş olduğu gibi, istek toplamayı uygulamak için esnek bir yol, koda göre özel hizmetlerle aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ef245-221">As introduced previously, a flexible way to implement requests aggregation is with custom services, by code.</span></span> <span data-ttu-id="ef245-222">Ayrıca, [Ocelot Içindeki Istek toplama özelliği](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation)ile istek toplamayı da uygulayabilirsiniz, ancak ihtiyacınız olduğu kadar esnek olmayabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-222">You could also implement request aggregation with the [Request Aggregation feature in Ocelot](https://ocelot.readthedocs.io/en/latest/features/requestaggregation.html#request-aggregation), but it might not be as flexible as you need.</span></span> <span data-ttu-id="ef245-223">Bu nedenle, eShopOnContainers 'da toplamayı uygulamak için seçilen yol, her toplayıcı için açık bir ASP.NET Core Web API hizmetleriyle birlikte bulunur.</span><span class="sxs-lookup"><span data-stu-id="ef245-223">Therefore, the selected way to implement aggregation in eShopOnContainers is with an explicit ASP.NET Core Web API services for each aggregator.</span></span>

<span data-ttu-id="ef245-224">Bu yaklaşıma göre, API ağ geçidi bileşim diyagramı, daha önce gösterilen Basitleştirilmiş küresel mimari diyagramında görünmeyen toplayıcı Hizmetleri düşünüldüğünde çok daha fazla uzatılmış bir bittir.</span><span class="sxs-lookup"><span data-stu-id="ef245-224">According to that approach, the API Gateway composition diagram is in reality a bit more extended when considering the aggregator services that are not shown in the simplified global architecture diagram shown previously.</span></span>

<span data-ttu-id="ef245-225">Aşağıdaki diyagramda, toplayıcı Hizmetleri 'nin ilgili API ağ geçitleriyle nasıl çalıştığını da görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-225">In the following diagram, you can also see how the aggregator services work with their related API Gateways.</span></span>

![Toplayıcı hizmetlerini gösteren eShopOnContainers mimarisinin diyagramı.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-architecture-aggregator-services.png)

<span data-ttu-id="ef245-227">**Şekil 6-37**.</span><span class="sxs-lookup"><span data-stu-id="ef245-227">**Figure 6-37**.</span></span> <span data-ttu-id="ef245-228">Toplayıcı Hizmetleri ile eShopOnContainers mimarisi</span><span class="sxs-lookup"><span data-stu-id="ef245-228">eShopOnContainers architecture with aggregator services</span></span>

<span data-ttu-id="ef245-229">Daha fazla yakınlaştırma, aşağıdaki görüntüde "alışveriş" iş alanında, API ağ geçitlerinde toplayıcı Hizmetleri kullanılırken istemci uygulamaları ve mikro hizmetler arasındaki azaltmaya azaldığını görebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-229">Zooming in further, on the “Shopping” business area in the following image, you can see that chattiness between the client apps and the microservices is reduced when using the aggregator services in the API Gateways.</span></span>

![EShopOnContainers mimarisi yakınlaştırmasını gösteren diyagram.](./media/implement-api-gateways-with-ocelot/zoom-in-vision-aggregator-services.png)

<span data-ttu-id="ef245-231">**Şekil 6-38**.</span><span class="sxs-lookup"><span data-stu-id="ef245-231">**Figure 6-38**.</span></span> <span data-ttu-id="ef245-232">Toplayıcı hizmetlerini yakından yakınlaştırın</span><span class="sxs-lookup"><span data-stu-id="ef245-232">Zoom in vision of the Aggregator services</span></span>

<span data-ttu-id="ef245-233">Diyagram, API ağ geçitlerinden gelen olası istekleri nasıl gösterdiğine, oldukça karmaşık bir şekilde sahip olduğunu fark edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-233">You can notice how when the diagram shows the possible requests coming from the API Gateways it can get pretty complex.</span></span> <span data-ttu-id="ef245-234">Mavi renkli okların nasıl basitleştiğini, bir istemci uygulamalar perspektifinden, iletişim kutusunda azaltmaya ve gecikme süresini azaltarak, uzak uygulamaların kullanıcı deneyimini önemli ölçüde geliştirerek ( Mobil ve SPA uygulamaları), özellikle.</span><span class="sxs-lookup"><span data-stu-id="ef245-234">Although you can see how the arrows in blue would be simplified, from a client apps perspective, when using the aggregator pattern by reducing chattiness and latency in the communication, ultimately significantly improving the user experience for the remote apps (mobile and SPA apps), especially.</span></span>

<span data-ttu-id="ef245-235">"Pazarlama" iş alanı ve mikro hizmetler söz konusu olduğunda, aggregators 'ı kullanmaya gerek olmadığı için çok basit bir kullanım durumdur, ancak gerektiğinde de mümkün olabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-235">In the case of the “Marketing” business area and microservices, it is a very simple use case so there was no need to use aggregators, but it could also be possible, if needed.</span></span>

### <a name="authentication-and-authorization-in-ocelot-api-gateways"></a><span data-ttu-id="ef245-236">Ocelot API ağ geçitlerinde kimlik doğrulama ve yetkilendirme</span><span class="sxs-lookup"><span data-stu-id="ef245-236">Authentication and authorization in Ocelot API Gateways</span></span>

<span data-ttu-id="ef245-237">Bir Ocelot API ağ geçidinde, kimlik doğrulama belirtecini veya API ağ geçidinin içinden veya içinden kimlik doğrulama [belirtecini sağlayan bir](https://identityserver.io/) ASP.NET Core Web API hizmeti gibi, kimlik doğrulama hizmetine oturtyükleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ef245-237">In an Ocelot API Gateway you can sit the authentication service, such as an ASP.NET Core Web API service using [IdentityServer](https://identityserver.io/) providing the auth token, either out or inside the API Gateway.</span></span>

<span data-ttu-id="ef245-238">EShopOnContainers, BFF ve iş alanlarını temel alan sınırların bulunduğu birden çok API ağ geçidi kullandığından, kimlik/kimlik doğrulama hizmeti, aşağıdaki diyagramda sarı renkle vurgulanmış şekilde API ağ geçitlerinden bırakılır.</span><span class="sxs-lookup"><span data-stu-id="ef245-238">Since eShopOnContainers is using multiple API Gateways with boundaries based on BFF and business areas, the Identity/Auth service is left out of the API Gateways, as highlighted in yellow in the following diagram.</span></span>

![API ağ geçidinin altındaki kimlik mikro hizmetini gösteren diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainers-identity-service-position.png)

<span data-ttu-id="ef245-240">**Şekil 6-39**.</span><span class="sxs-lookup"><span data-stu-id="ef245-240">**Figure 6-39**.</span></span> <span data-ttu-id="ef245-241">EShopOnContainers 'da kimlik hizmetinin konumu</span><span class="sxs-lookup"><span data-stu-id="ef245-241">Position of the Identity service in eShopOnContainers</span></span>

<span data-ttu-id="ef245-242">Ancak, Ocelot Ayrıca, bu diğer diyagramda olduğu gibi, API Gateway sınırının içinde kimlik/auth mikro hizmetini de destekler.</span><span class="sxs-lookup"><span data-stu-id="ef245-242">However, Ocelot also supports sitting the Identity/Auth microservice within the API Gateway boundary, as in this other diagram.</span></span>

![Bir Ocelot API ağ geçidinde kimlik doğrulamasını gösteren diyagram.](./media/implement-api-gateways-with-ocelot/ocelot-authentication.png)

<span data-ttu-id="ef245-244">**Şekil 6-40**.</span><span class="sxs-lookup"><span data-stu-id="ef245-244">**Figure 6-40**.</span></span> <span data-ttu-id="ef245-245">Ocelot 'de kimlik doğrulaması</span><span class="sxs-lookup"><span data-stu-id="ef245-245">Authentication in Ocelot</span></span>

<span data-ttu-id="ef245-246">Önceki diyagramda gösterildiği gibi, kimlik mikro hizmeti, API ağ geçidinin (AG) altında olduğunda, 1) AG, kimlik mikro hizmetinden bir kimlik doğrulama belirteci ister 2) kimlik doğrulama belirtecini kullanarak mikro hizmetlerden gelen bir kimlik doğrulaması belirteci 3-4 döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef245-246">As the previous diagram shows, when the Identity microservice is beneath the API gateway (AG): 1) AG requests an auth token from identity microservice, 2) The identity microservice returns token to AG, 3-4) AG requests from microservices using the auth token.</span></span> <span data-ttu-id="ef245-247">EShopOnContainers uygulaması, API ağ geçidini birden çok BFF (ön uç için arka uç) ve iş alanları API ağ geçitlerine böldüğü için, çapraz kesme sorunları için ek bir API ağ geçidi oluşturulması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef245-247">Because eShopOnContainers application has split the API Gateway into multiple BFF (Backend for Frontend) and business areas API Gateways, another option would had been to create an additional API Gateway for cross-cutting concerns.</span></span> <span data-ttu-id="ef245-248">Bu seçenek, birden çok çapraz kesme sorunları olan mikro hizmetlere sahip daha karmaşık bir mikro hizmet tabanlı mimaride yer alan bir şekilde yapılır.</span><span class="sxs-lookup"><span data-stu-id="ef245-248">That choice would be fair in a more complex microservice based architecture with multiple cross-cutting concerns microservices.</span></span> <span data-ttu-id="ef245-249">EShopOnContainers 'da yalnızca bir çapraz kesme sorunu olduğundan, basitlik 'in sake 'SI için API ağ geçidi bölgesinden yalnızca güvenlik hizmetini işlemeye karar verdi.</span><span class="sxs-lookup"><span data-stu-id="ef245-249">Since there's only one cross-cutting concern in eShopOnContainers, it was decided to just handle the security service out of the API Gateway realm, for simplicity’s sake.</span></span>

<span data-ttu-id="ef245-250">Herhangi bir durumda, uygulama API ağ geçidi düzeyinde güvenli hale getirildiğinden, güvenli mikro hizmeti kullanmaya çalışırken Ocelot API ağ geçidinin kimlik doğrulama modülü ilk olarak ziyaret edilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-250">In any case, if the app is secured at the API Gateway level, the authentication module of the Ocelot API Gateway is visited at first when trying to use any secured microservice.</span></span> <span data-ttu-id="ef245-251">Bu, access_token ile korunan hizmetleri ziyaret edebilmeniz için erişim belirtecini almak üzere kimliği veya auth mikro hizmetini ziyaret etmek üzere HTTP isteğini yeniden yönlendirir.</span><span class="sxs-lookup"><span data-stu-id="ef245-251">That re-directs the HTTP request to visit the Identity or auth microservice to get the access token so you can visit the protected services with the access_token.</span></span>

<span data-ttu-id="ef245-252">API ağ geçidi düzeyinde herhangi bir hizmette kimlik doğrulama ile güvenli hale getirmenin yolu, AuthenticationProviderKey değerini Configuration. JSON konumundaki ilgili ayarlarında ayarlamadır.</span><span class="sxs-lookup"><span data-stu-id="ef245-252">The way you secure with authentication any service at the API Gateway level is by setting the AuthenticationProviderKey in its related settings at the configuration.json.</span></span>

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

<span data-ttu-id="ef245-253">Ocelot çalıştırıldığında, AuthenticationOptions. AuthenticationProviderKey yeniden yönlendirmeler ' a bakar ve verilen anahtara kayıtlı bir kimlik doğrulama sağlayıcısı olup olmadığını kontrol eder.</span><span class="sxs-lookup"><span data-stu-id="ef245-253">When Ocelot runs, it will look at the Re-Routes AuthenticationOptions.AuthenticationProviderKey and check that there is an Authentication Provider registered with the given key.</span></span> <span data-ttu-id="ef245-254">Yoksa, Ocelot başlamacaktır.</span><span class="sxs-lookup"><span data-stu-id="ef245-254">If there isn't, then Ocelot will not start up.</span></span> <span data-ttu-id="ef245-255">Varsa, yeniden yönlendirme bu sağlayıcıyı çalıştırıldığında kullanır.</span><span class="sxs-lookup"><span data-stu-id="ef245-255">If there is, then the ReRoute will use that provider when it executes.</span></span>

<span data-ttu-id="ef245-256">Ocelot WebHost, `authenticationProviderKey = "IdentityApiKey"`ile yapılandırıldığından, bu hizmet kimlik doğrulama belirteci olmayan herhangi bir istek olduğunda kimlik doğrulaması gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ef245-256">Because the Ocelot WebHost is configured with the `authenticationProviderKey = "IdentityApiKey"`, that will require authentication whenever that service has any requests without any auth token.</span></span>

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

<span data-ttu-id="ef245-257">Daha sonra, aşağıdaki sepet mikro hizmet denetleyicisi gibi mikro hizmetler gibi erişilecek herhangi bir kaynaktaki [Yetkilendir] özniteliğiyle yetkilendirmeyi de ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="ef245-257">Then, you also need to set authorization with the [Authorize] attribute on any resource to be accessed like the microservices, such as in the following Basket microservice controller.</span></span>

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

<span data-ttu-id="ef245-258">"Sepet" gibi Validaudide, aşağıdaki kodda olduğu gibi, başlangıç sınıfının ConfigureServices () `AddJwtBearer()` ile her bir mikro hizmette tanımlanan hedef kitlelerle bağıntılı.</span><span class="sxs-lookup"><span data-stu-id="ef245-258">The ValidAudiences such as “basket” are correlated with the audience defined in each microservice with `AddJwtBearer()` at the ConfigureServices() of the Startup class, such as in the code below.</span></span>

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

<span data-ttu-id="ef245-259">`http://localhost:5202/api/v1/b/basket/1`gibi API ağ geçidine dayanan bir yeniden yönlendirme URL 'SI ile sepet mikro hizmeti gibi güvenli bir mikro hizmete erişmeye çalışırsanız, geçerli bir belirteç sağlamadığınız takdirde 401 Yetkisiz bir işlem alırsınız.</span><span class="sxs-lookup"><span data-stu-id="ef245-259">If you try to access any secured microservice, like the Basket microservice with a Re-Route URL based on the API Gateway like `http://localhost:5202/api/v1/b/basket/1`, then you’ll get a 401 Unauthorized unless you provide a valid token.</span></span> <span data-ttu-id="ef245-260">Öte yandan, bir yeniden yönlendirme URL 'SI doğrulandıysa, Ocelot onunla ilişkili olan bir aşağı akış şemasını (iç mikro hizmet URL 'SI) çağırır.</span><span class="sxs-lookup"><span data-stu-id="ef245-260">On the other hand, if a Re-Route URL is authenticated, Ocelot will invoke whatever downstream scheme is associated with it (the internal microservice URL).</span></span>

<span data-ttu-id="ef245-261">**Ocelot 'nin ReRoutes katmanında yetkilendirme.**</span><span class="sxs-lookup"><span data-stu-id="ef245-261">**Authorization at Ocelot’s ReRoutes tier.**</span></span>  <span data-ttu-id="ef245-262">Ocelot, kimlik doğrulamasından sonra değerlendirilen talep tabanlı yetkilendirmeyi destekler.</span><span class="sxs-lookup"><span data-stu-id="ef245-262">Ocelot supports claims-based authorization evaluated after the authentication.</span></span> <span data-ttu-id="ef245-263">Yeniden yönlendirme yapılandırmasına aşağıdaki satırları ekleyerek bir rota düzeyinde yetkilendirme ayarlarsınız.</span><span class="sxs-lookup"><span data-stu-id="ef245-263">You set the authorization at a route level by adding the following lines to the ReRoute configuration.</span></span>

```json
"RouteClaimsRequirement": {
    "UserType": "employee"
}
```

<span data-ttu-id="ef245-264">Bu örnekte, yetkilendirme ara yazılımı çağrıldığında, kullanıcının belirteçte ' UserType ' talep türüne sahip olup olmadığını ve bu talebin değeri ' Employee ' olup olmadığını bulur.</span><span class="sxs-lookup"><span data-stu-id="ef245-264">In that example, when the authorization middleware is called, Ocelot will find if the user has the claim type 'UserType' in the token and if the value of that claim is 'employee'.</span></span> <span data-ttu-id="ef245-265">Değilse, Kullanıcı yetkilendirilmez ve yanıt 403 olarak yasaklanmış olur.</span><span class="sxs-lookup"><span data-stu-id="ef245-265">If it isn’t, then the user will not be authorized and the response will be 403 forbidden.</span></span>

## <a name="using-kubernetes-ingress-plus-ocelot-api-gateways"></a><span data-ttu-id="ef245-266">Kubernetes ınress ve Ocelot API ağ geçitlerini kullanma</span><span class="sxs-lookup"><span data-stu-id="ef245-266">Using Kubernetes Ingress plus Ocelot API Gateways</span></span>

<span data-ttu-id="ef245-267">Kubernetes (bir Azure Kubernetes hizmet kümesinde olduğu gibi) kullanılırken, genellikle tüm HTTP isteklerini *NGINX*temelinde [Kubernetes giriş katmanı](https://kubernetes.io/docs/concepts/services-networking/ingress/) üzerinden birleştirmişsinizdir.</span><span class="sxs-lookup"><span data-stu-id="ef245-267">When using Kubernetes (like in an Azure Kubernetes Service cluster), you usually unify all the HTTP requests through the [Kubernetes Ingress tier](https://kubernetes.io/docs/concepts/services-networking/ingress/) based on *Nginx*.</span></span>

<span data-ttu-id="ef245-268">Kubernetes 'te herhangi bir giriş yaklaşımı kullanmıyorsanız, hizmetlerinizin ve klarınızın IP 'Leri yalnızca küme ağı tarafından yönlendirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-268">In Kubernetes, if you don’t use any ingress approach, then your services and pods have IPs only routable by the cluster network.</span></span>

<span data-ttu-id="ef245-269">Ancak, bir giriş yaklaşımı kullanıyorsanız Internet ve hizmetleriniz (API ağ geçitleriniz dahil) arasında bir orta katman ve ters proxy görevi gören bir orta katmanınız olacaktır.</span><span class="sxs-lookup"><span data-stu-id="ef245-269">But if you use an ingress approach, you'll have a middle tier between the Internet and your services (including your API Gateways), acting as a reverse proxy.</span></span>

<span data-ttu-id="ef245-270">Bir tanım olarak, giriş, gelen bağlantılara küme hizmetlerine ulaşmasına izin veren kuralların koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="ef245-270">As a definition, an Ingress is a collection of rules that allow inbound connections to reach the cluster services.</span></span> <span data-ttu-id="ef245-271">Giriş genellikle hizmetlere dışarıdan erişilebilen URL 'Ler, Yük Dengeleme trafiği, SSL sonlandırma ve daha fazlası sağlamak üzere yapılandırılır.</span><span class="sxs-lookup"><span data-stu-id="ef245-271">An ingress is usually configured to provide services externally reachable URLs, load balance traffic, SSL termination and more.</span></span> <span data-ttu-id="ef245-272">Kullanıcılar giriş kaynağını API sunucusuna naklederek giriş isteği ister.</span><span class="sxs-lookup"><span data-stu-id="ef245-272">Users request ingress by POSTing the Ingress resource to the API server.</span></span>

<span data-ttu-id="ef245-273">EShopOnContainers 'da, yerel olarak geliştirilirken ve yalnızca bir geliştirme makinenizi Docker Konağı olarak kullanırken, yalnızca birden fazla API ağ geçidi kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="ef245-273">In eShopOnContainers, when developing locally and using just your development machine as the Docker host, you are not using any ingress but only the multiple API Gateways.</span></span>

<span data-ttu-id="ef245-274">Ancak, Kubernetes tabanlı bir "üretim" ortamını hedeflerken eShopOnContainers, API ağ geçitlerinin önünde bir giriş kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="ef245-274">However, when targeting a “production” environment based on Kubernetes, eShopOnContainers is using an ingress in front of the API gateways.</span></span> <span data-ttu-id="ef245-275">Bu şekilde, istemciler yine de aynı temel URL 'YI çağırır, ancak istekler birden fazla API ağ geçidine veya BFF 'ye yönlendirilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-275">That way, the clients still call the same base URL but the requests are routed to multiple API Gateways or BFF.</span></span>

<span data-ttu-id="ef245-276">API ağ geçitlerinin ön uçları veya façades, genellikle kapsamlarından çıkan Web uygulamalarına değil, yalnızca hizmetlere yönelik olduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="ef245-276">Note that API Gateways are front-ends or façades surfacing only the services but not the web applications that are usually out of their scope.</span></span> <span data-ttu-id="ef245-277">Ayrıca, API ağ geçitleri bazı iç mikro hizmetleri gizleyebilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-277">In addition, the API Gateways might hide certain internal microservices.</span></span>

<span data-ttu-id="ef245-278">Ancak giriş, HTTP isteklerini yeniden yönlendirse de herhangi bir mikro hizmeti veya Web uygulamasını gizlemeyi denememelidir.</span><span class="sxs-lookup"><span data-stu-id="ef245-278">The ingress, however, is just redirecting HTTP requests but not trying to hide any microservice or web app.</span></span>

<span data-ttu-id="ef245-279">Web uygulamalarının önündeki Kubernetes 'de bir giriş Nginx katmanına sahip olmak ve çeşitli Ocelot API ağ geçitleri/BFF, aşağıdaki diyagramda gösterildiği gibi ideal mimaridir.</span><span class="sxs-lookup"><span data-stu-id="ef245-279">Having an ingress Nginx tier in Kubernetes in front of the web applications plus the several Ocelot API Gateways / BFF is the ideal architecture, as shown in the following diagram.</span></span>

![Bir giriş katmanının AKS ortamına nasıl uyduğunu gösteren bir diyagram.](./media/implement-api-gateways-with-ocelot/eshoponcontainer-ingress-tier.png)

<span data-ttu-id="ef245-281">**Şekil 6-41**.</span><span class="sxs-lookup"><span data-stu-id="ef245-281">**Figure 6-41**.</span></span> <span data-ttu-id="ef245-282">Kubernetes 'e dağıtıldığında eShopOnContainers içindeki giriş katmanı</span><span class="sxs-lookup"><span data-stu-id="ef245-282">The ingress tier in eShopOnContainers when deployed into Kubernetes</span></span>

<span data-ttu-id="ef245-283">Kubernetes girişi, genellikle API ağ geçidi kapsamından çıkan Web uygulamaları dahil olmak üzere, uygulamaya yönelik tüm trafik için ters proxy görevi görür.</span><span class="sxs-lookup"><span data-stu-id="ef245-283">A Kubernetes Ingress acts as a reverse proxy for all traffic to the app, including the web applications, that are usually out of the Api gateway scope.</span></span> <span data-ttu-id="ef245-284">EShopOnContainers 'ı Kubernetes 'e dağıttığınızda, temel olarak yalnızca birkaç hizmet veya uç _nokta Ile URL_'lerde aşağıdaki postdüzeltmelerin listesini sunar:</span><span class="sxs-lookup"><span data-stu-id="ef245-284">When you deploy eShopOnContainers into Kubernetes, it exposes just a few services or endpoints via _ingress_, basically the following list of postfixes on the URLs:</span></span>

- <span data-ttu-id="ef245-285">istemci SPA Web uygulaması için `/`</span><span class="sxs-lookup"><span data-stu-id="ef245-285">`/` for the client SPA web application</span></span>
- <span data-ttu-id="ef245-286">istemci MVC web uygulaması için `/webmvc`</span><span class="sxs-lookup"><span data-stu-id="ef245-286">`/webmvc` for the client MVC web application</span></span>
- <span data-ttu-id="ef245-287">durum/healthdenetimleri gösteren istemci Web uygulaması için `/webstatus`</span><span class="sxs-lookup"><span data-stu-id="ef245-287">`/webstatus` for the client web app showing the status/healthchecks</span></span>
- <span data-ttu-id="ef245-288">Web BFF ve alışveriş iş işlemlerine yönelik `/webshoppingapigw`</span><span class="sxs-lookup"><span data-stu-id="ef245-288">`/webshoppingapigw` for the web BFF and shopping business processes</span></span>
- <span data-ttu-id="ef245-289">Web BFF ve pazarlama iş işlemlerine yönelik `/webmarketingapigw`</span><span class="sxs-lookup"><span data-stu-id="ef245-289">`/webmarketingapigw` for the web BFF and marketing business processes</span></span>
- <span data-ttu-id="ef245-290">Mobil BFF ve alışveriş iş işlemlerine yönelik `/mobileshoppingapigw`</span><span class="sxs-lookup"><span data-stu-id="ef245-290">`/mobileshoppingapigw` for the mobile BFF and shopping business processes</span></span>
- <span data-ttu-id="ef245-291">Mobil BFF ve pazarlama iş işlemlerine yönelik `/mobilemarketingapigw`</span><span class="sxs-lookup"><span data-stu-id="ef245-291">`/mobilemarketingapigw` for the mobile BFF and marketing business processes</span></span>

<span data-ttu-id="ef245-292">Kubernetes 'e dağıtım yaparken, her Ocelot API ağ geçidi, API ağ geçitlerini çalıştıran her _Pod_ için farklı bir "Configuration. JSON" dosyası kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="ef245-292">When deploying to Kubernetes, each Ocelot API Gateway is using a different “configuration.json” file for each _pod_ running the API Gateways.</span></span> <span data-ttu-id="ef245-293">Bu "Configuration. JSON" dosyaları, ' Ocelot ' adlı bir Kubernetes _yapılandırma eşlemesi_ temel alınarak oluşturulan bir birimi bağlama tarafından sağlanır (başlangıçta Deploy. ps1 betiği ile).</span><span class="sxs-lookup"><span data-stu-id="ef245-293">Those “configuration.json” files are provided by mounting (originally with the deploy.ps1 script) a volume created based on a Kubernetes _config map_ named ‘ocelot’.</span></span> <span data-ttu-id="ef245-294">Her kapsayıcı, `/app/configuration`adlı kapsayıcı klasöründe ilgili yapılandırma dosyasını takar.</span><span class="sxs-lookup"><span data-stu-id="ef245-294">Each container mounts its related configuration file in the container’s folder named `/app/configuration`.</span></span>

<span data-ttu-id="ef245-295">EShopOnContainers kaynak kodu dosyalarında, özgün "Configuration. JSON" dosyaları `k8s/ocelot/` klasörü içinde bulunabilir.</span><span class="sxs-lookup"><span data-stu-id="ef245-295">In the source code files of eShopOnContainers, the original “configuration.json” files can be found within the `k8s/ocelot/` folder.</span></span> <span data-ttu-id="ef245-296">Her BFF/APIGateway için bir dosya vardır.</span><span class="sxs-lookup"><span data-stu-id="ef245-296">There’s one file for each BFF/APIGateway.</span></span>

## <a name="additional-cross-cutting-features-in-an-ocelot-api-gateway"></a><span data-ttu-id="ef245-297">Bir Ocelot API ağ geçidinde ek çapraz kesme özellikleri</span><span class="sxs-lookup"><span data-stu-id="ef245-297">Additional cross-cutting features in an Ocelot API Gateway</span></span>

<span data-ttu-id="ef245-298">Aşağıdaki bağlantılarda açıklanan bir Ocelot API ağ geçidi kullanırken araştırmak ve kullanmak için kullanabileceğiniz diğer önemli özellikler vardır.</span><span class="sxs-lookup"><span data-stu-id="ef245-298">There are other important features to research and use, when using an Ocelot API Gateway, described in the following links.</span></span>

- <span data-ttu-id="ef245-299">**İstemci tarafındaki hizmet keşfi, Cell veya Eureka ile tümleştirme** </span><span class="sxs-lookup"><span data-stu-id="ef245-299">**Service discovery in the client side integrating Ocelot with Consul or Eureka** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/servicediscovery.html>

- <span data-ttu-id="ef245-300">**API ağ geçidi katmanında önbelleğe alma** </span><span class="sxs-lookup"><span data-stu-id="ef245-300">**Caching at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/caching.html>

- <span data-ttu-id="ef245-301">**API ağ geçidi katmanında günlüğe kaydetme** </span><span class="sxs-lookup"><span data-stu-id="ef245-301">**Logging at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/logging.html>

- <span data-ttu-id="ef245-302">**API ağ geçidi katmanında hizmet kalitesi (yeniden denemeler ve devre kesiciler)**  </span><span class="sxs-lookup"><span data-stu-id="ef245-302">**Quality of Service (Retries and Circuit breakers) at the API Gateway tier** </span></span>\
  <https://ocelot.readthedocs.io/en/latest/features/qualityofservice.html>

- <span data-ttu-id="ef245-303">**Hız sınırlandırma** </span><span class="sxs-lookup"><span data-stu-id="ef245-303">**Rate limiting** </span></span>\
  [https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html](https://ocelot.readthedocs.io/en/latest/features/ratelimiting.html )

> [!div class="step-by-step"]
> <span data-ttu-id="ef245-304">[Önceki](background-tasks-with-ihostedservice.md)
> [İleri](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="ef245-304">[Previous](background-tasks-with-ihostedservice.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
