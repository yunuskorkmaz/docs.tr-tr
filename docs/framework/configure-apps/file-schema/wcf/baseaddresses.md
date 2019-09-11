---
title: <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
ms.openlocfilehash: 9b3ed6b39f1743249925d5b6d9a47845c87983bc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70850213"
---
# <a name="baseaddresses"></a><span data-ttu-id="b7a7e-101">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="b7a7e-101">\<baseAddresses></span></span>
<span data-ttu-id="b7a7e-102">Şirket içinde barındırılan bir `baseAddress` ortamdaki hizmet ana bilgisayarı için temel adres olan bir öğe koleksiyonunu temsil eder.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-102">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="b7a7e-103">Bir temel adres varsa, uç noktalar temel adrese göre adreslerle yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-103">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
<span data-ttu-id="b7a7e-104">[ **\<Yapılandırma >** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b7a7e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b7a7e-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b7a7e-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b7a7e-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Hizmetler >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="b7a7e-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="b7a7e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<hizmet >** ](service.md)</span><span class="sxs-lookup"><span data-stu-id="b7a7e-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<service>**](service.md)</span></span>\
<span data-ttu-id="b7a7e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Ana bilgisayar >** ](host.md)</span><span class="sxs-lookup"><span data-stu-id="b7a7e-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<host>**](host.md)</span></span>\
<span data-ttu-id="b7a7e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<baseAddresses >**</span><span class="sxs-lookup"><span data-stu-id="b7a7e-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<baseAddresses>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7a7e-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b7a7e-110">Syntax</span></span>  
  
```xml  
<baseAddresses>
  <add baseAddress="string" />
</baseAddresses>
```  
  
## <a name="type"></a><span data-ttu-id="b7a7e-111">Tür</span><span class="sxs-lookup"><span data-stu-id="b7a7e-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7a7e-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7a7e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b7a7e-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7a7e-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="b7a7e-114">Attributes</span></span>  
 <span data-ttu-id="b7a7e-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b7a7e-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7a7e-116">Child Elements</span></span>  
  
|<span data-ttu-id="b7a7e-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7a7e-117">Element</span></span>|<span data-ttu-id="b7a7e-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7a7e-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a7e-119">\<> Ekle</span><span class="sxs-lookup"><span data-stu-id="b7a7e-119">\<add></span></span>](add-of-baseaddresses.md)|<span data-ttu-id="b7a7e-120">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7a7e-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="b7a7e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b7a7e-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="b7a7e-122">Element</span></span>|<span data-ttu-id="b7a7e-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b7a7e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b7a7e-124">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="b7a7e-124">\<host></span></span>](host.md)|<span data-ttu-id="b7a7e-125">Bir hizmet ana bilgisayarı için ayarları belirten bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b7a7e-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b7a7e-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="b7a7e-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="b7a7e-127">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
