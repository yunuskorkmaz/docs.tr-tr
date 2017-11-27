---
title: '&lt;baseAddresses&gt; &lt;eklemesi&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1bd7426f-5f4f-43fc-b8e9-de842219aa32
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9e941b63e42af9237388df6be8223acbad8db745
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltbaseaddressesgt"></a><span data-ttu-id="730a4-102">&lt;baseAddresses&gt; &lt;eklemesi&gt;</span><span class="sxs-lookup"><span data-stu-id="730a4-102">&lt;add&gt; of &lt;baseAddresses&gt;</span></span>
<span data-ttu-id="730a4-103">Hizmet ana bilgisayar tarafından kullanılan temel adres belirten bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="730a4-103">Represents a configuration element that specifies the base addresses used by the service host.</span></span>  
  
 <span data-ttu-id="730a4-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="730a4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="730a4-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="730a4-105">\<client></span></span>  
<span data-ttu-id="730a4-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="730a4-106">\<endpoint></span></span>  
<span data-ttu-id="730a4-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="730a4-107">\<host></span></span>  
<span data-ttu-id="730a4-108">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="730a4-108">\<baseAddresses></span></span>  
<span data-ttu-id="730a4-109">\<baseAddress ></span><span class="sxs-lookup"><span data-stu-id="730a4-109">\<baseAddress></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="730a4-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="730a4-110">Syntax</span></span>  
  
```xml  
<add baseAddress="string" />  
```  
  
## <a name="type"></a><span data-ttu-id="730a4-111">Tür</span><span class="sxs-lookup"><span data-stu-id="730a4-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="730a4-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="730a4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="730a4-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="730a4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="730a4-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="730a4-114">Attributes</span></span>  
  
|<span data-ttu-id="730a4-115">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="730a4-115">Attribute</span></span>|<span data-ttu-id="730a4-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730a4-116">Description</span></span>|  
|---------------|-----------------|  
|`baseAddress`|<span data-ttu-id="730a4-117">Hizmet ana bilgisayar tarafından kullanılan bir taban adresi belirten bir dize.</span><span class="sxs-lookup"><span data-stu-id="730a4-117">A string that specifies a base address used by the service host.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="730a4-118">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="730a4-118">Child Elements</span></span>  
 <span data-ttu-id="730a4-119">Yok.</span><span class="sxs-lookup"><span data-stu-id="730a4-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="730a4-120">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="730a4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="730a4-121">Öğe</span><span class="sxs-lookup"><span data-stu-id="730a4-121">Element</span></span>|<span data-ttu-id="730a4-122">Açıklama</span><span class="sxs-lookup"><span data-stu-id="730a4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="730a4-123">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="730a4-123">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="730a4-124">Bir koleksiyonu `baseAddress` öğeleri.</span><span class="sxs-lookup"><span data-stu-id="730a4-124">A collection of `baseAddress` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="730a4-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="730a4-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="730a4-126">Barındırma</span><span class="sxs-lookup"><span data-stu-id="730a4-126">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
