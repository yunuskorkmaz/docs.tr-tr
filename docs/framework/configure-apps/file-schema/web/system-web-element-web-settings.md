---
title: "&lt;System.Web&gt; öğesi (Web Ayarları)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 59899178fd9fc8da2334883ed62d9f8655eb335b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="568ff-102">&lt;System.Web&gt; öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="568ff-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="568ff-103">ASP.NET barındırma katman işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="568ff-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="568ff-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="568ff-104">\<configuration></span></span>  
<span data-ttu-id="568ff-105">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="568ff-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="568ff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="568ff-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="568ff-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="568ff-107">Attributes and Elements</span></span>  
 <span data-ttu-id="568ff-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="568ff-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="568ff-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="568ff-109">Attributes</span></span>  
 <span data-ttu-id="568ff-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="568ff-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="568ff-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="568ff-111">Child Elements</span></span>  
  
|<span data-ttu-id="568ff-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="568ff-112">Element</span></span>|<span data-ttu-id="568ff-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="568ff-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="568ff-114">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="568ff-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="568ff-115">IIS uygulama havuzları için yapılandırma ayarlarını bir aspnet.config dosyasında belirtir.</span><span class="sxs-lookup"><span data-stu-id="568ff-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="568ff-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="568ff-116">Parent Elements</span></span>  
  
|<span data-ttu-id="568ff-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="568ff-117">Element</span></span>|<span data-ttu-id="568ff-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="568ff-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="568ff-119">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="568ff-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="568ff-120">Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesi belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="568ff-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="568ff-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="568ff-121">Remarks</span></span>  
 <span data-ttu-id="568ff-122">`system.web` Öğesi ve kendi alt `applicationPool` öğesi için eklendi [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürümünden [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="568ff-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="568ff-123">Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya tümleşik mod sonraki sürümlerinde, bu öğe birleşimini ASP.NET iş parçacıklarını nasıl yönettiğini ve nasıl, kuyruklar istekleri ASP.NET bir IIS uygulama havuzunda barındırıldığında yapılandırmanıza sağlar.</span><span class="sxs-lookup"><span data-stu-id="568ff-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="568ff-124">Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümleri bu ayarları Klasik veya ISAPI modunda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="568ff-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="568ff-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="568ff-125">Example</span></span>  
 <span data-ttu-id="568ff-126">Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında ASP.NET işlem genelinde davranışı aspnet.config dosyasındaki yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="568ff-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="568ff-127">Örnek IIS tümleşik çalıştığını varsayar modu ve uygulama kullanıyor [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="568ff-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="568ff-128">Bu davranış sürümlerinde oluşmaz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] öncesi [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="568ff-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="568ff-129">Örnek değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="568ff-129">The values in the example are the default values.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## <a name="element-information"></a><span data-ttu-id="568ff-130">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="568ff-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="568ff-131">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="568ff-131">Namespace</span></span>||  
|<span data-ttu-id="568ff-132">Şema adı</span><span class="sxs-lookup"><span data-stu-id="568ff-132">Schema Name</span></span>||  
|<span data-ttu-id="568ff-133">Dosya doğrulama</span><span class="sxs-lookup"><span data-stu-id="568ff-133">Validation File</span></span>||  
|<span data-ttu-id="568ff-134">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="568ff-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="568ff-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="568ff-135">See Also</span></span>  
 [<span data-ttu-id="568ff-136">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="568ff-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
