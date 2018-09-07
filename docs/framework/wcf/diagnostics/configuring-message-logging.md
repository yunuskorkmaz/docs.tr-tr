---
title: İleti Günlüğe Kaydetmeyi Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 80d852dd08e935d4c06e9b6d2e52b0a075849ef5
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085162"
---
# <a name="configuring-message-logging"></a>İleti Günlüğe Kaydetmeyi Yapılandırma
Bu konu, ileti günlüğe kaydetmeyi farklı senaryolar için nasıl yapılandırılacağını açıklar.  
  
## <a name="enabling-message-logging"></a>İleti günlüğe kaydetmeyi etkinleştirme  
 Windows Communication Foundation (WCF) iletilerini varsayılan olarak günlüğe kaydetmez. İleti günlüğe kaydetmeyi etkinleştirmek için bir izleme dinleyicisi için ekleme `System.ServiceModel.MessageLogging` kaynak izlemek ve ayarlamak için öznitelikler `<messagelogging>` yapılandırma dosyasındaki öğesi.  
  
 Aşağıdaki örnek, günlüğü etkinleştirmek ve ek seçenekleri belirlemek gösterilmektedir.  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel.MessageLogging">  
      <listeners>  
         <add name="messages"  
              type="System.Diagnostics.XmlWriterTraceListener"  
              initializeData="c:\logs\messages.svclog" />  
        </listeners>  
    </source>  
  </sources>  
</system.diagnostics>  
  
<system.serviceModel>  
  <diagnostics>  
    <messageLogging   
         logEntireMessage="true"   
         logMalformedMessages="false"  
         logMessagesAtServiceLevel="true"   
         logMessagesAtTransportLevel="false"  
         maxMessagesToLog="3000"  
         maxSizeOfMessageToLog="2000"/>  
  </diagnostics>  
</system.serviceModel>  
```  
  
 İleti günlüğe kaydetme ayarları hakkında daha fazla bilgi için bkz: [izleme ve ileti günlüğe kaydetme için önerilen ayarlar](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Kullanabileceğiniz `add` adını ve kullanmak istediğiniz dinleyicisi türünü belirtmek için. Örnek yapılandırma, dinleyici "ileti" adlı ve standart .NET Framework İzleme dinleyicisi ekler (`System.Diagnostics.XmlWriterTraceListener`) olarak kullanılacak türü. Kullanırsanız `System.Diagnostics.XmlWriterTraceListener`, yapılandırma dosyasında çıktı dosyasının konumunu ve adını belirtmeniz gerekir. Bu ayarı gerçekleştirilir `initializeData` günlük dosyasının adı. Aksi takdirde, sistemin bir özel durum oluşturur. Ayrıca, bir varsayılan dosya günlükleri yayan özel bir dinleyici uygulayabilirsiniz.  
  
> [!NOTE]
>  Günlüğe ileti kaydetme disk alanı eriştiğinden, belirli bir hizmet için diske yazılan iletilerin sayısını sınırlamanız gerekir. İleti sınırına ulaşıldığında, bilgi düzeyinde bir izleme oluşturulur ve tüm ileti günlüğe kaydetme etkinliklerini durdurun.  
  
 Ek seçenekler yanı sıra, günlüğe kaydetme düzeyi günlük düzeyi ve Seçenekleri bölümünde ele alınmıştır.  
  
 `switchValue` Özniteliği bir `source` yalnızca izleme için geçerlidir. Belirtirseniz bir `switchValue` özniteliğini `System.ServiceModel.MessageLogging` izleme kaynağı olarak izler, hiçbir etkisi olmaz.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 İzleme kaynağı devre dışı bırakmak isterseniz, kullanması gereken `logMessagesAtServiceLevel`, `logMalformedMessages`, ve `logMessagesAtTransportLevel` özniteliklerini `messageLogging` öğe yerine. Bu öznitelikler ayarlayın `false`. Bu, önceki kod örneğinde, yapılandırma dosyası kullanarak yapılandırma Düzenleyicisi kullanıcı Arabirimi arabirimi aracılığıyla veya WMI kullanılarak yapılabilir. Yapılandırma Düzenleyicisi araç hakkında daha fazla bilgi için bkz: [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). WMI hakkında daha fazla bilgi için bkz. [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Günlüğe kaydetme düzeylerini ve seçenekleri  
 Gelen iletiler için günlük hemen ileti hizmet düzeyi kullanıcı kodu alır. önce hemen ileti, biçimlendirilmiş sonra ve yanlış biçimlendirilmiş iletiler algılandığında gerçekleşir.  
  
 Giden iletiler için günlük ileti, kullanıcı kodu hemen ayrıldığında ve kablo iletisi göründükten hemen önce gerçekleşir.  
  
 WCF iki farklı düzeyleri, hizmet ve aktarım iletileri günlüğe kaydeder. Yanlış biçimlendirilmiş iletiler de günlüğe kaydedilir. Üç kategoriye birbirinden bağımsızdır ve yapılandırmada ayrı olarak etkinleştirilebilir.  
  
 Ayarlayarak günlüğe kaydetme düzeyini denetleyebilirsiniz `logMessagesAtServiceLevel`, `logMalformedMessages`, ve `logMessagesAtTransportLevel` özniteliklerini `messageLogging` öğesi.  
  
### <a name="service-level"></a>Hizmet düzeyi  
 Bu katmanda günlüğe ileti olan hakkında (alan)'ı girmenizi ya da (gönderme) bırakın kullanıcı kodu. Filtreler tanımladıysanız, filtrelerle eşleşen iletileri günlüğe kaydedilir. Aksi takdirde, hizmet düzeyinde tüm iletileri günlüğe kaydedilir. Altyapı iletileri (işlem, eş kanalı ve güvenlik), bu düzeyde güvenilir Mesajlaşma iletileri dışında da kaydedilir. Akış iletileri, yalnızca üst bilgileri günlüğe kaydedilir. Ayrıca, bu düzeyde şifresi güvenli iletiler kaydedilir.  
  
### <a name="transport-level"></a>Aktarım düzeyi  
 Bu katmanda günlüğe ileti kodlanması veya için veya kablo üzerinde nakliye sonra çözülmüş hazırsınız. Filtreler tanımladıysanız, filtrelerle eşleşen iletileri günlüğe kaydedilir. Aksi takdirde aktarım katmanında tüm iletileri günlüğe kaydedilir. Tüm altyapı iletileri güvenilir Mesajlaşma iletileri de dahil olmak üzere bu katmanda günlüğe kaydedilir. Akış iletileri, yalnızca üst bilgileri günlüğe kaydedilir. Ayrıca, güvenli iletiler, eğer dışında bu düzeyde HTTPS kullanılan gibi güvenli aktarım şifreli günlüğe kaydedilir.  
  
### <a name="malformed-level"></a>Hatalı biçimlendirilmiş düzeyi  
 Hatalı biçimlendirilmiş iletilerin WCF yığını tarafından herhangi bir işleme aşamasında reddedilir iletileri ' dir. Hatalı biçimlendirilmiş iletilerin kaydedilip olarak-olduğu: bunu uygun olmayan XML vb. ile olmaları durumunda şifreli. `maxSizeOfMessageToLog` CDATA günlüğe kaydedilecek ileti boyutu tanımlı. Varsayılan olarak, `maxSizeOfMessageToLog` 256 K eşittir. Bu özniteliği hakkında daha fazla bilgi için diğer seçenekleri bölümüne bakın.  
  
### <a name="other-options"></a>Diğer Seçenekler  
 Günlük düzeylerini ek olarak, kullanıcı, aşağıdaki seçenekleri belirtebilirsiniz:  
  
-   Tüm ileti (`logEntireMessage` öznitelik): Bu değer, iletinin tamamı (ileti üst bilgisi ve gövdesi) günlüğe kaydedilip kaydedilmeyeceğini belirtir. Varsayılan değer `false`, yani yalnızca üstbilgisi günlüğe kaydedilir. Bu ayar, hizmet ve aktarım ileti günlüğe kaydetme düzeylerini etkiler...  
  
-   Günlüğe kaydedilecek en yüksek ileti (`maxMessagesToLog` öznitelik): günlüğe kaydedilecek ileti sayısı bu değeri belirtir. Bu kota hesaplamanıza dahil tüm iletileri (hizmet, taşıma ve yanlış biçimlendirilmiş iletiler) sayılır. Kotasına ulaşıldığında izleme yayılır ve hiçbir ek ileti günlüğe kaydedilir. Varsayılan değer 10000'dir.  
  
-   Günlüğe kaydedilecek ileti en büyük boyutunu (`maxSizeOfMessageToLog` öznitelik): Bu değer, bayt cinsinden günlüğe kaydedilecek ileti en büyük boyutunu belirtir. Boyut sınırını aşan iletiler günlüğe ve başka bir etkinliği o ileti için gerçekleştirilir. Bu ayar, tüm izleme düzeylerini etkiler. ServiceModel izleme açıksa, bir uyarı düzeyi izleme ilk günlüğe kaydetme (ServiceModelSend * veya TransportReceive) kullanıcıya bildirmek için noktada yayılır. Yanlış biçimlendirilmiş iletiler için varsayılan değer 4 K olsa da hizmet düzeyi ve aktarım düzeyi iletiler için varsayılan değer 256 K ' dir.  
  
    > [!CAUTION]
    >  Karşılaştırılacak hesaplanan ileti boyutu `maxSizeOfMessageToLog` serileştirme önce bellekte ileti boyutu. Bu boyut günlüğe kaydedilir ve birçok yerde gerçek boyutundan daha büyük ileti dizesinin gerçek uzunluk farklı olabilir. Sonuç olarak, iletileri günlüğe kaydedilmeyebilir. İçin bu olgu belirterek hesabının `maxSizeOfMessageToLog` için öznitelik %10 beklenen bir ileti boyuttan daha büyük olmalıdır. Ayrıca, hatalı biçimlendirilmiş iletilerin kaydedilip, ileti günlüklerini tarafından kullanılan gerçek disk alanı tarafından belirtilen değere boyutunu en fazla 5 kez olabilir `maxSizeOfMessageToLog`.  
  
 Hiçbir İzleme dinleyicisi yapılandırma dosyasında tanımlandıysa, herhangi bir günlük çıktısı bakılmaksızın belirtilen günlük düzeyi oluşturulur.  
  
 Bu bölümde açıklanan öznitelikleri gibi ileti günlüğe kaydetme seçenekleri Windows Yönetim Araçları (WMI) kullanarak çalışma zamanında değiştirilebilir. Bu erişerek yapılabilir [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) bu Boolean özellikleri sunan bir örneği: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, ve `LogMalformedMessages`. Bu nedenle, İzleme dinleyicisi için ileti günlüğe kaydetmeyi yapılandırın, ancak ayarlayın, bu seçenekleri için `false` yapılandırması, daha sonra bunları değiştirebilirsiniz `true` uygulama çalışırken. Bu ileti günlüğe kaydetmeyi zamanında etkili bir şekilde sağlar. Yapılandırma dosyanızda günlük iletisi etkinleştirirseniz, benzer şekilde, size, WMI'yı kullanarak çalışma zamanında devre dışı bırakabilirsiniz. Daha fazla bilgi için [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 `source` Alanında bir ileti günlüğü belirtir hangi bağlamda iletisi kaydedilir: istek-yanıt ya da 1 yönlü isteği, hizmet modeli veya Aktarım katmanı veya hatalı bir ileti için bir istek iletisi gönderme/alma sırasında.  
  
 Hatalı biçimlendirilmiş iletilerin `source` eşittir `Malformed`. Aksi takdirde, kaynak bağlama göre aşağıdaki değerlere sahip.  
  
 İstek/yanıt  
  
||İsteği Gönder|İstek alma|Yanıt göndermesi|Yanıt alma|  
|-|------------------|---------------------|----------------|-------------------|  
|Hizmet modeli katmanını|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Alma<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> Yanıtla|Hizmet<br /><br /> Düzey<br /><br /> Alma<br /><br /> Yanıtla|  
|Aktarım Katmanı|Taşıma<br /><br /> Gönder|Taşıma<br /><br /> Alma|Taşıma<br /><br /> Gönder|Taşıma<br /><br /> Alma|  
  
 Tek yönlü iste  
  
||İsteği Gönder|İstek alma|  
|-|------------------|---------------------|  
|Hizmet modeli katmanını|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> Veri birimi|Hizmet<br /><br /> Düzey<br /><br /> Alma<br /><br /> Veri birimi|  
|Aktarım Katmanı|Taşıma<br /><br /> Gönder|Taşıma<br /><br /> Alma|  
  
## <a name="message-filters"></a>İleti Filtreleri  
 İleti filtreleri tanımlanmış `messageLogging` yapılandırma öğesinin `diagnostics` yapılandırma bölümü. Bu hizmet ve aktarım düzeyinde uygulanır. Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir. Filtre boş tanımlıysa, tüm iletileri geçirir.  
  
 Filtreler XPath tamamını destekler ve yapılandırma dosyasında göründükleri sırayla uygulanır. Sözdizimsel olarak yanlış bir filtre yapılandırma bir özel durum oluşur.  
  
 Filtreleri de sağlaması kullanarak bir güvenlik özelliği `nodeQuota` filtreyle eşleşen incelenmesi XPath DOM düğüm sayısını sınırlayan bir öznitelik.  
  
 Aşağıdaki örnekte bir filtre yapılandırın, nasıl bir SOAP üst bilgisi bölümü olan bu kayıtları yalnızca iletileri gösterir.  
  
```xml  
<messageLogging logEntireMessage="true"  
    logMalformedMessages="true"   
    logMessagesAtServiceLevel="true"  
    logMessagesAtTransportLevel="true"  
    maxMessagesToLog="420">  
    <filters>  
        <add nodeQuota="10" xmlns:soap="http://www.w3.org/2003/05/soap-envelope">  
                 /soap:Envelope/soap:Header  
        </add>  
     </filters>  
</messageLogging>  
```  
  
 Bir ileti gövdesi ile filtre uygulanamıyor. Bir ileti gövdesini düzenleme girişimi filtreleri filtreleri listesinden kaldırılır. Bir olay da bu gösteren yayılır. Örneğin, aşağıdaki filtre filtre tablosundan kaldırılan.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Özel bir dinleyici yapılandırma  
 Ayrıca, özel bir dinleyici ile ek seçenekleri yapılandırabilirsiniz. Özel bir dinleyici iletileri açmadan önce uygulamaya özgü PII öğeleri filtreleme yapmak yararlı olabilir. Aşağıdaki örnek bir özel dinleyici yapılandırması gösterir.  
  
```xml  
<system.diagnostics>  
   <sources>  
     <source name="System.ServiceModel.MessageLogging">  
           <listeners>  
             <add name="MyListener"   
                    type="YourCustomListener"  
                    initializeData="c:\logs\messages.svclog"  
                    maxDiskSpace="1000"/>  
           </listeners>  
     </source>  
   </sources>  
</system.diagnostics>  
```  
  
 Bilmeniz gereken, `type` öznitelik türü için bir koşullu derleme adı ayarlanmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<messageLogging >](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
