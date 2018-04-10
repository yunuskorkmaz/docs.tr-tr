---
title: WCF Performans Sayaçları
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: 37
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: be4ffac8444f6365dacb2b20db6abbb6792c2239
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="0ff72-102">WCF Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="0ff72-102">WCF Performance Counters</span></span>
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="0ff72-103">çok sayıda uygulamanızın performansını ölçmek yardımcı olması için performans sayaçları içerir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-103"> includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="0ff72-104">Performans sayaçları etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="0ff72-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="0ff72-105">İçin performans sayaçları etkinleştirebilirsiniz bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] app.config yapılandırma dosyası aracılığıyla hizmet [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] gibi hizmet:</span><span class="sxs-lookup"><span data-stu-id="0ff72-105">You can enable performance counters for a [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service through the app.config configuration file of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="0ff72-106">`performanceCounters` Özniteliği, performans sayaçları belirli bir tür etkinleştirmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="0ff72-107">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="0ff72-107">Valid values are</span></span>  
  
-   <span data-ttu-id="0ff72-108">Tümü: Tüm kategori sayaçları (ServiceModelService, ServiceModelEndpoint ve ServiceModelOperation) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="0ff72-109">ServiceOnly: Yalnızca ServiceModelService kategori sayaçları etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="0ff72-110">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="0ff72-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="0ff72-111">Kapalı: ServiceModel \* performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="0ff72-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="0ff72-112">Tüm performans sayaçlarını etkinleştirmek istiyorsanız, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uygulamalar, yapılandırma ayarlarını Machine.config dosyasındaki yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff72-112">If you want to enable performance counters for all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="0ff72-113">Lütfen bakın **performans sayaçları için bellek boyutu artırmayı** bölümünde aşağıdaki performans sayaçları için yeterli bellek makinenizde yapılandırma hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="0ff72-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="0ff72-114">Kullanırsanız [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] özel işlem invokers gibi genişletilebilirlik noktaları, ayrıca kendi performans sayaçlarını yayması.</span><span class="sxs-lookup"><span data-stu-id="0ff72-114">If you use [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="0ff72-115">Genişletilebilirlik noktanız uygulamak, bunun nedeni, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] varsayılan yolda standart performans sayacı verilerini artık yayabilir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-115">This is because if you implement an extensibility point, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="0ff72-116">El ile performans sayacı desteği uygulamaz, beklediğiniz performans sayacı verilerini göremeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff72-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="0ff72-117">Performans sayaçları, kodunuzda şu şekilde etkinleştirebilirsiniz,</span><span class="sxs-lookup"><span data-stu-id="0ff72-117">You can also enable performance counters in your code as follows,</span></span>  
  
```  
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="0ff72-118">Performans verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="0ff72-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="0ff72-119">Performans sayaçları tarafından yakalanan verileri görüntülemek için Windows ile birlikte gelen Performans İzleyicisi (Perfmon.exe) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff72-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="0ff72-120">Giderek bu aracı başlatabilirsiniz **Başlat**, tıklatıp **çalıştırmak** ve türü `perfmon.exe` iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="0ff72-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ff72-121">Performans sayacı örnekleri son iletileri uç nokta gönderici tarafından işlenen önce yayınlanan.</span><span class="sxs-lookup"><span data-stu-id="0ff72-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="0ff72-122">Bu performans verileri için birkaç iletileri yakalanan değil neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="0ff72-123">Performans sayaçları için bellek boyutunu artırma</span><span class="sxs-lookup"><span data-stu-id="0ff72-123">Increasing Memory Size for Performance Counters</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="0ff72-124">kullanır, performans sayacı kategorileri için paylaşılan bellek ayırın.</span><span class="sxs-lookup"><span data-stu-id="0ff72-124"> uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="0ff72-125">Varsayılan olarak, ayrı bir paylaşılan bellek bir üç aylık dönem için genel performans sayacı bellek boyutu ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="0ff72-126">Varsayılan genel performans sayacı bellek 524.288 bayttır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="0ff72-127">Bu nedenle, üç [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performans sayacı kategorileri yaklaşık 128 KB her varsayılan boyutuna sahip.</span><span class="sxs-lookup"><span data-stu-id="0ff72-127">Therefore, the three [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="0ff72-128">Çalışma zamanı özelliklerine bağlı olarak [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uygulamaları bir makineye performans sayacı bellek tükendi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-128">Depending upon the runtime characteristics of the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="0ff72-129">Bu gerçekleştiğinde, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir hata uygulama olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="0ff72-129">When this happens, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] writes an error to the application event log.</span></span> <span data-ttu-id="0ff72-130">Bir performans sayacı yüklenmedi ve özel durum girdisini içeriyor hata içeriğini durumlarını "System.InvalidOperationException: özel sayaçlar dosya görünümdür, bellek yetersiz."</span><span class="sxs-lookup"><span data-stu-id="0ff72-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="0ff72-131">Hata düzeyinde izleme etkinleştirilirse, bu hata Ayrıca izlenen.</span><span class="sxs-lookup"><span data-stu-id="0ff72-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="0ff72-132">Performans sayacı bellek biterse, çalışmaya devam eder, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performans sayaçları etkinleştirilmiş uygulamalarla performans düşüşüne neden.</span><span class="sxs-lookup"><span data-stu-id="0ff72-132">If performance counter memory is exhausted, continuing to run your [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="0ff72-133">Makinenin yöneticisiyseniz, herhangi bir anda var olabilen performans sayaçları en fazla sayısını desteklemek için yeterli bellek ayıramadı şekilde yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="0ff72-134">İçin performans sayacı bellek miktarını değiştirebilirsiniz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kayıt defterinde kategoriler.</span><span class="sxs-lookup"><span data-stu-id="0ff72-134">You can change the amount of performance counter memory for [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] categories in the registry.</span></span> <span data-ttu-id="0ff72-135">Bunu yapmak için adlı yeni bir DWORD değeri eklemeniz gerekir `FileMappingSize` için üç aşağıdaki konumlardan ve bayt istenilen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="0ff72-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="0ff72-136">Böylece bu değişiklikleri yürürlüğe alınır makinenizi yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="0ff72-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="0ff72-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="0ff72-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="0ff72-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="0ff72-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="0ff72-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="0ff72-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="0ff72-140">Ne zaman çok sayıda nesneleri (örneğin, ServiceHost) atıldı ancak atık toplanan olması bekleniyor `PrivateBytes` performans sayacı kayıt olağandışı ölçüde yüksek bir numarası.</span><span class="sxs-lookup"><span data-stu-id="0ff72-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="0ff72-141">Bu sorunu gidermek için kendi uygulamaya özgü sayaçları ekleyin veya kullanmak `performanceCounters` özniteliği yalnızca hizmet düzeyi sayaçları sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff72-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="0ff72-142">Performans sayaçları türleri</span><span class="sxs-lookup"><span data-stu-id="0ff72-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="0ff72-143">Performans sayaçları üç farklı düzeylere kapsamlı: hizmet ve uç nokta işlemi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="0ff72-144">WMI Performans sayacı örneği adını almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0ff72-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="0ff72-145">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="0ff72-145">For example,</span></span>  
  
-   <span data-ttu-id="0ff72-146">Hizmet sayaç örneği adı WMI aracılığıyla elde edilebilir [hizmet](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) örneğinin "CounterInstanceName" özelliği.</span><span class="sxs-lookup"><span data-stu-id="0ff72-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="0ff72-147">Uç nokta sayaç örneği adı WMI aracılığıyla elde edilebilir [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "CounterInstanceName" özelliği.</span><span class="sxs-lookup"><span data-stu-id="0ff72-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="0ff72-148">İşlem sayaç örneği adı WMI aracılığıyla elde edilebilir [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "GetOperationCounterInstanceName" yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="0ff72-149">WMI ile ilgili daha fazla bilgi için bkz [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="0ff72-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="0ff72-150">Hizmet performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="0ff72-150">Service performance counters</span></span>  
 <span data-ttu-id="0ff72-151">Hizmeti performans sayaçları hizmet davranışı bir bütün olarak ölçmek ve tüm hizmet performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="0ff72-152">Altında bulunabilir `ServiceModelService 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="0ff72-153">Örnekleri şu biçimi kullanarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="0ff72-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="0ff72-154">Bir hizmet kapsamındaki bir sayaç uç noktaları koleksiyonu sayaçtan toplanır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="0ff72-155">Yeni bir InstanceContext oluşturulduğunda, hizmet örneği oluşturma için performans sayaçları artırılır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="0ff72-156">Yeni bir InstanceContext bile (var olan bir hizmeti ile) etkinleştirme olmayan bir ileti aldığınızda veya ne zaman bir oturumdan bir örneğine bağlanmak, oturumu sonlandırmak ve başka bir oturumu yeniden oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="0ff72-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="0ff72-157">Uç noktası performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="0ff72-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="0ff72-158">Uç noktası performans sayaçlarını nasıl bir uç nokta iletileri kabul etmeye yansıtma verilerini görmesine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff72-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="0ff72-159">Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi'ni kullanarak görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="0ff72-160">Örnekleri şu biçimi kullanarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="0ff72-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="0ff72-161">Verileri ne tek tek işlemleri için toplanan olmakla birlikte, yalnızca son nokta toplanır benzer.</span><span class="sxs-lookup"><span data-stu-id="0ff72-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="0ff72-162">Bir uç nokta kapsamında bir sayaç işlemlerinin bir koleksiyondaki sayaçlardan toplanır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ff72-163">İki uç nokta aynı sözleşme adlar ve adresler varsa, bunlar aynı sayaç örneği eşlenir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="0ff72-164">İşlem performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="0ff72-164">Operation performance counters</span></span>  
 <span data-ttu-id="0ff72-165">İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="0ff72-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="0ff72-166">Her işlem tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-166">Each operation has an individual instance.</span></span> <span data-ttu-id="0ff72-167">Diğer bir deyişle, belirli bir sözleşme 10 işlemler varsa, 10 işlemi örnekleri bu sözleşme ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="0ff72-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="0ff72-168">Nesne örneklerini şu biçimi kullanarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="0ff72-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="0ff72-169">Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiren ölçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="0ff72-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="0ff72-170">Sayaçları birden çok kapsam görünür olduğunda, daha yüksek bir kapsamdan toplanan verileri daha düşük kapsamlardan verilerle toplanır.</span><span class="sxs-lookup"><span data-stu-id="0ff72-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="0ff72-171">Örneğin, `Calls` bir uç noktada; endpoint içindeki tüm işlem çağrıları toplamını temsil eder `Calls` bir hizmetin tüm uç noktaları hizmet içinde tüm çağrıları toplamını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0ff72-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0ff72-172">Bir sözleşmede yinelenen işlem adları varsa, her iki işlemleri için yalnızca bir örnekleri alın.</span><span class="sxs-lookup"><span data-stu-id="0ff72-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="0ff72-173">WCF performans sayaçları programlama</span><span class="sxs-lookup"><span data-stu-id="0ff72-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="0ff72-174">Böylece erişebilmeniz için birkaç dosyaları SDK yükleme klasöründe yüklü [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performans sayaçları programlı olarak.</span><span class="sxs-lookup"><span data-stu-id="0ff72-174">Several files are installed in the SDK install folder so that you can access the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performance counters programmatically.</span></span> <span data-ttu-id="0ff72-175">Bu dosyalar aşağıda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="0ff72-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="0ff72-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="0ff72-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="0ff72-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="0ff72-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="0ff72-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="0ff72-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="0ff72-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="0ff72-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="0ff72-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="0ff72-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="0ff72-181">Sayaçları programlı erişim hakkında daha fazla bilgi için bkz: [performans sayacı programlama mimarisi](http://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="0ff72-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](http://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ff72-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0ff72-182">See Also</span></span>  
 [<span data-ttu-id="0ff72-183">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="0ff72-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
