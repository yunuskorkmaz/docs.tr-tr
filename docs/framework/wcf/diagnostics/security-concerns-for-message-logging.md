---
title: İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: bb1a6ab84ceba27b398d397b4407a55aa02c4cae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185769"
---
# <a name="security-concerns-for-message-logging"></a>İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
Bu konu, hassas verilerin ileti günlüklerinde açığa çıkarılmasını nasıl koruyabileceğinizi ve ileti günlüğe kaydetmenin oluşturduğu olayları açıklar.  
  
## <a name="security-concerns"></a>Güvenlik Endişeleri  
  
### <a name="logging-sensitive-information"></a>Hassas Bilgileri Günlüğe Kaydetme  
 Windows Communication Foundation (WCF), uygulamaya özgü üstbilgiler ve gövdedeki verileri değiştirmez. WCF ayrıca uygulamaya özel üstbilgilerdeki veya gövde verilerindeki kişisel bilgileri izlemez.  
  
 İleti günlüğe kaydetme etkinleştirildiğinde, sorgu dizesi gibi uygulamaya özgü üstbilgilerdeki kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görülebilir. Uygulama dağıtıcı, yapılandırma ve günlük dosyaları üzerinde erişim denetimini zorlamakiçin sorumludur. Bu tür bilgilerin görünür olmasını istemiyorsanız, günlükleri paylaşmak istiyorsanız günlüğe kaydetmeyi devre dışı kesmeniz veya verilerin bir kısmını filtrelemeniz gerekir.  
  
 Aşağıdaki ipuçları, günlük dosyasının içeriğinin istemeden açığa çıkarOlmasını önlemenize yardımcı olabilir:  
  
- Günlük dosyalarının hem Web barındırma hem de kendi barındırma senaryolarında Erişim Denetim Listeleri (ACL) tarafından korunduğundan emin olun.  
  
- Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin. Örneğin, .xml dosya uzantısı güvenli bir seçim değildir. Sunulabilecek uzantıların listesini görmek için Internet Information Services (IIS) yönetim kılavuzuna bakabilirsiniz.  
  
- Bir Web tarayıcısı kullanarak harici bir taraf tarafından erişmesini önlemek için Web ana bilgisayar vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, kullanıcı adı ve parola gibi anahtarlar ve kişisel olarak tanımlanabilir bilgiler (PII) izlemelerde ve günlüğe kaydedilmiş iletilerde günlüğe kaydedilmez. Ancak bir makine yöneticisi, `enableLoggingKnownPII` Machine.config `machineSettings` dosyasının öğesindeki özniteliği, bilinen kişisel olarak tanımlanabilir bilgileri (PII) günlüğe kaydetmek için makinede çalışan uygulamalara izin vermek için kullanabilir. Aşağıdaki yapılandırma bunu nasıl yapacağız gösterir:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>
```  
  
 Bir uygulama dağıtıcısı `logKnownPii` daha sonra aşağıdaki gibi KIŞISEL günlüğe kaydetmeyi etkinleştirmek için App.config veya Web.config dosyasındaki özniteliği kullanabilir:  
  
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
  
 Yalnızca her iki `true` ayar da KIŞISEL olarak günlüğe kaydetme etkin olduğunda. İki anahtarın birleşimi, her uygulama için bilinen KIŞISEL Bilgiler'i günlüğe kaydetme esnekliğisağlar.  
  
> [!IMPORTANT]
> `logEntireMessage` Ve [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logKnownPii` bayraklar da Web.config `true` dosyasında veya App.config dosyasında pii günlüğe etkinleştirmek için `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`ayarlanmalıdır, aşağıdaki örnekte gösterdiği gibi .  
  
 Bir yapılandırma dosyasında iki veya daha fazla özel kaynak belirtirseniz, yalnızca ilk kaynağın özniteliklerinin okunduğunu unutmayın. Diğerleri yok sayılır. Bu, aşağıdaki App.config, dosya için, kişisel bilgiler ikinci kaynak için açıkça etkin olsa bile, her iki kaynak için de günlüğe kaydedilmez anlamına gelir.  
  
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
  
 `<machineSettings enableLoggingKnownPii="Boolean"/>` Öğe Machine.config dosyasının dışında varsa, sistem <xref:System.Configuration.ConfigurationErrorsException>bir .  
  
 Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında etkili dir. Her iki öznitelik de `true`'' de ayarlandığında, bir olay başlangıçta günlüğe kaydedilir. Bir olay, ayarlanmış `logKnownPii` `true` ancak `enableLoggingKnownPii` . `false`  
  
 Makine yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır. Kişisel günlük etkinse, güvenlik anahtarları ve KIŞISEL bilgiler günlüğe kaydedilir. Devre dışı bırakılmışsa, duyarlı ve uygulamaya özgü veriler ileti üstbilgileri ve gövdelerinde günlüğe kaydedilir. Gizlilik hakkında daha ayrıntılı bir tartışma ve kişisel bilgilerin açığa çıkarılmaktan korunması için [Bkz. Kullanıcı Gizliliği.](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10))  
  
> [!CAUTION]
> Kişisel bilgiler yanlış biçimlendirilmiş iletilerde gizli değildir. Bu tür iletiler herhangi bir değişiklik yapılmadan olduğu gibi günlüğe kaydedilir. Daha önce bahsedilen özniteliklerin bu konuda hiçbir etkisi yoktur.  
  
### <a name="custom-trace-listener"></a>Özel İzleme Dinleyicisi  
 İleti Günlüğü izleme kaynağına özel bir izleme dinleyicisi eklemek, yöneticiyle sınırlandırılması gereken bir ayrıcalıktır. Bunun nedeni, kötü amaçlı özel dinleyicilerin iletileri uzaktan gönderecek şekilde yapılandırılabiliyor ve bu da hassas bilgilerin açığa çıkmasına yol açabiliyor. Ayrıca, kabloya ileti gönderecek özel bir dinleyiciyi (örneğin, uzak bir veritabanına) yapılandırıyorsanız, uzak makinedeki ileti günlükleri üzerinde uygun erişim denetimini zorlamanız gerekir.  
  
## <a name="events-triggered-by-message-logging"></a>İleti Günlüğe Kaydetmenin Tetiklediği Olaylar  
 Aşağıda, ileti günlüğe kaydetme nin yaydığı tüm olaylar listelenir.  
  
- İleti oturumu açma: İleti günlüğe kaydetme yapılandırmada veya WMI aracılığıyla etkinleştirildiğinde bu olay yayımlanır. Etkinliğin içeriği "İleti günlüğe kaydetme açık. Hassas bilgiler, örneğin ileti gövdeleri gibi, telüzerinde şifrelenmiş olsalar bile, açık metin olarak günlüğe kaydedilebilir."  
  
- İleti oturumu kapatma: İleti günlüğe kaydetme WMI üzerinden devre dışı bırakıldığında bu olay yayımlanır. Etkinliğin içeriği "İleti günlüğe kaydetme kapatıldı."  
  
- Günlük Bilinen Kişisel Bilgiler: Bilinen KIŞISEL'lerin günlüğe kaydedilmesi etkinleştirildiğinde bu olay yayılır. `enableLoggingKnownPii` Bu, Machine.config `machineSettings` dosyasının öğesindeki öznitelik ayarlandığında `true`ve `logKnownPii` App.config `source` veya Web.config dosyasındaki öğenin özniteliği `true`.  
  
- Günlük Bilinen Kişisel Bilgiler'e Izin Verilmez: Bilinen KIŞISEL'in günlüğe kaydedilmesine izin verilmediğinde bu olay yayımlanır. Bu, App.config `source` veya Web.config dosyasındaki öğenin `true`özniteliği ayarlandığında `enableLoggingKnownPii` `machineSettings` `false` `logKnownPii` olur, ancak Machine.config dosyasının öğesindeki öznitelik . Özel durum oluşturulmaz.  
  
 Bu olaylar, Windows ile birlikte gelen Olay Görüntüleyici aracında görüntülenebilir. Bu konuda daha fazla bilgi için [Olay Günlüğü'ne](./event-logging/index.md)bakın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Günlüğe İleti Kaydetme](message-logging.md)
- [İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları](./tracing/security-concerns-and-useful-tips-for-tracing.md)
