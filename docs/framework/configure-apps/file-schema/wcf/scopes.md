---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399923"
---
# <a name="scopes"></a><span data-ttu-id="115f4-101">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="115f4-101">\<scopes></span></span>
<span data-ttu-id="115f4-102">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="115f4-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="115f4-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="115f4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="115f4-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="115f4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="115f4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranışlar >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="115f4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="115f4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Endpointdavranışlar >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="115f4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="115f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<davranış >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="115f4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="115f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="115f4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="115f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<kapsamlar >**</span><span class="sxs-lookup"><span data-stu-id="115f4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="115f4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="115f4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="115f4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="115f4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="115f4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="115f4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="115f4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="115f4-113">Attributes</span></span>  
 <span data-ttu-id="115f4-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="115f4-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="115f4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="115f4-115">Child Elements</span></span>  
  
|<span data-ttu-id="115f4-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="115f4-116">Attribute</span></span>|<span data-ttu-id="115f4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="115f4-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="115f4-118">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="115f4-118">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="115f4-119">Hizmet bulmak için eşleşen ölçütlerde kullanılabilen uç nokta için kapsam bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="115f4-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="115f4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="115f4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="115f4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="115f4-121">Element</span></span>|<span data-ttu-id="115f4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="115f4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="115f4-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="115f4-123">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="115f4-124">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="115f4-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="115f4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="115f4-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
