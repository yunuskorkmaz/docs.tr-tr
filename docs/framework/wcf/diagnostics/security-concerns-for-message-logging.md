---
title: İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: b635591b7a3b07385ed48c6b1ea556139c6d77c5
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044264"
---
# <a name="security-concerns-for-message-logging"></a>İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
Bu konu başlığı altında, gizli verilerin ileti günlüklerinde gösterilmesini ve ileti günlüğe kaydetme tarafından oluşturulan olayları nasıl koruyabileceğiniz açıklanmaktadır.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
  
### <a name="logging-sensitive-information"></a>Gizli bilgileri günlüğe kaydetme  
 Windows Communication Foundation (WCF), uygulamaya özgü üst bilgilerdeki ve gövdedeki hiçbir veriyi değiştirmez. WCF Ayrıca uygulamaya özgü üst bilgilerde veya gövde verilerinde kişisel bilgileri izlemez.  
  
 İleti günlüğe kaydetme etkin olduğunda, bir sorgu dizesi gibi uygulamaya özgü üst bilgilerde kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görünür hale gelebilir. Uygulama dağıtıcı, yapılandırma ve günlük dosyalarında erişim denetimini zormaktan sorumludur. Bu tür bilgilerin görünmesini istemiyorsanız, günlükleri paylaşmak istiyorsanız günlüğe kaydetmeyi devre dışı bırakmanız veya verilerin bir kısmını filtrelemeniz gerekir.  
  
 Aşağıdaki ipuçları, bir günlük dosyasının içeriğinin istenmeden gösterilmesini önlemeye yardımcı olabilir:  
  
- Günlük dosyalarının hem Web hem de Self-Host senaryolarında Access Control listeleriyle (ACL) korunduğundan emin olun.  
  
- Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin. Örneğin,. xml dosya uzantısı güvenli bir seçenek değildir. Sunulabilecek uzantıların bir listesini görmek için Internet Information Services (IIS) yönetim kılavuzunu kontrol edebilirsiniz.  
  
- Bir Web tarayıcısı kullanarak harici bir tarafın erişmesini engellemek için, günlük dosyası konumu için bir mutlak yol belirtin. Bu, Web Konağı vroot ortak dizininin dışında olmalıdır.  
  
 Varsayılan olarak, Kullanıcı adı ve parola gibi anahtarlar ve kişisel bilgiler (PII), izlemelerde ve günlüğe kaydedilen iletilerde günlüğe kaydedilmez. Ancak Makine Yöneticisi, makinede çalışan uygulamaların bilinen kişisel `enableLoggingKnownPII` olarak tanımlanabilen bilgileri `machineSettings` (PII) günlüğe almasına izin vermek için Machine. config dosyasının öğesindeki özniteliğini kullanabilir. Aşağıdaki yapılandırmada bunun nasıl yapılacağı gösterilmektedir:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Daha sonra bir uygulama dağıtıcı, bu `logKnownPii` özniteliği App. config veya Web. config dosyasında kullanarak PII günlüğünü aşağıdaki şekilde etkinleştirebilir:  
  
```xml  
<system.diagnostics>  
  <sources>  
      <source name="System.ServiceModel.MessageLogging"  
        logKnownPii="true">  
        <listeners>  
                 <add name="messages"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\logs\messages.svclog" />  
          </listeners>  
      </source>  
    </sources>  
</system.diagnostics>  
```  
  
 Yalnızca her iki ayar `true` de PII günlüğü etkin olduğunda. İki anahtar birleşimi, her bir uygulama için bilinen PII 'yi günlüğe kaydetme esnekliğini sağlar.  
  
> [!IMPORTANT]
> `true` Ve [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` bayrakları,`<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`aşağıdaki örnekte gösterildiği gibi, PII günlüğünü etkinleştirmek için Web. config dosyasında veya App. config dosyasında da olarak ayarlanmalıdır. `logKnownPii`  
  
 Bir yapılandırma dosyasında iki veya daha fazla özel kaynak belirtirseniz, yalnızca ilk kaynağın özniteliklerinin okunup okunduğuna dikkat edin. Diğerleri yok sayılır. Bu, aşağıdaki App. config, File, PII için her iki kaynak için de PII günlüğü, ikinci kaynak için açık olarak etkinleştirilmiş olsa da bu şekilde günlüğe kaydedilmez.  
  
```xml  
<system.diagnostics>  
   <sources>  
      <source name="System.ServiceModel.MessageLogging"  
              logKnownPii="false">  
              <listeners>  
                 <add name="messages"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\messages.svclog" />  
              </listeners>  
            </source>  
      <source name="System.ServiceModel"   
              logKnownPii="true">  
              <listeners>  
                 <add name="traces"  
                      type="System.Diagnostics.XmlWriterTraceListener"  
                      initializeData="c:\logs\traces.svclog" />  
              </listeners>  
      </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Öğesi Machine. config dosyasının dışında varsa, sistem bir <xref:System.Configuration.ConfigurationErrorsException>oluşturur. `<machineSettings enableLoggingKnownPii="Boolean"/>`  
  
 Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında geçerli olur. Her iki öznitelik olarak `true`ayarlandığında bir olay başlangıçta günlüğe kaydedilir. Bir `logKnownPii` olay, `true` olarak`enableLoggingKnownPii` ayarlanmışsagünlüğekaydedilir.`false`  
  
 Makine Yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır. PII günlüğü etkinse, güvenlik anahtarları ve PII günlüğe kaydedilir. Devre dışıysa, hassas ve uygulamaya özgü veriler hala ileti üstbilgilerinde ve gövdede günlüğe kaydedilir. Gizlilik ve PII 'nin gösterilmesini sağlama hakkında daha kapsamlı bir tartışma için bkz. [Kullanıcı gizliliği](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
> PII hatalı biçimlendirilmiş iletilerde gizli değil. Bu tür bir ileti, hiçbir değişiklik yapılmadan olduğu gibi kaydedilir. Daha önce bahsedilen özniteliklerin bunun üzerinde hiçbir etkisi yoktur.  
  
### <a name="custom-trace-listener"></a>Özel Izleme dinleyicisi  
 Ileti günlüğe kaydetme izleme kaynağına özel bir izleme dinleyicisi eklemek, yönetici ile kısıtlanması gereken bir ayrıcalıkdır. Bunun nedeni, kötü amaçlı özel dinleyicilerinin iletileri uzaktan göndermek üzere yapılandırılabilmektir. Bu, hassas bilgilerin açığa çıkmasına yol açar. Ayrıca, bir uzak veritabanına gibi, hatta ileti göndermek için özel bir dinleyici yapılandırırsanız, uzak makinedeki ileti günlüklerinde doğru erişim denetimini zorunlu kılabilirsiniz.  
  
## <a name="events-triggered-by-message-logging"></a>Ileti günlüğe kaydetme tarafından tetiklenen olaylar  
 İleti günlüğe kaydetme tarafından oluşturulan tüm olaylar aşağıda listelenmiştir.  
  
- İleti günlüğe kaydetme: Bu olay, yapılandırmada ileti günlüğe kaydetme etkinleştirildiğinde veya WMI aracılığıyla yayınlanır. Olay içeriği "Ileti günlüğe kaydetme açıldı. Hassas bilgiler, hatta ileti gövdeleri gibi, tel üzerinde şifrelenseler bile şifresiz metin olarak kaydedilebilir. "  
  
- İleti oturumu kapatma: Bu olay, ileti günlüğe kaydetme WMI aracılığıyla devre dışı bırakıldığında yayınlanır. Olayın içeriği "Ileti günlüğe kaydetme kapatıldı" dir.  
  
- Bilinen PII günlüğünü aç: Bu olay, bilinen PII günlüğü etkinken yayınlanır. Bu, Machine. `enableLoggingKnownPii` config dosyasının `machineSettings` öğesindeki özniteliği olarak `true`ayarlandığında ve App. config veya Web. config dosyasındaki `source` öğesinin `logKnownPii` özniteliği olarak `true`ayarlandığızamangerçekleşir.  
  
- Bilinen PII günlüğüne Izin verilmiyor: Bu olay, bilinen PII kaydına izin verilmediği zaman yayınlanır. `enableLoggingKnownPii` `source` `true`Bunun nedeni, App. config veya Web. config dosyasındaki öğesinin `machineSettings` özniteliğiolarakayarlanır,ancakMachine.configdosyasınınöğesindekiözniteliğiolarakayarlanır.`logKnownPii` `false`. Hiçbir özel durum oluşturulmaz.  
  
 Bu olaylar, Windows ile birlikte gelen Olay Görüntüleyicisi aracında görüntülenebilir. Bunun hakkında daha fazla bilgi için bkz. [olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
