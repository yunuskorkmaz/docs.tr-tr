---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: eee6382c578648866045fd9b283454d9e0e76fcb
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55275034"
---
# <a name="scopes"></a><span data-ttu-id="804c6-101">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="804c6-101">\<scopes></span></span>
<span data-ttu-id="804c6-102">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="804c6-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="804c6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="804c6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="804c6-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="804c6-104">\<behaviors></span></span>  
<span data-ttu-id="804c6-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="804c6-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="804c6-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="804c6-106">\<behavior></span></span>  
<span data-ttu-id="804c6-107">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="804c6-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="804c6-108">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="804c6-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="804c6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="804c6-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="804c6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="804c6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="804c6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="804c6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="804c6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="804c6-112">Attributes</span></span>  
 <span data-ttu-id="804c6-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="804c6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="804c6-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="804c6-114">Child Elements</span></span>  
  
|<span data-ttu-id="804c6-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="804c6-115">Attribute</span></span>|<span data-ttu-id="804c6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="804c6-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="804c6-117">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="804c6-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="804c6-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta için kapsam bilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="804c6-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="804c6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="804c6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="804c6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="804c6-120">Element</span></span>|<span data-ttu-id="804c6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="804c6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="804c6-122">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="804c6-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="804c6-123">Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="804c6-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="804c6-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="804c6-124">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
