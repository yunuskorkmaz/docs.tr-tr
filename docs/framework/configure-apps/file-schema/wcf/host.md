---
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: 524226cbb826486def18c1b3b66c5b4a3c456dec
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185684"
---
# \<host>

<span data-ttu-id="13aea-101">Hizmet ana bilgisayarının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="13aea-101">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="13aea-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="13aea-102">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="13aea-103">Tür</span><span class="sxs-lookup"><span data-stu-id="13aea-103">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13aea-104">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="13aea-104">Attributes and Elements</span></span>  

 <span data-ttu-id="13aea-105">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="13aea-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13aea-106">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="13aea-106">Attributes</span></span>  

 <span data-ttu-id="13aea-107">Yok.</span><span class="sxs-lookup"><span data-stu-id="13aea-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="13aea-108">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="13aea-108">Child Elements</span></span>  
  
|<span data-ttu-id="13aea-109">Öğe</span><span class="sxs-lookup"><span data-stu-id="13aea-109">Element</span></span>|<span data-ttu-id="13aea-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13aea-110">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="13aea-111">`baseAddress`Hizmet ana bilgisayarı tarafından kullanılan temel adresleri belirten öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="13aea-111">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="13aea-112">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="13aea-112">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="13aea-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="13aea-113">Parent Elements</span></span>  
  
|<span data-ttu-id="13aea-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="13aea-114">Element</span></span>|<span data-ttu-id="13aea-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13aea-115">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="13aea-116">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="13aea-116">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13aea-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="13aea-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="13aea-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="13aea-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
