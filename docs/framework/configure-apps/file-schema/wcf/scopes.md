---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935179"
---
# <a name="scopes"></a><span data-ttu-id="98a80-101">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="98a80-101">\<scopes></span></span>
<span data-ttu-id="98a80-102">Sorgu sırasında hizmet uç noktalarını filtrelemek için kullanılabilecek özel kapsam URI 'Leri belirten yapılandırma öğelerinin bir koleksiyonunu içerir.</span><span class="sxs-lookup"><span data-stu-id="98a80-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="98a80-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="98a80-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="98a80-104">\<davranışlar ></span><span class="sxs-lookup"><span data-stu-id="98a80-104">\<behaviors></span></span>  
<span data-ttu-id="98a80-105">\<Endpointdavranışlar ></span><span class="sxs-lookup"><span data-stu-id="98a80-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="98a80-106">\<davranış ></span><span class="sxs-lookup"><span data-stu-id="98a80-106">\<behavior></span></span>  
<span data-ttu-id="98a80-107">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="98a80-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="98a80-108">\<kapsamlar ></span><span class="sxs-lookup"><span data-stu-id="98a80-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98a80-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="98a80-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98a80-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="98a80-110">Attributes and Elements</span></span>  
 <span data-ttu-id="98a80-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="98a80-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98a80-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="98a80-112">Attributes</span></span>  
 <span data-ttu-id="98a80-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="98a80-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="98a80-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="98a80-114">Child Elements</span></span>  
  
|<span data-ttu-id="98a80-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="98a80-115">Attribute</span></span>|<span data-ttu-id="98a80-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a80-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="98a80-117">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="98a80-117">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="98a80-118">Hizmet bulmak için eşleşen ölçütlerde kullanılabilen uç nokta için kapsam bilgilerini ekler.</span><span class="sxs-lookup"><span data-stu-id="98a80-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98a80-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="98a80-119">Parent Elements</span></span>  
  
|<span data-ttu-id="98a80-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="98a80-120">Element</span></span>|<span data-ttu-id="98a80-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98a80-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="98a80-122">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="98a80-122">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="98a80-123">Bir uç nokta için, keşfedilebilirlik, kapsamları ve tüm özel uzantıları gibi çeşitli bulma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="98a80-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98a80-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98a80-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
