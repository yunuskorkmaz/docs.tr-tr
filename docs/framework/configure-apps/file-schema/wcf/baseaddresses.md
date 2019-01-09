---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 0af5dee41c6adf560c90874e6e9a44b62c5decc6
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54147362"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="e30d5-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="e30d5-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="e30d5-103">Bir koleksiyonunu temsil eder `baseAddress` kendiliğinden konak ortamdaki hizmet konak için temel adres olan öğeler.</span><span class="sxs-lookup"><span data-stu-id="e30d5-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="e30d5-104">Temel adres varsa, uç noktaları, adresler taban adresi göre ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e30d5-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="e30d5-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e30d5-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="e30d5-106">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e30d5-106">\<client></span></span>  
<span data-ttu-id="e30d5-107">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="e30d5-107">\<endpoint></span></span>  
<span data-ttu-id="e30d5-108">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e30d5-108">\<host></span></span>  
<span data-ttu-id="e30d5-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e30d5-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e30d5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e30d5-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="e30d5-111">Tür</span><span class="sxs-lookup"><span data-stu-id="e30d5-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e30d5-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e30d5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="e30d5-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e30d5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e30d5-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e30d5-114">Attributes</span></span>  
 <span data-ttu-id="e30d5-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="e30d5-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e30d5-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e30d5-116">Child Elements</span></span>  
  
|<span data-ttu-id="e30d5-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="e30d5-117">Element</span></span>|<span data-ttu-id="e30d5-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e30d5-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e30d5-119">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e30d5-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="e30d5-120">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e30d5-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e30d5-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e30d5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e30d5-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="e30d5-122">Element</span></span>|<span data-ttu-id="e30d5-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e30d5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e30d5-124">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e30d5-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e30d5-125">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e30d5-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e30d5-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e30d5-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="e30d5-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e30d5-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
