---
title: İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: 679975be44244f10232b805a6cc2776b48ed6058
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/14/2020
ms.locfileid: "75935763"
---
# <a name="security-concerns-for-message-logging"></a>İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
Bu konu başlığı altında, gizli verilerin ileti günlüklerinde gösterilmesini ve ileti günlüğe kaydetme tarafından oluşturulan olayları nasıl koruyabileceğiniz açıklanmaktadır.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
  
### <a name="logging-sensitive-information"></a>Gizli bilgileri günlüğe kaydetme  
 Windows Communication Foundation (WCF), uygulamaya özgü üst bilgilerdeki ve gövdedeki hiçbir veriyi değiştirmez. WCF Ayrıca uygulamaya özgü üst bilgilerde veya gövde verilerinde kişisel bilgileri izlemez.  
  
 İleti günlüğe kaydetme etkin olduğunda, bir sorgu dizesi gibi uygulamaya özgü üst bilgilerde kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görünür hale gelebilir. Uygulama dağıtıcı, yapılandırma ve günlük dosyalarında erişim denetimini zormaktan sorumludur. Bu tür bilgilerin görünmesini istemiyorsanız, günlükleri paylaşmak istiyorsanız günlüğe kaydetmeyi devre dışı bırakmanız veya verilerin bir kısmını filtrelemeniz gerekir.  
  
 Aşağıdaki ipuçları, bir günlük dosyasının içeriğinin istenmeden gösterilmesini önlemeye yardımcı olabilir:  
  
- Günlük dosyalarının hem Web hem de Self-Host senaryolarında Access Control listeleriyle (ACL) korunduğundan emin olun.  
  
- Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin. Örneğin,. xml dosya uzantısı güvenli bir seçenek değildir. Sunulabilecek uzantıların listesini görmek için Internet Information Services (IIS) yönetim kılavuzuna bakabilirsiniz.  
  
- Bir Web tarayıcısı kullanarak harici bir tarafın erişmesini engellemek için, günlük dosyası konumu için bir mutlak yol belirtin. Bu, Web Konağı vroot ortak dizininin dışında olmalıdır.  
  
 Varsayılan olarak, Kullanıcı adı ve parola gibi anahtarlar ve kişisel bilgiler (PII), izlemelerde ve günlüğe kaydedilen iletilerde günlüğe kaydedilmez. Ancak Makine Yöneticisi, makinede çalışan uygulamaların bilinen kişisel olarak tanımlanabilen bilgileri (PII) günlüğe almasına izin vermek için Machine. config dosyasının `machineSettings` öğesindeki `enableLoggingKnownPII` özniteliğini kullanabilir. Aşağıdaki yapılandırmada bunun nasıl yapılacağı gösterilmektedir:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Daha sonra bir uygulama dağıtıcısı, PII günlüğünü etkinleştirmek için App. config veya Web. config dosyasında `logKnownPii` özniteliğini aşağıdaki şekilde kullanabilir:  
  
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
  
 Yalnızca her iki ayar de PII günlüğü etkin `true`. İki anahtar birleşimi, her bir uygulama için bilinen PII 'yi günlüğe kaydetme esnekliğini sağlar.  
  
> [!IMPORTANT]
> [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` ve `logKnownPii` bayrakları, aşağıdaki `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`örnekte gösterildiği gibi, PII günlüğünü etkinleştirmek için Web. config dosyasında veya App. config dosyasında da `true` olarak ayarlanmalıdır.  
  
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
  
 `<machineSettings enableLoggingKnownPii="Boolean"/>` öğesi Machine. config dosyasının dışında varsa, sistem bir <xref:System.Configuration.ConfigurationErrorsException>oluşturur.  
  
 Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında geçerli olur. Her iki öznitelik de `true`olarak ayarlandığında, bir olay başlangıçta günlüğe kaydedilir. `logKnownPii`, `true` olarak ayarlanırsa `enableLoggingKnownPii` `false`bir olay da günlüğe kaydedilir.  
  
 Makine Yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır. PII günlüğü etkinse, güvenlik anahtarları ve PII günlüğe kaydedilir. Devre dışıysa, hassas ve uygulamaya özgü veriler hala ileti üstbilgilerinde ve gövdede günlüğe kaydedilir. Gizlilik ve PII 'nin gösterilmesini sağlama hakkında daha kapsamlı bir tartışma için bkz. [Kullanıcı gizliliği](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
> [!CAUTION]
> PII hatalı biçimlendirilmiş iletilerde gizli değil. Bu tür bir ileti, hiçbir değişiklik yapılmadan olduğu gibi kaydedilir. Daha önce bahsedilen özniteliklerin bunun üzerinde hiçbir etkisi yoktur.  
  
### <a name="custom-trace-listener"></a>Özel Izleme dinleyicisi  
 Ileti günlüğe kaydetme izleme kaynağına özel bir izleme dinleyicisi eklemek, yönetici ile kısıtlanması gereken bir ayrıcalıkdır. Bunun nedeni, kötü amaçlı özel dinleyicilerinin iletileri uzaktan göndermek üzere yapılandırılabilmektir. Bu, hassas bilgilerin açığa çıkmasına yol açar. Ayrıca, bir uzak veritabanına gibi, hatta ileti göndermek için özel bir dinleyici yapılandırırsanız, uzak makinedeki ileti günlüklerinde doğru erişim denetimini zorunlu kılabilirsiniz.  
  
## <a name="events-triggered-by-message-logging"></a>Ileti günlüğe kaydetme tarafından tetiklenen olaylar  
 İleti günlüğe kaydetme tarafından oluşturulan tüm olaylar aşağıda listelenmiştir.  
  
- İleti günlüğe kaydetme: Bu olay, yapılandırmada ileti günlüğe kaydetme etkin olduğunda veya WMI üzerinden yayınlanır. Olay içeriği "Ileti günlüğe kaydetme açıldı. Hassas bilgiler, hatta ileti gövdeleri gibi, tel üzerinde şifrelenseler bile şifresiz metin olarak kaydedilebilir. "  
  
- İleti oturumu kapatma: Bu olay, ileti günlüğü WMI aracılığıyla devre dışı bırakıldığında yayınlanır. Olayın içeriği "Ileti günlüğe kaydetme kapatıldı" dir.  
  
- Bilinen PII 'Yi günlüğe kaydet: Bu olay, bilinen PII günlüğü etkinken yayınlanır. Bu, Machine. config dosyasının `machineSettings` öğesindeki `enableLoggingKnownPii` özniteliği `true`olarak ayarlandığında ve App. config veya Web. config dosyasındaki `source` öğesinin `logKnownPii` özniteliği `true`olarak ayarlandığında gerçekleşir.  
  
- Bilinen PII günlüğüne Izin verilmiyor: Bu olay, bilinen PII kaydına izin verilmediği zaman yayınlanır. Bu durum, App. config veya Web. config dosyasındaki `source` öğesinin `logKnownPii` özniteliği `true`olarak ayarlandığında gerçekleşir ancak Machine. config dosyasının `machineSettings` öğesindeki `enableLoggingKnownPii` özniteliği `false`olarak ayarlanır. Özel durum oluşturulmaz.  
  
 Bu olaylar, Windows ile birlikte gelen Olay Görüntüleyicisi aracında görüntülenebilir. Bunun hakkında daha fazla bilgi için bkz. [olay günlüğü](./event-logging/index.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Günlüğe İleti Kaydetme](message-logging.md)
- [İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları](./tracing/security-concerns-and-useful-tips-for-tracing.md)
