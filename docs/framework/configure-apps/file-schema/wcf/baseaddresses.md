---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850213"
---
# \<baseAddresses>
<span data-ttu-id="c7517-101">`baseAddress`Şirket içinde barındırılan bir ortamdaki hizmet ana bilgisayarı için temel adres olan bir öğe koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c7517-101">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="c7517-102">Bir temel adres varsa, uç noktalar temel adrese göre adreslerle yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="c7517-102">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**  
  
## <a name="syntax"></a><span data-ttu-id="c7517-103">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7517-103">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="c7517-104">Tür</span><span class="sxs-lookup"><span data-stu-id="c7517-104">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7517-105">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7517-105">Attributes and Elements</span></span>  
 <span data-ttu-id="c7517-106">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="c7517-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7517-107">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="c7517-107">Attributes</span></span>  
 <span data-ttu-id="c7517-108">Yok.</span><span class="sxs-lookup"><span data-stu-id="c7517-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7517-109">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7517-109">Child Elements</span></span>  
  
|<span data-ttu-id="c7517-110">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7517-110">Element</span></span>|<span data-ttu-id="c7517-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7517-111">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-baseaddresses.md)|<span data-ttu-id="c7517-112">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c7517-112">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7517-113">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="c7517-113">Parent Elements</span></span>  
  
|<span data-ttu-id="c7517-114">Öğe</span><span class="sxs-lookup"><span data-stu-id="c7517-114">Element</span></span>|<span data-ttu-id="c7517-115">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7517-115">Description</span></span>|  
|-------------|-----------------|  
|[\<host>](host.md)|<span data-ttu-id="c7517-116">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="c7517-116">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c7517-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7517-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="c7517-118">Hosting</span><span class="sxs-lookup"><span data-stu-id="c7517-118">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
