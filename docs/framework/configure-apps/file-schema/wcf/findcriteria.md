---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: eb8ff3905f7696f4c71a79e31db1b8f82c9f0d3b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69925592"
---
# <a name="findcriteria"></a><span data-ttu-id="f2f10-101">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="f2f10-101">\<findCriteria></span></span>
<span data-ttu-id="f2f10-102">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="f2f10-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f2f10-103">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2f10-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="f2f10-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f2f10-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f2f10-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f2f10-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f10-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f2f10-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            </contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      </standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f10-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f10-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f2f10-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="f2f10-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f10-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="f2f10-109">Attributes</span></span>  
  
|<span data-ttu-id="f2f10-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="f2f10-110">Attribute</span></span>|<span data-ttu-id="f2f10-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f10-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2f10-112">süre</span><span class="sxs-lookup"><span data-stu-id="f2f10-112">duration</span></span>|<span data-ttu-id="f2f10-113">Ağdaki hizmetlerden gelen yanıtlar için beklenecek en uzun süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="f2f10-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="f2f10-114">Varsayılan süre 20 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="f2f10-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="f2f10-115">maxResults</span><span class="sxs-lookup"><span data-stu-id="f2f10-115">maxResults</span></span>|<span data-ttu-id="f2f10-116">Ağ veya Internet üzerindeki hizmetlerden, beklenecek en fazla yanıt sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="f2f10-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="f2f10-117">`duration` Öznitelikte belirtilen değerin süresi geçtiğinde en fazla yanıt alınmışsa, bulma işlemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="f2f10-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="f2f10-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="f2f10-118">scopeMatchBy</span></span>|<span data-ttu-id="f2f10-119">Araştırma iletisindeki kapsamları uç noktayla eşleştirirken kullanılacak eşleşen algoritmayı belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="f2f10-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="f2f10-120">Desteklenen beş kapsam eşleştirme kuralı vardır.</span><span class="sxs-lookup"><span data-stu-id="f2f10-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="f2f10-121">Kapsam eşleştirme kuralı belirtmezseniz, `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f2f10-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="f2f10-122">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="f2f10-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2f10-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f10-123">Child Elements</span></span>  
  
|<span data-ttu-id="f2f10-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2f10-124">Element</span></span>|<span data-ttu-id="f2f10-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f10-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f10-126">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="f2f10-126">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="f2f10-127">İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f2f10-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="f2f10-128">\<\<FindCriteria > Uzantıları ></span><span class="sxs-lookup"><span data-stu-id="f2f10-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="f2f10-129">Uzantıları sağlayan XML öğe nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f2f10-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="f2f10-130">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="f2f10-130">\<scopes></span></span>](scopes.md)|<span data-ttu-id="f2f10-131">Belirli bir hizmet veya hizmeti bulmak için bulma işlemi sırasında kullanılan mutlak URI 'Ler içeren nesneler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="f2f10-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="f2f10-132">Belirli bir hizmet bulunursa, hizmet URI 'si ile kapsam URI 'SI arasında başarılı bir eşleşme yapılmıştır, bazen eşleştirmeyi ele alan kapsam kurallarının yardımıyla.</span><span class="sxs-lookup"><span data-stu-id="f2f10-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f10-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="f2f10-133">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f10-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="f2f10-134">Element</span></span>|<span data-ttu-id="f2f10-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f2f10-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f10-136">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f2f10-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="f2f10-137">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="f2f10-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2f10-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f2f10-138">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
