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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b428d1a95ec6f1f493c831f66223f52e4723990c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="21af5-102">&lt;findCriteria&gt;</span><span class="sxs-lookup"><span data-stu-id="21af5-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="21af5-103">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="21af5-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="21af5-104">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="21af5-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="21af5-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="21af5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="21af5-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="21af5-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21af5-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21af5-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21af5-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="21af5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="21af5-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="21af5-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21af5-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="21af5-110">Attributes</span></span>  
  
|<span data-ttu-id="21af5-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="21af5-111">Attribute</span></span>|<span data-ttu-id="21af5-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21af5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="21af5-113">süre</span><span class="sxs-lookup"><span data-stu-id="21af5-113">duration</span></span>|<span data-ttu-id="21af5-114">Ağ üzerinde yanıtları Hizmetleri'nden için beklenecek en uzun süreyi belirtir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="21af5-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="21af5-115">Varsayılan süre 20 saniyedir...</span><span class="sxs-lookup"><span data-stu-id="21af5-115">The default duration is 20 seconds..</span></span>|  
|<span data-ttu-id="21af5-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="21af5-116">maxResults</span></span>|<span data-ttu-id="21af5-117">Bir ağ veya Internet üzerinde Hizmetleri'nden beklemek zorunda yanıtların en fazla sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="21af5-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="21af5-118">Belirtilen değer önce alınan en büyük yanıt varsa `duration` özniteliği geçtikten, bulma işlemi sona erer.</span><span class="sxs-lookup"><span data-stu-id="21af5-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="21af5-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="21af5-119">scopeMatchBy</span></span>|<span data-ttu-id="21af5-120">Uç noktası'nın araştırma iletiyle kapsamlarda eşleşen sırasında kullanılacak eşleştirme algoritması belirtin URI.</span><span class="sxs-lookup"><span data-stu-id="21af5-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="21af5-121">Beş desteklenen kapsam eşleştirme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="21af5-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="21af5-122">Bir kapsam eşleşen kural belirtmezseniz `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="21af5-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="21af5-123">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="21af5-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21af5-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="21af5-124">Child Elements</span></span>  
  
|<span data-ttu-id="21af5-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="21af5-125">Element</span></span>|<span data-ttu-id="21af5-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21af5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21af5-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="21af5-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="21af5-128">İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonunu...</span><span class="sxs-lookup"><span data-stu-id="21af5-128">A collection of configuration elements that contain the names of workflow service contract types..</span></span>|  
|<span data-ttu-id="21af5-129">\<Uzantıları >, \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="21af5-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="21af5-130">Uzantılar sağlarlar XML öğesi nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="21af5-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="21af5-131">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="21af5-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="21af5-132">Mutlak URI içeren bir bulma işlemi sırasında belirli bir hizmeti veya hizmetleri bulmak için kullanılan nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="21af5-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="21af5-133">Belirli hizmet bulunursa, başarılı bir eşleşme hizmet URI'si ile eşleşen zorluklar işlemek kapsam kuralları yardımıyla bazen kapsam URI arasındaki yapıldı.</span><span class="sxs-lookup"><span data-stu-id="21af5-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21af5-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="21af5-134">Parent Elements</span></span>  
  
|<span data-ttu-id="21af5-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="21af5-135">Element</span></span>|<span data-ttu-id="21af5-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21af5-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="21af5-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="21af5-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="21af5-138">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="21af5-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21af5-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21af5-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
