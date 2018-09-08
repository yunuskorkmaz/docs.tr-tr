---
title: WCF Performans Sayaçları
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: d0ad7ee0bc3ea1d15197e6b8d9888d60b21a2f15
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192192"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="9bc44-102">WCF Performans Sayaçları</span><span class="sxs-lookup"><span data-stu-id="9bc44-102">WCF Performance Counters</span></span>
<span data-ttu-id="9bc44-103">Çok sayıda performans sayaçları, uygulamanızın performansını ölçmek amacıyla Windows Communication Foundation (WCF) içerir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="9bc44-104">Performans sayaçlarını etkinleştirmek için</span><span class="sxs-lookup"><span data-stu-id="9bc44-104">Enabling Performance Counters</span></span>  
 <span data-ttu-id="9bc44-105">Bir WCF hizmeti için performans sayaçları app.config yapılandırma dosyası WCF hizmeti şu şekilde etkinleştirebilirsiniz:</span><span class="sxs-lookup"><span data-stu-id="9bc44-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9bc44-106">`performanceCounters` Özniteliği, belirli türde bir performans sayaçlarını etkinleştirmek için ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="9bc44-107">Geçerli değerler:</span><span class="sxs-lookup"><span data-stu-id="9bc44-107">Valid values are</span></span>  
  
-   <span data-ttu-id="9bc44-108">Tümü: Tüm kategori sayaçları (ServiceModelService, ServiceModelEndpoint ve ServiceModelOperation) etkinleştirilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
-   <span data-ttu-id="9bc44-109">ServiceOnly: Yalnızca ServiceModelService kategori sayaçları etkinleştirildi.</span><span class="sxs-lookup"><span data-stu-id="9bc44-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="9bc44-110">Varsayılan değer budur.</span><span class="sxs-lookup"><span data-stu-id="9bc44-110">This is the default value.</span></span>  
  
-   <span data-ttu-id="9bc44-111">Kapalı: ServiceModel \* performans sayaçları devre dışı bırakıldı.</span><span class="sxs-lookup"><span data-stu-id="9bc44-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="9bc44-112">Tüm WCF uygulamaları için performans sayaçlarını etkinleştirmek istiyorsanız, yapılandırma ayarlarını Machine.config dosyasında yerleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bc44-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="9bc44-113">Lütfen **performans sayaçları için artan bellek boyutunu** bölümünde aşağıdaki performans sayaçları için yeterli bellek makinenizde yapılandırma hakkında daha fazla bilgi için.</span><span class="sxs-lookup"><span data-stu-id="9bc44-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="9bc44-114">WCF genişletilebilirlik noktaları gibi özel işlemi invokers kullanırsanız, ayrıca kendi performans sayaçlarını yayması.</span><span class="sxs-lookup"><span data-stu-id="9bc44-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="9bc44-115">WCF genişletilebilirlik noktası uygularsanız, artık varsayılan yolda standart performans sayacı verilerini yayabilir olmasıdır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="9bc44-116">El ile performans sayacı desteği uygulamaz, beklediğiniz performans sayacı verilerini göremeyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bc44-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="9bc44-117">Ayrıca performans sayaçlarını kodunuzda şu şekilde etkinleştirebilirsiniz,</span><span class="sxs-lookup"><span data-stu-id="9bc44-117">You can also enable performance counters in your code as follows,</span></span>  
  
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
  
## <a name="viewing-performance-data"></a><span data-ttu-id="9bc44-118">Performans verileri görüntüleme</span><span class="sxs-lookup"><span data-stu-id="9bc44-118">Viewing Performance Data</span></span>  
 <span data-ttu-id="9bc44-119">Performans sayaçlarını tarafından yakalanan verileri görüntülemek için Windows ile birlikte gelen Performans İzleyicisi (Perfmon.exe) kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bc44-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="9bc44-120">Giderek bu araç başlatabilirsiniz **Başlat**, tıklatıp **çalıştırma** ve türü `perfmon.exe` iletişim kutusunda.</span><span class="sxs-lookup"><span data-stu-id="9bc44-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bc44-121">Uç nokta gönderici tarafından işlenen son iletilerin önce performans sayaç örnekleri yayımlanabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="9bc44-122">Bu performans verileri için birkaç ileti yakalanan değil neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="9bc44-123">Performans sayaçları için artan bellek boyutu</span><span class="sxs-lookup"><span data-stu-id="9bc44-123">Increasing Memory Size for Performance Counters</span></span>  
 <span data-ttu-id="9bc44-124">WCF kendi performans sayacı kategorileri için ayrı bir paylaşılan bellek kullanır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="9bc44-125">Varsayılan olarak, ayrı bir paylaşılan bellek, üç aylık dönem için genel performans sayacı bellek boyutunu ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="9bc44-126">Varsayılan genel performans sayacı bellek 524.288 bayttır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="9bc44-127">Bu nedenle, varsayılan boyutu yaklaşık 128 KB her üç WCF performans sayacı kategorileri gerekir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="9bc44-128">Bir makinede WCF uygulamaları çalışma zamanı özelliklerine bağlı olarak, performans sayacı bellek tükenmiş olabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="9bc44-129">Bu durumda, WCF hata uygulama olay günlüğüne yazar.</span><span class="sxs-lookup"><span data-stu-id="9bc44-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="9bc44-130">Bir performans sayacı yüklenmedi ve özel durum girişini içeren hata içeriğini durumları "System.InvalidOperationException: özel sayaç dosya görünümdür, bellek yetersiz."</span><span class="sxs-lookup"><span data-stu-id="9bc44-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="9bc44-131">Hata düzeyinde izleme etkinleştirilirse, bu hata Ayrıca izlenen.</span><span class="sxs-lookup"><span data-stu-id="9bc44-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="9bc44-132">Performans sayacı bellek biterse, etkin performans sayaçlarını kullanarak, WCF uygulamaları çalıştırmaya devam içinde performans düşüşüne neden olabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="9bc44-133">Makinenin yöneticisiyseniz, herhangi bir zamanda bulunabilir performans sayaçları sayısı desteklemek için yeterli bellek ayırmak için yapılandırmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="9bc44-134">Kayıt defterinde WCF kategorileri için performans sayacı bellek miktarını değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bc44-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="9bc44-135">Bunu yapmak için yeni bir DWORD değeri adlı eklemeniz gerekir `FileMappingSize` için üç aşağıdaki konumlardan ve bayt cinsinden istenen değere ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="9bc44-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="9bc44-136">Bu değişikliklerin devreye alınır böylece, makineyi yeniden başlatın.</span><span class="sxs-lookup"><span data-stu-id="9bc44-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
-   <span data-ttu-id="9bc44-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="9bc44-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="9bc44-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="9bc44-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
-   <span data-ttu-id="9bc44-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="9bc44-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="9bc44-140">Ne zaman nesneleri (örneğin, ServiceHost) çok sayıda kaldırıldıklarından atık olarak toplanmış olması bekleniyor, ancak `PrivateBytes` performans sayacı kayıt olağandışı ölçüde yüksek bir sayı.</span><span class="sxs-lookup"><span data-stu-id="9bc44-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="9bc44-141">Bu sorunu çözmek için kendi uygulamaya özgü sayaçları ekleyin veya kullanın `performanceCounters` yalnızca hizmet düzeyi sayaçları etkinleştirmek için özniteliği.</span><span class="sxs-lookup"><span data-stu-id="9bc44-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="9bc44-142">Performans sayaçları türleri</span><span class="sxs-lookup"><span data-stu-id="9bc44-142">Types of Performance Counters</span></span>  
 <span data-ttu-id="9bc44-143">Performans sayaçları için üç farklı düzeyde kapsamlı: hizmet uç noktası ve işlem.</span><span class="sxs-lookup"><span data-stu-id="9bc44-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="9bc44-144">WMI Performans sayacı örneğinin adını almak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="9bc44-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="9bc44-145">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="9bc44-145">For example,</span></span>  
  
-   <span data-ttu-id="9bc44-146">Hizmet sayaç örneği adı WMI aracılığıyla elde edilebilir [hizmet](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) örneğinin "CounterInstanceName" özelliği.</span><span class="sxs-lookup"><span data-stu-id="9bc44-146">Service counter instance name can be obtained through WMI [Service](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="9bc44-147">Uç nokta sayaç örneği adı WMI aracılığıyla elde edilebilir [uç nokta](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "CounterInstanceName" özelliği.</span><span class="sxs-lookup"><span data-stu-id="9bc44-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
-   <span data-ttu-id="9bc44-148">İşlem sayaç örneği adı WMI aracılığıyla elde edilebilir [uç nokta](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "GetOperationCounterInstanceName" yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9bc44-148">Operation counter instance name can be obtained through WMI [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="9bc44-149">WMI hakkında daha fazla bilgi için bkz. [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span><span class="sxs-lookup"><span data-stu-id="9bc44-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="9bc44-150">Hizmeti performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="9bc44-150">Service performance counters</span></span>  
 <span data-ttu-id="9bc44-151">Hizmeti performans sayaçları, hizmet davranışı bir bütün olarak ölçmek ve tüm servis performansını tanılamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="9bc44-152">Altında bulunabilir `ServiceModelService 4.0.0.0` Performansı İzleyicisi ile görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9bc44-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="9bc44-153">Örnekleri aşağıdaki deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="9bc44-153">The instances are named using the following pattern:</span></span>  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 <span data-ttu-id="9bc44-154">Uç noktaları koleksiyonu içinde sayacından hizmet kapsamındaki bir sayacı toplanır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="9bc44-155">Hizmet örneği oluşturma için performans sayaçları, yeni bir InstanceContext oluşturulduğunda artırılır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="9bc44-156">Yeni bir InstanceContext bile (varolan bir hizmeti ile) etkinleştirme bir ileti aldığınızda veya ne zaman bir oturumdan bir örneğine bağlanmak, oturumu sonlandırmak ve ardından başka bir oturumu yeniden oluşturulduğunu unutmayın.</span><span class="sxs-lookup"><span data-stu-id="9bc44-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="9bc44-157">Uç nokta performans sayaçları</span><span class="sxs-lookup"><span data-stu-id="9bc44-157">Endpoint performance counters</span></span>  
 <span data-ttu-id="9bc44-158">Uç nokta performans sayaçları, bir uç nokta ileti nasıl kabul yansıtan verilere bakmak etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="9bc44-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="9bc44-159">Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi'ni kullanarak görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9bc44-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="9bc44-160">Örnekleri aşağıdaki deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="9bc44-160">The instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 <span data-ttu-id="9bc44-161">Veriler ne tek işlemler için toplanır, ancak yalnızca uç nokta toplanır benzer.</span><span class="sxs-lookup"><span data-stu-id="9bc44-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="9bc44-162">Uç nokta bir kapsamda bir sayaç işlemlerinin bir koleksiyondaki sayaçlardan toplanır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bc44-163">İki uç noktaları, aynı sözleşme adlarını ve adreslerini varsa, bunlar aynı sayacı örneğine eşlenir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="9bc44-164">İşlem performansı sayaçları</span><span class="sxs-lookup"><span data-stu-id="9bc44-164">Operation performance counters</span></span>  
 <span data-ttu-id="9bc44-165">İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` ile performans izleme görüntülerken Performans nesnesi.</span><span class="sxs-lookup"><span data-stu-id="9bc44-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="9bc44-166">Her işlem, tek bir örneği vardır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-166">Each operation has an individual instance.</span></span> <span data-ttu-id="9bc44-167">Diğer bir deyişle, verilen bir sözleşme 10 işlemi varsa, 10 işlem örnekleri bu anlaşması ile ilişkilidir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="9bc44-168">Nesne örneklerini şu deseni kullanılarak adlandırılır:</span><span class="sxs-lookup"><span data-stu-id="9bc44-168">The object instances are named using the following pattern:</span></span>  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 <span data-ttu-id="9bc44-169">Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiriyor ölçmek sağlar.</span><span class="sxs-lookup"><span data-stu-id="9bc44-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="9bc44-170">Sayaçları birden çok kapsam görünür olduğunda, daha yüksek bir kapsamdan toplanan verileri daha düşük kapsamlardan ile verileri toplanır.</span><span class="sxs-lookup"><span data-stu-id="9bc44-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="9bc44-171">Örneğin, `Calls` bir uç noktada uç nokta; içindeki tüm işlem çağrıları toplamını temsil eder. `Calls` bir hizmetin tüm uç hizmetindeki tüm çağrıları toplamını temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9bc44-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bc44-172">Yinelenen işlem adları bir sözleşmede varsa, her iki işlemleri için yalnızca bir sayaç örnekleri alın.</span><span class="sxs-lookup"><span data-stu-id="9bc44-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="9bc44-173">WCF performans sayaçları programlama</span><span class="sxs-lookup"><span data-stu-id="9bc44-173">Programming the WCF Performance Counters</span></span>  
 <span data-ttu-id="9bc44-174">WCF performans sayaçları program aracılığıyla erişebilmesi için çeşitli dosyaları SDK yükleme klasörüne yüklenir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="9bc44-175">Bu dosyalar aşağıda listelenmiştir.</span><span class="sxs-lookup"><span data-stu-id="9bc44-175">These files are listed as follows.</span></span>  
  
-   <span data-ttu-id="9bc44-176">_ServiceModelEndpointPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="9bc44-176">_ServiceModelEndpointPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="9bc44-177">_ServiceModelOperationPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="9bc44-177">_ServiceModelOperationPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="9bc44-178">_ServiceModelServicePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="9bc44-178">_ServiceModelServicePerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="9bc44-179">_SMSvcHostPerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="9bc44-179">_SMSvcHostPerfCounters.vrg</span></span>  
  
-   <span data-ttu-id="9bc44-180">_TransactionBridgePerfCounters.vrg</span><span class="sxs-lookup"><span data-stu-id="9bc44-180">_TransactionBridgePerfCounters.vrg</span></span>  
  
 <span data-ttu-id="9bc44-181">Sayaçları programlama yoluyla erişim hakkında daha fazla bilgi için bkz. [performans sayacı programlama mimarisi](https://go.microsoft.com/fwlink/?LinkId=95179).</span><span class="sxs-lookup"><span data-stu-id="9bc44-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](https://go.microsoft.com/fwlink/?LinkId=95179).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bc44-182">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9bc44-182">See Also</span></span>  
 [<span data-ttu-id="9bc44-183">Yönetim ve Tanılama</span><span class="sxs-lookup"><span data-stu-id="9bc44-183">Administration and Diagnostics</span></span>](../../../../../docs/framework/wcf/diagnostics/index.md)
