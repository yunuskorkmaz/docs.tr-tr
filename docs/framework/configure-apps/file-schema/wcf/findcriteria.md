---
title: '&lt;findCriteria&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f804cdb57355b62db25a559dc3c5db7d4d69369e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="d1e3c-102">&lt;findCriteria&gt;</span><span class="sxs-lookup"><span data-stu-id="d1e3c-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="d1e3c-103">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="d1e3c-104">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="d1e3c-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="d1e3c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="d1e3c-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d1e3c-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1e3c-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d1e3c-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String" namespace="String" />
            <contractTypeNames>
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1e3c-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1e3c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1e3c-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1e3c-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d1e3c-110">Attributes</span></span>  
  
|<span data-ttu-id="d1e3c-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d1e3c-111">Attribute</span></span>|<span data-ttu-id="d1e3c-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1e3c-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1e3c-113">süre</span><span class="sxs-lookup"><span data-stu-id="d1e3c-113">duration</span></span>|<span data-ttu-id="d1e3c-114">Ağ üzerinde yanıtları Hizmetleri'nden için beklenecek en uzun süreyi belirtir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="d1e3c-115">Varsayılan süre 20 saniyedir...</span><span class="sxs-lookup"><span data-stu-id="d1e3c-115">The default duration is 20 seconds..</span></span>|  
|<span data-ttu-id="d1e3c-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="d1e3c-116">maxResults</span></span>|<span data-ttu-id="d1e3c-117">Bir ağ veya Internet üzerinde Hizmetleri'nden beklemek zorunda yanıtların en fazla sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="d1e3c-118">Belirtilen değer önce alınan en büyük yanıt varsa `duration` özniteliği geçtikten, bulma işlemi sona erer.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="d1e3c-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="d1e3c-119">scopeMatchBy</span></span>|<span data-ttu-id="d1e3c-120">Uç noktası'nın araştırma iletiyle kapsamlarda eşleşen sırasında kullanılacak eşleştirme algoritması belirtin URI.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="d1e3c-121">Beş desteklenen kapsam eşleştirme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="d1e3c-122">Bir kapsam eşleşen kural belirtmezseniz `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="d1e3c-123">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1e3c-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1e3c-124">Child Elements</span></span>  
  
|<span data-ttu-id="d1e3c-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1e3c-125">Element</span></span>|<span data-ttu-id="d1e3c-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1e3c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1e3c-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="d1e3c-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="d1e3c-128">İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonunu...</span><span class="sxs-lookup"><span data-stu-id="d1e3c-128">A collection of configuration elements that contain the names of workflow service contract types..</span></span>|  
|<span data-ttu-id="d1e3c-129">\<Uzantıları >, \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="d1e3c-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="d1e3c-130">Uzantılar sağlarlar XML öğesi nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="d1e3c-131">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="d1e3c-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="d1e3c-132">Mutlak URI içeren bir bulma işlemi sırasında belirli bir hizmeti veya hizmetleri bulmak için kullanılan nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="d1e3c-133">Belirli hizmet bulunursa, başarılı bir eşleşme hizmet URI'si ile eşleşen zorluklar işlemek kapsam kuralları yardımıyla bazen kapsam URI arasındaki yapıldı.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1e3c-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d1e3c-134">Parent Elements</span></span>  
  
|<span data-ttu-id="d1e3c-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="d1e3c-135">Element</span></span>|<span data-ttu-id="d1e3c-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d1e3c-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1e3c-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d1e3c-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d1e3c-138">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1e3c-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d1e3c-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
