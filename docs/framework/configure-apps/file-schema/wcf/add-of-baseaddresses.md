---
title: <add> / <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70850590"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="7659f-102">\<add> / \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="7659f-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="7659f-103">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="7659f-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="7659f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7659f-104">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="7659f-105">Tür</span><span class="sxs-lookup"><span data-stu-id="7659f-105">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7659f-106">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="7659f-106">Attributes and Elements</span></span>  
 <span data-ttu-id="7659f-107">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="7659f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7659f-108">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="7659f-108">Attributes</span></span>  
  
|<span data-ttu-id="7659f-109">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="7659f-109">Attribute</span></span>|<span data-ttu-id="7659f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7659f-110">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="7659f-111">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="7659f-111">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7659f-112">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="7659f-112">Child Elements</span></span>  
 <span data-ttu-id="7659f-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="7659f-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7659f-114">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="7659f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="7659f-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="7659f-115">Element</span></span>|<span data-ttu-id="7659f-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7659f-116">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="7659f-117">`baseAddress`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="7659f-117">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7659f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7659f-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="7659f-119">Hosting</span><span class="sxs-lookup"><span data-stu-id="7659f-119">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
