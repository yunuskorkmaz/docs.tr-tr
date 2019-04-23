---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 7d0afd638e9a311b69ff47b6789d5fde093945ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212108"
---
# <a name="baseaddresses"></a><span data-ttu-id="d03d4-101">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d03d4-101">\<baseAddresses></span></span>
<span data-ttu-id="d03d4-102">Bir koleksiyonunu temsil eder `baseAddress` kendiliğinden konak ortamdaki hizmet konak için temel adres olan öğeler.</span><span class="sxs-lookup"><span data-stu-id="d03d4-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="d03d4-103">Temel adres varsa, uç noktaları, adresler taban adresi göre ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="d03d4-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="d03d4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d03d4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d03d4-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="d03d4-105">\<client></span></span>  
<span data-ttu-id="d03d4-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="d03d4-106">\<endpoint></span></span>  
<span data-ttu-id="d03d4-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="d03d4-107">\<host></span></span>  
<span data-ttu-id="d03d4-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="d03d4-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d03d4-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d03d4-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="d03d4-110">Tür</span><span class="sxs-lookup"><span data-stu-id="d03d4-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d03d4-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="d03d4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d03d4-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d03d4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d03d4-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="d03d4-113">Attributes</span></span>  
 <span data-ttu-id="d03d4-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="d03d4-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d03d4-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="d03d4-115">Child Elements</span></span>  
  
|<span data-ttu-id="d03d4-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="d03d4-116">Element</span></span>|<span data-ttu-id="d03d4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d03d4-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d03d4-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="d03d4-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="d03d4-119">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d03d4-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d03d4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="d03d4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="d03d4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="d03d4-121">Element</span></span>|<span data-ttu-id="d03d4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d03d4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d03d4-123">\<konak ></span><span class="sxs-lookup"><span data-stu-id="d03d4-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="d03d4-124">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="d03d4-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d03d4-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d03d4-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="d03d4-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d03d4-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
