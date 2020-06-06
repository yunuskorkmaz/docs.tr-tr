---
title: <findCriteria>
ms.date: 03/30/2017
ms.assetid: 5454cd19-6bf5-4ba8-94d1-f58d10dc1917
ms.openlocfilehash: 44e068ee205bc5e04382164e7ab00716b2c07dcf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855159"
---
# \<findCriteria>
<span data-ttu-id="641d3-101">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="641d3-101">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="641d3-102">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="641d3-102">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<discoveryClientSettings>**](discoveryclientsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<findCriteria>**  
  
## <a name="syntax"></a><span data-ttu-id="641d3-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="641d3-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="641d3-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="641d3-104">Attributes and Elements</span></span>  
 <span data-ttu-id="641d3-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="641d3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="641d3-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="641d3-106">Attributes</span></span>  
  
|<span data-ttu-id="641d3-107">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="641d3-107">Attribute</span></span>|<span data-ttu-id="641d3-108">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641d3-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="641d3-109">süre</span><span class="sxs-lookup"><span data-stu-id="641d3-109">duration</span></span>|<span data-ttu-id="641d3-110">Ağdaki hizmetlerden gelen yanıtlar için beklenecek en uzun süreyi belirten bir TimeSpan değeri.</span><span class="sxs-lookup"><span data-stu-id="641d3-110">A Timespan value that specifies the maximum time to wait for replies from services on the network.</span></span> <span data-ttu-id="641d3-111">Varsayılan süre 20 saniyedir.</span><span class="sxs-lookup"><span data-stu-id="641d3-111">The default duration is 20 seconds.</span></span>|  
|<span data-ttu-id="641d3-112">maxResults</span><span class="sxs-lookup"><span data-stu-id="641d3-112">maxResults</span></span>|<span data-ttu-id="641d3-113">Ağ veya Internet üzerindeki hizmetlerden, beklenecek en fazla yanıt sayısını belirten bir tamsayı.</span><span class="sxs-lookup"><span data-stu-id="641d3-113">An integer that specifies the maximum number of replies to wait for, from services on a network or the Internet.</span></span> <span data-ttu-id="641d3-114">Öznitelikte belirtilen değerin süresi geçtiğinde en fazla yanıt `duration` alınmışsa, bulma işlemi sonlanır.</span><span class="sxs-lookup"><span data-stu-id="641d3-114">If maximum replies are received before the value specified in the `duration` attribute has elapsed, the find operation ends.</span></span>|  
|<span data-ttu-id="641d3-115">scopeMatchBy</span><span class="sxs-lookup"><span data-stu-id="641d3-115">scopeMatchBy</span></span>|<span data-ttu-id="641d3-116">Araştırma iletisindeki kapsamları uç noktayla eşleştirirken kullanılacak eşleşen algoritmayı belirten bir URI.</span><span class="sxs-lookup"><span data-stu-id="641d3-116">A URI that specify the matching algorithm to use while matching the scopes in the Probe message with that of the endpoint.</span></span><br /><br /> <span data-ttu-id="641d3-117">Desteklenen beş kapsam eşleştirme kuralı vardır.</span><span class="sxs-lookup"><span data-stu-id="641d3-117">There are five supported scope-matching rules.</span></span> <span data-ttu-id="641d3-118">Kapsam eşleştirme kuralı belirtmezseniz, `ScopeMatchByPrefix` kullanılır.</span><span class="sxs-lookup"><span data-stu-id="641d3-118">If you do not specify a scope-matching rule, `ScopeMatchByPrefix` is used.</span></span> <span data-ttu-id="641d3-119">Bu hakkında daha fazla bilgi için bkz <xref:System.ServiceModel.Discovery.FindCriteria>.</span><span class="sxs-lookup"><span data-stu-id="641d3-119">For more information on this, see <xref:System.ServiceModel.Discovery.FindCriteria>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="641d3-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="641d3-120">Child Elements</span></span>  
  
|<span data-ttu-id="641d3-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="641d3-121">Element</span></span>|<span data-ttu-id="641d3-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641d3-122">Description</span></span>|  
|-------------|-----------------|  
|[\<contractTypeNames>](contracttypenames.md)|<span data-ttu-id="641d3-123">İş akışı hizmeti sözleşme türlerinin adlarını içeren yapılandırma öğelerinin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="641d3-123">A collection of configuration elements that contain the names of workflow service contract types.</span></span>|  
|<span data-ttu-id="641d3-124">\<extensions> / \<findCriteria></span><span class="sxs-lookup"><span data-stu-id="641d3-124">\<extensions> of \<findCriteria></span></span>|<span data-ttu-id="641d3-125">Uzantıları sağlayan XML öğe nesneleri koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="641d3-125">A collection of XML element objects that provide extensions.</span></span>|  
|[\<scopes>](scopes.md)|<span data-ttu-id="641d3-126">Belirli bir hizmet veya hizmeti bulmak için bulma işlemi sırasında kullanılan mutlak URI 'Ler içeren nesneler koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="641d3-126">A collection of objects that contain absolute URIs that are used during a find operation to locate a specific service or services.</span></span><br /><br /> <span data-ttu-id="641d3-127">Belirli bir hizmet bulunursa, hizmet URI 'si ile kapsam URI 'SI arasında başarılı bir eşleşme yapılmıştır, bazen eşleştirmeyi ele alan kapsam kurallarının yardımıyla.</span><span class="sxs-lookup"><span data-stu-id="641d3-127">If the specific service is found, a successful match has been made between the service URI and the Scope URI, sometimes with the help of scope rules that handle complications of matching.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="641d3-128">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="641d3-128">Parent Elements</span></span>  
  
|<span data-ttu-id="641d3-129">Öğe</span><span class="sxs-lookup"><span data-stu-id="641d3-129">Element</span></span>|<span data-ttu-id="641d3-130">Açıklama</span><span class="sxs-lookup"><span data-stu-id="641d3-130">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="641d3-131">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="641d3-131">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="641d3-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="641d3-132">See also</span></span>

- <xref:System.ServiceModel.Discovery.FindCriteria>
- <xref:System.ServiceModel.Discovery.Configuration.FindCriteriaElement>
