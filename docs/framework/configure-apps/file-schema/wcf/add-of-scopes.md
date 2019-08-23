---
title: <add> / <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: b190cb72e21d47bdc62aab2daba0f6eea1ee04ac
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926626"
---
# <a name="add-of-scopes"></a><span data-ttu-id="544c0-102">\<\<kapsamların > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="544c0-102">\<add> of \<scopes></span></span>
<span data-ttu-id="544c0-103">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek bir özel kapsam URI 'Si ekler.</span><span class="sxs-lookup"><span data-stu-id="544c0-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="544c0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="544c0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="544c0-105">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="544c0-105">\<behaviors></span></span>  
<span data-ttu-id="544c0-106">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="544c0-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="544c0-107">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="544c0-107">\<behavior></span></span>  
<span data-ttu-id="544c0-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="544c0-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="544c0-109">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="544c0-109">\<scopes></span></span>  
<span data-ttu-id="544c0-110">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="544c0-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="544c0-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="544c0-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="544c0-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="544c0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="544c0-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="544c0-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="544c0-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="544c0-114">Attributes</span></span>  
  
|<span data-ttu-id="544c0-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="544c0-115">Attribute</span></span>|<span data-ttu-id="544c0-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="544c0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="544c0-117">kapsam</span><span class="sxs-lookup"><span data-stu-id="544c0-117">scope</span></span>|<span data-ttu-id="544c0-118">Uç nokta için hizmet bulmaya yönelik eşleştirme ölçütlerinde kullanılabilecek kapsam bilgilerini içeren bir URI.</span><span class="sxs-lookup"><span data-stu-id="544c0-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="544c0-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="544c0-119">Child Elements</span></span>  
 <span data-ttu-id="544c0-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="544c0-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="544c0-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="544c0-121">Parent Elements</span></span>  
  
|<span data-ttu-id="544c0-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="544c0-122">Element</span></span>|<span data-ttu-id="544c0-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="544c0-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="544c0-124">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="544c0-124">\<scopes></span></span>](scopes.md)|<span data-ttu-id="544c0-125">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="544c0-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="544c0-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="544c0-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
