---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5e586437e3b269d361c254744e820ee8e8c0ca0a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400397"
---
# <a name="discoveryclient"></a><span data-ttu-id="9ca9f-101">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="9ca9f-101">\<discoveryClient></span></span>
<span data-ttu-id="9ca9f-102">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan özel bir bağlama oluşturmak için bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="9ca9f-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9ca9f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9ca9f-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9ca9f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9ca9f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bağlama >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="9ca9f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9ca9f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="9ca9f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="9ca9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<bağlama >** </span><span class="sxs-lookup"><span data-stu-id="9ca9f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="9ca9f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="9ca9f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca9f-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ca9f-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9ca9f-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ca9f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9ca9f-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9ca9f-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9ca9f-112">Attributes</span></span>  
  
|<span data-ttu-id="9ca9f-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="9ca9f-113">Attribute</span></span>|<span data-ttu-id="9ca9f-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ca9f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9ca9f-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="9ca9f-115">discoveryEndpoint</span></span>|<span data-ttu-id="9ca9f-116">İstemci uygulamanın, keşfedilebilir bir hizmeti otomatik olarak aramasını ve çalışma zamanında adresini bulmasını sağlayan bulma uç noktası adını içeren bir dize.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9ca9f-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ca9f-117">Child Elements</span></span>  
  
|<span data-ttu-id="9ca9f-118">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ca9f-118">Element</span></span>|<span data-ttu-id="9ca9f-119">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ca9f-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ca9f-120">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="9ca9f-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="9ca9f-121">Bir bulma hizmetini aramak için bir istemci uygulaması tarafından kullanılan bir ölçüt kümesi sağlayan yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="9ca9f-122">Ölçütler, arama ölçütlerine göre gruplandırılabilir (hangi hizmetleri aradığınızı belirtebilir) ve sonlandırma ölçütlerini (aramanın en son ne kadar süreyle) bulabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9ca9f-123">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9ca9f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9ca9f-124">Öğe</span><span class="sxs-lookup"><span data-stu-id="9ca9f-124">Element</span></span>|<span data-ttu-id="9ca9f-125">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ca9f-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9ca9f-126">\<bağlama ></span><span class="sxs-lookup"><span data-stu-id="9ca9f-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="9ca9f-127">Özel bağlamanın tüm bağlama yeteneklerini tanımlar.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9ca9f-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ca9f-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
