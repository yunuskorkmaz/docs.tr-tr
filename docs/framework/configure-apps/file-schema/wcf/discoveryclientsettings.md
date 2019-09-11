---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855405"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="5cc88-101">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="5cc88-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="5cc88-102">Bir uygulama tarafından hizmet keşif işlemine bir istemci olarak katılmak için gerekli olan ayarları içerir.</span><span class="sxs-lookup"><span data-stu-id="5cc88-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="5cc88-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5cc88-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5cc88-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5cc88-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5cc88-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="5cc88-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="5cc88-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="5cc88-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="5cc88-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="5cc88-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="5cc88-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClientSettings >**</span><span class="sxs-lookup"><span data-stu-id="5cc88-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5cc88-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5cc88-109">Syntax</span></span>  
  
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
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5cc88-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cc88-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5cc88-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5cc88-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5cc88-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5cc88-112">Attributes</span></span>  
  
|<span data-ttu-id="5cc88-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5cc88-113">Attribute</span></span>|<span data-ttu-id="5cc88-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cc88-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5cc88-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="5cc88-115">discoveryEndpoint</span></span>|<span data-ttu-id="5cc88-116">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="5cc88-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5cc88-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cc88-117">Child Elements</span></span>  
  
|<span data-ttu-id="5cc88-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="5cc88-118">Element</span></span>|<span data-ttu-id="5cc88-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cc88-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cc88-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5cc88-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="5cc88-121">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="5cc88-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="5cc88-122">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5cc88-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5cc88-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5cc88-123">Parent Elements</span></span>  
  
|<span data-ttu-id="5cc88-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="5cc88-124">Element</span></span>|<span data-ttu-id="5cc88-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5cc88-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5cc88-126">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="5cc88-126">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="5cc88-127">Bir uygulamanın, çalışma zamanında dinamik olarak uç nokta adresini bulabilmesini sağlayan bir istemci program olarak çalışmasını sağlamak için bilgi içeren bir standart uç nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5cc88-127">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5cc88-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5cc88-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
