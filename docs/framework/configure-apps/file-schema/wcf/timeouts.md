---
title: "&lt;zaman aşımları&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: da80ab797078e1fe912ccbfff07d7fb2da49664e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="402c1-102">&lt;zaman aşımları&gt;</span><span class="sxs-lookup"><span data-stu-id="402c1-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="402c1-103">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="402c1-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="402c1-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="402c1-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="402c1-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="402c1-105">\<client></span></span>  
<span data-ttu-id="402c1-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="402c1-106">\<endpoint></span></span>  
<span data-ttu-id="402c1-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="402c1-107">\<host></span></span>  
<span data-ttu-id="402c1-108">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="402c1-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="402c1-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="402c1-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="402c1-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="402c1-110">Attributes and Elements</span></span>  
 <span data-ttu-id="402c1-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="402c1-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="402c1-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="402c1-112">Attributes</span></span>  
  
|<span data-ttu-id="402c1-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="402c1-113">Attribute</span></span>|<span data-ttu-id="402c1-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="402c1-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="402c1-115">A <xref:System.TimeSpan> hizmet ana bilgisayarı kapatmak izin verilen zaman aralığını belirtir değer.</span><span class="sxs-lookup"><span data-stu-id="402c1-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="402c1-116">A <xref:System.TimeSpan> açmak hizmet ana bilgisayarı için izin verilen zaman aralığını belirtir değer.</span><span class="sxs-lookup"><span data-stu-id="402c1-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="402c1-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="402c1-117">Child Elements</span></span>  
 <span data-ttu-id="402c1-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="402c1-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="402c1-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="402c1-119">Parent Elements</span></span>  
  
|<span data-ttu-id="402c1-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="402c1-120">Element</span></span>|<span data-ttu-id="402c1-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="402c1-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="402c1-122">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="402c1-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="402c1-123">Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="402c1-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="402c1-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="402c1-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="402c1-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="402c1-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
