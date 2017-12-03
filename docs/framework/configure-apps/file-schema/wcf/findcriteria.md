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
ms.openlocfilehash: 8643c4f0affb9f693b42cd7631696200bb279489
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltfindcriteriagt"></a><span data-ttu-id="ccd78-102">&lt;findCriteria&gt;</span><span class="sxs-lookup"><span data-stu-id="ccd78-102">&lt;findCriteria&gt;</span></span>
<span data-ttu-id="ccd78-103">Bir bulma hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ccd78-103">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ccd78-104">Ölçüt arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütleri (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="ccd78-104">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="ccd78-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="ccd78-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="ccd78-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ccd78-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd78-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ccd78-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ccd78-108">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccd78-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ccd78-109">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ccd78-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ccd78-110">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ccd78-110">Attributes</span></span>  
  
|<span data-ttu-id="ccd78-111">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ccd78-111">Attribute</span></span>|<span data-ttu-id="ccd78-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccd78-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ccd78-113">süre</span><span class="sxs-lookup"><span data-stu-id="ccd78-113">duration</span></span>|<span data-ttu-id="ccd78-114">Ağ üzerinde yanıtları Hizmetleri'nden için beklenecek en uzun süreyi belirtir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="ccd78-114">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="ccd78-115">Varsayılan süre 20 saniyedir...</span><span class="sxs-lookup"><span data-stu-id="ccd78-115">The default duration is 20 seconds..</span></span>|  
|<span data-ttu-id="ccd78-116">maxResults</span><span class="sxs-lookup"><span data-stu-id="ccd78-116">maxResults</span></span>|<span data-ttu-id="ccd78-117">Bir ağ veya Internet üzerinde Hizmetleri'nden beklemek zorunda yanıtların en fazla sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ccd78-117">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="ccd78-118">Belirtilen değer önce alınan en büyük yanıt varsa `duration` özniteliği geçtikten, bulma işlemi sona erer.</span><span class="sxs-lookup"><span data-stu-id="ccd78-118">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="ccd78-119">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="ccd78-119">scopeMatchBy</span></span>|<span data-ttu-id="ccd78-120">Uç noktası'nın araştırma iletiyle kapsamlarda eşleşen sırasında kullanılacak eşleştirme algoritması belirtin URI.</span><span class="sxs-lookup"><span data-stu-id="ccd78-120">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="ccd78-121">Beş desteklenen kapsam eşleştirme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="ccd78-121">There are five supported scope-matching rules.</span></span> <span data-ttu-id="ccd78-122">Bir kapsam eşleşen kural belirtmezseniz `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ccd78-122">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="ccd78-123">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="ccd78-123">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ccd78-124">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccd78-124">Child Elements</span></span>  
  
|<span data-ttu-id="ccd78-125">Öğe</span><span class="sxs-lookup"><span data-stu-id="ccd78-125">Element</span></span>|<span data-ttu-id="ccd78-126">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccd78-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccd78-127">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="ccd78-127">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="ccd78-128">İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonunu...</span><span class="sxs-lookup"><span data-stu-id="ccd78-128">A collection of configuration elements that contain the names of workflow service contract types..</span></span>|  
|<span data-ttu-id="ccd78-129">\<Uzantıları >, \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="ccd78-129">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="ccd78-130">Uzantılar sağlarlar XML öğesi nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ccd78-130">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="ccd78-131">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="ccd78-131">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="ccd78-132">Mutlak URI içeren bir bulma işlemi sırasında belirli bir hizmeti veya hizmetleri bulmak için kullanılan nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ccd78-132">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="ccd78-133">Belirli hizmet bulunursa, başarılı bir eşleşme hizmet URI'si ile eşleşen zorluklar işlemek kapsam kuralları yardımıyla bazen kapsam URI arasındaki yapıldı.</span><span class="sxs-lookup"><span data-stu-id="ccd78-133">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ccd78-134">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ccd78-134">Parent Elements</span></span>  
  
|<span data-ttu-id="ccd78-135">Öğe</span><span class="sxs-lookup"><span data-stu-id="ccd78-135">Element</span></span>|<span data-ttu-id="ccd78-136">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ccd78-136">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ccd78-137">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ccd78-137">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="ccd78-138">Hizmet bulma işlemi bir istemci olarak'na katılmak için bir uygulama tarafından gerekli ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ccd78-138">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccd78-139">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ccd78-139">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.FindCriteria>  
 <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
