---
title: '&lt;Ana bilgisayar&gt;'
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 1fb35058d407d0fbae78092bb4ccd45b0aaa40e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702034"
---
# <a name="lthostgt"></a><span data-ttu-id="6e0e2-102">&lt;Ana bilgisayar&gt;</span><span class="sxs-lookup"><span data-stu-id="6e0e2-102">&lt;host&gt;</span></span>
<span data-ttu-id="6e0e2-103">Hizmet konak makinesi ayarlarını belirler.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="6e0e2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6e0e2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6e0e2-105">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="6e0e2-105">\<services></span></span>  
<span data-ttu-id="6e0e2-106">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="6e0e2-106">\<service></span></span>  
<span data-ttu-id="6e0e2-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="6e0e2-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e0e2-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e0e2-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="6e0e2-109">Tür</span><span class="sxs-lookup"><span data-stu-id="6e0e2-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6e0e2-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e0e2-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6e0e2-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6e0e2-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="6e0e2-112">Attributes</span></span>  
 <span data-ttu-id="6e0e2-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6e0e2-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e0e2-114">Child Elements</span></span>  
  
|<span data-ttu-id="6e0e2-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e0e2-115">Element</span></span>|<span data-ttu-id="6e0e2-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e0e2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e0e2-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="6e0e2-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="6e0e2-118">Bir koleksiyonu `baseAddress` hizmet ana bilgisayarı tarafından kullanılan tabanı belirten öğeleri.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="6e0e2-119">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="6e0e2-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="6e0e2-120">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6e0e2-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="6e0e2-121">Parent Elements</span></span>  
  
|<span data-ttu-id="6e0e2-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="6e0e2-122">Element</span></span>|<span data-ttu-id="6e0e2-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6e0e2-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6e0e2-124">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="6e0e2-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="6e0e2-125">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6e0e2-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6e0e2-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="6e0e2-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="6e0e2-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
