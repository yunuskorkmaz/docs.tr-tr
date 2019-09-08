---
title: Analitik İzlemeyi Dinamik Olarak Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: bea64ac9a9312d17b7f47e72a46d876552e20a12
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798103"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Analitik İzlemeyi Dinamik Olarak Etkinleştirme
Windows işletim sistemiyle birlikte gelen araçları kullanarak izlemeyi Windows için olay Izleme (ETW) kullanarak dinamik olarak etkinleştirebilir veya devre dışı bırakabilirsiniz. Tüm [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] Windows Communication Foundation (WCF) hizmetlerinde analiz izleme, uygulamanın Web. config dosyasını değiştirmeden veya hizmeti yeniden başlatmadan dinamik olarak etkinleştirilebilir ve devre dışı bırakılabilir. Bu, izleme olaylarını gösteren uygulamanın olumsuz şekilde kalmasını sağlar.  
  
 WCF izleme seçenekleri benzer bir şekilde yapılandırılabilir. Örneğin, uygulamayı etkilemeden önem düzeyini **hata** durumundan **bilgi** olarak değiştirebilirsiniz. Bu, aşağıdaki araçlar kullanılarak yapılabilir:  
  
- **Logman** : izleme verileri yapılandırmak, denetlemek ve sorgulamak için bir komut satırı aracı. Daha fazla bilgi için bkz. [Logman create trace](https://go.microsoft.com/fwlink/?LinkId=165426) ve [Logman Update Trace](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
- **Eventviewer** -izlemenin sonuçlarını görüntülemek için Windows grafik yönetim aracı. Daha fazla bilgi için bkz. [Windows Için WCF Hizmetleri ve olay izleme](../../samples/wcf-services-and-event-tracing-for-windows.md) ve [Olay Görüntüleyicisi](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
- **Perfmon** – izleme sayaçlarını izlemek için sayaçları kullanan Windows grafik yönetim aracı ve performans üzerindeki izlemenin etkileri. Daha fazla bilgi için bkz. [veri toplayıcı kümesi oluşturma el ile](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>anahtar sözcükler  
 <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> Sınıfı kullanılırken, .NET Framework izleme iletileri genellikle önem düzeyine (örneğin, hata, uyarı ve bilgi) göre filtrelenir. ETW önem düzeyi kavramını destekler, ancak anahtar sözcükler kullanarak yeni ve esnek bir filtre mekanizması sunar. Anahtar sözcükler, izleme olaylarının, olayın anlamı hakkında ek bağlam sağlamasına izin veren rastgele metinsel değerlerdir.  
  
 WCF analitik izleme için, her izleme olayının iki tür anahtar sözcüğü vardır. İlk olarak, her olayda bir veya daha fazla senaryo anahtar sözcüğü vardır. Bu anahtar sözcükler, bu olayın desteklemeye yönelik senaryolar olduğunu gösterir. Her biri aşağıdaki tabloda gösterildiği gibi, belirli bir amaç için tasarlanan üç senaryo anahtar sözcüğü vardır. Anahtar sözcükleri kullanarak filtreleme, WCF hizmetini bozmadan dinamik olarak değiştirilebilir. Yani, geçerli izleme senaryonuzu ve topladığınız izleme bilgilerini dinamik olarak değiştirebileceðiniz anlamına gelir. Örneğin, öğesini değiştirebilir `HealthMonitoring` `Troubleshooting` ve olay ayrıntı düzeyini izlemeyi artırabilirsiniz.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`HealthMonitoring`|Hizmetinizin etkinliklerini izlemenize olanak tanıyan çok hafif ve en az izleme.|  
|`EndToEndMonitoring`|İleti akışı izlemeyi desteklemek için kullanılan olaylar.|  
|`Troubleshooting`|WCF genişletilebilirlik noktaları etrafında daha ayrıntılı olaylar.|  
  
 İkinci anahtar sözcük grubu, .NET Framework hangi bileşenin olayı yayındığını tanımlar.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`UserEvents`|.NET Framework değil, Kullanıcı kodu tarafından yayılan olaylar.|  
|`ServiceModel`|WCF çalışma zamanı tarafından yayılan olaylar.|  
|`ServiceHost`|Hizmet ana bilgisayarı tarafından yayılan olaylar.|  
|`WCFMessageLogging`|WCF ileti günlüğe kaydetme olayları.|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WCF Hizmetleri ve Windows için Olay İzleme](../../samples/wcf-services-and-event-tracing-for-windows.md)
