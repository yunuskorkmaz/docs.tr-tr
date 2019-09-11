---
title: <add> / <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d75142209ad8706d0cad5ce188d9d991a5e881bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850590"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="94415-102">\<\<BaseAddresses > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="94415-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="94415-103">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="94415-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
<span data-ttu-id="94415-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="94415-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="94415-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="94415-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="94415-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="94415-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="94415-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<hizmet >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="94415-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="94415-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ana bilgisayar >** ](host.md)</span><span class="sxs-lookup"><span data-stu-id="94415-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="94415-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<baseAddresses >** ](baseaddresses.md)</span><span class="sxs-lookup"><span data-stu-id="94415-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<baseAddresses>**](baseaddresses.md)</span></span>\
<span data-ttu-id="94415-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> Ekle**</span><span class="sxs-lookup"><span data-stu-id="94415-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94415-111">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="94415-111">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="94415-112">Tür</span><span class="sxs-lookup"><span data-stu-id="94415-112">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="94415-113">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="94415-113">Attributes and Elements</span></span>  
 <span data-ttu-id="94415-114">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="94415-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="94415-115">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="94415-115">Attributes</span></span>  
  
|<span data-ttu-id="94415-116">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="94415-116">Attribute</span></span>|<span data-ttu-id="94415-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94415-117">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="94415-118">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="94415-118">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="94415-119">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="94415-119">Child Elements</span></span>  
 <span data-ttu-id="94415-120">Yok.</span><span class="sxs-lookup"><span data-stu-id="94415-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="94415-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="94415-121">Parent Elements</span></span>  
  
|<span data-ttu-id="94415-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="94415-122">Element</span></span>|<span data-ttu-id="94415-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="94415-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="94415-124">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="94415-124">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="94415-125">`baseAddress` Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="94415-125">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94415-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="94415-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="94415-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="94415-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
