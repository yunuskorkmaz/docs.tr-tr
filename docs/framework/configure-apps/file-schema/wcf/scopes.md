---
description: 'Hakkında daha fazla bilgi edinin: <scopes>'
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 2df1101beb5b1bc09c2d98eb89a8200303c5b456
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786869"
---
# \<scopes>

<span data-ttu-id="0fc0b-102">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="0fc0b-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="0fc0b-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="0fc0b-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fc0b-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fc0b-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0fc0b-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="0fc0b-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fc0b-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="0fc0b-106">Attributes</span></span>  

 <span data-ttu-id="0fc0b-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="0fc0b-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fc0b-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fc0b-108">Child Elements</span></span>  
  
|<span data-ttu-id="0fc0b-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="0fc0b-109">Attribute</span></span>|<span data-ttu-id="0fc0b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fc0b-110">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="0fc0b-111">Hizmet bulmak için eşleşen ölçütlerde kullanılabilen uç nokta için kapsam bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="0fc0b-111">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fc0b-112">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="0fc0b-112">Parent Elements</span></span>  
  
|<span data-ttu-id="0fc0b-113">Öğe</span><span class="sxs-lookup"><span data-stu-id="0fc0b-113">Element</span></span>|<span data-ttu-id="0fc0b-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0fc0b-114">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="0fc0b-115">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="0fc0b-115">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fc0b-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0fc0b-116">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
