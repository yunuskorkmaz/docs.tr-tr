---
title: '&lt;Kapsamları&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7afab700c2d9eb91ffe57bfefaf5864782a0af5f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145334"
---
# <a name="ltscopesgt"></a><span data-ttu-id="a0c3e-102">&lt;Kapsamları&gt;</span><span class="sxs-lookup"><span data-stu-id="a0c3e-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="a0c3e-103">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="a0c3e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a0c3e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a0c3e-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-105">\<behaviors></span></span>  
<span data-ttu-id="a0c3e-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="a0c3e-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-107">\<behavior></span></span>  
<span data-ttu-id="a0c3e-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="a0c3e-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0c3e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a0c3e-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a0c3e-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0c3e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a0c3e-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a0c3e-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="a0c3e-113">Attributes</span></span>  
 <span data-ttu-id="a0c3e-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a0c3e-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0c3e-115">Child Elements</span></span>  
  
|<span data-ttu-id="a0c3e-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="a0c3e-116">Attribute</span></span>|<span data-ttu-id="a0c3e-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0c3e-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="a0c3e-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="a0c3e-119">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta için kapsam bilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a0c3e-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="a0c3e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="a0c3e-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="a0c3e-121">Element</span></span>|<span data-ttu-id="a0c3e-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a0c3e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a0c3e-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="a0c3e-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="a0c3e-124">Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a0c3e-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a0c3e-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
