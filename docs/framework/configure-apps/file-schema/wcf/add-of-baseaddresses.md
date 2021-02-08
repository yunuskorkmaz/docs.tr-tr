---
description: 'Hakkında daha fazla bilgi <add> edinin: <baseAddresses>'
title: <add> / <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: b25a4b5551784ecd8e67569c82c1388a144a9c9f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99804068"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="bbc5b-103">\<add> / \<baseAddresses></span><span class="sxs-lookup"><span data-stu-id="bbc5b-103">\<add> of \<baseAddresses></span></span>

<span data-ttu-id="bbc5b-104">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="bbc5b-104">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="bbc5b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bbc5b-105">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="bbc5b-106">Tür</span><span class="sxs-lookup"><span data-stu-id="bbc5b-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bbc5b-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbc5b-107">Attributes and Elements</span></span>  

 <span data-ttu-id="bbc5b-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="bbc5b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bbc5b-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="bbc5b-109">Attributes</span></span>  
  
|<span data-ttu-id="bbc5b-110">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="bbc5b-110">Attribute</span></span>|<span data-ttu-id="bbc5b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc5b-111">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="bbc5b-112">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="bbc5b-112">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bbc5b-113">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbc5b-113">Child Elements</span></span>  

 <span data-ttu-id="bbc5b-114">Yok.</span><span class="sxs-lookup"><span data-stu-id="bbc5b-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bbc5b-115">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="bbc5b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="bbc5b-116">Öğe</span><span class="sxs-lookup"><span data-stu-id="bbc5b-116">Element</span></span>|<span data-ttu-id="bbc5b-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bbc5b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<baseAddresses>](baseaddresses.md)|<span data-ttu-id="bbc5b-118">`baseAddress`Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="bbc5b-118">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bbc5b-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bbc5b-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="bbc5b-120">Hosting</span><span class="sxs-lookup"><span data-stu-id="bbc5b-120">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
