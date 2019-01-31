---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: e82312cb17fbd3f76f781ea37f761e946319a0a0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55284874"
---
# <a name="findcriteria"></a><span data-ttu-id="12c3a-101">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="12c3a-101">\<findCriteria></span></span>
<span data-ttu-id="12c3a-102">Keşif hizmeti için bir istemci uygulaması tarafından aramak için kullanılan ölçüt kümesi sağlayan bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="12c3a-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="12c3a-103">Ölçüt, arama ölçütleri (aradığınız hangi hizmetlerin belirtme) toplanabilir ve sonlandırma ölçütünü (ne kadar süreyle arama son) bulun.</span><span class="sxs-lookup"><span data-stu-id="12c3a-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
 <span data-ttu-id="12c3a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="12c3a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="12c3a-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="12c3a-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12c3a-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12c3a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="12c3a-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c3a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="12c3a-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="12c3a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="12c3a-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="12c3a-109">Attributes</span></span>  
  
|<span data-ttu-id="12c3a-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="12c3a-110">Attribute</span></span>|<span data-ttu-id="12c3a-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c3a-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="12c3a-112">süre</span><span class="sxs-lookup"><span data-stu-id="12c3a-112">duration</span></span>|<span data-ttu-id="12c3a-113">Ağdaki hizmetlerden yanıtları için beklenecek en uzun süreyi belirten bir Timespan değeri.</span><span class="sxs-lookup"><span data-stu-id="12c3a-113">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="12c3a-114">Varsayılan süre 20 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="12c3a-114">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="12c3a-115">maxresults bağımsız değişkenini</span><span class="sxs-lookup"><span data-stu-id="12c3a-115">maxResults</span></span>|<span data-ttu-id="12c3a-116">İçin bir ağ veya Internet üzerinde hizmetlerden beklenilecek en fazla sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="12c3a-116">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="12c3a-117">En yüksek yanıt belirtilen değerden önce almış `duration` özniteliği geçti, bulma işlemi sona erer.</span><span class="sxs-lookup"><span data-stu-id="12c3a-117">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="12c3a-118">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="12c3a-118">scopeMatchBy</span></span>|<span data-ttu-id="12c3a-119">Kapsamlar araştırma iletisi ve onun uç noktasında alanları eşleştirirken kullanılan eşleştirme algoritmasını belirleyen bir URI.</span><span class="sxs-lookup"><span data-stu-id="12c3a-119">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="12c3a-120">Desteklenen beş kapsam eşleştirme kuralları vardır.</span><span class="sxs-lookup"><span data-stu-id="12c3a-120">There are five supported scope-matching rules.</span></span> <span data-ttu-id="12c3a-121">Bir kapsam eşleşen kural belirtmezseniz `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12c3a-121">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="12c3a-122">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="12c3a-122">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="12c3a-123">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c3a-123">Child Elements</span></span>  
  
|<span data-ttu-id="12c3a-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="12c3a-124">Element</span></span>|<span data-ttu-id="12c3a-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c3a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12c3a-126">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="12c3a-126">\<contractTypeNames></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/contracttypenames.md)|<span data-ttu-id="12c3a-127">İş akışı hizmeti sözleşmesi türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="12c3a-127">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="12c3a-128">\<Uzantılar >, \<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="12c3a-128">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="12c3a-129">XML öğesi uzantıları sağlayan bir nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="12c3a-129">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="12c3a-130">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="12c3a-130">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="12c3a-131">Mutlak bir URI'leri içeren bir bulma işlemi sırasında belirli bir hizmet veya hizmetleri bulmak için kullanılan nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="12c3a-131">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="12c3a-132">Hizmete bulunursa başarılı bir eşleşme hizmet URI'si ile eşleşen zorluklar işleyen kapsam kuralları yardımıyla bazen kapsam URI arasındaki yapıldı.</span><span class="sxs-lookup"><span data-stu-id="12c3a-132">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="12c3a-133">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="12c3a-133">Parent Elements</span></span>  
  
|<span data-ttu-id="12c3a-134">Öğe</span><span class="sxs-lookup"><span data-stu-id="12c3a-134">Element</span></span>|<span data-ttu-id="12c3a-135">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12c3a-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="12c3a-136">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="12c3a-136">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="12c3a-137">Hizmet keşif işlemine bir istemci olarak katılmak için bir uygulama tarafından gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="12c3a-137">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12c3a-138">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12c3a-138">See also</span></span>
- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
