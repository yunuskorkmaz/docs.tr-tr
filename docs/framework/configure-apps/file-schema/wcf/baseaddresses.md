---
description: 'Hakkında daha fazla bilgi edinin: <baseAddresses>'
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: a32afc23d4332bad149765a318c3ecdc73f99be0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749694"
---
# \<baseAddresses>

<span data-ttu-id="c49ba-102">`baseAddress`Şirket içinde barındırılan bir ortamdaki hizmet ana bilgisayarı için temel adres olan bir öğe koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c49ba-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="c49ba-103">Bir temel adres varsa, uç noktalar temel adrese göre adreslerle yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c49ba-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="c49ba-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="c49ba-104">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="c49ba-105">Tür</span><span class="sxs-lookup"><span data-stu-id="c49ba-105">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c49ba-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c49ba-106">Attributes and Elements</span></span>  

 <span data-ttu-id="c49ba-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c49ba-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c49ba-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c49ba-108">Attributes</span></span>  

 <span data-ttu-id="c49ba-109">Yok.</span><span class="sxs-lookup"><span data-stu-id="c49ba-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c49ba-110">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c49ba-110">Child Elements</span></span>  
  
|<span data-ttu-id="c49ba-111">Öğe</span><span class="sxs-lookup"><span data-stu-id="c49ba-111">Element</span></span>|<span data-ttu-id="c49ba-112">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c49ba-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="c49ba-113">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c49ba-113">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c49ba-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c49ba-114">Parent Elements</span></span>  
  
|<span data-ttu-id="c49ba-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="c49ba-115">Element</span></span>|<span data-ttu-id="c49ba-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c49ba-116">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="c49ba-117">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c49ba-117">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c49ba-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c49ba-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="c49ba-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="c49ba-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
