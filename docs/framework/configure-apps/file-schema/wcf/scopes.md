---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670631"
---
# <a name="scopes"></a><span data-ttu-id="d7dde-101">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="d7dde-101">\<scopes></span></span>
<span data-ttu-id="d7dde-102">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="d7dde-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="d7dde-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d7dde-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d7dde-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="d7dde-104">\<behaviors></span></span>  
<span data-ttu-id="d7dde-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="d7dde-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="d7dde-106">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="d7dde-106">\<behavior></span></span>  
<span data-ttu-id="d7dde-107">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d7dde-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="d7dde-108">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="d7dde-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7dde-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d7dde-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d7dde-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7dde-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d7dde-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d7dde-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d7dde-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d7dde-112">Attributes</span></span>  
 <span data-ttu-id="d7dde-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="d7dde-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d7dde-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7dde-114">Child Elements</span></span>  
  
|<span data-ttu-id="d7dde-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="d7dde-115">Attribute</span></span>|<span data-ttu-id="d7dde-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7dde-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="d7dde-117">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d7dde-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="d7dde-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta için kapsam bilgileri ekler.</span><span class="sxs-lookup"><span data-stu-id="d7dde-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d7dde-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d7dde-119">Parent Elements</span></span>  
  
|<span data-ttu-id="d7dde-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="d7dde-120">Element</span></span>|<span data-ttu-id="d7dde-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d7dde-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d7dde-122">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="d7dde-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="d7dde-123">Bir uç nokta bulunabilirliği, kapsamı ve meta verilerine özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="d7dde-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7dde-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d7dde-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
