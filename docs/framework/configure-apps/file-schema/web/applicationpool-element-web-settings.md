---
title: <applicationPool> Öğesi (Web Ayarları)
ms.date: 03/30/2017
helpviewer_keywords:
- applicationPool element
- <applicationPool> element
ms.assetid: 46d1baaa-e343-4639-b70d-2a43a9f62b2a
ms.openlocfilehash: 6feaa801610fa0ffbbf47575f25aff29fa46a66c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152860"
---
# <a name="applicationpool-element-web-settings"></a><span data-ttu-id="45abf-102">\<applicationPool> Elemanı (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="45abf-102">\<applicationPool> Element (Web Settings)</span></span>
<span data-ttu-id="45abf-103">ASP.NET tarafından, bir ASP.NET uygulaması IIS 7.0 veya daha sonraki bir sürümde Tümleşik modda çalışırken, işlem genelindeki davranışı yönetmek için kullanılan yapılandırma ayarlarını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45abf-103">Specifies configuration settings that are used by ASP.NET to manage process-wide behavior when an ASP.NET application is running in Integrated mode on IIS 7.0 or a later version.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45abf-104">Bu öğe ve desteklediği özellik yalnızca ASP.NET uygulamanız IIS 7.0 veya sonraki sürümlerinde barındırılırsa çalışır.</span><span class="sxs-lookup"><span data-stu-id="45abf-104">This element and the feature it supports only work if your ASP.NET application is hosted on IIS 7.0 or later versions.</span></span>  
  
[<span data-ttu-id="45abf-105">**\<yapılandırma>**</span><span class="sxs-lookup"><span data-stu-id="45abf-105">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="45abf-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span><span class="sxs-lookup"><span data-stu-id="45abf-106">&nbsp;&nbsp;[**\<system.web>**](system-web-element-web-settings.md)</span></span>  
<span data-ttu-id="45abf-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<uygulamaHavuz>**</span><span class="sxs-lookup"><span data-stu-id="45abf-107">&nbsp;&nbsp;&nbsp;&nbsp;**\<applicationPool>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45abf-108">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45abf-108">Syntax</span></span>  
  
```xml  
<applicationPool
    maxConcurrentRequestsPerCPU="5000"
    maxConcurrentThreadsPerCPU="0"
    requestQueueLimit="5000" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="45abf-109">Öznitelikler ve Öğeler</span><span class="sxs-lookup"><span data-stu-id="45abf-109">Attributes and Elements</span></span>  

<span data-ttu-id="45abf-110">Öznitelikler, alt ve üst öğeler aşağıdaki bölümlerde açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="45abf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="45abf-111">Öznitelikler</span><span class="sxs-lookup"><span data-stu-id="45abf-111">Attributes</span></span>  
  
|<span data-ttu-id="45abf-112">Öznitelik</span><span class="sxs-lookup"><span data-stu-id="45abf-112">Attribute</span></span>|<span data-ttu-id="45abf-113">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45abf-113">Description</span></span>|  
|---------------|-----------------|  
|`maxConcurrentRequestsPerCPU`|<span data-ttu-id="45abf-114">CPU başına kaç eşzamanlı istek ASP.NET izin verdiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="45abf-114">Specifies how many simultaneous requests ASP.NET allows per CPU.</span></span>|  
|`maxConcurrentThreadsPerCPU`|<span data-ttu-id="45abf-115">Her CPU için bir uygulama havuzu için kaç eşzamanlı iş parçacığının çalıştığını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45abf-115">Specifies how many simultaneous threads can be running for an application pool for each CPU.</span></span> <span data-ttu-id="45abf-116">Bu, istekleri sunmak için CPU başına kullanılabilecek yönetilen iş parçacığı sayısını sınırlayabilirsiniz, çünkü ASP.NET eşzamanlılık denetlemek için alternatif bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="45abf-116">This provides an alternative way to control ASP.NET concurrency, because you can limit the number of managed threads that can be used per CPU to serve requests.</span></span> <span data-ttu-id="45abf-117">Varsayılan olarak bu ayar 0'dır, bu da ASP.NET CPU başına oluşturulabilecek iş parçacığı sayısını sınırlamadığı anlamına gelir, ancak CLR iş parçacığı havuzu oluşturulabilecek iş parçacığı sayısını da sınırlar.</span><span class="sxs-lookup"><span data-stu-id="45abf-117">By default this setting is 0, which means that ASP.NET does not limit the number of threads that can be created per CPU, although the CLR thread pool also limits the number of threads that can be created.</span></span>|  
|`requestQueueLimit`|<span data-ttu-id="45abf-118">Tek bir işlemde ASP.NET için sıraya alınabilecek en fazla istek sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="45abf-118">Specifies the maximum number of requests that can be queued for ASP.NET in a single process.</span></span> <span data-ttu-id="45abf-119">İki veya daha fazla ASP.NET uygulama tek bir uygulama havuzunda çalıştırıldığında, uygulama havuzundaki herhangi bir uygulamaya yapılan toplu istek kümesi bu ayara tabidir.</span><span class="sxs-lookup"><span data-stu-id="45abf-119">When two or more ASP.NET applications run in a single application pool, the cumulative set of requests being made to any application in the application pool is subject to this setting.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="45abf-120">Alt Öğeler</span><span class="sxs-lookup"><span data-stu-id="45abf-120">Child Elements</span></span>  
 <span data-ttu-id="45abf-121">Yok.</span><span class="sxs-lookup"><span data-stu-id="45abf-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="45abf-122">Üst Öğeler</span><span class="sxs-lookup"><span data-stu-id="45abf-122">Parent Elements</span></span>  
  
|<span data-ttu-id="45abf-123">Öğe</span><span class="sxs-lookup"><span data-stu-id="45abf-123">Element</span></span>|<span data-ttu-id="45abf-124">Açıklama</span><span class="sxs-lookup"><span data-stu-id="45abf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="45abf-125">\<system.web></span><span class="sxs-lookup"><span data-stu-id="45abf-125">\<system.web></span></span>](system-web-element-web-settings.md)|<span data-ttu-id="45abf-126">ASP.NET'nin ana bilgisayar uygulamasıyla nasıl etkileşimde bulunduğuhakkında bilgi içerir.</span><span class="sxs-lookup"><span data-stu-id="45abf-126">Contains information about how ASP.NET interacts with a host application.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45abf-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45abf-127">Remarks</span></span>  

<span data-ttu-id="45abf-128">IIS 7.0 veya daha sonraki bir sürümü Tümleşik modunda çalıştırdığınızda, bu öğe birleşimi, uygulama bir IIS uygulama havuzunda barındırıldığında iş parçacığı ve kuyruk isteklerini nasıl ASP.NET yapılandırmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="45abf-128">When you run IIS 7.0 or a later version in Integrated mode, this element combination lets you configure how ASP.NET manages threads and queues requests when the application is hosted in an IIS application pool.</span></span> <span data-ttu-id="45abf-129">IIS 6 çalıştırırsanız veya IIS 7.0'ı Klasik modda veya ISAPI modunda çalıştırırsanız, bu ayarlar yoksayılır.</span><span class="sxs-lookup"><span data-stu-id="45abf-129">If you run IIS 6 or you run IIS 7.0 in Classic mode or in ISAPI mode, these settings are ignored.</span></span>  
  
<span data-ttu-id="45abf-130">Ayarlar,.NET `applicationPool` Framework'ün belirli bir sürümünde çalışan tüm uygulama havuzları için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="45abf-130">The `applicationPool` settings apply to all application pools that run on a particular version of the .NET Framework.</span></span> <span data-ttu-id="45abf-131">Ayarlar bir aspnet.config dosyasında bulunur.</span><span class="sxs-lookup"><span data-stu-id="45abf-131">The settings are contained in an aspnet.config file.</span></span> <span data-ttu-id="45abf-132">Bu dosyanın .NET Framework'ün 2.0 ve 4.0 sürümleri için bir sürümü vardır.</span><span class="sxs-lookup"><span data-stu-id="45abf-132">There is a version of this file for versions 2.0 and 4.0 of the .NET Framework.</span></span> <span data-ttu-id="45abf-133">(.NET Framework'ün 3.0 ve 3.5 sürümleri aspnet.config dosyasını sürüm 2.0 ile paylaşır.)</span><span class="sxs-lookup"><span data-stu-id="45abf-133">(Versions 3.0 and 3.5 of the .NET Framework share the aspnet.config file with version 2.0.)</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45abf-134">Windows 7'de IIS 7.0 çalıştırıyorsanız, her uygulama havuzu için ayrı bir aspnet.config dosyası yapılandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="45abf-134">If you run IIS 7.0 on Windows 7, you can configure a separate aspnet.config file for every application pool.</span></span> <span data-ttu-id="45abf-135">Bu, her uygulama havuzu için iş parçacıklarının performansını uyarlamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="45abf-135">This lets you tailor the performance of the threads for each application pool.</span></span>  
  
<span data-ttu-id="45abf-136">Ayar `maxConcurrentRequestsPerCPU` için, .NET Framework 4'teki varsayılan "5000" ayarı, CPU başına 5000 veya daha fazla isteğiniz yoksa, ASP.NET tarafından denetlenir olan istek azaltmayı etkin bir şekilde kapatır.</span><span class="sxs-lookup"><span data-stu-id="45abf-136">For the `maxConcurrentRequestsPerCPU` setting, the default setting of "5000" in the .NET Framework 4 effectively turns off request throttling that is controlled by ASP.NET, unless you actually have 5000 or more requests per CPU.</span></span> <span data-ttu-id="45abf-137">Varsayılan ayar, bunun yerine CPU başına eşzamanlılık otomatik olarak yönetmek için CLR iş parçacığı havuzuna bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="45abf-137">The default setting depends instead on the CLR thread-pool to automatically manage concurrency per CPU.</span></span> <span data-ttu-id="45abf-138">Eşzamanlı istek işlemeyi kapsamlı olarak kullanan veya ağ I/O'da uzun süreli istekleri engellenen uygulamalar,.NET Framework 4'teki artan varsayılan sınırdan yararlanır.</span><span class="sxs-lookup"><span data-stu-id="45abf-138">Applications that make extensive use of asynchronous request processing, or that have many long-running requests blocked on network I/O, will benefit from the increased default limit in the .NET Framework 4.</span></span> <span data-ttu-id="45abf-139">Sıfıra ayar, `maxConcurrentRequestsPerCPU` ASP.NET isteklerini işlemek için yönetilen iş parçacıklarının kullanımını kapatır.</span><span class="sxs-lookup"><span data-stu-id="45abf-139">Setting `maxConcurrentRequestsPerCPU` to zero turns off the use of managed threads for processing ASP.NET requests.</span></span> <span data-ttu-id="45abf-140">Bir uygulama bir IIS uygulama havuzunda çalıştığında, istekler IIS G/Ç iş parçacığında kalır ve bu nedenle eşzamanlılık IIS iş parçacığı ayarları tarafından daraltılır.</span><span class="sxs-lookup"><span data-stu-id="45abf-140">When an application runs in an IIS application pool, requests stay on the IIS I/O thread and therefore concurrency is throttled by IIS thread settings.</span></span>  
  
<span data-ttu-id="45abf-141">Ayar, `requestQueueLimit` ASP.NET uygulamalar için `requestQueueLimit` Web.config dosyalarında ayarlanan [işlemModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) öğesinin özniteliğiyle aynı şekilde çalışır.</span><span class="sxs-lookup"><span data-stu-id="45abf-141">The `requestQueueLimit` setting works the same way as the `requestQueueLimit` attribute of the [processModel](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/7w2sway1(v=vs.100)) element, which is set in the Web.config files for ASP.NET applications.</span></span> <span data-ttu-id="45abf-142">Ancak, `requestQueueLimit` aspnet.config dosyasındaki ayar, `requestQueueLimit` Web.config dosyasındaki ayarı geçersiz kılar.</span><span class="sxs-lookup"><span data-stu-id="45abf-142">However, the `requestQueueLimit` setting in an aspnet.config file overrides the `requestQueueLimit` setting in a Web.config file.</span></span> <span data-ttu-id="45abf-143">Başka bir deyişle, her iki öznitelik de ayarlanmışsa (varsayılan olarak bu doğrudur), aspnet.config dosyasındaki `requestQueueLimit` ayar önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="45abf-143">In other words, if both attributes are set (by default, this is true), the `requestQueueLimit` setting in the aspnet.config file takes precedence.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45abf-144">Örnek</span><span class="sxs-lookup"><span data-stu-id="45abf-144">Example</span></span>  

<span data-ttu-id="45abf-145">Aşağıdaki örnek, aşağıdaki durumlarda aspnet.config dosyasındaki ASP.NET işlem genelindedavranışın nasıl yapılandırılabildiğini gösterir:</span><span class="sxs-lookup"><span data-stu-id="45abf-145">The following example shows how to configure ASP.NET process-wide behavior in the aspnet.config file in the following circumstances:</span></span>  
  
- <span data-ttu-id="45abf-146">Uygulama, IIS 7.0 uygulama havuzunda barındırılır.</span><span class="sxs-lookup"><span data-stu-id="45abf-146">The application is hosted in an IIS 7.0 application pool.</span></span>  
  
- <span data-ttu-id="45abf-147">IIS 7.0 Tümleşik modda çalışıyor.</span><span class="sxs-lookup"><span data-stu-id="45abf-147">IIS 7.0 is running in Integrated mode.</span></span>  
  
- <span data-ttu-id="45abf-148">Uygulama .NET Framework 3.5 SP1 veya daha sonraki bir sürümü kullanıyor.</span><span class="sxs-lookup"><span data-stu-id="45abf-148">The application is using the .NET Framework 3.5 SP1 or a later version.</span></span>  
  
<span data-ttu-id="45abf-149">Örnekteki değerler varsayılan değerlerdir.</span><span class="sxs-lookup"><span data-stu-id="45abf-149">The values in the example are the default values.</span></span>  
  
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
  
## <a name="element-information"></a><span data-ttu-id="45abf-150">Öğe Bilgisi</span><span class="sxs-lookup"><span data-stu-id="45abf-150">Element Information</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="45abf-151">Ad Alanı</span><span class="sxs-lookup"><span data-stu-id="45abf-151">Namespace</span></span>||  
|<span data-ttu-id="45abf-152">Şema Adı</span><span class="sxs-lookup"><span data-stu-id="45abf-152">Schema Name</span></span>||  
|<span data-ttu-id="45abf-153">Doğrulama Dosyası</span><span class="sxs-lookup"><span data-stu-id="45abf-153">Validation File</span></span>||  
|<span data-ttu-id="45abf-154">Boş Olabilir</span><span class="sxs-lookup"><span data-stu-id="45abf-154">Can be Empty</span></span>||  
  
## <a name="see-also"></a><span data-ttu-id="45abf-155">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45abf-155">See also</span></span>

- [<span data-ttu-id="45abf-156">\<system.web> Element (Web Ayarları)</span><span class="sxs-lookup"><span data-stu-id="45abf-156">\<system.web> Element (Web Settings)</span></span>](system-web-element-web-settings.md)
