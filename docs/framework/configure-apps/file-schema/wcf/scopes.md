---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399923"
---
# \<scopes>
<span data-ttu-id="579bc-101">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="579bc-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="579bc-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="579bc-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="579bc-103">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="579bc-103">Attributes and Elements</span></span>  
 <span data-ttu-id="579bc-104">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="579bc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="579bc-105">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="579bc-105">Attributes</span></span>  
 <span data-ttu-id="579bc-106">Yok.</span><span class="sxs-lookup"><span data-stu-id="579bc-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="579bc-107">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="579bc-107">Child Elements</span></span>  
  
|<span data-ttu-id="579bc-108">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="579bc-108">Attribute</span></span>|<span data-ttu-id="579bc-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="579bc-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="579bc-110">Hizmet bulmak için eşleşen ölçütlerde kullanılabilen uç nokta için kapsam bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="579bc-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="579bc-111">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="579bc-111">Parent Elements</span></span>  
  
|<span data-ttu-id="579bc-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="579bc-112">Element</span></span>|<span data-ttu-id="579bc-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="579bc-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="579bc-114">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="579bc-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="579bc-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="579bc-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
