---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 21d53df12c2b2d703b771e2b9cb5ee87dafc410e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918715"
---
# <a name="host"></a><span data-ttu-id="ea9ef-101">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-101">\<host></span></span>
<span data-ttu-id="ea9ef-102">Hizmet ana bilgisayarının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="ea9ef-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ea9ef-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ea9ef-104">\<Hizmetler ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-104">\<services></span></span>  
<span data-ttu-id="ea9ef-105">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-105">\<service></span></span>  
<span data-ttu-id="ea9ef-106">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea9ef-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea9ef-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="ea9ef-108">Tür</span><span class="sxs-lookup"><span data-stu-id="ea9ef-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea9ef-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea9ef-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ea9ef-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea9ef-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="ea9ef-111">Attributes</span></span>  
 <span data-ttu-id="ea9ef-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea9ef-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea9ef-113">Child Elements</span></span>  
  
|<span data-ttu-id="ea9ef-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea9ef-114">Element</span></span>|<span data-ttu-id="ea9ef-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea9ef-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea9ef-116">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-116">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="ea9ef-117">Hizmet ana bilgisayarı `baseAddress` tarafından kullanılan temel adresleri belirten öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="ea9ef-118">\<Zaman aşımları ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-118">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="ea9ef-119">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea9ef-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="ea9ef-120">Parent Elements</span></span>  
  
|<span data-ttu-id="ea9ef-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="ea9ef-121">Element</span></span>|<span data-ttu-id="ea9ef-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ea9ef-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea9ef-123">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="ea9ef-123">\<service></span></span>](service.md)|<span data-ttu-id="ea9ef-124">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ea9ef-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea9ef-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="ea9ef-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="ea9ef-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
