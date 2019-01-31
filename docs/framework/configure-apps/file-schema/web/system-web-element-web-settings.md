---
title: < System.web > öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- Web.config configuration file [ASP.NET]
- system.Web element
- <system.Web> element
- ASP.NET configuration system
- configuration files [ASP.NET]
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
ms.openlocfilehash: a8d0905dc64ae3e3c4977639ccf881a677de73a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272818"
---
# <a name="systemweb-element-web-settings"></a><span data-ttu-id="609d9-102">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="609d9-102">\<system.web> Element (Web Settings)</span></span>
<span data-ttu-id="609d9-103">ASP.NET barındırma katman işlem geneline yönelik davranışını nasıl yönettiği hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="609d9-103">Contains information about how the ASP.NET hosting layer manages process-wide behavior.</span></span>  
  
 <span data-ttu-id="609d9-104">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="609d9-104">\<configuration></span></span>  
<span data-ttu-id="609d9-105">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="609d9-105">\<system.web> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="609d9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="609d9-106">Syntax</span></span>  
  
```xml  
<system.web>  
</system.web>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="609d9-107">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="609d9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="609d9-108">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="609d9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="609d9-109">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="609d9-109">Attributes</span></span>  
 <span data-ttu-id="609d9-110">Yok.</span><span class="sxs-lookup"><span data-stu-id="609d9-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="609d9-111">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="609d9-111">Child Elements</span></span>  
  
|<span data-ttu-id="609d9-112">Öğe</span><span class="sxs-lookup"><span data-stu-id="609d9-112">Element</span></span>|<span data-ttu-id="609d9-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="609d9-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="609d9-114">\<ApplicationPool ></span><span class="sxs-lookup"><span data-stu-id="609d9-114">\<applicationPool></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|<span data-ttu-id="609d9-115">IIS uygulama havuzları için yapılandırma ayarlarını bir aspnet.config dosyasını belirtir.</span><span class="sxs-lookup"><span data-stu-id="609d9-115">Specifies configuration settings for IIS application pools in an aspnet.config file.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="609d9-116">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="609d9-116">Parent Elements</span></span>  
  
|<span data-ttu-id="609d9-117">Öğe</span><span class="sxs-lookup"><span data-stu-id="609d9-117">Element</span></span>|<span data-ttu-id="609d9-118">Açıklama</span><span class="sxs-lookup"><span data-stu-id="609d9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="609d9-119">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="609d9-119">\<configuration></span></span>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="609d9-120">Her yapılandırma dosyasında ortak dil çalışma zamanı tarafından kullanılan kök öğesini belirtir ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] uygulamalar.</span><span class="sxs-lookup"><span data-stu-id="609d9-120">Specifies the root element in every configuration file that is used by the common language runtime and [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] applications.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="609d9-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="609d9-121">Remarks</span></span>  
 <span data-ttu-id="609d9-122">`system.web` Öğesi ve kendi alt `applicationPool` öğesi eklendi [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] sürümünden [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="609d9-122">The `system.web` element and its child `applicationPool` element were added to the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] as of [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="609d9-123">Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya tümleşik modu sonraki sürümlerde, bu öğe birleşim ASP.NET iş parçacıkları nasıl yönettiğini ve nasıl Bu istekler kuyruğa bir IIS uygulama havuzunda ASP.NET barındırıldığında yapılandırmanıza sağlar.</span><span class="sxs-lookup"><span data-stu-id="609d9-123">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Integrated mode, this element combination lets you configure how ASP.NET manages threads and how it queues requests when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="609d9-124">Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümleri bu ayarları Klasik veya ISAPI modunda yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="609d9-124">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions in Classic or ISAPI mode, these settings are ignored.</span></span>  
  
## <a name="example"></a><span data-ttu-id="609d9-125">Örnek</span><span class="sxs-lookup"><span data-stu-id="609d9-125">Example</span></span>  
 <span data-ttu-id="609d9-126">Aşağıdaki örnek, bir IIS uygulama havuzunda ASP.NET barındırıldığında aspnet.config dosyasında ASP.NET işlem geneline yönelik davranışını yapılandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="609d9-126">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file when ASP.NET is hosted in an IIS application pool.</span></span> <span data-ttu-id="609d9-127">Örnek IIS içinde tümleşik çalıştığını varsayar modu ve uygulama kullanıyor [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="609d9-127">The example assumes that IIS is running in Integrated mode and that the application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span> <span data-ttu-id="609d9-128">Bu davranış sürümlerinde oluşmaz [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] öncesi [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="609d9-128">This behavior does not occur in versions of the [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] earlier than the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)].</span></span> <span data-ttu-id="609d9-129">Varsayılan değerleri örnekte değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="609d9-129">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="609d9-130">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="609d9-130">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="609d9-131">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="609d9-131">Namespace</span></span>||  
|<span data-ttu-id="609d9-132">Şema adı</span><span class="sxs-lookup"><span data-stu-id="609d9-132">Schema Name</span></span>||  
|<span data-ttu-id="609d9-133">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="609d9-133">Validation File</span></span>||  
|<span data-ttu-id="609d9-134">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="609d9-134">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="609d9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="609d9-135">See also</span></span>
- [<span data-ttu-id="609d9-136">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="609d9-136">\<applicationPool> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)
