---
title: WCF Performans Sayaçları
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 7c8a134039526abf046136ac383fbaff3a5abbfe
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90541219"
---
# <a name="wcf-performance-counters"></a>WCF Performans Sayaçları
Windows Communication Foundation (WCF), uygulamanızın performansını ölçgetirmenize yardımcı olacak büyük bir performans sayacı kümesi içerir.  
  
## <a name="enabling-performance-counters"></a>Performans sayaçlarını etkinleştirme  
 WCF hizmetinin app.config yapılandırma dosyası aracılığıyla bir WCF hizmeti için performans sayaçlarını aşağıdaki şekilde etkinleştirebilirsiniz:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters`Özniteliği, belirli bir performans sayacı türünü etkinleştirecek şekilde ayarlanabilir. Geçerli değerler şunlardır  
  
- All: tüm kategori sayaçları (ServiceModelService, ServiceModelEndpoint ve ServiceModelOperation) etkinleştirilir.  
  
- ServiceOnly: yalnızca ServiceModelService kategori sayaçları etkindir. Varsayılan değer budur.  
  
- Kapalı: ServiceModel * performans sayaçları devre dışı bırakıldı.  
  
 Tüm WCF uygulamaları için performans sayaçlarını etkinleştirmek istiyorsanız, yapılandırma ayarlarını Machine.config dosyasına yerleştirebilirsiniz.  Makinenizde performans sayaçları için yeterli bellek yapılandırma hakkında daha fazla bilgi için lütfen aşağıdaki **performans sayaçları Için bellek boyutunu artırma** bölümüne bakın.  
  
 Özel işlem invokers gibi WCF genişletilebilirlik noktalarını kullanırsanız, kendi performans Sayaçlarınızı da yaymalısınız. Bunun nedeni, bir genişletilebilirlik noktası uyguladığınızda WCF 'nin varsayılan yoldaki standart performans sayacı verilerini artık yaymayabilir. El ile performans sayacı desteğini uygulamadıysanız, beklediğinizi performans sayacı verilerini göremeyebilirsiniz.  
  
 Ayrıca kodunuzda performans sayaçlarını aşağıdaki şekilde etkinleştirebilirsiniz.  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a>Performans verilerini görüntüleme  
 Performans sayaçları tarafından yakalanan verileri görüntülemek için, Windows ile birlikte gelen performans Izleyicisini (Perfmon.exe) kullanabilirsiniz. **Başlat**' a gidip **Çalıştır** ' a tıklayıp iletişim kutusuna yazarak bu aracı başlatabilirsiniz `perfmon.exe` .  
  
> [!NOTE]
> Son iletiler bitiş noktası dağıtıcısı tarafından işlenmeden önce performans sayacı örnekleri serbest bırakılmış olabilir. Bu, performans verilerinin birkaç ileti için yakalanmasına yol açabilir.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Performans sayaçları için bellek boyutunu artırma  
 WCF, performans sayacı kategorileri için ayrı paylaşılan bellek kullanır.  
  
 Varsayılan olarak, ayrı paylaşılan bellek, genel performans sayacı belleğinin boyutu için bir çeyreğe ayarlanır. Varsayılan genel performans sayacı belleği 524.288 bayttır. Bu nedenle, üç WCF performans sayacı kategorisinin her biri yaklaşık 128KB varsayılan boyutu vardır. Bir makinedeki WCF uygulamalarının çalışma zamanı özelliklerine bağlı olarak, performans sayacı belleği tükenebilir. Bu durumda, WCF uygulama olay günlüğüne bir hata yazar. Hatanın içeriği bir performans sayacının yüklenmediğini ve girişin "System. InvalidOperationException: özel sayaçlar dosya görünümü bellek dışında" özel durum içerdiğini belirtir. İzleme hata düzeyinde etkinleştirilirse, bu hata da izleniyor. Performans sayacı belleği tükenirse, WCF uygulamalarınızı performans sayaçlarıyla çalıştırmaya devam etmek performans düşüşüne neden olabilir. Makinenin yöneticisiyseniz, her zaman var olan en fazla performans sayacı sayısını destekleyecek şekilde yeterli bellek ayırabilecek şekilde yapılandırmanız gerekir.  
  
 Kayıt defterindeki WCF kategorilerinin performans sayacı bellek miktarını değiştirebilirsiniz. Bunu yapmak için, aşağıdaki üç konuma adlı yeni bir DWORD değeri eklemeniz `FileMappingSize` ve bayt cinsinden istenen değere ayarlamanız gerekir. Bu değişikliklerin yürürlüğe alınması için makinenizi yeniden başlatın.  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0 \ performans  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0 \ performans  
  
- HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0 \ performans  
  
 Çok sayıda nesne (örneğin, ServiceHost) atıldığında ancak çöp toplanmayı beklerken, `PrivateBytes` performans sayacı alışılmadık bir yüksek sayıyı kaydeder. Bu sorunu çözmek için uygulamaya özel Sayaçlarınızı ekleyebilir ya da `performanceCounters` yalnızca hizmet düzeyi sayaçlarını etkinleştirmek için özniteliğini kullanabilirsiniz.  
  
## <a name="types-of-performance-counters"></a>Performans sayacı türleri  
 Performans sayaçları üç farklı düzeye sahiptir: hizmet, uç nokta ve Işlem.  
  
 Bir performans sayacı örneğinin adını almak için WMI ' y i kullanabilirsiniz. Örneğin,  
  
- Hizmet sayacı örnek adı, WMI [hizmeti](../wmi/service.md) örneğinin "CounterInstanceName" özelliği aracılığıyla alınabilir.  
  
- Uç nokta sayacı örneği adı, WMI [uç noktası](../wmi/endpoint.md) örneğinin "CounterInstanceName" özelliği aracılığıyla alınabilir.  
  
- İşlem sayacı örnek adı, WMI [uç noktası](../wmi/endpoint.md) örneğinin "GetOperationCounterInstanceName" yöntemiyle elde edilebilir.  
  
 WMI hakkında daha fazla bilgi için bkz. [Tanılama için Windows Yönetim araçları kullanma](../wmi/index.md).  
  
### <a name="service-performance-counters"></a>Hizmet performans sayaçları  
 Hizmet performans sayaçları, hizmet davranışını bir bütün olarak ölçer ve tüm hizmetin performansını tanılamak için kullanılabilir. Performans `ServiceModelService 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında bulunabilir. Örnekler aşağıdaki model kullanılarak adlandırılır:  
  
`ServiceName@ServiceBaseAddress`
  
 Bir hizmet kapsamındaki sayaç, bir uç nokta koleksiyonundaki sayaçdan toplanır.  
  
 Yeni bir InstanceContext oluşturulduğunda hizmet örneği oluşturma için performans sayaçları artırılır. Etkinleştirme dışı bir ileti (var olan bir hizmetle) aldığınızda ya da bir oturumdan bir örneğe bağlanıp oturumu sonlandırdığınızda ve sonra başka bir oturumdan yeniden bağlandığınızda bile yeni bir InstanceContext oluşturulduğunu unutmayın.  
  
### <a name="endpoint-performance-counters"></a>Uç nokta performans sayaçları  
 Uç nokta performans sayaçları, bir uç noktanın iletileri nasıl kabul ettiğini yansıtan verileri gözden etkinleştirmenizi sağlar. Performans `ServiceModelEndpoint 4.0.0.0` İzleyicisi kullanılarak görüntüleme sırasında performans nesnesi altında bulunabilir. Örnekler aşağıdaki model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 Veriler tek tek işlemler için toplanmaya benzerdir, ancak yalnızca uç nokta boyunca toplanır.  
  
 Bir uç nokta kapsamındaki sayaç, bir işlem koleksiyonundaki sayaçlardan toplanır.  
  
> [!NOTE]
> İki uç noktanın aynı sözleşme adları ve adresleri varsa, bunlar aynı sayaç örneğiyle eşleştirilir.  
  
### <a name="operation-performance-counters"></a>İşlem performansı sayaçları  
 Performans `ServiceModelOperation 4.0.0.0` İzleyicisi ile görüntülenirken Performans nesnesi altında işlem performansı sayaçları bulunur. Her işlemin tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşmede 10 işlem varsa, bu sözleşmeyle ilişkili 10 işlem sayacı örneği vardır. Nesne örnekleri aşağıdaki model kullanılarak adlandırılır:  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 Bu sayaç, çağrının nasıl kullanıldığını ve işlemin ne kadar iyi çalıştığını ölçmenize olanak sağlar.  
  
 Sayaçlar birden çok kapsamda görünür olduğunda, daha yüksek bir kapsamdan toplanan veriler, daha düşük kapsamlardan alınan verilerle toplanır. Örneğin, `Calls` bir uç nokta içindeki tüm işlem çağrılarının toplamını temsil eder; `Calls` bir hizmette, hizmet içindeki tüm uç noktalara yapılan çağrıların toplamı temsil eder.  
  
> [!NOTE]
> Bir sözleşmede yinelenen işlem adları varsa, her iki işlem için yalnızca bir sayaç örneği alırsınız.  
  
## <a name="programming-the-wcf-performance-counters"></a>WCF performans sayaçlarını programlama  

WCF performans sayaçlarına programlı bir şekilde erişebilmeniz için SDK yükleme klasörüne birkaç dosya yüklenir. Bu dosyalar aşağıdaki gibi listelenmiştir:
  
- *\_ServiceModelEndpointPerfCounters. VRG*
- *\_ServiceModelOperationPerfCounters. VRG*
- *\_ServiceModelServicePerfCounters. VRG*  
- *\_SMSvcHostPerfCounters. VRG*
- *\_Transactionköprüperfcounters. VRG*
  
Sayaçlara programlı olarak erişme hakkında daha fazla bilgi için bkz. [performans sayacı programlama mimarisi](/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).
  
## <a name="see-also"></a>Ayrıca bkz.

- [Yönetim ve tanılama](../index.md)
