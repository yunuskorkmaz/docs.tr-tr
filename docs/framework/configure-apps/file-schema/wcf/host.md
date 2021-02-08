---
description: 'Hakkında daha fazla bilgi edinin: <host>'
title: <host>
ms.date: 03/30/2017
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
ms.openlocfilehash: ff240c85af3aab7c1208a6a49b1943f3c6a8cd99
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802287"
---
# \<host>

<span data-ttu-id="9b2a9-102">Hizmet ana bilgisayarının ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-102">Specifies settings for a service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<host>**  
  
## <a name="syntax"></a><span data-ttu-id="9b2a9-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="9b2a9-103">Syntax</span></span>  
  
```xml  
<host>
  <baseAddresses>
    <add baseAddress="string" />
  </baseAddresses>
  <timeOuts closeTimeout="TimeSpan"
            openTimeout="TimeSpan" />
</host>
```  
  
## <a name="type"></a><span data-ttu-id="9b2a9-104">Tür</span><span class="sxs-lookup"><span data-stu-id="9b2a9-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b2a9-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b2a9-105">Attributes and Elements</span></span>  

 <span data-ttu-id="9b2a9-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b2a9-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="9b2a9-107">Attributes</span></span>  

 <span data-ttu-id="9b2a9-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b2a9-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b2a9-109">Child Elements</span></span>  
  
|<span data-ttu-id="9b2a9-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b2a9-110">Element</span></span>|<span data-ttu-id="9b2a9-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b2a9-111">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="9b2a9-112">`baseAddress`Hizmet ana bilgisayarı tarafından kullanılan temel adresleri belirten öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-112">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[\<timeOuts>](timeouts.md)|<span data-ttu-id="9b2a9-113">Hizmet ana bilgisayarının açması veya kapatılması için izin verilen zaman aralığını belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-113">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b2a9-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="9b2a9-114">Parent Elements</span></span>  
  
|<span data-ttu-id="9b2a9-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="9b2a9-115">Element</span></span>|<span data-ttu-id="9b2a9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9b2a9-116">Description</span></span>|  
|-------------|-----------------|  
|[\<service>](service.md)|<span data-ttu-id="9b2a9-117">Bir Windows Communication Foundation (WCF) hizmetinin ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-117">Specifies the settings for a Windows Communication Foundation (WCF) service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b2a9-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9b2a9-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="9b2a9-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="9b2a9-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
