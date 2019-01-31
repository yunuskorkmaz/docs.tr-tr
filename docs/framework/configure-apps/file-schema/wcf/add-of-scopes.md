---
title: <add> , <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: 2681d5e757a1c1efc33fb3ef8804e94f8b391757
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55288684"
---
# <a name="add-of-scopes"></a><span data-ttu-id="85c99-102">\<Ekle >, \<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="85c99-102">\<add> of \<scopes></span></span>
<span data-ttu-id="85c99-103">Özel bir kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan URI ekler.</span><span class="sxs-lookup"><span data-stu-id="85c99-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="85c99-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="85c99-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="85c99-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="85c99-105">\<behaviors></span></span>  
<span data-ttu-id="85c99-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="85c99-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="85c99-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="85c99-107">\<behavior></span></span>  
<span data-ttu-id="85c99-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="85c99-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="85c99-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="85c99-109">\<scopes></span></span>  
<span data-ttu-id="85c99-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="85c99-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85c99-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="85c99-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85c99-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="85c99-112">Attributes and Elements</span></span>  
 <span data-ttu-id="85c99-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="85c99-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85c99-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="85c99-114">Attributes</span></span>  
  
|<span data-ttu-id="85c99-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="85c99-115">Attribute</span></span>|<span data-ttu-id="85c99-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85c99-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85c99-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="85c99-117">scope</span></span>|<span data-ttu-id="85c99-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="85c99-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85c99-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="85c99-119">Child Elements</span></span>  
 <span data-ttu-id="85c99-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="85c99-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85c99-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="85c99-121">Parent Elements</span></span>  
  
|<span data-ttu-id="85c99-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="85c99-122">Element</span></span>|<span data-ttu-id="85c99-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="85c99-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85c99-124">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="85c99-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="85c99-125">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="85c99-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="85c99-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="85c99-126">See also</span></span>
- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
