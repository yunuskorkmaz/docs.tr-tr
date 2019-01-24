---
title: '&lt;baseAddresses&gt; &lt;eklemesi&gt;'
ms.date: 03/30/2017
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
ms.openlocfilehash: 31edf570a7374a4b4fe31760d35ec196ecfcb3c6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54553574"
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="60bc5-102">&lt;baseAddresses&gt; &lt;eklemesi&gt;</span><span class="sxs-lookup"><span data-stu-id="60bc5-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="60bc5-103">Hizmet ana bilgisayarı tarafından kullanılan tabanı belirten bir yapılandırma öğesini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="60bc5-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="60bc5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="60bc5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="60bc5-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="60bc5-105">\<client></span></span>  
<span data-ttu-id="60bc5-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="60bc5-106">\<endpoint></span></span>  
<span data-ttu-id="60bc5-107">\<konak ></span><span class="sxs-lookup"><span data-stu-id="60bc5-107">\<host></span></span>  
<span data-ttu-id="60bc5-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="60bc5-108">\<baseAddresses></span></span>  
<span data-ttu-id="60bc5-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="60bc5-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60bc5-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60bc5-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />
```  
  
## <a name="type"></a><span data-ttu-id="60bc5-111">Tür</span><span class="sxs-lookup"><span data-stu-id="60bc5-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="60bc5-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="60bc5-112">Attributes and Elements</span></span>  
 <span data-ttu-id="60bc5-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="60bc5-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="60bc5-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="60bc5-114">Attributes</span></span>  
  
|<span data-ttu-id="60bc5-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="60bc5-115">Attribute</span></span>|<span data-ttu-id="60bc5-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60bc5-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="60bc5-117">Hizmet ana bilgisayarı tarafından kullanılan taban adresini belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="60bc5-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="60bc5-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="60bc5-118">Child Elements</span></span>  
 <span data-ttu-id="60bc5-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="60bc5-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="60bc5-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="60bc5-120">Parent Elements</span></span>  
  
|<span data-ttu-id="60bc5-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="60bc5-121">Element</span></span>|<span data-ttu-id="60bc5-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="60bc5-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="60bc5-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="60bc5-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="60bc5-124">Bir koleksiyonu `baseAddress` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="60bc5-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="60bc5-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60bc5-125">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>
- [<span data-ttu-id="60bc5-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="60bc5-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
