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
ms.openlocfilehash: 44a978eae9ae85e1ba12f117288a3c9ce4db75b4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="ltsystemwebgt-element-web-settings"></a><span data-ttu-id="63eee-102">&lt;System.Web&gt; öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="63eee-102">&lt;system.web&gt; Element (Web Settings)</span></span>
<span data-ttu-id="63eee-103">ASP.NET barındırma katman işlem genelinde davranışı nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="63eee-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="63eee-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="63eee-104">\<configuration></span></span>  
<span data-ttu-id="63eee-105">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="63eee-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63eee-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="63eee-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63eee-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="63eee-107">Attributes and Elements</span></span>  
 <span data-ttu-id="63eee-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="63eee-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63eee-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="63eee-109">Attributes</span></span>  
 <span data-ttu-id="63eee-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="63eee-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="63eee-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="63eee-111">Child Elements</span></span>  
  
|<span data-ttu-id="63eee-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="63eee-112">Element</span></span>|<span data-ttu-id="63eee-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63eee-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63eee-114">\<applicationPool ></span><span class="sxs-lookup"><span data-stu-id="63eee-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="63eee-115">IIS uygulama havuzları için yapılandırma ayarlarını bir aspnet.config dosyasında belirtir.</span><span class="sxs-lookup"><span data-stu-id="63eee-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63eee-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="63eee-116">Parent Elements</span></span>  
  
|<span data-ttu-id="63eee-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="63eee-117">Element</span></span>|<span data-ttu-id="63eee-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="63eee-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63eee-119">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="63eee-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="63eee-120">Ortak dil çalışma zamanı tarafından kullanılan her yapılandırma dosyası kök öğesi belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="63eee-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63eee-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="63eee-121">Remarks</span></span>  
 <span data-ttu-id="63eee-122">`system.web` Öğesi ve kendi alt `applicationPool` öğesi için eklendi [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürümünden [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63eee-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="63eee-123">Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya tümleşik mod sonraki sürümlerinde, bu öğe birleşimini ASP.NET iş parçacıklarını nasıl yönettiğini ve nasıl, kuyruklar istekleri ASP.NET bir IIS uygulama havuzunda barındırıldığında yapılandırmanıza sağlar.</span><span class="sxs-lookup"><span data-stu-id="63eee-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="63eee-124">Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümleri bu ayarları Klasik veya ISAPI modunda göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="63eee-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63eee-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="63eee-125">Example</span></span>  
 <span data-ttu-id="63eee-126">Aşağıdaki örnek, ASP.NET bir IIS uygulama havuzunda barındırıldığında ASP.NET işlem genelinde davranışı aspnet.config dosyasındaki yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="63eee-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="63eee-127">Örnek IIS tümleşik çalıştığını varsayar modu ve uygulama kullanıyor [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="63eee-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="63eee-128">Bu davranış sürümlerinde oluşmaz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] öncesi [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63eee-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="63eee-129">Örnek değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="63eee-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="63eee-130">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="63eee-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="63eee-131">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="63eee-131">Namespace</span></span>||  
|<span data-ttu-id="63eee-132">Şema adı</span><span class="sxs-lookup"><span data-stu-id="63eee-132">Schema Name</span></span>||  
|<span data-ttu-id="63eee-133">Dosya doğrulama</span><span class="sxs-lookup"><span data-stu-id="63eee-133">Validation File</span></span>||  
|<span data-ttu-id="63eee-134">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="63eee-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="63eee-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="63eee-135">See Also</span></span>  
 [<span data-ttu-id="63eee-136">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="63eee-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
