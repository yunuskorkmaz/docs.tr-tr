---
title: Analitik İzlemeyi Dinamik Olarak Etkinleştirme
ms.date: 03/30/2017
ms.assetid: 58b63cfc-307a-427d-b69d-9917ff9f44ac
ms.openlocfilehash: f03d2ce381be430121a11df95341886a4be667e2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43529525"
---
# <a name="dynamically-enabling-analytic-tracing"></a>Analitik İzlemeyi Dinamik Olarak Etkinleştirme
Windows işletim sistemiyle birlikte sevk araçlarını kullanarak etkinleştirebilir veya dinamik olarak olay izleme için Windows (ETW) kullanarak izlemeyi devre dışı. Tüm [!INCLUDE[netfx_current_long](../../../../../includes/netfx-current-long-md.md)] Windows Communication Foundation (WCF) Hizmetleri, çözümleme izleme uygulamanın Web.config dosyasında etkin ve devre dışı olmadan dinamik olarak değiştirme veya hizmeti yeniden başlatılıyor olabilir. Bu izleme olaylarının bozulmadan kalmasını yayan uygulama sağlar.  
  
 WCF izleme seçenekleri benzer şekilde yapılandırılabilir. Örneğin, önem derecesi düzeyden değiştirebilirsiniz **hata** için **bilgi** uygulama bozmadan olmadan. Bu yapılabilir aşağıdaki araçları kullanarak:  
  
-   **Logman** – yapılandırma, denetleme ve izleme verileri sorgulama için bir komut satırı aracı. Daha fazla bilgi için [Logman oluşturma izleme](https://go.microsoft.com/fwlink/?LinkId=165426) ve [Logman güncelleştirme izleme](https://go.microsoft.com/fwlink/?LinkId=165427).  
  
-   **Görüntüleyicide** -izleme sonuçlarını görüntülemek için Windows grafik yönetim aracıdır. Daha fazla bilgi için [WCF hizmetleri ve olay izleme için Windows](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) ve [Olay Görüntüleyicisi'ni](https://go.microsoft.com/fwlink/?LinkId=165428).  
  
-   **Perfmon** – performans sayaçları İzleyici izleme sayaçları ve izleme etkilerini kullanan bir Windows grafik yönetim aracıdır. Daha fazla bilgi için [bir veri toplayıcı kümesi el ile oluşturmanız](https://go.microsoft.com/fwlink/?LinkId=165429).  
  
### <a name="keywords"></a>Anahtar Sözcükler  
 Kullanırken <xref:System.ServiceModel.Activation.Configuration.ServiceModelActivationSectionGroup.Diagnostics%2A> sınıfı, .NET Framework izleme iletilerini genellikle önem derecesini (örneğin, hata, uyarı ve bilgi) tarafından filtrelenir. ETW, önem derecesi düzeyi kavramını destekler, ancak anahtar sözcüklerini kullanarak yeni ve esnek filtre mekanizması sunar. İzleme olayları olay ne anlama geldiği hakkında ek bağlam sağlamak olanak tanıyan rastgele metin değerleri anahtar sözcüklerdir.  
  
 WCF analiz izleme için her bir izleme olayı anahtar sözcükleri iki tür vardır. İlk olarak, her olay, bir veya daha fazla senaryo anahtar sözcük yok. Bu anahtar sözcükler senaryoları göstermek, bu olay desteklemek üzere tasarlanmıştır. Üç senaryo anahtar sözcükler, her aşağıdaki tabloda gösterildiği gibi belirli bir amaç için tasarlanmıştır. Anahtar sözcükler kullanılarak filtreleme, dinamik olarak WCF Hizmeti etkilemeden değiştirilebilir. Dinamik olarak geçerli izleme senaryonuza ve izleme bilgileri Topladığınızdan miktarını değiştirebilirsiniz, anlamına gelir. Örneğin, değiştirebileceğiniz `HealthMonitoring` için `Troubleshooting` ve olay izleme ayrıntı düzeyi artırın.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`HealthMonitoring`|Basit, minimum, izleme hizmetinizin etkinlikleri izlemenize olanak tanır.|  
|`EndToEndMonitoring`|İleti akışı izlemeyi desteklemek için kullanılan olayları.|  
|`Troubleshooting`|Daha ayrıntılı olay WCF genişletilebilirlik noktaları etrafında.|  
  
 İkinci grup anahtar sözcükler tanımlama hangi bileşeninin [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] olay yayılır.  
  
|Anahtar sözcüğü|Açıklama|  
|-------------|-----------------|  
|`UserEvents`|Kullanıcı kodu tarafından oluşturulan olayları ve [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)].|  
|`ServiceModel`|WCF çalışma zamanı tarafından oluşturulan olaylar.|  
|`ServiceHost`|Hizmet ana bilgisayarı tarafından oluşturulan olaylar.|  
|`WCFMessageLogging`|WCF ileti günlüğe kaydetme olayları.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [WCF Hizmetleri ve Windows için Olay İzleme](../../../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md)
