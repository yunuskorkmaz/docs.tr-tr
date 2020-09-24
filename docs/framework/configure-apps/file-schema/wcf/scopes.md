---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 63f46753da13469147b378f373de9888a007bf52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162224"
---
# \<scopes>

<span data-ttu-id="e7eda-101">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="e7eda-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="e7eda-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7eda-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7eda-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7eda-103">Attributes and Elements</span></span>  

 <span data-ttu-id="e7eda-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e7eda-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7eda-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e7eda-105">Attributes</span></span>  

 <span data-ttu-id="e7eda-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="e7eda-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e7eda-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7eda-107">Child Elements</span></span>  
  
|<span data-ttu-id="e7eda-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="e7eda-108">Attribute</span></span>|<span data-ttu-id="e7eda-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7eda-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="e7eda-110">Hizmet bulmak için eşleşen ölçütlerde kullanılabilen uç nokta için kapsam bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="e7eda-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7eda-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e7eda-111">Parent Elements</span></span>  
  
|<span data-ttu-id="e7eda-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="e7eda-112">Element</span></span>|<span data-ttu-id="e7eda-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e7eda-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="e7eda-114">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e7eda-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7eda-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7eda-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
