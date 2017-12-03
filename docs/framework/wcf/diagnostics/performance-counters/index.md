---
title: "WCF Performans Sayaçları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
caps.latest.revision: "37"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3f9834e99fb7fa98e2f986a1ce5460aa387143f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-performance-counters"></a>WCF Performans Sayaçları
[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]çok sayıda uygulamanızın performansını ölçmek yardımcı olması için performans sayaçları içerir.  
  
## <a name="enabling-performance-counters"></a>Performans sayaçları etkinleştirme  
 İçin performans sayaçları etkinleştirebilirsiniz bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] app.config yapılandırma dosyası aracılığıyla hizmet [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] gibi hizmet:  
  
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
  
 Tüm performans sayaçlarını etkinleştirmek istiyorsanız, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uygulamalar, yapılandırma ayarlarını Machine.config dosyasındaki yerleştirebilirsiniz.  Lütfen bakın **performans sayaçları için bellek boyutu artırmayı** bölümünde aşağıdaki performans sayaçları için yeterli bellek makinenizde yapılandırma hakkında daha fazla bilgi için.  
  
 Kullanırsanız [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] özel işlem invokers gibi genişletilebilirlik noktaları, ayrıca kendi performans sayaçlarını yayması. Genişletilebilirlik noktanız uygulamak, bunun nedeni, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] varsayılan yolda standart performans sayacı verilerini artık yayabilir. El ile performans sayacı desteği uygulamaz, beklediğiniz performans sayacı verilerini göremeyebilirsiniz.  
  
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
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]kullanır, performans sayacı kategorileri için paylaşılan bellek ayırın.  
  
 Varsayılan olarak, ayrı bir paylaşılan bellek bir üç aylık dönem için genel performans sayacı bellek boyutu ayarlanır. Varsayılan genel performans sayacı bellek 524.288 bayttır. Bu nedenle, üç [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performans sayacı kategorileri yaklaşık 128 KB her varsayılan boyutuna sahip. Çalışma zamanı özelliklerine bağlı olarak [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] uygulamaları bir makineye performans sayacı bellek tükendi. Bu gerçekleştiğinde, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir hata uygulama olay günlüğüne yazar. Bir performans sayacı yüklenmedi ve özel durum girdisini içeriyor hata içeriğini durumlarını "System.InvalidOperationException: özel sayaçlar dosya görünümdür, bellek yetersiz." Hata düzeyinde izleme etkinleştirilirse, bu hata Ayrıca izlenen. Performans sayacı bellek biterse, çalışmaya devam eder, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performans sayaçları etkinleştirilmiş uygulamalarla performans düşüşüne neden. Makinenin yöneticisiyseniz, herhangi bir anda var olabilen performans sayaçları en fazla sayısını desteklemek için yeterli bellek ayıramadı şekilde yapılandırmanız gerekir.  
  
 İçin performans sayacı bellek miktarını değiştirebilirsiniz [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] kayıt defterinde kategoriler. Bunu yapmak için adlı yeni bir DWORD değeri eklemeniz gerekir `FileMappingSize` için üç aşağıdaki konumlardan ve bayt istenilen değere ayarlayın. Böylece bu değişiklikleri yürürlüğe alınır makinenizi yeniden başlatın.  
  
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
 Böylece erişebilmeniz için birkaç dosyaları SDK yükleme klasöründe yüklü [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] performans sayaçları programlı olarak. Bu dosyalar aşağıda listelenmiştir.  
  
-   _ServiceModelEndpointPerfCounters.vrg  
  
-   _ServiceModelOperationPerfCounters.vrg  
  
-   _ServiceModelServicePerfCounters.vrg  
  
-   _SMSvcHostPerfCounters.vrg  
  
-   _TransactionBridgePerfCounters.vrg  
  
 Sayaçları programlı erişim hakkında daha fazla bilgi için bkz: [performans sayacı programlama mimarisi](http://go.microsoft.com/fwlink/?LinkId=95179).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Yönetim ve tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
