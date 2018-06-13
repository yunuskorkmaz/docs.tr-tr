---
title: '&lt;BaseAddresses&gt;'
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 8de962cc70e1399dd1e9459473055651f9aca5fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747492"
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="92f79-102">&lt;BaseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="92f79-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="92f79-103">Bir koleksiyonunu temsil eder `baseAddress` otomatik olarak barındırılan bir ortamda hizmet ana bilgisayarı için temel adresler öğeleri.</span><span class="sxs-lookup"><span data-stu-id="92f79-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="92f79-104">Taban adresi varsa, taban adresi göre adresleriyle uç noktaları yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="92f79-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="92f79-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92f79-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="92f79-106">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="92f79-106">\<client></span></span>  
<span data-ttu-id="92f79-107">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="92f79-107">\<endpoint></span></span>  
<span data-ttu-id="92f79-108">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="92f79-108">\<host></span></span>  
<span data-ttu-id="92f79-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="92f79-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f79-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92f79-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="92f79-111">Tür</span><span class="sxs-lookup"><span data-stu-id="92f79-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92f79-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="92f79-112">Attributes and Elements</span></span>  
 <span data-ttu-id="92f79-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="92f79-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92f79-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="92f79-114">Attributes</span></span>  
 <span data-ttu-id="92f79-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="92f79-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="92f79-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="92f79-116">Child Elements</span></span>  
  
|<span data-ttu-id="92f79-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="92f79-117">Element</span></span>|<span data-ttu-id="92f79-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92f79-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92f79-119">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="92f79-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="92f79-120">Hizmet ana bilgisayar tarafından kullanılan temel adres belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="92f79-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="92f79-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="92f79-121">Parent Elements</span></span>  
  
|<span data-ttu-id="92f79-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="92f79-122">Element</span></span>|<span data-ttu-id="92f79-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="92f79-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92f79-124">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="92f79-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="92f79-125">Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="92f79-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="92f79-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="92f79-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="92f79-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="92f79-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
