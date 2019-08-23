---
title: <add> / <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: a94c5144d907c26e6f5eef09b1a17b17eb6c9e0f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920217"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="985f1-102">\<\<BaseAddresses > ekleyin ></span><span class="sxs-lookup"><span data-stu-id="985f1-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="985f1-103">Hizmet ana bilgisayarı tarafından kullanılan taban adresleri belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="985f1-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="985f1-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="985f1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="985f1-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="985f1-105">\<client></span></span>  
<span data-ttu-id="985f1-106">\<uç nokta ></span><span class="sxs-lookup"><span data-stu-id="985f1-106">\<endpoint></span></span>  
<span data-ttu-id="985f1-107">\<Ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="985f1-107">\<host></span></span>  
<span data-ttu-id="985f1-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="985f1-108">\<baseAddresses></span></span>  
<span data-ttu-id="985f1-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="985f1-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="985f1-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="985f1-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="985f1-111">Tür</span><span class="sxs-lookup"><span data-stu-id="985f1-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="985f1-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="985f1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="985f1-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="985f1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="985f1-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="985f1-114">Attributes</span></span>  
  
|<span data-ttu-id="985f1-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="985f1-115">Attribute</span></span>|<span data-ttu-id="985f1-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="985f1-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="985f1-117">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="985f1-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="985f1-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="985f1-118">Child Elements</span></span>  
 <span data-ttu-id="985f1-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="985f1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="985f1-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="985f1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="985f1-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="985f1-121">Element</span></span>|<span data-ttu-id="985f1-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="985f1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="985f1-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="985f1-123">\<baseAddresses></span></span>](baseaddresses.md)|<span data-ttu-id="985f1-124">`baseAddress` Öğelerin koleksiyonu.</span><span class="sxs-lookup"><span data-stu-id="985f1-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="985f1-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="985f1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="985f1-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="985f1-126">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
