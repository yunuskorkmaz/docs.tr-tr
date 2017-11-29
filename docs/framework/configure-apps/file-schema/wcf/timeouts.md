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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41ebd88f64b001b577342562c9c3010b307aaccc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="72bc6-102">&lt;zaman aşımları&gt;</span><span class="sxs-lookup"><span data-stu-id="72bc6-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="72bc6-103">Hizmet ana bilgisayarı açmak veya kapatmak izin verilen zaman aralığını belirtir bir yapılandırma öğesi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="72bc6-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="72bc6-104">\<Sistem. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="72bc6-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="72bc6-105">\<İstemci ></span><span class="sxs-lookup"><span data-stu-id="72bc6-105">\<client></span></span>  
<span data-ttu-id="72bc6-106">\<uç noktası ></span><span class="sxs-lookup"><span data-stu-id="72bc6-106">\<endpoint></span></span>  
<span data-ttu-id="72bc6-107">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="72bc6-107">\<host></span></span>  
<span data-ttu-id="72bc6-108">\<zaman aşımı ></span><span class="sxs-lookup"><span data-stu-id="72bc6-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72bc6-109">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72bc6-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"  
   openTimeout="TimeSpan" >  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="72bc6-110">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="72bc6-110">Attributes and Elements</span></span>  
 <span data-ttu-id="72bc6-111">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="72bc6-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="72bc6-112">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="72bc6-112">Attributes</span></span>  
  
|<span data-ttu-id="72bc6-113">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="72bc6-113">Attribute</span></span>|<span data-ttu-id="72bc6-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72bc6-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="72bc6-115">A <xref:System.TimeSpan> hizmet ana bilgisayarı kapatmak izin verilen zaman aralığını belirtir değer.</span><span class="sxs-lookup"><span data-stu-id="72bc6-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="72bc6-116">A <xref:System.TimeSpan> açmak hizmet ana bilgisayarı için izin verilen zaman aralığını belirtir değer.</span><span class="sxs-lookup"><span data-stu-id="72bc6-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="72bc6-117">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="72bc6-117">Child Elements</span></span>  
 <span data-ttu-id="72bc6-118">Yok.</span><span class="sxs-lookup"><span data-stu-id="72bc6-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="72bc6-119">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="72bc6-119">Parent Elements</span></span>  
  
|<span data-ttu-id="72bc6-120">Öğe</span><span class="sxs-lookup"><span data-stu-id="72bc6-120">Element</span></span>|<span data-ttu-id="72bc6-121">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72bc6-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="72bc6-122">\<ana bilgisayar ></span><span class="sxs-lookup"><span data-stu-id="72bc6-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="72bc6-123">Hizmet ana bilgisayarı ayarlarını belirtir. bir yapılandırma öğesi.</span><span class="sxs-lookup"><span data-stu-id="72bc6-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72bc6-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="72bc6-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="72bc6-125">Barındırma</span><span class="sxs-lookup"><span data-stu-id="72bc6-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
