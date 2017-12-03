---
title: '&lt;baseAddresses&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78918102-2898-46e0-9ea8-6b8afe65603e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bfe66b499eb50a058ed8b6a46769893f6dc5fd6e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="ltbaseaddressesgt"></a><span data-ttu-id="4f621-102">&lt;baseAddresses&gt;</span><span class="sxs-lookup"><span data-stu-id="4f621-102">&lt;baseAddresses&gt;</span></span>
<span data-ttu-id="4f621-103">Bir koleksiyonunu temsil eder `baseAddress` otomatik olarak barındırılan bir ortamda hizmet ana bilgisayarı için temel adresler öğeleri.</span><span class="sxs-lookup"><span data-stu-id="4f621-103">Represents a collection of `baseAddress` elements, which are base addresses for a service host in a self-hosted environment.</span></span> <span data-ttu-id="4f621-104">Taban adresi varsa, taban adresi göre adresleriyle uç noktaları yapılandırılabilir.</span><span class="sxs-lookup"><span data-stu-id="4f621-104">If a base address is present, endpoints can be configured with addresses relative to the base address.</span></span>  
  
 <span data-ttu-id="4f621-105">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4f621-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4f621-106">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="4f621-106">\<client></span></span>  
<span data-ttu-id="4f621-107">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="4f621-107">\<endpoint></span></span>  
<span data-ttu-id="4f621-108">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="4f621-108">\<host></span></span>  
<span data-ttu-id="4f621-109">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="4f621-109">\<baseAddresses></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f621-110">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f621-110">Syntax</span></span>  
  
```xml  
<baseAddresses>  
   <add baseAddress="string" />  
</baseAddresses>  
```  
  
## <a name="type"></a><span data-ttu-id="4f621-111">Tür</span><span class="sxs-lookup"><span data-stu-id="4f621-111">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4f621-112">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f621-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4f621-113">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="4f621-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4f621-114">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="4f621-114">Attributes</span></span>  
 <span data-ttu-id="4f621-115">Yok.</span><span class="sxs-lookup"><span data-stu-id="4f621-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="4f621-116">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f621-116">Child Elements</span></span>  
  
|<span data-ttu-id="4f621-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f621-117">Element</span></span>|<span data-ttu-id="4f621-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f621-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f621-119">\<ekleme ></span><span class="sxs-lookup"><span data-stu-id="4f621-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)|<span data-ttu-id="4f621-120">Hizmet ana bilgisayar tarafından kullanılan temel adres belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f621-120">A configuration element that specifies the base addresses used by the service host.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4f621-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="4f621-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4f621-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="4f621-122">Element</span></span>|<span data-ttu-id="4f621-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f621-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4f621-124">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="4f621-124">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="4f621-125">Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="4f621-125">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f621-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4f621-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 <xref:System.ServiceModel.ServiceHostBase.BaseAddresses%2A>  
 [<span data-ttu-id="4f621-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="4f621-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
