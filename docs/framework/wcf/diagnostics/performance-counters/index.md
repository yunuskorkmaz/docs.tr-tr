---
title: WCF Performans Sayaçları
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: 1d9e6b83a78967193c4cb0343f6c77560354a837
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-performance-counters"></a>WCF Performans Sayaçları
Windows Communication Foundation (WCF) çok sayıda uygulamanızın performansını ölçmek yardımcı olması için performans sayaçları içerir.  
  
## <a name="enabling-performance-counters"></a>Performans sayaçları etkinleştirme  
 WCF Hizmeti app.config yapılandırma dosyası aracılığıyla şu şekilde bir WCF hizmeti için performans sayaçları etkinleştirebilirsiniz:  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 `performanceCounters` Özniteliği, performans sayaçları belirli bir tür etkinleştirmek için ayarlanabilir. Geçerli değerler:  
  
-   Tümü: Tüm kategori sayaçları (ServiceModelService, ServiceModelEndpoint ve ServiceModelOperation) etkinleştirilir.  
  
-   ServiceOnly: Yalnızca ServiceModelService kategori sayaçları etkinleştirildi. Varsayılan değer budur.  
  
-   Kapalı: ServiceModel * performans sayaçları devre dışı bırakıldı.  
  
 Tüm WCF uygulamaları için performans sayaçları etkinleştirmek istiyorsanız, yapılandırma ayarlarını Machine.config dosyasındaki yerleştirebilirsiniz.  Lütfen bakın **performans sayaçları için bellek boyutu artırmayı** bölümünde aşağıdaki performans sayaçları için yeterli bellek makinenizde yapılandırma hakkında daha fazla bilgi için.  
  
 Özel işlem invokers gibi WCF genişletilebilirlik noktaları kullanıyorsa, kendi performans sayaçlarını yayması. Genişletilebilirlik noktanız uygularsanız, WCF artık varsayılan yolda standart performans sayacı verilerini yayabilir olmasıdır. El ile performans sayacı desteği uygulamaz, beklediğiniz performans sayacı verilerini göremeyebilirsiniz.  
  
 Performans sayaçları, kodunuzda şu şekilde etkinleştirebilirsiniz,  
  
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
 Performans sayaçları tarafından yakalanan verileri görüntülemek için Windows ile birlikte gelen Performans İzleyicisi (Perfmon.exe) kullanabilirsiniz. Giderek bu aracı başlatabilirsiniz **Başlat**, tıklatıp **çalıştırmak** ve türü `perfmon.exe` iletişim kutusunda.  
  
> [!NOTE]
>  Performans sayacı örnekleri son iletileri uç nokta gönderici tarafından işlenen önce yayınlanan. Bu performans verileri için birkaç iletileri yakalanan değil neden olabilir.  
  
## <a name="increasing-memory-size-for-performance-counters"></a>Performans sayaçları için bellek boyutunu artırma  
 WCF kendi performans sayacı kategorileri için ayrı bir paylaşılan bellek kullanır.  
  
 Varsayılan olarak, ayrı bir paylaşılan bellek bir üç aylık dönem için genel performans sayacı bellek boyutu ayarlanır. Varsayılan genel performans sayacı bellek 524.288 bayttır. Bu nedenle, üç WCF performans sayacı kategorisi yaklaşık 128 KB her varsayılan boyutuna sahip. WCF uygulamaları bir makineye çalışma zamanı özelliklerine bağlı olarak, performans sayacı belleği tükendi. Bu durumda, WCF hata uygulama olay günlüğüne yazar. Bir performans sayacı yüklenmedi ve özel durum girdisini içeriyor hata içeriğini durumlarını "System.InvalidOperationException: özel sayaçlar dosya görünümdür, bellek yetersiz." Hata düzeyinde izleme etkinleştirilirse, bu hata Ayrıca izlenen. Performans sayacı bellek biterse, etkin performans sayaçları ile WCF uygulamaları çalıştırmaya devam performans düşüşüne neden olabilir. Makinenin yöneticisiyseniz, herhangi bir anda var olabilen performans sayaçları en fazla sayısını desteklemek için yeterli bellek ayıramadı şekilde yapılandırmanız gerekir.  
  
 Kayıt defterinde WCF kategorileri için performans sayacı bellek miktarını değiştirebilirsiniz. Bunu yapmak için adlı yeni bir DWORD değeri eklemeniz gerekir `FileMappingSize` için üç aşağıdaki konumlardan ve bayt istenilen değere ayarlayın. Böylece bu değişiklikleri yürürlüğe alınır makinenizi yeniden başlatın.  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance  
  
-   HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance  
  
 Ne zaman çok sayıda nesneleri (örneğin, ServiceHost) atıldı ancak atık toplanan olması bekleniyor `PrivateBytes` performans sayacı kayıt olağandışı ölçüde yüksek bir numarası. Bu sorunu gidermek için kendi uygulamaya özgü sayaçları ekleyin veya kullanmak `performanceCounters` özniteliği yalnızca hizmet düzeyi sayaçları sağlar.  
  
## <a name="types-of-performance-counters"></a>Performans sayaçları türleri  
 Performans sayaçları üç farklı düzeylere kapsamlı: hizmet ve uç nokta işlemi.  
  
 WMI Performans sayacı örneği adını almak için kullanabilirsiniz. Örneğin,  
  
-   Hizmet sayaç örneği adı WMI aracılığıyla elde edilebilir [hizmet](../../../../../docs/framework/wcf/diagnostics/wmi/service.md) örneğinin "CounterInstanceName" özelliği.  
  
-   Uç nokta sayaç örneği adı WMI aracılığıyla elde edilebilir [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "CounterInstanceName" özelliği.  
  
-   İşlem sayaç örneği adı WMI aracılığıyla elde edilebilir [Endpoint](../../../../../docs/framework/wcf/diagnostics/wmi/endpoint.md) örneğinin "GetOperationCounterInstanceName" yöntemi.  
  
 WMI ile ilgili daha fazla bilgi için bkz [tanılama için Windows Yönetim araçları kullanarak](../../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
### <a name="service-performance-counters"></a>Hizmet performansı sayaçları  
 Hizmeti performans sayaçları hizmet davranışı bir bütün olarak ölçmek ve tüm hizmet performansını tanılamak için kullanılabilir. Altında bulunabilir `ServiceModelService 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi. Örnekleri şu biçimi kullanarak adlandırılır:  
  
```  
ServiceName@ServiceBaseAddress  
```  
  
 Bir hizmet kapsamındaki bir sayaç uç noktaları koleksiyonu sayaçtan toplanır.  
  
 Yeni bir InstanceContext oluşturulduğunda, hizmet örneği oluşturma için performans sayaçları artırılır. Yeni bir InstanceContext bile (var olan bir hizmeti ile) etkinleştirme olmayan bir ileti aldığınızda veya ne zaman bir oturumdan bir örneğine bağlanmak, oturumu sonlandırmak ve başka bir oturumu yeniden oluşturulduğunu unutmayın.  
  
### <a name="endpoint-performance-counters"></a>Uç noktası performans sayaçları  
 Uç noktası performans sayaçlarını nasıl bir uç nokta iletileri kabul etmeye yansıtma verilerini görmesine olanak sağlar. Altında bulunabilir `ServiceModelEndpoint 4.0.0.0` Performans İzleyicisi'ni kullanarak görüntülerken Performans nesnesi. Örnekleri şu biçimi kullanarak adlandırılır:  
  
```  
(ServiceName).(ContractName)@(endpoint listener address)  
```  
  
 Verileri ne tek tek işlemleri için toplanan olmakla birlikte, yalnızca son nokta toplanır benzer.  
  
 Bir uç nokta kapsamında bir sayaç işlemlerinin bir koleksiyondaki sayaçlardan toplanır.  
  
> [!NOTE]
>  İki uç nokta aynı sözleşme adlar ve adresler varsa, bunlar aynı sayaç örneği eşlenir.  
  
### <a name="operation-performance-counters"></a>İşlem performansı sayaçları  
 İşlem performansı sayaçları altında bulunan `ServiceModelOperation 4.0.0.0` Performans İzleyicisi ile görüntülerken Performans nesnesi. Her işlem tek bir örneği vardır. Diğer bir deyişle, belirli bir sözleşme 10 işlemler varsa, 10 işlemi örnekleri bu sözleşme ile ilişkilendirilmiş. Nesne örneklerini şu biçimi kullanarak adlandırılır:  
  
```  
(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)  
```  
  
 Bu sayaç, çağrı nasıl kullanıldığını ve ne kadar iyi işlemi gerçekleştiren ölçmek sağlar.  
  
 Sayaçları birden çok kapsam görünür olduğunda, daha yüksek bir kapsamdan toplanan verileri daha düşük kapsamlardan verilerle toplanır. Örneğin, `Calls` bir uç noktada; endpoint içindeki tüm işlem çağrıları toplamını temsil eder `Calls` bir hizmetin tüm uç noktaları hizmet içinde tüm çağrıları toplamını temsil eder.  
  
> [!NOTE]
>  Bir sözleşmede yinelenen işlem adları varsa, her iki işlemleri için yalnızca bir örnekleri alın.  
  
## <a name="programming-the-wcf-performance-counters"></a>WCF performans sayaçları programlama  
 WCF performans sayaçları program aracılığıyla erişebilmesi için birkaç dosya SDK yükleme klasörüne yüklenir. Bu dosyalar aşağıda listelenmiştir.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Sayaçları programlı erişim hakkında daha fazla bilgi için bkz: [performans sayacı programlama mimarisi](http://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
