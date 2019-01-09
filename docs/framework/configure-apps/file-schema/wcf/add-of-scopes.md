---
title: '&lt;kapsamların&gt; &lt;eklenmesi&gt;'
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: e2bf649259d6ccb0e55428ab3619fe561d051ff7
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146248"
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="43d1f-102">&lt;kapsamların&gt; &lt;eklenmesi&gt;</span><span class="sxs-lookup"><span data-stu-id="43d1f-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="43d1f-103">Özel bir kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan URI ekler.</span><span class="sxs-lookup"><span data-stu-id="43d1f-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="43d1f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43d1f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="43d1f-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="43d1f-105">\<behaviors></span></span>  
<span data-ttu-id="43d1f-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="43d1f-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="43d1f-107">\<davranışı ></span><span class="sxs-lookup"><span data-stu-id="43d1f-107">\<behavior></span></span>  
<span data-ttu-id="43d1f-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="43d1f-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="43d1f-109">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="43d1f-109">\<scopes></span></span>  
<span data-ttu-id="43d1f-110">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="43d1f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43d1f-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43d1f-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43d1f-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="43d1f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="43d1f-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="43d1f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43d1f-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="43d1f-114">Attributes</span></span>  
  
|<span data-ttu-id="43d1f-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="43d1f-115">Attribute</span></span>|<span data-ttu-id="43d1f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43d1f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="43d1f-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="43d1f-117">scope</span></span>|<span data-ttu-id="43d1f-118">Eşleşme ölçütlerinde Hizmetleri bulmak için kullanılabilir uç nokta kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="43d1f-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43d1f-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="43d1f-119">Child Elements</span></span>  
 <span data-ttu-id="43d1f-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="43d1f-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43d1f-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="43d1f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="43d1f-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="43d1f-122">Element</span></span>|<span data-ttu-id="43d1f-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="43d1f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43d1f-124">\<kapsamları ></span><span class="sxs-lookup"><span data-stu-id="43d1f-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="43d1f-125">Özel kapsam sorgu sırasında hizmet bitiş noktası süzmek için kullanılan bir URI'leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="43d1f-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43d1f-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43d1f-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
