---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 34d400e74b24e9eb4140d1b43597b0217b23d80c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730132"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="55c70-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="55c70-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="55c70-103">Bir koleksiyonunu temsil eder `baseAddress` kendiliğinden konak ortamdaki hizmet konak için temel adres olan öğeler.</span><span class="sxs-lookup"><span data-stu-id="55c70-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="55c70-104">Temel adres varsa, uç noktaları, adresler taban adresi göre ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="55c70-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="55c70-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="55c70-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="55c70-106">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="55c70-106">\<client></span></span>  
<span data-ttu-id="55c70-107">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="55c70-107">\<endpoint></span></span>  
<span data-ttu-id="55c70-108">\<konak ></span><span class="sxs-lookup"><span data-stu-id="55c70-108">\<host></span></span>  
<span data-ttu-id="55c70-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="55c70-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55c70-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="55c70-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="55c70-111">Tür</span><span class="sxs-lookup"><span data-stu-id="55c70-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="55c70-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c70-112">Attributes and Elements</span></span>  
 <span data-ttu-id="55c70-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="55c70-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="55c70-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="55c70-114">Attributes</span></span>  
 <span data-ttu-id="55c70-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="55c70-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="55c70-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c70-116">Child Elements</span></span>  
  
|<span data-ttu-id="55c70-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="55c70-117">Element</span></span>|<span data-ttu-id="55c70-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c70-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55c70-119">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="55c70-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="55c70-120">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="55c70-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="55c70-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="55c70-121">Parent Elements</span></span>  
  
|<span data-ttu-id="55c70-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="55c70-122">Element</span></span>|<span data-ttu-id="55c70-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="55c70-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="55c70-124">\<konak ></span><span class="sxs-lookup"><span data-stu-id="55c70-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="55c70-125">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="55c70-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="55c70-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="55c70-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="55c70-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="55c70-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
