---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 7d0afd638e9a311b69ff47b6789d5fde093945ba
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212108"
---
# <a name="baseaddresses"></a><span data-ttu-id="e78ed-101">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e78ed-101">\<baseAddresses></span></span>
<span data-ttu-id="e78ed-102">Bir koleksiyonunu temsil eder `baseAddress` kendiliğinden konak ortamdaki hizmet konak için temel adres olan öğeler.</span><span class="sxs-lookup"><span data-stu-id="e78ed-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="e78ed-103">Temel adres varsa, uç noktaları, adresler taban adresi göre ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="e78ed-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="e78ed-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e78ed-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e78ed-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="e78ed-105">\<client></span></span>  
<span data-ttu-id="e78ed-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="e78ed-106">\<endpoint></span></span>  
<span data-ttu-id="e78ed-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e78ed-107">\<host></span></span>  
<span data-ttu-id="e78ed-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="e78ed-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e78ed-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e78ed-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="e78ed-110">Tür</span><span class="sxs-lookup"><span data-stu-id="e78ed-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e78ed-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="e78ed-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e78ed-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="e78ed-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e78ed-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="e78ed-113">Attributes</span></span>  
 <span data-ttu-id="e78ed-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="e78ed-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e78ed-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="e78ed-115">Child Elements</span></span>  
  
|<span data-ttu-id="e78ed-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="e78ed-116">Element</span></span>|<span data-ttu-id="e78ed-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e78ed-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e78ed-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="e78ed-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="e78ed-119">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e78ed-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e78ed-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="e78ed-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e78ed-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="e78ed-121">Element</span></span>|<span data-ttu-id="e78ed-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e78ed-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e78ed-123">\<konak ></span><span class="sxs-lookup"><span data-stu-id="e78ed-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e78ed-124">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="e78ed-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e78ed-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e78ed-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="e78ed-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="e78ed-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
