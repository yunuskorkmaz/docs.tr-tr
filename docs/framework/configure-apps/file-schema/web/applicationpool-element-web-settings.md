---
title: <applicationPool> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 548f7de2753ef0c30aa787f4c879af87987bfbde
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621513"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="dc4b4-102">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="dc4b4-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="dc4b4-103">Bir ASP.NET uygulaması tümleşik modda çalıştırılan işlem genelinde yönetmesi için ASP.NET tarafından kullanılan yapılandırma ayarlarını belirten [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc4b4-104">ASP.NET uygulamanızı üzerinde barındırılıyorsa bu öğeyi ve bu özellik yalnızca iş desteklediği [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki sürümler.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-104">This element and the feature it supports only work if your ASP.NET application is hosted on [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or later versions.</span></span>  
  
 <span data-ttu-id="dc4b4-105">\<Yapılandırma ></span><span class="sxs-lookup"><span data-stu-id="dc4b4-105">\<configuration></span></span>  
<span data-ttu-id="dc4b4-106">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="dc4b4-106">\<system.web> Element (Web Settings)</span></span>  
<span data-ttu-id="dc4b4-107">\<applicationPool > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="dc4b4-107">\<applicationPool> Element (Web Settings)</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc4b4-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc4b4-108">Syntax</span></span>  
  
```xml  
<applicationPool   
    maxConcurrentRequestsPerCPU="5000"   
    maxConcurrentThreadsPerCPU="0"   
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dc4b4-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc4b4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dc4b4-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dc4b4-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="dc4b4-111">Attributes</span></span>  
  
|<span data-ttu-id="dc4b4-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="dc4b4-112">Attribute</span></span>|<span data-ttu-id="dc4b4-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc4b4-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="dc4b4-114">CPU ASP.NET sağlayan kaç tane eş zamanlı istek belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="dc4b4-115">Kaç tane eşzamanlı iş parçacığı her CPU için bir uygulama havuzu için çalışabilir belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="dc4b4-116">CPU isteklere hizmet için kullanılabilir yönetilen iş parçacığı sayısı sınırı, çünkü bu ASP.NET eşzamanlılık denetimi için alternatif bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="dc4b4-117">Varsayılan olarak bu ayar, CLR iş parçacığı havuzu da oluşturulabilir iş parçacığı sayısını sınırlar olsa da ASP.NET CPU oluşturulan iş parçacığı sayısını sınırlamaz anlamına gelen 0 ' dır.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="dc4b4-118">ASP.NET için tek bir işlemde sıraya alınabilecek istekleri en yüksek sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="dc4b4-119">İki veya daha fazla ASP.NET uygulamaları tek bir uygulama havuzunda çalıştırdığınızda, toplu uygulama havuzundaki herhangi bir uygulama için yapılan istekleri bu ayar tabi kümesidir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dc4b4-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc4b4-120">Child Elements</span></span>  
 <span data-ttu-id="dc4b4-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dc4b4-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="dc4b4-122">Parent Elements</span></span>  
  
|<span data-ttu-id="dc4b4-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="dc4b4-123">Element</span></span>|<span data-ttu-id="dc4b4-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dc4b4-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dc4b4-125">\<System.Web ></span><span class="sxs-lookup"><span data-stu-id="dc4b4-125">\<system.web></span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)|<span data-ttu-id="dc4b4-126">ASP.NET bir ana bilgisayar uygulaması ile nasıl etkileşim kurduğunu hakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc4b4-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc4b4-127">Remarks</span></span>  
 <span data-ttu-id="dc4b4-128">Çalıştırdığınızda [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] veya sonraki bir sürümünü tümleşik modunda bu öğe birleşimi, nasıl ASP.NET iş parçacıkları ve Kuyruklar isteklerini yöneten bir IIS uygulama havuzunda uygulama barındırıldığında yapılandırmanıza olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-128">When you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="dc4b4-129">IIS 6 çalıştırın ya da çalıştırdığınız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] Klasik modda veya ISAPI modunu, bu ayarları göz ardı edilir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-129">If you run IIS 6 or you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
 <span data-ttu-id="dc4b4-130">`applicationPool` .NET Framework'ün belirli bir sürümü çalıştıran tüm uygulama havuzları için ayarlar uygulanır.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="dc4b4-131">Ayarları bir aspnet.config dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="dc4b4-132">Bu dosya sürümleri 2.0 ve .NET Framework 4.0 sürümü yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="dc4b4-133">(Sürüm 3.0 ve 3.5 .NET Framework sürüm 2.0 ile aspnet.config dosyayı paylaşın.)</span><span class="sxs-lookup"><span data-stu-id="dc4b4-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dc4b4-134">Çalıştırırsanız [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] üzerinde [!INCLUDE[win7](../../../../../includes/win7-md.md)], ayrı aspnet.config dosyası her bir uygulama havuzu için yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-134">If you run [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] on [!INCLUDE[win7](../../../../../includes/win7-md.md)], you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="dc4b4-135">Bu, her bir uygulama havuzu için bir iş parçacığı performansını uyumlu hale getirmenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
 <span data-ttu-id="dc4b4-136">İçin `maxConcurrentRequestsPerCPU` ayarı, varsayılan ayar "5000" [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] gerçekten CPU başına 5000 veya daha fazla istek olmadığı sürece etkili bir şekilde başka bir deyişle, istek azaltma devre dışı bırakır ASP.NET tarafından denetlenir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="dc4b4-137">Varsayılan ayar yerine CLR iş parçacığı eşzamanlılık CPU başına otomatik olarak yönetmek için havuzu bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="dc4b4-138">Zaman uyumsuz istek işlemeye kapsamlı kullanımını olun veya ağ g/ç üzerinde engellendi çok uzun süre çalışan istekleri olan uygulamaların, artırılmış varsayılan sınırı'ndan yararlanacaktır [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dc4b4-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)].</span></span> <span data-ttu-id="dc4b4-139">Ayar `maxConcurrentRequestsPerCPU` için ASP.NET isteklerini işlemek için yönetilen iş parçacığı kullanımı sıfır kapatır.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="dc4b4-140">Bir IIS uygulama havuzunda uygulama çalıştığında, istekleri IIS g/ç iş parçacığı üzerinde kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından kısıtlanmış.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
 <span data-ttu-id="dc4b4-141">`requestQueueLimit` Ayarını aynı şekilde çalışır `requestQueueLimit` özniteliği [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) ASP.NET uygulamaları için Web.config dosyalarında ayarlanan öğesi.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="dc4b4-142">Ancak, `requestQueueLimit` aspnet.config dosyasındaki ayarını geçersiz kılar `requestQueueLimit` Web.config dosyasında ayarı.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="dc4b4-143">Diğer bir deyişle, her iki öznitelik ayarlarsanız (varsayılan olarak true budur), `requestQueueLimit` aspnet.config dosyasındaki ayarı öncelik alır.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc4b4-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="dc4b4-144">Example</span></span>  
 <span data-ttu-id="dc4b4-145">Aşağıdaki örnek, aşağıdaki koşullarda aspnet.config dosyasında ASP.NET işlem geneline yönelik davranışını yapılandırmak gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="dc4b4-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="dc4b4-146">Uygulama içinde barındırılan bir [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] uygulama havuzu.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-146">The application is hosted in an [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] application pool.</span></span>  
  
- [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] <span data-ttu-id="dc4b4-147">Tümleşik modda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-147">is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="dc4b4-148">Uygulamayı kullanarak [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] veya sonraki bir sürümü.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-148">The application is using the [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] or a later version.</span></span>  
  
 <span data-ttu-id="dc4b4-149">Varsayılan değerleri örnekte değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="dc4b4-150">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="dc4b4-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="dc4b4-151">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="dc4b4-151">Namespace</span></span>||  
|<span data-ttu-id="dc4b4-152">Şema adı</span><span class="sxs-lookup"><span data-stu-id="dc4b4-152">Schema Name</span></span>||  
|<span data-ttu-id="dc4b4-153">Doğrulama dosyası</span><span class="sxs-lookup"><span data-stu-id="dc4b4-153">Validation File</span></span>||  
|<span data-ttu-id="dc4b4-154">Boş olabilir.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="dc4b4-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc4b4-155">See also</span></span>

- [<span data-ttu-id="dc4b4-156">\<System.Web > öğesi (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="dc4b4-156">\<system.web> Element (Web Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/web/system-web-element-web-settings.md)
