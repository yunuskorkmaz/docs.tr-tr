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
# <a name="wcf-performance-counters"></a>WCF Performans Sayaçları
Çok sayıda performans sayaçları, uygulamanızın performansını ölçmek amacıyla Windows Communication Foundation (WCF) içerir.  
  
## <a name="enabling-performance-counters"></a>Performans sayaçlarını etkinleştirmek için  
 Bir WCF hizmeti için performans sayaçları app.config yapılandırma dosyası WCF hizmeti şu şekilde etkinleştirebilirsiniz:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Özniteliği, belirli türde bir performans sayaçlarını etkinleştirmek için ayarlanabilir. Geçerli değerler:  
  
-   Tümü: Tüm kategori sayaçları (ServiceModelService, ServiceModelEndpoint ve ServiceModelOperation) etkinleştirilir.  
  
-   ServiceOnly: Yalnızca ServiceModelService kategori sayaçları etkinleştirildi. Varsayılan değer budur.  
  
-   Kapalı: ServiceModel * performans sayaçları devre dışı bırakıldı.  
  
 Tüm WCF uygulamaları için performans sayaçlarını etkinleştirmek istiyorsanız, yapılandırma ayarlarını Machine.config dosyasında yerleştirebilirsiniz.  Lütfen **performans sayaçları için artan bellek boyutunu** bölümünde aşağıdaki performans sayaçları için yeterli bellek makinenizde yapılandırma hakkında daha fazla bilgi için.  
  
 WCF genişletilebilirlik noktaları gibi özel işlemi invokers kullanırsanız, ayrıca kendi performans sayaçlarını yayması. WCF genişletilebilirlik noktası uygularsanız, artık varsayılan yolda standart performans sayacı verilerini yayabilir olmasıdır. El ile performans sayacı desteği uygulamaz, beklediğiniz performans sayacı verilerini göremeyebilirsiniz.  
  
 Ayrıca performans sayaçlarını kodunuzda şu şekilde etkinleştirebilirsiniz,  
  
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
  
## <a name="viewing-performance-data"></a>Performans verileri görüntüleme  
 Performans sayaçlarını tarafından yakalanan verileri görüntülemek için Windows ile birlikte gelen Performans İzleyicisi (Perfmon.exe) kullanabilirsiniz. Giderek bu araç başlatabilirsiniz **Başlat**, tıklatıp **çalıştırma** ve türü `perfmon.exe` iletişim kutusunda.  
  
> [!NOTE]
>  Uç nokta gönderici tarafından işlenen son iletilerin önce performans sayaç örnekleri yayımlanabilir. Bu performans verileri için birkaç ileti yakalanan değil neden olabilir.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Performans sayaçları için artan bellek boyutu  
 WCF kendi performans sayacı kategorileri için ayrı bir paylaşılan bellek kullanır.  
  
 Varsayılan olarak, ayrı bir paylaşılan bellek, üç aylık dönem için genel performans sayacı bellek boyutunu ayarlanır. Varsayılan genel performans sayacı bellek 524.288 bayttır. Bu nedenle, varsayılan boyutu yaklaşık 128 KB her üç WCF performans sayacı kategorileri gerekir. Bir makinede WCF uygulamaları çalışma zamanı özelliklerine bağlı olarak, performans sayacı bellek tükenmiş olabilir. Bu durumda, WCF hata uygulama olay günlüğüne yazar. Bir performans sayacı yüklenmedi ve özel durum girişini içeren hata içeriğini durumları "System.InvalidOperationException: özel sayaç dosya görünümdür, bellek yetersiz." Hata düzeyinde izleme etkinleştirilirse, bu hata Ayrıca izlenen. Performans sayacı bellek biterse, etkin performans sayaçlarını kullanarak, WCF uygulamaları çalıştırmaya devam içinde performans düşüşüne neden olabilir. Makinenin yöneticisiyseniz, herhangi bir zamanda bulunabilir performans sayaçları sayısı desteklemek için yeterli bellek ayırmak için yapılandırmanız gerekir.  
  
 Kayıt defterinde WCF kategorileri için performans sayacı bellek miktarını değiştirebilirsiniz. Bunu yapmak için yeni bir DWORD değeri adlı eklemeniz gerekir `FileMappingSize` için üç aşağıdaki konumlardan ve bayt cinsinden istenen değere ayarlayın. Bu değişikliklerin devreye alınır böylece, makineyi yeniden başlatın.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Ne zaman nesneleri (örneğin, ServiceHost) çok sayıda kaldırıldıklarından atık olarak toplanmış olması bekleniyor, ancak `PrivateBytes` performans sayacı kayıt olağandışı ölçüde yüksek bir sayı. Bu sorunu çözmek için kendi uygulamaya özgü sayaçları ekleyin veya kullanın `performanceCounters` yalnızca hizmet düzeyi sayaçları etkinleştirmek için özniteliği.  
  
## <a name="types-of-performance-counters"></a>Performans sayaçları türleri  
 Performans sayaçları için üç farklı düzeyde kapsamlı: hizmet uç noktası ve işlem.  
  
 WMI Performans sayacı örneğinin adını almak için kullanabilirsiniz. Örneğin,  
  
-   Hizmet sayaç örneği adı WMI aracılığıyla elde edilebilir [hizmet](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) örneğinin "CounterInstanceName" özelliği.  
  
-   Uç nokta sayaç örneği adı WMI aracılığıyla elde edilebilir [uç nokta](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "CounterInstanceName" özelliği.  
  
-   İşlem sayaç örneği adı WMI aracılığıyla elde edilebilir [uç nokta](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "GetOperationCounterInstanceName" yöntemi.  
  
 WMI hakkında daha fazla bilgi için bkz. [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Hizmeti performans sayaçları  
 Hizmeti performans sayaçları, hizmet davranışı bir bütün olarak ölçmek ve tüm servis performansını tanılamak için kullanılabilir. Altında bulunabilir `ServiceModelService 4.0.0.0` Performansı İzleyicisi ile görüntülerken Performans nesnesi. Örnekleri aşağıdaki deseni kullanılarak adlandırılır:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Uç noktaları koleksiyonu içinde sayacından hizmet kapsamındaki bir sayacı toplanır.  
  
 Hizmet örneği oluşturma için performans sayaçları, yeni bir InstanceContext oluşturulduğunda artırılır. Yeni bir InstanceContext bile (varolan bir hizmeti ile) etkinleştirme bir ileti aldığınızda veya ne zaman bir oturumdan bir örneğine bağlanmak, oturumu sonlandırmak ve ardından başka bir oturumu yeniden oluşturulduğunu unutmayın.  
  
### <a name="endpoint-performance-counters"></a>Uç nokta performans sayaçları  
 Uç nokta performans sayaçları, bir uç nokta ileti nasıl kabul yansıtan verilere bakmak etkinleştirin. Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi'ni kullanarak görüntülerken Performans nesnesi. Örnekleri aşağıdaki deseni kullanılarak adlandırılır:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Veriler ne tek işlemler için toplanır, ancak yalnızca uç nokta toplanır benzer.  
  
 Uç nokta bir kapsamda bir sayaç işlemlerinin bir koleksiyondaki sayaçlardan toplanır.  
  
> [!NOTE]
>  İki uç noktaları, aynı sözleşme adlarını ve adreslerini varsa, bunlar aynı sayacı örneğine eşlenir.  
  
### <a name="operation-performance-counters"></a>İşlem performansı sayaçları  
 İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` ile performans izleme görüntülerken Performans nesnesi. Her işlem, tek bir örneği vardır. Diğer bir deyişle, verilen bir sözleşme 10 işlemi varsa, 10 işlem örnekleri bu anlaşması ile ilişkilidir. Nesne örneklerini şu deseni kullanılarak adlandırılır:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiriyor ölçmek sağlar.  
  
 Sayaçları birden çok kapsam görünür olduğunda, daha yüksek bir kapsamdan toplanan verileri daha düşük kapsamlardan ile verileri toplanır. Örneğin, `Calls` bir uç noktada uç nokta; içindeki tüm işlem çağrıları toplamını temsil eder. `Calls` bir hizmetin tüm uç hizmetindeki tüm çağrıları toplamını temsil eder.  
  
> [!NOTE]
>  Yinelenen işlem adları bir sözleşmede varsa, her iki işlemleri için yalnızca bir sayaç örnekleri alın.  
  
## <a name="programming-the-wcf-performance-counters"></a>WCF performans sayaçları programlama  
 WCF performans sayaçları program aracılığıyla erişebilmesi için çeşitli dosyaları SDK yükleme klasörüne yüklenir. Bu dosyalar aşağıda listelenmiştir.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Sayaçları programlama yoluyla erişim hakkında daha fazla bilgi için bkz. [performans sayacı programlama mimarisi](https://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
