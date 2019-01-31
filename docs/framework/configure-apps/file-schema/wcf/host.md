---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 8a8f9db96281d8d775ff5c2923018228b3a9c1e5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269035"
---
# <a name="host"></a><span data-ttu-id="996e6-101">\<konak ></span><span class="sxs-lookup"><span data-stu-id="996e6-101">\<host></span></span>
<span data-ttu-id="996e6-102">Hizmet konak makinesi ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="996e6-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="996e6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="996e6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="996e6-104">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="996e6-104">\<services></span></span>  
<span data-ttu-id="996e6-105">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="996e6-105">\<service></span></span>  
<span data-ttu-id="996e6-106">\<konak ></span><span class="sxs-lookup"><span data-stu-id="996e6-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996e6-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="996e6-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="996e6-108">Tür</span><span class="sxs-lookup"><span data-stu-id="996e6-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="996e6-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="996e6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="996e6-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="996e6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="996e6-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="996e6-111">Attributes</span></span>  
 <span data-ttu-id="996e6-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="996e6-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="996e6-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="996e6-113">Child Elements</span></span>  
  
|<span data-ttu-id="996e6-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="996e6-114">Element</span></span>|<span data-ttu-id="996e6-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="996e6-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="996e6-116">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="996e6-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="996e6-117">Bir koleksiyonu `baseAddress` hizmet ana bilgisayarı tarafından kullanılan tabanı belirten öğeleri.</span><span class="sxs-lookup"><span data-stu-id="996e6-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="996e6-118">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="996e6-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="996e6-119">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="996e6-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="996e6-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="996e6-120">Parent Elements</span></span>  
  
|<span data-ttu-id="996e6-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="996e6-121">Element</span></span>|<span data-ttu-id="996e6-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="996e6-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="996e6-123">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="996e6-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="996e6-124">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="996e6-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="996e6-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="996e6-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="996e6-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="996e6-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
