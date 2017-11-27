---
title: "İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21f513f2-815b-47f3-85a6-03c008510038
caps.latest.revision: "17"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 1f3d62e8b6771666dd3a55855ca0c5e41853f439
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-concerns-for-message-logging"></a>İleti Günlüğe Kaydetme ile İlgili Güvenlik Konuları
Bu konu, ileti günlüğe kaydetme tarafından oluşturulan olayları yanı sıra ileti günlüklerini de sağlanmaktadır hassas verilerinizi nasıl koruyabilirsiniz açıklar.  
  
## <a name="security-concerns"></a>Güvenlik sorunları  
  
### <a name="logging-sensitive-information"></a>Hassas bilgileri günlüğe kaydetme  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]uygulamaya özgü üstbilgi ve gövde herhangi bir veri değiştirmez. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Ayrıca uygulamaya özgü üstbilgileri veya gövde verileri kişisel bilgilerin izlemez.  
  
 İleti günlüğe kaydetme etkinleştirildiğinde, uygulamaya özgü üstbilgiler, sorgu dize gibi kişisel bilgilerinizi; ve kredi kartı numarası gibi bilgileri gövde, günlüklerde görünür hale gelebilir. Erişim denetimini yapılandırma ve günlük dosyaları uygulama için uygulama dağıtıcı sorumludur. Bu tür bilgilerin görünür olmasını istemiyorsanız günlüğü devre dışı bırakın veya günlükleri paylaşmak istiyorsanız verilerin bir kısmını filtre gerekir.  
  
 Aşağıdaki ipuçları bir günlük dosyasının içeriğinin istenmeden açıklanmasını engellemek yardımcı olabilir:  
  
-   Tarafından erişim denetim listeleri (ACL) hem de Web ana bilgisayarı ve kendi kendini barındıran senaryoları korunan dosyaları günlük emin olun.  
  
-   Web isteği kullanarak kolayca sunulamıyor bir dosya uzantısı seçin. Örneğin, .xml dosya uzantısı güvenli bir seçenek değil. Sunulabilecek uzantıların listesini görmek için Internet Information Services (IIS) yönetim kılavuzuna bakabilirsiniz.  
  
-   Bir Web tarayıcısı kullanılarak harici bir tarafça erişilmesini önlemek üzere Web ana bilgisayar vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, anahtarları ve kullanıcı adı ve parola gibi kişisel bilgileri (PII) içindeki oturum açmadığı ve iletileri günlüğe. Bir Makine Yöneticisi, ancak kullanabilirsiniz `enableLoggingKnownPII` özniteliğini `machineSettings` makinede çalışan uygulamaların bilinen kişisel bilgileri (PII) oturum izin vermek için Machine.config dosyasının öğesi. Aşağıdaki yapılandırma bunun nasıl yapılacağı gösterilmektedir:  
  
```xml  
<configuration>  
   <system.serviceModel>  
      <machineSettings enableLoggingKnownPii="true"/>  
   </system.serviceModel>  
</configuration>   
```  
  
 Bir uygulama dağıtıcı sonra kullanabileceğiniz `logKnownPii` özniteliği PII gibi günlüğe kaydetmeyi etkinleştirmek için App.config veya Web.config dosyasında:  
  
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
  
 Yalnızca her iki ayarın olduğunda `true` PII günlük kaydı etkin. İki anahtar birleşimi her uygulama için bilinen PII oturum esnekliği sağlar.  
  
> [!IMPORTANT]
>  İçinde [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] `logEntireMessage` ve `logKnownPii` bayrakları da ayarlanmalıdır `true` olarak Web.config dosyasını veya PII günlük kaydını etkinleştirmek için App.config dosyasında, aşağıdaki örnekte Göster `<system.serviceModel><messageLogging logEntireMessage="true" logKnownPii="true" …`.  
  
 İki veya daha fazla özel kaynağı bir yapılandırma dosyası belirtirseniz, yalnızca ilk kaynak özniteliklerini okuma bilmeniz gerekir. Diğerleri yoksayılır. Bu, PII günlüğü açıkça ikinci kaynağı için etkin olsa bile aşağıdaki App.config için dosya, PII hem kaynakları için günlüğe kaydedilmez, anlamına gelir.  
  
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
  
 Varsa `<machineSettings enableLoggingKnownPii="Boolean"/>` öğesi dışında Machine.config dosyasının var, sistem oluşturur bir <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Uygulama başlatıldığında veya yeniden başlatır değişiklikler etkili olur. Her iki öznitelik ayarlandığında bir olay başlangıçta kaydedilir `true`. Bir olay, ayrıca kaydedilir `logKnownPii` ayarlanır `true` ancak `enableLoggingKnownPii` olan `false`.  
  
 Makine Yöneticisi ve bu iki anahtar kullanıldığında, uygulama dağıtıcı son derece dikkatli olun çalışma. PII günlüğe kaydetme işlemi etkinleştirilmişse, güvenlik anahtarlarını ve PII günlüğe kaydedilir. Devre dışı ise, hala ileti üstbilgilerini ve gövdeleri hassas ve uygulamaya özgü veriler günlüğe kaydedilir. Gizlilik ve maruz kalma PII koruma hakkında daha kapsamlı bir açıklama için bkz: [kullanıcı gizliliği](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
> [!CAUTION]
>  PII hatalı biçimlendirilmiş iletilerinde gizli değildir. Olarak oturum gibi messaged-herhangi bir değişiklik yapılmadan olduğu. Belirtilen öznitelikler, daha önce bu üzerinde etkisi yoktur.  
  
### <a name="custom-trace-listener"></a>Özel İzleme dinleyicisi  
 Özel İzleme dinleyicisi ileti oturum açma ekleme izleme yöneticinin kısıtlanmış bir ayrıcalık kaynağıdır. Kötü amaçlı özel dinleyicileri uzaktan iletileri göndermek için yapılandırılmış olmasıdır hassas bilgilerin gösterilmesine yol açar. Ayrıca, kablo, iletileri gibi uzak bir veritabanına göndermek için özel bir dinleyici yapılandırırsanız, uzak makinede ileti günlüklerini uygun erişim denetimini uygulamalıdır.  
  
## <a name="events-triggered-by-message-logging"></a>İleti günlüğe kaydetme tarafından tetiklenen olayları  
 İleti günlüğe kaydetme tarafından gösterilen tüm olayları listeler.  
  
-   İleti oturum açma: yapılandırmasında veya WMI üzerinden ileti günlüğe kaydetme etkinleştirildiğinde, bu olay yayınlanır. Olay içeriği olan "ileti günlüğü açıldı. Kablo, örneğin, İleti gövdeleri şifrelenmiş olsa bile hassas bilgiler düz metin olarak kaydedilebilir."  
  
-   İleti günlüğü devre dışı: WMI üzerinden ileti günlüğe kaydetme devre dışı bırakıldığında bu olay yayınlanır. Olay içeriği olan "iletisi günlüğünü devre dışı."  
  
-   Günlük PII üzerinde bilinen: bilinen PII günlüğü etkinleştirildiğinde, bu olay yayınlanır. Böyle olduğunda `enableLoggingKnownPii` özniteliğini `machineSettings` Machine.config dosyasının öğesinin ayarlanmış `true`ve `logKnownPii` özniteliği `source` öğesi App.config veya Web.config dosyasında içinayarlanmış`true`.  
  
-   Bilinen oturum PII izin verilmiyor: Bu olay günlüğü bilinen PII izin verilmediğinde yayınlanır. Böyle olduğunda `logKnownPii` özniteliği `source` App.config veya Web.config dosyasında ayarlanır `true`, ancak `enableLoggingKnownPii` özniteliğini `machineSettings` Machine.config dosyasının öğesinin içinayarlanmış`false`. Hiçbir özel durum oluşur.  
  
 Bu olaylar, Windows ile birlikte gelen Olay Görüntüleyicisi'ni aracında görüntülenebilir. Bunun hakkında daha fazla bilgi için bkz: [olay günlüğü](../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İleti günlüğe kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Güvenlikle ilgili noktalar ve izleme için yararlı ipuçları](../../../../docs/framework/wcf/diagnostics/tracing/security-concerns-and-useful-tips-for-tracing.md)
