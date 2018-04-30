---
title: Keşif Bulma ve FindCriteria
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 99016fa4-1778-495b-b4cc-0e22fbec42c6
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17ca5e12390e33525f0223917e4c72556a2a2ec7
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="discovery-find-and-findcriteria"></a><span data-ttu-id="b3f9e-102">Keşif Bulma ve FindCriteria</span><span class="sxs-lookup"><span data-stu-id="b3f9e-102">Discovery Find and FindCriteria</span></span>
<span data-ttu-id="b3f9e-103">Bir bulma bulma işlemi bir veya daha fazla Hizmetleri bulmak için bir istemci tarafından başlatılan ve bulma ana Eylemler biridir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-103">A discovery find operation is initiated by a client to discover one or more services and is one of the main actions in discovery.</span></span> <span data-ttu-id="b3f9e-104">Bir bulma gerçekleştirme WS-bulma araştırma ileti ağ üzerinden gönderir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-104">Performing a find sends a WS-Discovery Probe message over the network.</span></span> <span data-ttu-id="b3f9e-105">Ölçütlere uyan Hizmetleri yanıt WS-bulma ProbeMatch iletileriyle belirtilen.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-105">Services that match the criteria specified reply with WS-Discovery ProbeMatch messages.</span></span> <span data-ttu-id="b3f9e-106">Bulma iletileri hakkında daha fazla bilgi için bkz: [WS-bulma belirtimi](http://go.microsoft.com/fwlink/?LinkID=122347).</span><span class="sxs-lookup"><span data-stu-id="b3f9e-106">For more information about discovery messages, see the [WS-Discovery specification](http://go.microsoft.com/fwlink/?LinkID=122347).</span></span>  
  
## <a name="discoveryclient"></a><span data-ttu-id="b3f9e-107">DiscoveryClient</span><span class="sxs-lookup"><span data-stu-id="b3f9e-107">DiscoveryClient</span></span>  
 <span data-ttu-id="b3f9e-108"><xref:System.ServiceModel.Discovery.DiscoveryClient> Sınıfı, bulma işlemleri ve kolay bulma istemci işlemlerini gerçekleştirme sağlar yapmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-108">The <xref:System.ServiceModel.Discovery.DiscoveryClient> class provides the mechanism to perform find operations and makes performing discovery client operations easy.</span></span> <span data-ttu-id="b3f9e-109">İçerdiği bir <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> (engelleme) olarak zaman uyumlu bir bulma gerçekleştirir, yöntemi ve <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> engelleyici olmayan bir zaman uyumsuz bulma başlatan yöntem.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-109">It contains a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> method, which performs a (blocking) synchronous find, and a <xref:System.ServiceModel.Discovery.DiscoveryClient.FindAsync%2A> method, which initiates a non-blocking asynchronous find.</span></span> <span data-ttu-id="b3f9e-110">Her iki yöntem ele bir <xref:System.ServiceModel.Discovery.FindCriteria> parametresi ve kullanıcı sonuçları sağlamak bir <xref:System.ServiceModel.Discovery.FindResponse> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-110">Both methods take a <xref:System.ServiceModel.Discovery.FindCriteria> parameter, and provide results to the user through a <xref:System.ServiceModel.Discovery.FindResponse> object.</span></span>  
  
## <a name="findcriteria"></a><span data-ttu-id="b3f9e-111">FindCriteria</span><span class="sxs-lookup"><span data-stu-id="b3f9e-111">FindCriteria</span></span>  
 <span data-ttu-id="b3f9e-112"><xref:System.ServiceModel.Discovery.FindCriteria> Aradığınız hangi hizmetlerin belirtin, arama ölçütleri gruplandırılır ve (ne kadar süreyle arama son) sonlandırma ölçütleri Bul çeşitli özelliklere sahiptir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-112"><xref:System.ServiceModel.Discovery.FindCriteria> has several properties, which can be grouped into search criteria, which specify what services you are looking for, and find termination criteria (how long the search should last).</span></span> <span data-ttu-id="b3f9e-113">A <xref:System.ServiceModel.Discovery.FindCriteria> birden fazla arama ölçütü içerebilir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-113">A <xref:System.ServiceModel.Discovery.FindCriteria> can contain multiple search criteria.</span></span> <span data-ttu-id="b3f9e-114">Varsayılan olarak, hizmet bileşenlerinin tümünü eşleşmelidir Aksi takdirde, kendisini eşleşen hizmet dikkate almaz.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-114">By default, the service has to match all of the components otherwise it does not consider itself a matching service.</span></span> <span data-ttu-id="b3f9e-115">Yalnızca bazı ölçütlerle eşleşen Hizmetleri bulmak istiyorsanız, hizmette özel bulma mantığını uygulayabilirsiniz veya birden çok sorgu kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-115">If you want to find services that only match some of the criteria, you can implement custom find logic on the service or you can use multiple queries.</span></span>  
  
 <span data-ttu-id="b3f9e-116">Arama ölçütlerini şunları içerir:</span><span class="sxs-lookup"><span data-stu-id="b3f9e-116">Search criteria include:</span></span>  
  
-   <span data-ttu-id="b3f9e-117"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> -İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-117"><xref:System.ServiceModel.Discovery.Configuration.ContractTypeNameElement> - Optional.</span></span> <span data-ttu-id="b3f9e-118">Aranan hizmeti ve genellikle bir hizmet için arama yaparken kullanılan ölçütleri sözleşme adı.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-118">The contract name of the service being searched for and the criteria typically used when searching for a service.</span></span> <span data-ttu-id="b3f9e-119">Birden fazla sözleşme adı belirtilirse, yalnızca hizmet uç noktaları tüm sözleşmeleri eşleşen yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-119">If more than one contract name is specified, only service endpoints matching ALL contracts reply.</span></span> <span data-ttu-id="b3f9e-120">İçinde unutmayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir uç nokta yalnızca bir sözleşme destekleyebilir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-120">Note that in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] an endpoint can only support one contract.</span></span>  
  
-   <span data-ttu-id="b3f9e-121"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> -İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-121"><xref:System.ServiceModel.Discovery.Configuration.ScopeElement> - Optional.</span></span> <span data-ttu-id="b3f9e-122">Tek tek hizmet uç noktaları kategorilere ayırmak için kullanılan mutlak URI kapsamlardır.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-122">Scopes are absolute URIs that are used to categorize individual service endpoints.</span></span> <span data-ttu-id="b3f9e-123">Bu burada aynı sözleşme birden çok uç noktalarını kullanıma sunar ve uç noktaları kısmı için bir şekilde aramak istediğiniz senaryolarda kullanmak isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-123">You may want to use this in scenarios where multiple endpoints expose the same contract and you want a way to search for a subset of the endpoints.</span></span> <span data-ttu-id="b3f9e-124">Birden çok kapsam belirtilmezse, yalnızca tüm kapsamlar eşleşen hizmet uç yanıtlayın.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-124">If more than one scope is specified, only service endpoints matching ALL scopes reply.</span></span>  
  
-   <span data-ttu-id="b3f9e-125"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> -Bitiş Noktası'nın araştırma iletiyle kapsamlarda eşleşen sırasında kullanılacak eşleşen algoritmasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-125"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchBy%2A> - Specifies the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span> <span data-ttu-id="b3f9e-126">Beş desteklenen kapsam eşleşen kural vardır:</span><span class="sxs-lookup"><span data-stu-id="b3f9e-126">There are five supported scope-matching rules:</span></span>  
  
    -   <span data-ttu-id="b3f9e-127"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> büyük küçük harfe duyarlı temel bir karşılaştırma dizesi.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-127"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByExact?displayProperty=nameWithType> does a basic case-sensitive string comparison.</span></span>  
  
    -   <span data-ttu-id="b3f9e-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> eşleşme kesimleri tarafından ayrılmış "/".</span><span class="sxs-lookup"><span data-stu-id="b3f9e-128"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix?displayProperty=nameWithType> matches by segments separated by "/".</span></span> <span data-ttu-id="b3f9e-129">Bir arama http://contoso/building1 kapsamlı bir hizmet eşleşen http://contoso/building/floor1.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-129">A search for http://contoso/building1 matches a service with scope http://contoso/building/floor1.</span></span> <span data-ttu-id="b3f9e-130">Eşleşmiyor Not http://contoso/building100 son iki bölümü eşleşmediği için.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-130">Note that it does not match http://contoso/building100 because the last two segments do not match.</span></span>  
  
    -   <span data-ttu-id="b3f9e-131"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> kapsamları bir LDAP URL'si kullanarak kesimleri ile eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-131"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByLdap?displayProperty=nameWithType> matches scopes by segments using an LDAP URL.</span></span>  
  
    -   <span data-ttu-id="b3f9e-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> tam olarak bir UUID dizesi kullanarak kapsamları eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-132"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByUuid?displayProperty=nameWithType> matches scopes exactly using a UUID string.</span></span>  
  
    -   <span data-ttu-id="b3f9e-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> bir kapsam belirtmeyen Hizmetleri eşleşir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-133"><xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByNone?displayProperty=nameWithType> matches only those services that do not specify a scope.</span></span>  
  
     <span data-ttu-id="b3f9e-134">Bir kapsam eşleşen kural belirtilmezse, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-134">If a scope-matching rule is not specified, <xref:System.ServiceModel.Discovery.FindCriteria.ScopeMatchByPrefix> is used.</span></span>  
  
 <span data-ttu-id="b3f9e-135">Sonlandırma kriterleri içerir:</span><span class="sxs-lookup"><span data-stu-id="b3f9e-135">Termination criteria include:</span></span>  
  
1.  <span data-ttu-id="b3f9e-136"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> -Ağ üzerinde yanıtları Hizmetleri'nden beklemek en uzun süre.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-136"><xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> - The maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="b3f9e-137">Varsayılan süre 20 saniye kullanılır.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-137">The default duration is 20 seconds.</span></span>  
  
2.  <span data-ttu-id="b3f9e-138"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> -En fazla bekleme yanıt sayısı.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-138"><xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> - The maximum number of replies to wait for.</span></span> <span data-ttu-id="b3f9e-139">Varsa <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> önce alınan yanıtların <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> geçtikten, bulma işlemi sona erer.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-139">If <xref:System.ServiceModel.Discovery.FindCriteria.MaxResults%2A> replies are received before <xref:System.ServiceModel.Discovery.FindCriteria.Duration%2A> has elapsed, the find operation ends.</span></span>  
  
## <a name="findresponse"></a><span data-ttu-id="b3f9e-140">FindResponse</span><span class="sxs-lookup"><span data-stu-id="b3f9e-140">FindResponse</span></span>  
 <span data-ttu-id="b3f9e-141"><xref:System.ServiceModel.Discovery.FindResponse> sahip bir <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> eşleşen ağ üzerindeki hizmet tarafından gönderilen yanıtı içeren koleksiyon özelliği.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-141"><xref:System.ServiceModel.Discovery.FindResponse> has an <xref:System.ServiceModel.Discovery.FindResponse.Endpoints%2A> collection property that contains any replies sent by matching services on the network.</span></span> <span data-ttu-id="b3f9e-142">Hiçbir hizmet yanıtlanan, boş bir koleksiyonudur.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-142">If no services replied, the collection is empty.</span></span> <span data-ttu-id="b3f9e-143">Bir veya daha fazla hizmet yanıt verdi, her yanıt depolanan bir <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> adresi, sözleşme ve hizmet hakkında bazı ek bilgiler içeren nesne.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-143">If one or more services replied, each reply is stored in an <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> object, which contains the address, contract, and some additional information about the service.</span></span>  
  
 <span data-ttu-id="b3f9e-144">Aşağıdaki örnek kodda bir bulma işlemi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-144">The following example shows how to perform a find operation in code.</span></span>  
  
```  
// Create DiscoveryClient  
DiscoveryClient discoveryClient = new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
// Create FindCriteria  
FindCriteria findCriteria = new FindCriteria(typeof(IPrinterService));  
findCriteria.Scopes.Add(new Uri("http://www.contoso.com/building1/floor1"));  
findCriteria.Duration = TimeSpan.FromSeconds(10);   
  
// Find ICalculatorService endpoints              
FindResponse findResponse = discoveryClient.Find(findCriteria);  
  
Console.WriteLine("Found {0} ICalculatorService endpoint(s).", findResponse.Endpoints.Count)  
```  
  
## <a name="see-also"></a><span data-ttu-id="b3f9e-145">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b3f9e-145">See Also</span></span>  
 [<span data-ttu-id="b3f9e-146">WCF Bulmaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b3f9e-146">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 [<span data-ttu-id="b3f9e-147">Keşif İstemcisi Kanalını Kullanma</span><span class="sxs-lookup"><span data-stu-id="b3f9e-147">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 [<span data-ttu-id="b3f9e-148">Kapsamlarla Bulma</span><span class="sxs-lookup"><span data-stu-id="b3f9e-148">Discovery with Scopes</span></span>](../../../../docs/framework/wcf/samples/discovery-with-scopes-sample.md)  
 [<span data-ttu-id="b3f9e-149">Zaman Uyumsuz Bulma</span><span class="sxs-lookup"><span data-stu-id="b3f9e-149">Asynchronous Find</span></span>](../../../../docs/framework/wcf/samples/asynchronous-find-sample.md)  
 [<span data-ttu-id="b3f9e-150">Temel</span><span class="sxs-lookup"><span data-stu-id="b3f9e-150">Basic</span></span>](../../../../docs/framework/wcf/samples/basic-sample.md)
