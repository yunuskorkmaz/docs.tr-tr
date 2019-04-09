---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 3d1f7774f61060880a5c3b0327bdd6c2cc4dd74e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103005"
---
# <a name="host"></a><span data-ttu-id="3f912-101">\<konak ></span><span class="sxs-lookup"><span data-stu-id="3f912-101">\<host></span></span>
<span data-ttu-id="3f912-102">Hizmet konak makinesi ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="3f912-102">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="3f912-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3f912-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3f912-104">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="3f912-104">\<services></span></span>  
<span data-ttu-id="3f912-105">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="3f912-105">\<service></span></span>  
<span data-ttu-id="3f912-106">\<konak ></span><span class="sxs-lookup"><span data-stu-id="3f912-106">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f912-107">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3f912-107">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="3f912-108">Tür</span><span class="sxs-lookup"><span data-stu-id="3f912-108">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3f912-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f912-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3f912-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3f912-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3f912-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="3f912-111">Attributes</span></span>  
 <span data-ttu-id="3f912-112">Yok.</span><span class="sxs-lookup"><span data-stu-id="3f912-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3f912-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f912-113">Child Elements</span></span>  
  
|<span data-ttu-id="3f912-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f912-114">Element</span></span>|<span data-ttu-id="3f912-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f912-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f912-116">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="3f912-116">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="3f912-117">Bir koleksiyonu `baseAddress` hizmet ana bilgisayarı tarafından kullanılan tabanı belirten öğeleri.</span><span class="sxs-lookup"><span data-stu-id="3f912-117">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="3f912-118">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="3f912-118">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="3f912-119">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="3f912-119">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3f912-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="3f912-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3f912-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="3f912-121">Element</span></span>|<span data-ttu-id="3f912-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3f912-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3f912-123">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="3f912-123">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="3f912-124">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="3f912-124">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3f912-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3f912-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="3f912-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="3f912-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
