---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855220"
---
# <a name="host"></a><span data-ttu-id="1b306-101">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="1b306-101">\<host></span></span>
<span data-ttu-id="1b306-102">Hizmet ana bilgisayarının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b306-102">Specifies settings for a service host.</span></span>  
  
<span data-ttu-id="1b306-103">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1b306-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1b306-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1b306-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1b306-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="1b306-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="1b306-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<hizmet >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="1b306-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="1b306-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Ana bilgisayar >**</span><span class="sxs-lookup"><span data-stu-id="1b306-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b306-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1b306-108">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="1b306-109">Tür</span><span class="sxs-lookup"><span data-stu-id="1b306-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b306-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b306-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1b306-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="1b306-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b306-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="1b306-112">Attributes</span></span>  
 <span data-ttu-id="1b306-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="1b306-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b306-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b306-114">Child Elements</span></span>  
  
|<span data-ttu-id="1b306-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b306-115">Element</span></span>|<span data-ttu-id="1b306-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b306-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b306-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="1b306-117">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="1b306-118">Hizmet ana bilgisayarı `baseAddress` tarafından kullanılan temel adresleri belirten öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="1b306-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="1b306-119">\<Zaman aşımları ></span><span class="sxs-lookup"><span data-stu-id="1b306-119">\<timeOuts></span></span>](timeouts.md)|<span data-ttu-id="1b306-120">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="1b306-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1b306-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="1b306-121">Parent Elements</span></span>  
  
|<span data-ttu-id="1b306-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="1b306-122">Element</span></span>|<span data-ttu-id="1b306-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1b306-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1b306-124">\<hizmet ></span><span class="sxs-lookup"><span data-stu-id="1b306-124">\<service></span></span>](service.md)|<span data-ttu-id="1b306-125">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="1b306-125">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1b306-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1b306-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="1b306-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="1b306-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
