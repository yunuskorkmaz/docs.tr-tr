---
title: <add> , <baseAddresses>
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: d66be51fa2626283063c250905efdb7d47babfb0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279948"
---
# <a name="add-of-baseaddresses"></a><span data-ttu-id="5ea49-102">\<Ekle >, \<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="5ea49-102">\<add> of \<baseAddresses></span></span>
<span data-ttu-id="5ea49-103">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5ea49-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="5ea49-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ea49-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ea49-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="5ea49-105">\<client></span></span>  
<span data-ttu-id="5ea49-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="5ea49-106">\<endpoint></span></span>  
<span data-ttu-id="5ea49-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="5ea49-107">\<host></span></span>  
<span data-ttu-id="5ea49-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="5ea49-108">\<baseAddresses></span></span>  
<span data-ttu-id="5ea49-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="5ea49-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ea49-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ea49-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="5ea49-111">Tür</span><span class="sxs-lookup"><span data-stu-id="5ea49-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ea49-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ea49-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5ea49-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="5ea49-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ea49-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="5ea49-114">Attributes</span></span>  
  
|<span data-ttu-id="5ea49-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="5ea49-115">Attribute</span></span>|<span data-ttu-id="5ea49-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ea49-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="5ea49-117">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="5ea49-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ea49-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ea49-118">Child Elements</span></span>  
 <span data-ttu-id="5ea49-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="5ea49-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ea49-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="5ea49-120">Parent Elements</span></span>  
  
|<span data-ttu-id="5ea49-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="5ea49-121">Element</span></span>|<span data-ttu-id="5ea49-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5ea49-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ea49-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="5ea49-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="5ea49-124">Bir koleksiyonu `baseAddress` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="5ea49-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5ea49-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ea49-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="5ea49-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="5ea49-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
