---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855159"
---
# <a name="findcriteria"></a><span data-ttu-id="ab821-101">\<findCriteria ></span><span class="sxs-lookup"><span data-stu-id="ab821-101">\<findCriteria></span></span>
<span data-ttu-id="ab821-102">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ab821-102">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="ab821-103">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ab821-103">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
<span data-ttu-id="ab821-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ab821-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ab821-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="ab821-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ab821-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="ab821-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="ab821-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="ab821-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="ab821-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="ab821-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="ab821-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<discoveryClientSettings >** ](discoveryclientsettings.md)</span><span class="sxs-lookup"><span data-stu-id="ab821-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)</span></span>\
<span data-ttu-id="ab821-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<findCriteria >**</span><span class="sxs-lookup"><span data-stu-id="ab821-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab821-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab821-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab821-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab821-112">Attributes and Elements</span></span>  
 <span data-ttu-id="ab821-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ab821-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab821-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ab821-114">Attributes</span></span>  
  
|<span data-ttu-id="ab821-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="ab821-115">Attribute</span></span>|<span data-ttu-id="ab821-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab821-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab821-117">süre</span><span class="sxs-lookup"><span data-stu-id="ab821-117">duration</span></span>|<span data-ttu-id="ab821-118">Ağdaki hizmetlerden gelen yanıtlar için beklenecek en uzun süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="ab821-118">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="ab821-119">Varsayılan süre 20 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="ab821-119">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="ab821-120">maxResults</span><span class="sxs-lookup"><span data-stu-id="ab821-120">maxResults</span></span>|<span data-ttu-id="ab821-121">Ağ veya Internet üzerindeki hizmetlerden, beklenecek en fazla yanıt sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="ab821-121">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="ab821-122">`duration` Öznitelikte belirtilen değerin süresi geçtiğinde en fazla yanıt alınmışsa, bulma işlemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="ab821-122">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="ab821-123">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="ab821-123">scopeMatchBy</span></span>|<span data-ttu-id="ab821-124">Araştırma iletisindeki kapsamları uç noktayla eşleştirirken kullanılacak eşleşen algoritmayı belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="ab821-124">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="ab821-125">Desteklenen beş kapsam eşleştirme kuralı vardır.</span><span class="sxs-lookup"><span data-stu-id="ab821-125">There are five supported scope-matching rules.</span></span> <span data-ttu-id="ab821-126">Kapsam eşleştirme kuralı belirtmezseniz, `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="ab821-126">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="ab821-127">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="ab821-127">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab821-128">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab821-128">Child Elements</span></span>  
  
|<span data-ttu-id="ab821-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab821-129">Element</span></span>|<span data-ttu-id="ab821-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab821-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab821-131">\<contractTypeNames ></span><span class="sxs-lookup"><span data-stu-id="ab821-131">\<contractTypeNames></span></span>](contracttypenames.md)|<span data-ttu-id="ab821-132">İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ab821-132">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="ab821-133">\<\<FindCriteria > Uzantıları ></span><span class="sxs-lookup"><span data-stu-id="ab821-133">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="ab821-134">Uzantıları sağlayan XML öğe nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ab821-134">A collection of XML element objects that provide extensions.</span></span>|  
|[<span data-ttu-id="ab821-135">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="ab821-135">\<scopes></span></span>](scopes.md)|<span data-ttu-id="ab821-136">Belirli bir hizmet veya hizmeti bulmak için bulma işlemi sırasında kullanılan mutlak URI 'Ler içeren nesneler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ab821-136">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="ab821-137">Belirli bir hizmet bulunursa, hizmet URI 'si ile kapsam URI 'SI arasında başarılı bir eşleşme yapılmıştır, bazen eşleştirmeyi ele alan kapsam kurallarının yardımıyla.</span><span class="sxs-lookup"><span data-stu-id="ab821-137">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ab821-138">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ab821-138">Parent Elements</span></span>  
  
|<span data-ttu-id="ab821-139">Öğe</span><span class="sxs-lookup"><span data-stu-id="ab821-139">Element</span></span>|<span data-ttu-id="ab821-140">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab821-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab821-141">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="ab821-141">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="ab821-142">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="ab821-142">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab821-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ab821-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
