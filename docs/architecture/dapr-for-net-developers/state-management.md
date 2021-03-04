---
title: Davpr durum yönetimi yapı taşı
description: Durum yönetimi oluşturma bloğunun açıklaması, özellikleri, avantajları ve nasıl uygulanacağı.
author: amolenk
ms.date: 02/07/2021
ms.reviewer: robvet
ms.openlocfilehash: 05daf18ece1da377f3d5d6a91c4839f196f14f80
ms.sourcegitcommit: 42d436ebc2a7ee02fc1848c7742bc7d80e13fc2f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/04/2021
ms.locfileid: "102106222"
---
# <a name="the-dapr-state-management-building-block"></a><span data-ttu-id="e659b-103">Davpr durum yönetimi yapı taşı</span><span class="sxs-lookup"><span data-stu-id="e659b-103">The Dapr state management building block</span></span>

<span data-ttu-id="e659b-104">Dağıtılmış uygulamalar bağımsız hizmetlerden oluşur.</span><span class="sxs-lookup"><span data-stu-id="e659b-104">Distributed applications are composed of independent services.</span></span> <span data-ttu-id="e659b-105">Her hizmetin durum bilgisiz olması gerekir, ancak bazı hizmetler iş işlemlerinin tamamlanabilmesi için durumu izlemeli olmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-105">While each service should be stateless, some services must track state to complete business operations.</span></span> <span data-ttu-id="e659b-106">E-ticaret sitesi için bir alışveriş sepeti hizmeti düşünün.</span><span class="sxs-lookup"><span data-stu-id="e659b-106">Consider a shopping basket service for an e-Commerce site.</span></span> <span data-ttu-id="e659b-107">Hizmet durumu izleyemiyor, müşteri web sitesini bırakarak alışveriş sepeti içeriğini gevşekerek kayıp satışı ve memnun olmayan müşteri deneyimine neden olur.</span><span class="sxs-lookup"><span data-stu-id="e659b-107">If the service can't track state, the customer could loose the shopping basket content by leaving the website, resulting in a lost sale and an unhappy customer experience.</span></span> <span data-ttu-id="e659b-108">Bu senaryolar için durumun dağıtılmış bir durum deposuna kalıcı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e659b-108">For these scenarios, state needs to be persisted to a distributed state store.</span></span> <span data-ttu-id="e659b-109">[Davpr durum yönetimi yapı taşı](https://docs.dapr.io/developing-applications/building-blocks/state-management/) durum izlemeyi basitleştirir ve çeşitli veri depoları arasında gelişmiş özellikler sunar.</span><span class="sxs-lookup"><span data-stu-id="e659b-109">The [Dapr state management building block](https://docs.dapr.io/developing-applications/building-blocks/state-management/) simplifies state tracking and offers advanced features across various data stores.</span></span>

<span data-ttu-id="e659b-110">Durum yönetimi oluşturma bloğunu denemek için, [Bölüm 3 ' teki sayaç uygulaması örneğine](getting-started.md)göz atın.</span><span class="sxs-lookup"><span data-stu-id="e659b-110">To try out the state management building block, have a look at the [counter application sample in chapter 3](getting-started.md).</span></span>

## <a name="what-it-solves"></a><span data-ttu-id="e659b-111">Ne çözdüğü</span><span class="sxs-lookup"><span data-stu-id="e659b-111">What it solves</span></span>

<span data-ttu-id="e659b-112">Dağıtılmış bir uygulamadaki izleme durumu zor olabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-112">Tracking state in a distributed application can be challenging.</span></span> <span data-ttu-id="e659b-113">Örnek:</span><span class="sxs-lookup"><span data-stu-id="e659b-113">For example:</span></span>

- <span data-ttu-id="e659b-114">Uygulama farklı türlerde veri depoları gerektirebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-114">The application may require different types of data stores.</span></span>
- <span data-ttu-id="e659b-115">Verilere erişmek ve verileri güncelleştirmek için farklı tutarlılık düzeyleri gerekebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-115">Different consistency levels may be required for accessing and updating data.</span></span>
- <span data-ttu-id="e659b-116">Aynı anda birden çok Kullanıcı, çakışma çözümü gerektiren verileri güncelleştirebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-116">Multiple users may update data at the same time, requiring  conflict resolution.</span></span>
- <span data-ttu-id="e659b-117">Hizmetler, veri deposuyla etkileşim kurarken oluşan kısa süreli [geçici hataları](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) yeniden denemelidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-117">Services must retry any short-lived [transient errors](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/transient-fault-handling) that  occur while interacting with the data store.</span></span>

<span data-ttu-id="e659b-118">Davpr durum yönetimi oluşturma bloğunda bu sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e659b-118">The Dapr state management building block addresses these challenges.</span></span> <span data-ttu-id="e659b-119">Bağımlılıklar olmadan izleme durumunu veya üçüncü taraf depolama SDK 'lerinde öğrenme eğrisini kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="e659b-119">It streamlines tracking state without dependencies or a learning curve on third-party storage SDKs.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e659b-120">Davpr durum yönetimi bir [anahtar/değer](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API 'si sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-120">Dapr state management offers a [key/value](/azure/architecture/guide/technology-choices/data-store-overview#keyvalue-stores) API.</span></span> <span data-ttu-id="e659b-121">Özelliği ilişkisel veya grafik veri depolamayı desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e659b-121">The feature doesn't support relational or graph data storage.</span></span>

## <a name="how-it-works"></a><span data-ttu-id="e659b-122">Nasıl çalışır?</span><span class="sxs-lookup"><span data-stu-id="e659b-122">How it works</span></span>

<span data-ttu-id="e659b-123">Uygulama, anahtar/değer verilerini depolamak ve almak için bir davpr sepet ile etkileşime girer.</span><span class="sxs-lookup"><span data-stu-id="e659b-123">The application interacts with a Dapr sidecar to store and retrieve key/value data.</span></span> <span data-ttu-id="e659b-124">Altyapı API 'SI, dışarıdan veri kalıcı hale getirmek için yapılandırılabilir bir durum depolama bileşeni kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-124">Under the hood, the sidecar API consumes a configurable state store component to persist data.</span></span> <span data-ttu-id="e659b-125">Geliştiriciler Azure Cosmos DB, SQL Server ve Cassandra içeren [desteklenen bir durum depoları](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) koleksiyonu arasından seçim yapabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-125">Developers can choose from a growing collection of [supported state stores](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/) that include Azure Cosmos DB, SQL Server, and Cassandra.</span></span>

<span data-ttu-id="e659b-126">API, HTTP ya da gRPC ile çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-126">The API can be called with either HTTP or gRPC.</span></span> <span data-ttu-id="e659b-127">HTTP API 'sini çağırmak için aşağıdaki URL 'YI kullanın:</span><span class="sxs-lookup"><span data-stu-id="e659b-127">Use the following URL to call the HTTP API:</span></span>

```http
http://localhost:<dapr-port>/v1.0/state/<store-name>/
```

- <span data-ttu-id="e659b-128">`<dapr-port>`: Bu, Davpr 'nin dinlediği HTTP bağlantı noktasıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-128">`<dapr-port>`: the HTTP port that Dapr listens on.</span></span>
- <span data-ttu-id="e659b-129">`<store-name>`: kullanılacak durum depolama bileşeninin adı.</span><span class="sxs-lookup"><span data-stu-id="e659b-129">`<store-name>`: the name of the state store component to use.</span></span>

<span data-ttu-id="e659b-130">Şekil 5-1 ' de, bir Davpr etkin alışveriş sepeti hizmetinin adlı bir anahtar/değer çiftini nasıl depoladığı gösterilmektedir `statestore` .</span><span class="sxs-lookup"><span data-stu-id="e659b-130">Figure 5-1 shows how a Dapr-enabled shopping basket service stores a key/value pair using the Dapr state store component named `statestore`.</span></span>

![Bir anahtar/değer çiftinin bir Davpr durum deposunda depolanması diyagramı.](media/state-management/state-management-flow.png)

<span data-ttu-id="e659b-132">**Şekil 5-1**.</span><span class="sxs-lookup"><span data-stu-id="e659b-132">**Figure 5-1**.</span></span> <span data-ttu-id="e659b-133">Bir anahtar/değer çiftinin bir Davpr durum deposunda depolanması.</span><span class="sxs-lookup"><span data-stu-id="e659b-133">Storing a key/value pair in a Dapr state store.</span></span>

<span data-ttu-id="e659b-134">Önceki şekildeki adımlara göz önünde edin:</span><span class="sxs-lookup"><span data-stu-id="e659b-134">Note the steps in the previous figure:</span></span>

1. <span data-ttu-id="e659b-135">Sepet hizmeti, Davpr sidecar üzerinde durum yönetimi API 'sini çağırır.</span><span class="sxs-lookup"><span data-stu-id="e659b-135">The basket service calls the state management API on the Dapr sidecar.</span></span> <span data-ttu-id="e659b-136">İsteğin gövdesi birden çok anahtar/değer çifti içerebilen bir JSON dizisi barındırır.</span><span class="sxs-lookup"><span data-stu-id="e659b-136">The body of the request encloses a JSON array that can contain multiple key/value pairs.</span></span>
1. <span data-ttu-id="e659b-137">Davpr sepet, bileşen yapılandırma dosyasına göre durum deposunu belirler.</span><span class="sxs-lookup"><span data-stu-id="e659b-137">The Dapr sidecar determines the state store based on the component configuration file.</span></span> <span data-ttu-id="e659b-138">Bu durumda, Redsıs cache durum deposudur.</span><span class="sxs-lookup"><span data-stu-id="e659b-138">In this case, it's a Redis cache state store.</span></span>
1. <span data-ttu-id="e659b-139">Sepet, verileri redsıs önbelleğine devam ettirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-139">The sidecar persists the data to the Redis cache.</span></span>

<span data-ttu-id="e659b-140">Depolanan verilerin alınması benzer bir API çağrıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-140">Retrieving the stored data is a similar API call.</span></span> <span data-ttu-id="e659b-141">Aşağıdaki örnekte, bir *kıvrımlı* komutu, bu verileri, davpr sepet API 'sini çağırarak alır:</span><span class="sxs-lookup"><span data-stu-id="e659b-141">In the example below, a *curl* command retrieves the data by calling the Dapr sidecar API:</span></span>

```console
curl http://localhost:3500/v1.0/state/statestore/basket1
```

<span data-ttu-id="e659b-142">Komut, yanıt gövdesinde depolanan durumu döndürür:</span><span class="sxs-lookup"><span data-stu-id="e659b-142">The command returns the stored state in the response body:</span></span>

```json
{
  "items": [
    {
      "itemId": "DaprHoodie",
      "quantity": 1
    }
  ],
  "customerId": 1
}
```

<span data-ttu-id="e659b-143">Aşağıdaki bölümlerde, durum yönetimi oluşturma bloğunun daha gelişmiş özelliklerinin nasıl kullanılacağı açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e659b-143">The following sections explain how to use the more advanced features of the state management building block.</span></span>

### <a name="consistency"></a><span data-ttu-id="e659b-144">Tutarlılık</span><span class="sxs-lookup"><span data-stu-id="e659b-144">Consistency</span></span>

<span data-ttu-id="e659b-145">[Cap](https://en.wikipedia.org/wiki/CAP_theorem) 'ler, durumu depolayan dağıtılmış sistemler için uygulanan bir ilkeler kümesidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-145">The [CAP theorem](https://en.wikipedia.org/wiki/CAP_theorem) is a set of principles that apply to distributed systems that store state.</span></span> <span data-ttu-id="e659b-146">Şekil 5-2, CAP 'in üç özelliğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="e659b-146">Figure 5-2 shows the three properties of the CAP theorem.</span></span>

![Üst sınır.](media/state-management/cap-theorem.png)

<span data-ttu-id="e659b-148">**Şekil 5-2**.</span><span class="sxs-lookup"><span data-stu-id="e659b-148">**Figure 5-2**.</span></span> <span data-ttu-id="e659b-149">Üst sınır.</span><span class="sxs-lookup"><span data-stu-id="e659b-149">The CAP theorem.</span></span>

<span data-ttu-id="e659b-150">Bu, dağıtılmış veri sistemlerinin tutarlılık, kullanılabilirlik ve bölüm toleransı arasında bir denge sunmadığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e659b-150">The theorem states that distributed data systems offer a trade-off between consistency, availability, and partition tolerance.</span></span> <span data-ttu-id="e659b-151">Ve tüm veri deposu, *üç özelliği yalnızca iki özelliği garanti* edebilir:</span><span class="sxs-lookup"><span data-stu-id="e659b-151">And, that any datastore can only *guarantee two of the three properties*:</span></span>

- <span data-ttu-id="e659b-152">*Tutarlılık* (**C**).</span><span class="sxs-lookup"><span data-stu-id="e659b-152">*Consistency* (**C**).</span></span> <span data-ttu-id="e659b-153">Kümedeki her düğüm, sistemin tüm çoğaltmalar güncellene kadar isteği engellemeniz gerekir olsa bile en son verilerle yanıt verir.</span><span class="sxs-lookup"><span data-stu-id="e659b-153">Every node in the cluster responds with the most recent data, even if the system must block the request until all replicas update.</span></span> <span data-ttu-id="e659b-154">Şu anda güncelleştirilen bir öğe için "tutarlı bir sistem" sorgusu yaparsanız, tüm çoğaltmalar başarıyla güncelleştirilene kadar bir yanıt almazsınız.</span><span class="sxs-lookup"><span data-stu-id="e659b-154">If you query a "consistent system" for an item that is currently updating, you won't get a response until all replicas successfully update.</span></span> <span data-ttu-id="e659b-155">Ancak, en güncel verileri her zaman alacaksınız.</span><span class="sxs-lookup"><span data-stu-id="e659b-155">However, you'll always receive the most current data.</span></span>

- <span data-ttu-id="e659b-156">*Kullanılabilirlik* (**A**).</span><span class="sxs-lookup"><span data-stu-id="e659b-156">*Availability* (**A**).</span></span> <span data-ttu-id="e659b-157">Her düğüm, bu yanıt en son veriler olmasa bile anında yanıt döndürür.</span><span class="sxs-lookup"><span data-stu-id="e659b-157">Every node returns an immediate response, even if that response isn't the most recent data.</span></span> <span data-ttu-id="e659b-158">Güncelleştiren bir öğe için "kullanılabilir sistem" i sorgulayıp, hizmetin bu anda sağlayabilmesini sağlayacak en iyi yanıtı alırsınız.</span><span class="sxs-lookup"><span data-stu-id="e659b-158">If you query an "available system" for an item that is updating, you'll get the best possible answer the service can provide at that moment.</span></span>

- <span data-ttu-id="e659b-159">*Bölüm toleransı* (**P**).</span><span class="sxs-lookup"><span data-stu-id="e659b-159">*Partition Tolerance* (**P**).</span></span> <span data-ttu-id="e659b-160">Çoğaltılan bir veri düğümü başarısız olsa da veya diğer çoğaltılan veri düğümleriyle bağlantıyı kaybederse bile sistemin çalışmaya devam etmesini güvence altına alır.</span><span class="sxs-lookup"><span data-stu-id="e659b-160">Guarantees the system continues to operate even if a replicated data node fails or loses connectivity with other replicated data nodes.</span></span>

<span data-ttu-id="e659b-161">Dağıtılmış uygulamalar **P** özelliğini işlemelidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-161">Distributed applications must handle the **P** property.</span></span> <span data-ttu-id="e659b-162">Hizmetler ağ çağrılarında birbirleriyle iletişim kurduklarında, ağ kesintileri (**P**) oluşur.</span><span class="sxs-lookup"><span data-stu-id="e659b-162">As services communicate among each other with network calls, network disruptions (**P**) will occur.</span></span> <span data-ttu-id="e659b-163">Bu şekilde, Dağıtılmış uygulamaların **AP** veya **CP** olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e659b-163">With that in mind, distributed applications must either be **AP** or **CP**.</span></span>

<span data-ttu-id="e659b-164">**AP** uygulamaları tutarlılık üzerinde kullanılabilirlik seçer.</span><span class="sxs-lookup"><span data-stu-id="e659b-164">**AP** applications choose availability over consistency.</span></span> <span data-ttu-id="e659b-165">Davpr, bu seçeneği **nihai tutarlılık** stratejisiyle destekler.</span><span class="sxs-lookup"><span data-stu-id="e659b-165">Dapr supports this choice with its **eventual consistency** strategy.</span></span> <span data-ttu-id="e659b-166">Çok sayıda çoğaltmalarda gereksiz verileri depolayan Azure CosmosDB gibi temel bir veri deposunu göz önünde bulundurun.</span><span class="sxs-lookup"><span data-stu-id="e659b-166">Consider an underlying data store, such as Azure CosmosDB, which stores redundant data on multiple replicas.</span></span> <span data-ttu-id="e659b-167">Nihai tutarlılık sayesinde, durum deposu güncelleştirmeyi bir çoğaltmaya yazar ve yazma isteğini istemcisiyle tamamlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-167">With eventual consistency, the state store writes the update to one replica and completes the write request with the client.</span></span> <span data-ttu-id="e659b-168">Bu süreden sonra mağaza, çoğaltmaları zaman uyumsuz olarak güncelleştirecektir.</span><span class="sxs-lookup"><span data-stu-id="e659b-168">After this time, the store will asynchronously update its replicas.</span></span> <span data-ttu-id="e659b-169">Okuma istekleri, en son güncelleştirmeyi henüz almamış olan çoğaltmalar dahil olmak üzere çoğaltmalardan herhangi birinden veri döndürebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-169">Read requests can return data from any of the replicas, including those replicas that haven't yet received the latest update.</span></span>

<span data-ttu-id="e659b-170">**CP** uygulamaları kullanılabilirlik üzerinden tutarlılık seçer.</span><span class="sxs-lookup"><span data-stu-id="e659b-170">**CP** applications choose consistency over availability.</span></span> <span data-ttu-id="e659b-171">Davpr bu seçeneği **güçlü tutarlılık** stratejisi ile destekler.</span><span class="sxs-lookup"><span data-stu-id="e659b-171">Dapr supports this choice with its **strong consistency** strategy.</span></span> <span data-ttu-id="e659b-172">Bu senaryoda, durum deposu yazma isteğini tamamlamadan *önce* gerekli *çoğaltmaları (veya* bazı durumlarda, bir *çekirdeğin çekirdeği* ) zaman uyumlu olarak güncelleştirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-172">In this scenario, the state store will synchronously update *all* (or, in some cases, a *quorum* of) required replicas *before* completing the write request.</span></span> <span data-ttu-id="e659b-173">Okuma işlemleri, düzenli olarak çoğaltmalar genelinde en güncel verileri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e659b-173">Read operations will return the most up-to-date data consistently across replicas.</span></span>

<span data-ttu-id="e659b-174">Bir durum işleminin tutarlılık düzeyi, işleme bir *tutarlılık ipucu* ekleyerek belirtilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-174">The consistency level for a state operation is specified by attaching a *consistency hint* to the operation.</span></span> <span data-ttu-id="e659b-175">Aşağıdaki *kıvrımlı* komutu, güçlü bir `Hello=World` tutarlılık ipucu kullanarak bir durum deposuna bir anahtar/değer çifti Yazar:</span><span class="sxs-lookup"><span data-stu-id="e659b-175">The following *curl* command writes a `Hello=World` key/value pair to a state store using a strong consistency hint:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        {
          "key": "Hello",
          "value": "World",
          "options": {
            "consistency": "strong"
          }
        }
      ]'
```

> [!IMPORTANT]
> <span data-ttu-id="e659b-176">Bu işlem, işleme eklenen tutarlılık ipucunu karşılamak için bir Davpr durum depolama bileşenine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="e659b-176">It is up to the Dapr state store component to fulfill the consistency hint attached to the operation.</span></span> <span data-ttu-id="e659b-177">Tüm veri depoları, her iki tutarlılık düzeyini de desteklemez.</span><span class="sxs-lookup"><span data-stu-id="e659b-177">Not all data stores support both consistency levels.</span></span> <span data-ttu-id="e659b-178">Tutarlılık İpucu **ayarlanmamışsa, varsayılan** davranış son ' dur.</span><span class="sxs-lookup"><span data-stu-id="e659b-178">If no consistency hint is set, the default behavior is **eventual**.</span></span>

### <a name="concurrency"></a><span data-ttu-id="e659b-179">Eşzamanlılık</span><span class="sxs-lookup"><span data-stu-id="e659b-179">Concurrency</span></span>

<span data-ttu-id="e659b-180">Çok kullanıcılı bir uygulamada, birden çok kullanıcının aynı anda aynı verileri (aynı zamanda) güncelleştirmesidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-180">In a multi-user application, there's a chance that multiple users will update the same data concurrently (at the same time).</span></span> <span data-ttu-id="e659b-181">Davpr, çakışmaları yönetmek için iyimser eşzamanlılık denetimini (OCC) destekler.</span><span class="sxs-lookup"><span data-stu-id="e659b-181">Dapr supports optimistic concurrency control (OCC) to manage conflicts.</span></span> <span data-ttu-id="e659b-182">OCC, kullanıcıların verilerin farklı bölümlerinde çalıştığı için güncelleştirme çakışmalarının yaygın olmayan bir varsayımına dayanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-182">OCC is based on an assumption that update conflicts are uncommon because users work on different parts of the data.</span></span> <span data-ttu-id="e659b-183">Bir güncelleştirmenin başarılı olacağını varsaymak ve değilse yeniden denemek daha etkilidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-183">It's more efficient to assume an update will succeed and retry if it doesn't.</span></span> <span data-ttu-id="e659b-184">Alternatif olarak, kötümser kilitlemeyi uygulamak, veri çekişmesine neden olan uzun süreli kilitleme ile performansı etkileyebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-184">The alternative, implementing pessimistic locking, can affect performance with long-running locking causing data contention.</span></span>

<span data-ttu-id="e659b-185">DAPR, ETags kullanarak iyimser eşzamanlılık denetimini (OCC) destekler.</span><span class="sxs-lookup"><span data-stu-id="e659b-185">Dapr supports optimistic concurrency control (OCC) using ETags.</span></span> <span data-ttu-id="e659b-186">ETag, depolanan anahtar/değer çiftinin belirli bir sürümüyle ilişkili bir değerdir.</span><span class="sxs-lookup"><span data-stu-id="e659b-186">An ETag is a value associated with a specific version of a stored key/value pair.</span></span> <span data-ttu-id="e659b-187">Anahtar/değer çifti her güncelleştirilişinde ETag değeri de güncelleştirilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-187">Each time a key/value pair updates, the ETag value updates as well.</span></span> <span data-ttu-id="e659b-188">İstemci bir anahtar/değer çifti aldığında, yanıt geçerli ETag değerini içerir.</span><span class="sxs-lookup"><span data-stu-id="e659b-188">When a client retrieves a key/value pair, the response includes the current ETag value.</span></span> <span data-ttu-id="e659b-189">Bir istemci bir anahtar/değer çiftini güncelleştirdiğinde veya sildiği zaman, bu ETag değerini istek gövdesinde geri göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-189">When a client updates or deletes a key/value pair, it must send that ETag value back in the request body.</span></span> <span data-ttu-id="e659b-190">Bu sırada başka bir istemci verileri güncelleştirdiyseniz Eetiketler eşleşmez ve istek başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e659b-190">If another client has updated the data in the meantime, the ETags won't match and the request will fail.</span></span> <span data-ttu-id="e659b-191">Bu noktada, istemci güncelleştirilmiş verileri almalıdır, değişikliği yeniden yapar ve güncelleştirmeyi yeniden göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-191">At this point, the client must retrieve the updated data, make the change again, and resubmit the update.</span></span> <span data-ttu-id="e659b-192">Bu strateji **ilk yazma-WINS** olarak adlandırılır.</span><span class="sxs-lookup"><span data-stu-id="e659b-192">This strategy is called **first-write-wins**.</span></span>

<span data-ttu-id="e659b-193">Davpr Ayrıca **son yazma WINS** stratejisini da destekler.</span><span class="sxs-lookup"><span data-stu-id="e659b-193">Dapr also supports a **last-write-wins** strategy.</span></span> <span data-ttu-id="e659b-194">Bu yaklaşımda istemci, yazma isteğine bir ETag iliştirmez.</span><span class="sxs-lookup"><span data-stu-id="e659b-194">With this approach, the client doesn't attach an ETag to the write request.</span></span> <span data-ttu-id="e659b-195">Durum depolama bileşeni, temel alınan değer oturum sırasında değişmiş olsa bile güncelleştirmeye her zaman izin verir.</span><span class="sxs-lookup"><span data-stu-id="e659b-195">The state store component will always allow the update, even if the underlying value has changed during the session.</span></span> <span data-ttu-id="e659b-196">Son yazma-WINS, düşük veri çekişmesi sayesinde yüksek aktarım hızı yazma senaryolarında kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-196">Last-write-wins is useful for high-throughput write scenarios with low data contention.</span></span> <span data-ttu-id="e659b-197">Ayrıca, zaman zaman bir Kullanıcı güncelleştirmesinin üzerine yazılması toleranslı olabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-197">As well, overwriting an occasional user update can be tolerated.</span></span>

### <a name="transactions"></a><span data-ttu-id="e659b-198">İşlemler</span><span class="sxs-lookup"><span data-stu-id="e659b-198">Transactions</span></span>

<span data-ttu-id="e659b-199">Davpr, bir veri deposuna bir işlem olarak uygulanan tek bir işlem olarak *çok öğe değişiklikleri* yazabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-199">Dapr can write *multi-item changes* to a data store as a single operation implemented as a transaction.</span></span> <span data-ttu-id="e659b-200">Bu işlevsellik yalnızca [ACID](https://en.wikipedia.org/wiki/ACID) işlemlerini destekleyen veri depoları için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-200">This functionality is only available for data stores that support [ACID](https://en.wikipedia.org/wiki/ACID) transactions.</span></span> <span data-ttu-id="e659b-201">Bu yazma sırasında, bu depolar redin, MongoDB, PostgreSQL, SQL Server ve Azure CosmosDB 'yi içerir.</span><span class="sxs-lookup"><span data-stu-id="e659b-201">At the time of this writing, these stores include Redis, MongoDB, PostgreSQL, SQL Server, and Azure CosmosDB.</span></span>

<span data-ttu-id="e659b-202">Aşağıdaki örnekte, tek bir işlemde durum deposuna çoklu öğe işlemi gönderilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-202">In the example below, a multi-item operation is sent to the state store in a single transaction.</span></span> <span data-ttu-id="e659b-203">İşlemin yürütülmesi için tüm işlemlerin başarılı olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="e659b-203">All operations must succeed for the transaction to commit.</span></span> <span data-ttu-id="e659b-204">Bir veya daha fazla işlem başarısız olursa, tüm işlem geri alınır.</span><span class="sxs-lookup"><span data-stu-id="e659b-204">If one or more of the operations fail, the entire transaction rolls back.</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name>/transaction \
  -H "Content-Type: application/json" \
  -d '{
        "operations": [
          {
            "operation": "upsert",
            "request": { "key": "Key1", "value": "Value1"
            }
          },
          {
            "operation": "delete",
            "request": { "key": "Key2" }
          }
        ]
      }'
```

<span data-ttu-id="e659b-205">İşlemleri desteklemeyen veri depoları için, birden çok anahtar hala tek bir istek olarak gönderilebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-205">For data stores that don't support transactions, multiple keys can still be sent as a single request.</span></span> <span data-ttu-id="e659b-206">Aşağıdaki örnek bir **toplu** yazma işlemini göstermektedir:</span><span class="sxs-lookup"><span data-stu-id="e659b-206">The following example shows a **bulk** write operation:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/<store-name> \
  -H "Content-Type: application/json" \
  -d '[
        { "key": "Key1", "value": "Value1" },
        { "key": "Key2", "value": "Value2" }
      ]'
```

<span data-ttu-id="e659b-207">Yığın işlemleri için, Davpr her anahtar/değer çifti güncelleştirmesini, veri deposuna ayrı bir istek olarak gönderir.</span><span class="sxs-lookup"><span data-stu-id="e659b-207">For bulk operations, Dapr will submit each key/value pair update as a separate request to the data store.</span></span>

## <a name="use-the-dapr-net-sdk"></a><span data-ttu-id="e659b-208">Davpr .NET SDK 'sını kullanma</span><span class="sxs-lookup"><span data-stu-id="e659b-208">Use the Dapr .NET SDK</span></span>

<span data-ttu-id="e659b-209">Davpr .NET SDK, .NET Core platformu için dile özgü destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-209">The Dapr .NET SDK provides language-specific support for .NET Core platform.</span></span> <span data-ttu-id="e659b-210">Geliştiriciler, `DaprClient` veri okumak ve yazmak için [Bölüm 3](getting-started.md) ' te tanıtılan sınıfı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-210">Developers can use the `DaprClient` class introduced in [chapter 3](getting-started.md) to read and write data.</span></span> <span data-ttu-id="e659b-211">Aşağıdaki örnek, `DaprClient.GetStateAsync<TValue>` bir durum deposundan veri okumak için yönteminin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="e659b-211">The following example shows how to use the `DaprClient.GetStateAsync<TValue>` method to read data from a state store.</span></span> <span data-ttu-id="e659b-212">Yöntemi, depolama adını, `statestore` ve anahtarını `AMS` Parametreler olarak bekler:</span><span class="sxs-lookup"><span data-stu-id="e659b-212">The method expects the store name, `statestore`, and key, `AMS`, as parameters:</span></span>

```csharp
var weatherForecast = await daprClient.GetStateAsync<WeatherForecast>("statestore", "AMS");
```

<span data-ttu-id="e659b-213">Durum deposu anahtar için veri içermiyorsa `AMS` , sonuç olur `default(WeatherForecast)` .</span><span class="sxs-lookup"><span data-stu-id="e659b-213">If the state store contains no data for key `AMS`, the result will be `default(WeatherForecast)`.</span></span>

<span data-ttu-id="e659b-214">Veri deposuna veri yazmak için `DaprClient.SaveStateAsync<TValue>` yöntemini kullanın:</span><span class="sxs-lookup"><span data-stu-id="e659b-214">To write data to the data store, use the `DaprClient.SaveStateAsync<TValue>` method:</span></span>

```csharp
daprClient.SaveStateAsync("statestore", "AMS", weatherForecast);
```

<span data-ttu-id="e659b-215">Örnek, **en son yazma WINS** stratejisini bir ETag değeri olarak durum depolama bileşenine geçirilmediğinden kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-215">The example uses the **last-write-wins** strategy as an ETag value isn't passed to the state store component.</span></span> <span data-ttu-id="e659b-216">İyimser eşzamanlılık denetimini (OCC) **ilk yazma WINS** stratejisi ile kullanmak için, ilk olarak yöntemi kullanarak geçerli ETag 'i alın `DaprClient.GetStateAndETagAsync` .</span><span class="sxs-lookup"><span data-stu-id="e659b-216">To use optimistic concurrency control (OCC) with a **first-write-wins** strategy, first retrieve the current ETag using the `DaprClient.GetStateAndETagAsync` method.</span></span> <span data-ttu-id="e659b-217">Ardından, güncelleştirilmiş değeri yazın ve yöntemi kullanarak alınan ETag üzerinde geçiş yapın `DaprClient.TrySaveStateAsync` .</span><span class="sxs-lookup"><span data-stu-id="e659b-217">Then write the updated value and pass along the retrieved ETag using the `DaprClient.TrySaveStateAsync` method.</span></span>

```csharp
var (weatherForecast, etag) = await daprClient.GetStateAndETagAsync<WeatherForecast>("statestore", city);

// ... make some changes to the retrieved weather forecast

var result = await daprClient.TrySaveStateAsync("statestore", city, weatherForecast, etag);
```

<span data-ttu-id="e659b-218">Veriler `DaprClient.TrySaveStateAsync` alındıktan sonra durum deposunda veri (ve Ilişkili ETag) değiştirildiğinde yöntem başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="e659b-218">The `DaprClient.TrySaveStateAsync` method fails when the data (and associated ETag) has been changed in the state store after the data was retrieved.</span></span> <span data-ttu-id="e659b-219">Yöntemi, çağrının başarılı olup olmadığını göstermek için bir Boole değeri döndürür.</span><span class="sxs-lookup"><span data-stu-id="e659b-219">The method returns a boolean value to indicate whether the call succeeded.</span></span> <span data-ttu-id="e659b-220">Hata işleme stratejisi, güncelleştirilmiş verileri durum deposundan yeniden yüklemeniz, değişikliği yeniden yapmanız ve güncelleştirmeyi yeniden göndermelidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-220">A strategy to handle the failure is to simply reload the updated data from the state store, make the change again, and resubmit the update.</span></span>

<span data-ttu-id="e659b-221">Verilerdeki diğer değişikliklerden bağımsız olarak her zaman bir yazma işleminin başarılı olmasını istiyorsanız, **son yazma WINS** stratejisini kullanın.</span><span class="sxs-lookup"><span data-stu-id="e659b-221">If you always want a write to succeed regardless of other changes to the data, use the **last-write-wins** strategy.</span></span>

<span data-ttu-id="e659b-222">SDK, verileri toplu olarak alma, verileri silme ve işlemleri yürütme gibi diğer yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-222">The SDK provides other methods to retrieve data in bulk, delete data, and execute transactions.</span></span> <span data-ttu-id="e659b-223">Daha fazla bilgi için bkz. [Davpr .NET SDK deposu](https://github.com/dapr/dotnet-sdk).</span><span class="sxs-lookup"><span data-stu-id="e659b-223">For more information, see the [Dapr .NET SDK repository](https://github.com/dapr/dotnet-sdk).</span></span>

### <a name="aspnet-core-integration"></a><span data-ttu-id="e659b-224">ASP.NET Core tümleştirme</span><span class="sxs-lookup"><span data-stu-id="e659b-224">ASP.NET Core integration</span></span>

<span data-ttu-id="e659b-225">Davpr, modern bulut tabanlı Web uygulamaları oluşturmaya yönelik platformlar arası bir çatı olan ASP.NET Core da destekler.</span><span class="sxs-lookup"><span data-stu-id="e659b-225">Dapr also supports ASP.NET Core, a cross-platform framework for building modern cloud-based web applications.</span></span> <span data-ttu-id="e659b-226">Davpr SDK, durum yönetimi yeteneklerini doğrudan [ASP.NET Core modeli bağlama](/aspnet/core/mvc/models/model-binding) özelliklerine tümleştirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-226">The Dapr SDK integrates state management capabilities directly into the [ASP.NET Core model binding](/aspnet/core/mvc/models/model-binding) capabilities.</span></span> <span data-ttu-id="e659b-227">Yapılandırma basittir.</span><span class="sxs-lookup"><span data-stu-id="e659b-227">Configuration is simple.</span></span> <span data-ttu-id="e659b-228">Bir `IMVCBuilder.AddDapr` `.AddDapr` `Startup.cs` sonraki örnekte gösterildiği gibi sınıfınıza Extension metodunu ekleyerek öğesini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="e659b-228">Add the `IMVCBuilder.AddDapr` by appending the `.AddDapr` extension method in your `Startup.cs` class as shown in the next example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddControllers().AddDapr();
}
```

<span data-ttu-id="e659b-229">Bir kez yapılandırıldıktan sonra, Davpr ASP.NET Core özniteliğini kullanarak doğrudan bir denetleyici eylemine bir anahtar/değer çifti ekleyebilir `FromState` .</span><span class="sxs-lookup"><span data-stu-id="e659b-229">Once configured, Dapr can inject a key/value pair directly into a controller action using the ASP.NET Core `FromState` attribute.</span></span> <span data-ttu-id="e659b-230">Nesnesine başvurmak `DaprClient` artık gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e659b-230">Referencing the `DaprClient` object is no longer necessary.</span></span> <span data-ttu-id="e659b-231">Sonraki örnekte, belirli bir şehirde Hava durumu tahminini döndüren bir Web API 'SI gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="e659b-231">The next example shows a Web API that returns the weather forecast for a given city:</span></span>

```csharp
[HttpGet("{city}")]
public ActionResult<WeatherForecast> Get([FromState("statestore", "city")] StateEntry<WeatherForecast> forecast)
{
    if (forecast.Value == null)
    {
      return NotFound();
    }

    return forecast.Value;
}
```

<span data-ttu-id="e659b-232">Örnekte, denetleyici, özelliği kullanarak hava durumu tahminini yükler `FromState` .</span><span class="sxs-lookup"><span data-stu-id="e659b-232">In the example, the controller loads the weather forecast using the `FromState` attribute.</span></span> <span data-ttu-id="e659b-233">İlk öznitelik parametresi durum deposudur, `statestore` .</span><span class="sxs-lookup"><span data-stu-id="e659b-233">The first attribute parameter is the state store, `statestore`.</span></span> <span data-ttu-id="e659b-234">İkinci öznitelik parametresi, `city` , durum anahtarını almak için [yol şablonu](/aspnet/core/mvc/controllers/routing#route-templates) değişkeninin adıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-234">The second attribute parameter, `city`, is the name of the [route template](/aspnet/core/mvc/controllers/routing#route-templates) variable to get the state key.</span></span> <span data-ttu-id="e659b-235">İkinci parametreyi atlarsanız, `forecast` yol şablonu değişkenini aramak için, bağlantılı yöntem parametresi () adı kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e659b-235">If you omit the second parameter, the name of the bound method parameter (`forecast`) is used to look up the route template variable.</span></span>

<span data-ttu-id="e659b-236">`StateEntry`Sınıfı, tek bir anahtar/değer çifti için alınan tüm bilgilerin özelliklerini içerir: `StoreName` , `Key` , `Value` ve `ETag` .</span><span class="sxs-lookup"><span data-stu-id="e659b-236">The `StateEntry` class contains properties for all the information that is retrieved for a single key/value pair: `StoreName`, `Key`, `Value`, and `ETag`.</span></span> <span data-ttu-id="e659b-237">ETag, iyimser eşzamanlılık denetimi (OCC) stratejisi uygulamak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-237">The ETag is useful for implementing optimistic concurrency control (OCC) strategy.</span></span> <span data-ttu-id="e659b-238">Sınıfı ayrıca bir örnek gerekmeden alınan anahtar/değer verilerini silmek veya güncelleştirmek için yöntemler sağlar `DaprClient` .</span><span class="sxs-lookup"><span data-stu-id="e659b-238">The class also provides methods to delete or update retrieved key/value data without requiring a `DaprClient` instance.</span></span> <span data-ttu-id="e659b-239">Sonraki örnekte `TrySaveAsync` yöntemi, OCC kullanılarak alınan hava durumu tahminini güncelleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="e659b-239">In the next example, the `TrySaveAsync` method is used to update the retrieved weather forecast using OCC.</span></span>

```csharp
[HttpPut("{city}")]
public async Task Put(WeatherForecast updatedForecast, [FromState("statestore", "city")] StateEntry<WeatherForecast> currentForecast)
{
    // update cached current forecast with updated forecast passed into service endpoint
    currentForecast.Value = updatedForecast;

    // update state store
    var success = await currentForecast.TrySaveAsync();

    // ... check result
}
```

## <a name="state-store-components"></a><span data-ttu-id="e659b-240">Durum depolama bileşenleri</span><span class="sxs-lookup"><span data-stu-id="e659b-240">State store components</span></span>

<span data-ttu-id="e659b-241">Bu yazma sırasında, Davpr aşağıdaki işlemsel durum depoları için destek sağlar:</span><span class="sxs-lookup"><span data-stu-id="e659b-241">At the time of this writing, Dapr provides support for the following transactional state stores:</span></span>

- <span data-ttu-id="e659b-242">Azure CosmosDB</span><span class="sxs-lookup"><span data-stu-id="e659b-242">Azure CosmosDB</span></span>
- <span data-ttu-id="e659b-243">Azure SQL Sunucusu</span><span class="sxs-lookup"><span data-stu-id="e659b-243">Azure SQL Server</span></span>
- <span data-ttu-id="e659b-244">MongoDB</span><span class="sxs-lookup"><span data-stu-id="e659b-244">MongoDB</span></span>
- <span data-ttu-id="e659b-245">PostgreSQL</span><span class="sxs-lookup"><span data-stu-id="e659b-245">PostgreSQL</span></span>
- <span data-ttu-id="e659b-246">Redis</span><span class="sxs-lookup"><span data-stu-id="e659b-246">Redis</span></span>

<span data-ttu-id="e659b-247">Davpr Ayrıca CRUD işlemlerini destekleyen durum depoları için destek içerir, ancak işlemsel özellikleri içermez:</span><span class="sxs-lookup"><span data-stu-id="e659b-247">Dapr also includes support for state stores that support CRUD operations, but not transactional capabilities:</span></span>

- <span data-ttu-id="e659b-248">Hava çıkış</span><span class="sxs-lookup"><span data-stu-id="e659b-248">Aerospike</span></span>
- <span data-ttu-id="e659b-249">Azure Blob Depolama</span><span class="sxs-lookup"><span data-stu-id="e659b-249">Azure Blob Storage</span></span>
- <span data-ttu-id="e659b-250">Azure Tablo Depolama</span><span class="sxs-lookup"><span data-stu-id="e659b-250">Azure Table Storage</span></span>
- <span data-ttu-id="e659b-251">Cassandra</span><span class="sxs-lookup"><span data-stu-id="e659b-251">Cassandra</span></span>
- <span data-ttu-id="e659b-252">Cloudstate</span><span class="sxs-lookup"><span data-stu-id="e659b-252">Cloudstate</span></span>
- <span data-ttu-id="e659b-253">Couchbase</span><span class="sxs-lookup"><span data-stu-id="e659b-253">Couchbase</span></span>
- <span data-ttu-id="e659b-254">etcd</span><span class="sxs-lookup"><span data-stu-id="e659b-254">etcd</span></span>
- <span data-ttu-id="e659b-255">Google Cloud Firestore</span><span class="sxs-lookup"><span data-stu-id="e659b-255">Google Cloud Firestore</span></span>
- <span data-ttu-id="e659b-256">HashiCorp Tüketil</span><span class="sxs-lookup"><span data-stu-id="e659b-256">Hashicorp Consul</span></span>
- <span data-ttu-id="e659b-257">Tehlikeli elcast</span><span class="sxs-lookup"><span data-stu-id="e659b-257">Hazelcast</span></span>
- <span data-ttu-id="e659b-258">Memcached</span><span class="sxs-lookup"><span data-stu-id="e659b-258">Memcached</span></span>
- <span data-ttu-id="e659b-259">Zookeeper</span><span class="sxs-lookup"><span data-stu-id="e659b-259">Zookeeper</span></span>

### <a name="configuration"></a><span data-ttu-id="e659b-260">Yapılandırma</span><span class="sxs-lookup"><span data-stu-id="e659b-260">Configuration</span></span>

<span data-ttu-id="e659b-261">Yerel, şirket içinde barındırılan geliştirme için başlatıldığında, Davpr kayıtları Reddir olarak varsayılan durum deposu olarak kaydedilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-261">When initialized for local, self-hosted development, Dapr registers Redis as the default state store.</span></span> <span data-ttu-id="e659b-262">Varsayılan durum deposu yapılandırmasına bir örnek aşağıda verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="e659b-262">Here's an example of the default state store configuration.</span></span> <span data-ttu-id="e659b-263">Varsayılan adı aklınızda bulunan `statestore` :</span><span class="sxs-lookup"><span data-stu-id="e659b-263">Note the default name, `statestore`:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: statestore
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: localhost:6379
  - name: redisPassword
    value: ""
  - name: actorStateStore
    value: "true"
```

 > [!NOTE]
 > <span data-ttu-id="e659b-264">Birçok durum deposu, her biri farklı bir ada sahip tek bir uygulamaya kaydedilebilir.</span><span class="sxs-lookup"><span data-stu-id="e659b-264">Many state stores can be registered to a single application each with a different name.</span></span>

<span data-ttu-id="e659b-265">Redsıs durum deposu için `redisHost` ve `redisPassword` redsıs örneğine bağlanmak için meta veriler gerekir.</span><span class="sxs-lookup"><span data-stu-id="e659b-265">The Redis state store requires `redisHost` and `redisPassword` metadata to connect to the Redis instance.</span></span> <span data-ttu-id="e659b-266">Yukarıdaki örnekte, Red, Password (varsayılan olarak boş bir dize) düz bir dize olarak depolanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-266">In the example above, the Redis password (which is an empty string by default) is stored as a plain string.</span></span> <span data-ttu-id="e659b-267">En iyi uygulama, şifresiz metin dizelerinden kaçınmaktır ve her zaman gizli başvuruları kullanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e659b-267">The best practice is to avoid clear-text strings and always use secret references.</span></span> <span data-ttu-id="e659b-268">Gizli yönetim hakkında daha fazla bilgi edinmek için bkz. [Bölüm 10](secrets.md).</span><span class="sxs-lookup"><span data-stu-id="e659b-268">To learn more about secret management, see [chapter 10](secrets.md).</span></span>

<span data-ttu-id="e659b-269">Diğer meta veri alanı, `actorStateStore` durum deposunun aktör yapı taşı tarafından kullanılıp kullanılamayacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e659b-269">The other metadata field, `actorStateStore`, indicates whether the state store can be consumed by the actors building block.</span></span>

### <a name="key-prefix-strategies"></a><span data-ttu-id="e659b-270">Anahtar öneki stratejileri</span><span class="sxs-lookup"><span data-stu-id="e659b-270">Key prefix strategies</span></span>

<span data-ttu-id="e659b-271">Durum depolama bileşenleri, temel depodaki anahtar/değer çiftlerini depolamak için farklı stratejileri etkinleştirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-271">State store components enable different strategies to store key/value pairs in the underlying store.</span></span> <span data-ttu-id="e659b-272">Bir alışveriş sepeti hizmetinin önceki örneğini geri çekin bir müşteri dileklerimizin satın almasını isteyen öğeleri depoluyor:</span><span class="sxs-lookup"><span data-stu-id="e659b-272">Recall the earlier example of a shopping basket service storing items a customer wishes to purchase:</span></span>

```console
curl -X POST http://localhost:3500/v1.0/state/statestore \
  -H "Content-Type: application/json" \
  -d '[{
        "key": "basket1",
        "value": {
          "customerId": 1,
          "items": [
            { "itemId": "DaprHoodie", "quantity": 1 }
          ]
        }
     }]'
```

<span data-ttu-id="e659b-273">Redsıs konsol aracını kullanarak redsıs durum deposu bileşeninin verileri nasıl kalıcı hale kullandığını görmek için redo önbelleğinin içine bakın:</span><span class="sxs-lookup"><span data-stu-id="e659b-273">Using the Redis Console tool, look inside the Redis cache to see how the Redis state store component persisted the data:</span></span>

```
127.0.0.1:6379> KEYS *
1) "basketservice||basket1"

127.0.0.1:6379> HGETALL basketservice||basket1
1) "data"
2) "{\"items\":[{\"itemId\":\"DaprHoodie\",\"quantity\":1}],\"customerId\":1}"
3) "version"
4) "1"
```

<span data-ttu-id="e659b-274">Çıktı, verilerin tam redin **anahtarını** olarak gösterir `basketservice||basket1` .</span><span class="sxs-lookup"><span data-stu-id="e659b-274">The output shows the full Redis **key** for the data as `basketservice||basket1`.</span></span> <span data-ttu-id="e659b-275">Varsayılan olarak, Davpr, `application id` `basketservice` anahtar için ön ek olarak, davpr örneğinin () öğesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-275">By default, Dapr uses the `application id` of the Dapr instance (`basketservice`) as a prefix for the key.</span></span> <span data-ttu-id="e659b-276">Bu adlandırma kuralı, birden çok Davpr örneğinin, anahtar adı çakışmaları olmadan aynı veri deposunu paylaşmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-276">This naming convention enables multiple Dapr instances to share the same data store without key name collisions.</span></span> <span data-ttu-id="e659b-277">Geliştirici için her zaman, `application id` uygulamayı Davpr ile çalıştırırken aynı şekilde belirtmeniz önemlidir.</span><span class="sxs-lookup"><span data-stu-id="e659b-277">For the developer, it's critical always to specify the same `application id` when running the application with Dapr.</span></span> <span data-ttu-id="e659b-278">Atlanırsa, Davpr benzersiz bir uygulama KIMLIĞI oluşturacaktır.</span><span class="sxs-lookup"><span data-stu-id="e659b-278">If omitted, Dapr will generate a unique application ID.</span></span> <span data-ttu-id="e659b-279">Değişiklikler varsa `application id` , uygulama önceki anahtar öneki ile depolanan duruma artık erişemez.</span><span class="sxs-lookup"><span data-stu-id="e659b-279">If the `application id` changes, the application can no longer access the state stored with the previous key prefix.</span></span>

<span data-ttu-id="e659b-280">Yani, durum depolama bileşeni dosyasındaki meta veri alanındaki anahtar öneki için sabit bir *değer* yapılandırmak mümkündür `keyPrefix` .</span><span class="sxs-lookup"><span data-stu-id="e659b-280">That said, it's possible to configure a *constant value* for the key prefix in the `keyPrefix` metadata field in the state store component file.</span></span> <span data-ttu-id="e659b-281">Aşağıdaki örneği inceleyin:</span><span class="sxs-lookup"><span data-stu-id="e659b-281">Consider the following example:</span></span>

```yaml
spec:
  metadata:
  - name: keyPrefix
  - value: MyPrefix
```

<span data-ttu-id="e659b-282">Sabit anahtar ön eki, durum deposuna birden çok Davpr uygulamasında erişilmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-282">A constant key prefix enables the state store to be accessed across multiple Dapr applications.</span></span> <span data-ttu-id="e659b-283">Daha fazlası, ' ı ' `keyPrefix` nin `none` öneki tamamen atlayacak şekilde ayarlanıyor.</span><span class="sxs-lookup"><span data-stu-id="e659b-283">What's more, setting the `keyPrefix` to `none` omits the prefix completely.</span></span>

## <a name="reference-application-eshopondapr"></a><span data-ttu-id="e659b-284">Başvuru uygulaması: Eshopondadpr</span><span class="sxs-lookup"><span data-stu-id="e659b-284">Reference application: eShopOnDapr</span></span>

<span data-ttu-id="e659b-285">Bu kitap, bir başvuru uygulaması içerir `eShopOnDapr` .</span><span class="sxs-lookup"><span data-stu-id="e659b-285">This book includes a reference application entitled `eShopOnDapr`.</span></span> <span data-ttu-id="e659b-286">Daha önceki bir Microsoft mikro hizmetler başvuru uygulamasından modellenmiştir `eShopOnContainers` .</span><span class="sxs-lookup"><span data-stu-id="e659b-286">It's modeled from an earlier Microsoft microservices reference application, `eShopOnContainers`.</span></span>

<span data-ttu-id="e659b-287">Özgün [Eshoponcontainers](https://github.com/dotnet-architecture/eShopOnContainers) mimarisi, `IBasketRepository` sepet hizmeti için veri okumak ve yazmak üzere bir arabirim kullandı.</span><span class="sxs-lookup"><span data-stu-id="e659b-287">The original [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) architecture used an `IBasketRepository` interface to read and write data for the basket service.</span></span> <span data-ttu-id="e659b-288">`RedisBasketRepository`Temel veri deposu olarak Reddir kullanılarak uygulamayı sağlayan sınıf:</span><span class="sxs-lookup"><span data-stu-id="e659b-288">The `RedisBasketRepository` class provided the implementation using Redis as the underlying data store:</span></span>

```csharp
public class RedisBasketRepository : IBasketRepository
{
    private readonly ConnectionMultiplexer _redis;
    private readonly IDatabase _database;

    public RedisBasketRepository(ConnectionMultiplexer redis)
    {
        _redis = redis;
        _database = redis.GetDatabase();
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        var data = await _database.StringGetAsync(customerId);

        if (data.IsNullOrEmpty)
        {
            return null;
        }

        return JsonConvert.DeserializeObject<CustomerBasket>(data);
    }

    // ...
}
```

<span data-ttu-id="e659b-289">Bu kod, üçüncü taraf `StackExchange.Redis` NuGet paketini kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-289">This code uses the third-party `StackExchange.Redis` NuGet package.</span></span> <span data-ttu-id="e659b-290">Belirli bir müşteri için alışveriş sepetini yüklemek için aşağıdaki adımlar gereklidir:</span><span class="sxs-lookup"><span data-stu-id="e659b-290">The following steps are required to load the shopping basket for a given customer:</span></span>

1. <span data-ttu-id="e659b-291">Oluşturucuya bir Ekle `ConnectionMultiplexer` .</span><span class="sxs-lookup"><span data-stu-id="e659b-291">Inject a `ConnectionMultiplexer` into the constructor.</span></span> <span data-ttu-id="e659b-292">, `ConnectionMultiplexer` Dosyadaki bağımlılık ekleme çerçevesine kaydedilir `Startup.cs` :</span><span class="sxs-lookup"><span data-stu-id="e659b-292">The `ConnectionMultiplexer` is registered with the dependency injection framework in the `Startup.cs` file:</span></span>

   ```csharp
   services.AddSingleton<ConnectionMultiplexer>(sp =>
   {
       var settings = sp.GetRequiredService<IOptions<BasketSettings>>().Value;
       var configuration = ConfigurationOptions.Parse(settings.ConnectionString, true);
       configuration.ResolveDns = true;
       return ConnectionMultiplexer.Connect(configuration);
   });
   ```

1. <span data-ttu-id="e659b-293">`ConnectionMultiplexer`Her bir tüketen sınıfta bir örnek oluşturmak için öğesini kullanın `IDatabase` .</span><span class="sxs-lookup"><span data-stu-id="e659b-293">Use the `ConnectionMultiplexer` to create an `IDatabase` instance in each consuming class.</span></span>

1. <span data-ttu-id="e659b-294">`IDatabase`Anahtar olarak verilen öğesini kullanarak bir redin StringGet çağrısını yürütmek için örneği kullanın `customerId` .</span><span class="sxs-lookup"><span data-stu-id="e659b-294">Use the `IDatabase` instance to execute a Redis StringGet call using the given `customerId` as the key.</span></span>

1. <span data-ttu-id="e659b-295">Redsıs 'ten verilerin yüklenip yüklenmediğini denetle; Aksi takdirde, döndürün `null` .</span><span class="sxs-lookup"><span data-stu-id="e659b-295">Check if data is loaded from Redis; if not, return `null`.</span></span>

1. <span data-ttu-id="e659b-296">Redsıs 'den nesnesine veri serisini kaldırma `CustomerBasket` ve sonucu döndürme.</span><span class="sxs-lookup"><span data-stu-id="e659b-296">Deserialize the data from Redis to a `CustomerBasket` object and return the result.</span></span>

<span data-ttu-id="e659b-297">Güncelleştirilmiş [Eshopondadpr](https://github.com/dotnet-architecture/eShopOnDapr) başvuru uygulamasında, `DaprBasketRepository` sınıfının yerini alan yeni bir sınıf `RedisBasketRepository` :</span><span class="sxs-lookup"><span data-stu-id="e659b-297">In the updated [eShopOnDapr](https://github.com/dotnet-architecture/eShopOnDapr) reference application, a new `DaprBasketRepository` class replaces the `RedisBasketRepository` class:</span></span>

```csharp
public class DaprBasketRepository : IBasketRepository
{
    private const string StoreName = "eshop-basket-statestore";

    private readonly DaprClient _daprClient;

    public DaprBasketRepository(DaprClient daprClient)
    {
        _daprClient = daprClient ?? throw new ArgumentNullException(nameof(daprClient));;
    }

    public async Task<CustomerBasket> GetBasketAsync(string customerId)
    {
        return await _daprClient.GetStateAsync<CustomerBasket>(StoreName, customerId);
    }

    // ...
}
```

<span data-ttu-id="e659b-298">Güncelleştirilmiş kod, durum yönetimi yapı taşını kullanarak veri okumak ve yazmak için Davpr .NET SDK 'sını kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-298">The updated code uses the Dapr .NET SDK to read and write data using the state management building block.</span></span> <span data-ttu-id="e659b-299">Bir müşterinin sepetini yüklemeye yönelik yeni adımlar önemli ölçüde basitleştirilmiştir:</span><span class="sxs-lookup"><span data-stu-id="e659b-299">The new steps to load the basket for a customer are dramatically simplified:</span></span>

1. <span data-ttu-id="e659b-300">Oluşturucuya bir Ekle `DaprClient` .</span><span class="sxs-lookup"><span data-stu-id="e659b-300">Inject a `DaprClient` into the constructor.</span></span> <span data-ttu-id="e659b-301">, `DaprClient` Dosyadaki bağımlılık ekleme çerçevesine kaydedilir `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="e659b-301">The `DaprClient` is registered with the dependency injection framework in the `Startup.cs` file.</span></span>
1. <span data-ttu-id="e659b-302">Bu `DaprClient.GetStateAsync` yöntemi, müşterinin alışveriş sepeti öğelerini yapılandırılmış durum deposundan yüklemek ve sonucu döndürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="e659b-302">Use the `DaprClient.GetStateAsync` method to load the customer's shopping basket items from the configured state store and return the result.</span></span>

<span data-ttu-id="e659b-303">Güncelleştirilmiş uygulama yine de temel alınan veri deposu olarak redde kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-303">The updated implementation still uses Redis as the underlying data store.</span></span> <span data-ttu-id="e659b-304">Ancak, DAPR `StackExchange.Redis` başvuruları ve karmaşıklığı uygulamadan soyutlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-304">But, Dapr abstracts the `StackExchange.Redis` references and complexity from the application.</span></span> <span data-ttu-id="e659b-305">Bir Davpr yapılandırma dosyası gereklidir:</span><span class="sxs-lookup"><span data-stu-id="e659b-305">A Dapr configuration file is all that's needed:</span></span>

```yaml
apiVersion: dapr.io/v1alpha1
kind: Component
metadata:
  name: eshop-basket-statestore
  namespace: eshop
spec:
  type: state.redis
  version: v1
  metadata:
  - name: redisHost
    value: redis:6379
  - name: redisPassword
    secretKeyRef:
      name: redisPassword
auth:
  secretStore: eshop-secretstore
```

<span data-ttu-id="e659b-306">Ayrıca, Davpr uygulamasının temel veri deposunun değiştirilmesini de basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-306">The Dapr implementation also simplifies changing the underlying data store.</span></span> <span data-ttu-id="e659b-307">Örneğin, Azure Tablo depolamaya geçiş yalnızca yapılandırma dosyasının içeriğinin değiştirilmesini gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-307">For example, switching to Azure Table Storage requires only changing the contents of the configuration file.</span></span> <span data-ttu-id="e659b-308">Kod değişikliği gerekli değildir.</span><span class="sxs-lookup"><span data-stu-id="e659b-308">No code changes are necessary.</span></span>

## <a name="summary"></a><span data-ttu-id="e659b-309">Özet</span><span class="sxs-lookup"><span data-stu-id="e659b-309">Summary</span></span>

<span data-ttu-id="e659b-310">Davpr durum yönetimi yapı taşı, anahtar/değer verilerini çeşitli veri depolarında depolamak için bir API sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-310">The Dapr state management building block offers an API for storing key/value data across various data stores.</span></span> <span data-ttu-id="e659b-311">API, için destek sağlar:</span><span class="sxs-lookup"><span data-stu-id="e659b-311">The API provides support for:</span></span>

- <span data-ttu-id="e659b-312">Toplu işlemler</span><span class="sxs-lookup"><span data-stu-id="e659b-312">Bulk operations</span></span>
- <span data-ttu-id="e659b-313">Güçlü ve nihai tutarlılık</span><span class="sxs-lookup"><span data-stu-id="e659b-313">Strong and eventual consistency</span></span>
- <span data-ttu-id="e659b-314">İyimser eşzamanlılık denetimi</span><span class="sxs-lookup"><span data-stu-id="e659b-314">Optimistic concurrency control</span></span>
- <span data-ttu-id="e659b-315">Çoklu öğe işlemleri</span><span class="sxs-lookup"><span data-stu-id="e659b-315">Multi-item transactions</span></span>

<span data-ttu-id="e659b-316">.NET SDK, .NET Core ve ASP.NET Core için dile özgü destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="e659b-316">The .NET SDK provides language-specific support for .NET Core and ASP.NET Core.</span></span> <span data-ttu-id="e659b-317">Model bağlama tümleştirmesi, ASP.NET Core denetleyicisi eylem yöntemlerinden durum erişimini ve güncelleştirilmesini basitleştirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-317">Model binding integration simplifies accessing and updating state from ASP.NET Core controller action methods.</span></span>

<span data-ttu-id="e659b-318">Eshopondadpr başvuru uygulamasında, Davpr durum yönetimine geçme avantajları net değildir:</span><span class="sxs-lookup"><span data-stu-id="e659b-318">In the eShopOnDapr reference application, the benefits to moving to Dapr state management are clear:</span></span>

1. <span data-ttu-id="e659b-319">Yeni uygulama daha az kod satırı kullanır.</span><span class="sxs-lookup"><span data-stu-id="e659b-319">The new implementation uses fewer lines of code.</span></span>
1. <span data-ttu-id="e659b-320">Üçüncü taraf API 'nin karmaşıklığını soyutlar `StackExchange.Redis` .</span><span class="sxs-lookup"><span data-stu-id="e659b-320">It abstracts away the complexity of the third-party `StackExchange.Redis` API.</span></span>
1. <span data-ttu-id="e659b-321">Temel Redsıs önbelleğinin farklı bir veri deposu türüyle değiştirilmesi artık yalnızca durum depolama yapılandırma dosyasında değişiklik yapılmasını gerektirir.</span><span class="sxs-lookup"><span data-stu-id="e659b-321">Replacing the underlying Redis cache with a different type of data store now only requires changes to the state store configuration file.</span></span>

### <a name="references"></a><span data-ttu-id="e659b-322">Başvurular</span><span class="sxs-lookup"><span data-stu-id="e659b-322">References</span></span>

- [<span data-ttu-id="e659b-323">Davpr desteklenen durum depoları</span><span class="sxs-lookup"><span data-stu-id="e659b-323">Dapr supported state stores</span></span>](https://docs.dapr.io/operations/components/setup-state-store/supported-state-stores/)

> [!div class="step-by-step"]
> <span data-ttu-id="e659b-324">[Önceki](reference-application.md) 
>  [Sonraki](service-invocation.md)</span><span class="sxs-lookup"><span data-stu-id="e659b-324">[Previous](reference-application.md)
[Next](service-invocation.md)</span></span>
