---
title: <add> , <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: c29e47f688118e34fbdb4deb396c930d478f0582
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59187090"
---
# <a name="add-of-scopes"></a><span data-ttu-id="8ae23-102">\<Ekle >, \<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="8ae23-102">\<add> of \<scopes></span></span>
<span data-ttu-id="8ae23-103">Özel bir kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan URI ekler.</span><span class="sxs-lookup"><span data-stu-id="8ae23-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="8ae23-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8ae23-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8ae23-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="8ae23-105">\<behaviors></span></span>  
<span data-ttu-id="8ae23-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8ae23-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="8ae23-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="8ae23-107">\<behavior></span></span>  
<span data-ttu-id="8ae23-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="8ae23-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="8ae23-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="8ae23-109">\<scopes></span></span>  
<span data-ttu-id="8ae23-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="8ae23-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ae23-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ae23-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8ae23-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ae23-112">Attributes and Elements</span></span>  
 <span data-ttu-id="8ae23-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="8ae23-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8ae23-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="8ae23-114">Attributes</span></span>  
  
|<span data-ttu-id="8ae23-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="8ae23-115">Attribute</span></span>|<span data-ttu-id="8ae23-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ae23-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8ae23-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="8ae23-117">scope</span></span>|<span data-ttu-id="8ae23-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="8ae23-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8ae23-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ae23-119">Child Elements</span></span>  
 <span data-ttu-id="8ae23-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="8ae23-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8ae23-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="8ae23-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8ae23-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="8ae23-122">Element</span></span>|<span data-ttu-id="8ae23-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8ae23-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8ae23-124">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="8ae23-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="8ae23-125">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="8ae23-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8ae23-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ae23-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
