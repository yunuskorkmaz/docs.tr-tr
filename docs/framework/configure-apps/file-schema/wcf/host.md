---
title: '&lt;ana bilgisayar&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a><span data-ttu-id="600d6-102">&lt;ana bilgisayar&gt;</span><span class="sxs-lookup"><span data-stu-id="600d6-102">&lt;host&gt;</span></span>
<span data-ttu-id="600d6-103">Hizmet ana bilgisayarı ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="600d6-103">Specifies settings for a service host.</span></span>  
  
 <span data-ttu-id="600d6-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="600d6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="600d6-105">\<Hizmetleri ></span><span class="sxs-lookup"><span data-stu-id="600d6-105">\<services></span></span>  
<span data-ttu-id="600d6-106">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="600d6-106">\<service></span></span>  
<span data-ttu-id="600d6-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="600d6-107">\<host></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="600d6-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="600d6-108">Syntax</span></span>  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a><span data-ttu-id="600d6-109">Tür</span><span class="sxs-lookup"><span data-stu-id="600d6-109">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="600d6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="600d6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="600d6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="600d6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="600d6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="600d6-112">Attributes</span></span>  
 <span data-ttu-id="600d6-113">Yok.</span><span class="sxs-lookup"><span data-stu-id="600d6-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="600d6-114">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="600d6-114">Child Elements</span></span>  
  
|<span data-ttu-id="600d6-115">Öğe</span><span class="sxs-lookup"><span data-stu-id="600d6-115">Element</span></span>|<span data-ttu-id="600d6-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="600d6-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="600d6-117">\<baseAddresses ></span><span class="sxs-lookup"><span data-stu-id="600d6-117">\<baseAddresses></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|<span data-ttu-id="600d6-118">Bir koleksiyonu `baseAddress` hizmeti ana bilgisayar tarafından kullanılan temel adres belirtir öğeleri.</span><span class="sxs-lookup"><span data-stu-id="600d6-118">A collection of `baseAddress` elements that specifies the base addresses used by the service host.</span></span>|  
|[<span data-ttu-id="600d6-119">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="600d6-119">\<timeOuts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|<span data-ttu-id="600d6-120">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="600d6-120">A configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="600d6-121">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="600d6-121">Parent Elements</span></span>  
  
|<span data-ttu-id="600d6-122">Öğe</span><span class="sxs-lookup"><span data-stu-id="600d6-122">Element</span></span>|<span data-ttu-id="600d6-123">Açıklama</span><span class="sxs-lookup"><span data-stu-id="600d6-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="600d6-124">\<Hizmet ></span><span class="sxs-lookup"><span data-stu-id="600d6-124">\<service></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|<span data-ttu-id="600d6-125">Ayarlarını belirten bir [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] hizmet.</span><span class="sxs-lookup"><span data-stu-id="600d6-125">Specifies the settings for a [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] service.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="600d6-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="600d6-126">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="600d6-127">Barındırma</span><span class="sxs-lookup"><span data-stu-id="600d6-127">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
