---
title: İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
ms.date: 03/30/2017
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
ms.openlocfilehash: 5ed2529d82c3994a245d2132909cd1e88b6ed62d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188813"
---
# <a name="security-concerns-for-message-logging"></a>İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
Bu konu, ileti günlüğe kaydetmeyi tarafından oluşturulan olayları yanı sıra ileti günlüklerini sunulan hassas verilerinizi nasıl koruyabilirsiniz açıklar.  
  
## <a name="security-concerns"></a>Güvenlik konuları  
  
### <a name="logging-sensitive-information"></a>Hassas bilgi günlük kaydı  
 Windows Communication Foundation (WCF) uygulamaya özgü üstbilgi ve gövde herhangi bir veri değiştirmez. WCF uygulamaya özgü üstbilgi ve gövde verilerini kişisel bilgileri de izlemez.  
  
 İleti günlüğe kaydetme etkinleştirildiğinde, uygulamaya özgü üstbilgiler, sorgu dizesi gibi kişisel bilgileri; ve kredi kartı numarası gibi bilgileri gövde, günlüklerde görünür hale gelebilir. Uygulama dağıtıcısı, erişim denetimi yapılandırması ve günlük dosyaları uygulamaktan sorumludur. Bu tür bilgilerin görünür olmasını istemiyorsanız günlüğünü devre dışı veya verilerin bir kısmını günlüklerini paylaşmak istiyorsanız filtre gerekir.  
  
 Aşağıdaki ipuçları bir günlük dosyasının içeriği istenmeden açıklanmasını önlemenize yardımcı olabilir:  
  
-   Günlük dosyaları tarafından erişim denetim listeleri (ACL) hem de Web ana bilgisayarı ve barındırma senaryoları korunan emin olun.  
  
-   Bir Web isteği sunularak kolayca sunulamayan bir dosya uzantısı'nı seçin. Örneğin, .xml dosya uzantısı güvenli bir seçenek değil. Sunulabilecek uzantıların listesini görmek için Internet Information Services (IIS) yönetim kılavuzuna bakabilirsiniz.  
  
-   Bir Web tarayıcısı kullanılarak harici bir tarafça erişilmesini önlemek üzere Web ana bilgisayar vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, anahtarları ve kullanıcı adı ve parola gibi kişisel bilgileri (PII) izlemeleri günlüğe kaydedilmez ve iletileri günlüğe. Bir makine yöneticisinin ancak kullanabilirsiniz `enableLoggingKnownPII` özniteliğini `machineSettings` Machine.config dosyasının makine üzerinde çalışan uygulamalar, bilinen kişisel olarak tanımlanabilen bilgileri (PII) için izin vermek için öğesi. Aşağıdaki yapılandırma, bunun nasıl yapılacağı gösterilmektedir:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Bir uygulama dağıtıcı ardından kullanabilirsiniz `logKnownPii` PII gibi günlüğe kaydetmeyi etkinleştirmek için App.config veya Web.config dosyasında özniteliği:  
  
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
  
 Yalnızca her iki ayarın olduğunda `true` PII ünlüğe kaydetme etkin olduğunu. İki anahtar bileşimi, her uygulama için bilinen PII oturum esnekliği sağlar.  
  
> [!IMPORTANT]
>  İçinde [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` ve `logKnownPii` bayrakları da ayarlanmalıdır `true` olarak Web.config dosyasını veya PII günlüğe kaydetmeyi etkinleştirmek için App.config dosyasında, aşağıdaki örnekte Göster `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 Bir yapılandırma dosyasında iki veya daha fazla özel kaynağı belirtirseniz, yalnızca ilk kaynak özniteliklerini okunduğu bilmeniz gerekir. Diğerlerine göz ardı edilir. Bu, PII günlük açıkça ikinci kaynağı için etkinleştirilmiş olsa da aşağıdaki App.config için dosya, PII hem kaynakları için günlüğe kaydedilmez, anlamına gelir.  
  
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
  
 Varsa `<machineSettings enableLoggingKnownPii="Boolean"/>` öğesi Machine.config dosyasının dışında var, sistem oluşturur bir <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Uygulama başlatıldığında veya yeniden değişiklikleri etkili olur. Her iki öznitelik ayarlandığında başlangıçta bir olay kaydedilir `true`. Bir olay, ayrıca kaydedilir `logKnownPii` ayarlanır `true` ancak `enableLoggingKnownPii` olduğu `false`.  
  
 Makine Yöneticisi ve uygulama dağıtıcı aşırı bu iki anahtar kullanırken dikkatli. PII günlüğe kaydetme etkinleştirilmişse, güvenlik anahtarları ve PII günlüğe kaydedilir. Etkinleştirilirse, hala ileti üstbilgileri ve gövdeleri hassas ve uygulamaya özgü veriler günlüğe kaydedilir. Gizlilik ve açıklanmasını PII koruma hakkında daha kapsamlı bir tartışma için bkz [kullanıcı gizliliğini](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  PII hatalı biçimlendirilmiş iletiler gizli değildir. Olarak oturum gibi messaged-herhangi bir değişikliği. Belirtilen öznitelikleri, daha önce bu üzerinde etkisi yoktur.  
  
### <a name="custom-trace-listener"></a>Özel İzleme dinleyicisi  
 İleti günlüğünü özel İzleme dinleyicisi ekleme izleme yöneticinin sınırlı bir ayrıcalık kaynağıdır. Kötü amaçlı özel dinleyicileri uzaktan ileti göndermek için yapılandırılabilir olmasıdır hassas bilgilerin açığa çıkmasına yol açar. Ayrıca, kablo, iletileri gibi uzak bir veritabanına göndermek için özel bir dinleyici yapılandırırsanız ileti günlüklerini uzak makinede uygun erişim denetimini uygulamalıdır.  
  
## <a name="events-triggered-by-message-logging"></a>Günlüğe ileti kaydetme tarafından tetiklenen olayları  
 Günlüğe ileti kaydetme tarafından yayılan tüm olayları listeler.  
  
-   Oturum açma'iletisi: Bu olay günlüğe ileti kaydetme yapılandırmasında veya WMI üzerinden etkinleştirildiğinde yayılır. "İleti günlüğü açıldı. olayın içeriktir Şifrelenmeden kablo, örneğin, İleti gövdeleri bile hassas bilgileri düz metin olarak kaydedilebilir."  
  
-   İleti günlüğü devre dışı: Bu olay günlüğe ileti kaydetme WMI aracılığıyla devre dışı bırakıldığında yayılır. Olay içeriği "ileti günlüğe kaydetme devre dışı." olur.  
  
-   Günlük PII üzerinde bilinen: Bu olay günlüğe kaydedilmesini bilinen PII etkinleştirildiğinde yayılır. Böyle olduğunda `enableLoggingKnownPii` özniteliğini `machineSettings` Machine.config dosyasının öğesinin ayarlanmış `true`ve `logKnownPii` özniteliği `source` App.config veya Web.config dosyasında öğe içinayarlanmış`true`.  
  
-   Bilinen oturum PII izin verilmiyor: Bu olay günlüğe kaydedilmesini bilinen PII izin verilmediğinde yayılır. Böyle olduğunda `logKnownPii` özniteliği `source` App.config veya Web.config dosyasında ayarlanır `true`, ancak `enableLoggingKnownPii` özniteliğini `machineSettings` Machine.config dosyasının öğesi içinayarlanmış`false`. Hiçbir özel durum oluşturulur.  
  
 Bu olaylar, Windows ile birlikte gelen Olay Görüntüleyicisi'ni Aracı'nda görüntülenebilir. Bunun hakkında daha fazla bilgi için bkz. [olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
