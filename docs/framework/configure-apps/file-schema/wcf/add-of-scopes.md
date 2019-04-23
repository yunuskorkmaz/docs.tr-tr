---
title: <add> / <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: c29e47f688118e34fbdb4deb396c930d478f0582
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187090"
---
# <a name="add-of-scopes"></a><span data-ttu-id="1a721-102">\<Ekle >, \<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="1a721-102">\<add> of \<scopes></span></span>
<span data-ttu-id="1a721-103">Özel bir kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan URI ekler.</span><span class="sxs-lookup"><span data-stu-id="1a721-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="1a721-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1a721-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="1a721-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="1a721-105">\<behaviors></span></span>  
<span data-ttu-id="1a721-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="1a721-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="1a721-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="1a721-107">\<behavior></span></span>  
<span data-ttu-id="1a721-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="1a721-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="1a721-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="1a721-109">\<scopes></span></span>  
<span data-ttu-id="1a721-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="1a721-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a721-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1a721-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1a721-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a721-112">Attributes and Elements</span></span>  
 <span data-ttu-id="1a721-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1a721-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1a721-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1a721-114">Attributes</span></span>  
  
|<span data-ttu-id="1a721-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="1a721-115">Attribute</span></span>|<span data-ttu-id="1a721-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a721-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1a721-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="1a721-117">scope</span></span>|<span data-ttu-id="1a721-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="1a721-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1a721-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a721-119">Child Elements</span></span>  
 <span data-ttu-id="1a721-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="1a721-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1a721-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1a721-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1a721-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1a721-122">Element</span></span>|<span data-ttu-id="1a721-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1a721-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1a721-124">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="1a721-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="1a721-125">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="1a721-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1a721-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1a721-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
