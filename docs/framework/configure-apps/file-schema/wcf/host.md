---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: b764bc21e9c4555b39c3d096212b6e6bcabb62ff
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855220"
---
# \<host>
<span data-ttu-id="5a736-101">Hizmet ana bilgisayarının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a736-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="5a736-102">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a736-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="5a736-103">Tür</span><span class="sxs-lookup"><span data-stu-id="5a736-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a736-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a736-104">Attributes and Elements</span></span>  
 <span data-ttu-id="5a736-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5a736-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a736-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5a736-106">Attributes</span></span>  
 <span data-ttu-id="5a736-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="5a736-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5a736-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a736-108">Child Elements</span></span>  
  
|<span data-ttu-id="5a736-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a736-109">Element</span></span>|<span data-ttu-id="5a736-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a736-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="5a736-111">`baseAddress`Hizmet ana bilgisayarı tarafından kullanılan temel adresleri belirten öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="5a736-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="5a736-112">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="5a736-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a736-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5a736-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5a736-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="5a736-114">Element</span></span>|<span data-ttu-id="5a736-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5a736-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="5a736-116">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a736-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5a736-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5a736-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="5a736-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="5a736-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
