---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 7d0afd638e9a311b69ff47b6789d5fde093945ba
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673530"
---
# <a name="baseaddresses"></a><span data-ttu-id="49cff-101">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="49cff-101">\<baseAddresses></span></span>
<span data-ttu-id="49cff-102">Bir koleksiyonunu temsil eder `baseAddress` kendiliğinden konak ortamdaki hizmet konak için temel adres olan öğeler.</span><span class="sxs-lookup"><span data-stu-id="49cff-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="49cff-103">Temel adres varsa, uç noktaları, adresler taban adresi göre ile yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="49cff-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="49cff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="49cff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="49cff-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="49cff-105">\<client></span></span>  
<span data-ttu-id="49cff-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="49cff-106">\<endpoint></span></span>  
<span data-ttu-id="49cff-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="49cff-107">\<host></span></span>  
<span data-ttu-id="49cff-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="49cff-108">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49cff-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="49cff-109">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="49cff-110">Tür</span><span class="sxs-lookup"><span data-stu-id="49cff-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49cff-111">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="49cff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="49cff-112">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="49cff-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49cff-113">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="49cff-113">Attributes</span></span>  
 <span data-ttu-id="49cff-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="49cff-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="49cff-115">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="49cff-115">Child Elements</span></span>  
  
|<span data-ttu-id="49cff-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="49cff-116">Element</span></span>|<span data-ttu-id="49cff-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49cff-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49cff-118">\<Ekle ></span><span class="sxs-lookup"><span data-stu-id="49cff-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="49cff-119">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="49cff-119">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="49cff-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="49cff-120">Parent Elements</span></span>  
  
|<span data-ttu-id="49cff-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="49cff-121">Element</span></span>|<span data-ttu-id="49cff-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="49cff-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49cff-123">\<konak ></span><span class="sxs-lookup"><span data-stu-id="49cff-123">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="49cff-124">Hizmet konak makinesi ayarlarını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="49cff-124">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="49cff-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="49cff-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="49cff-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="49cff-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
