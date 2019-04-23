---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213083"
---
# <a name="scopes"></a><span data-ttu-id="d2e21-101">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="d2e21-101">\<scopes></span></span>
<span data-ttu-id="d2e21-102">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d2e21-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="d2e21-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d2e21-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d2e21-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d2e21-104">\<behaviors></span></span>  
<span data-ttu-id="d2e21-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d2e21-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="d2e21-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d2e21-106">\<behavior></span></span>  
<span data-ttu-id="d2e21-107">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d2e21-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="d2e21-108">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="d2e21-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2e21-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d2e21-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d2e21-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2e21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d2e21-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d2e21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d2e21-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d2e21-112">Attributes</span></span>  
 <span data-ttu-id="d2e21-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="d2e21-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d2e21-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2e21-114">Child Elements</span></span>  
  
|<span data-ttu-id="d2e21-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d2e21-115">Attribute</span></span>|<span data-ttu-id="d2e21-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2e21-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d2e21-117">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d2e21-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="d2e21-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta için kapsam bilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="d2e21-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d2e21-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d2e21-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d2e21-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="d2e21-120">Element</span></span>|<span data-ttu-id="d2e21-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d2e21-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d2e21-122">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d2e21-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="d2e21-123">Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d2e21-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2e21-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d2e21-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
