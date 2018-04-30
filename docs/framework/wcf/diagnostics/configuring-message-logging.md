---
title: İleti Günlüğe Kaydetmeyi Yapılandırma
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
caps.latest.revision: 40
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6e2d45e7b8769ee525835ad3dc50262a03a5a7b6
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="configuring-message-logging"></a>İleti Günlüğe Kaydetmeyi Yapılandırma
Bu konuda, ileti günlüğe kaydetme farklı senaryolar için nasıl yapılandırabileceğiniz açıklanmaktadır.  
  
## <a name="enabling-message-logging"></a>İleti günlüğü etkinleştirme  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ileti, varsayılan olarak günlüğe kaydetmez. İleti günlüğe kaydetmeyi etkinleştirmek için bir izleme dinleyicisi eklemek `System.ServiceModel.MessageLogging` izleme kaynağı ve ayarlamak için öznitelikler `<messagelogging>` yapılandırma dosyası öğesi.  
  
 Aşağıdaki örnek, günlüğe yazılmasını etkinleştirmek ve ek seçenekleri belirtmek gösterilmektedir.  
  
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
  
 İleti günlüğe kaydetme ayarlarını hakkında daha fazla bilgi için bkz: [izleme ve ileti günlüğe kaydetme için önerilen ayarları](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
 Kullanabileceğiniz `add` adını ve kullanmak istediğiniz dinleyici türünü belirtmek için. Örnek yapılandırma dinleyicisi "iletileri" olarak adlandırılır ve standart .NET Framework İzleme dinleyicisi ekler (`System.Diagnostics.XmlWriterTraceListener`) olarak kullanmak üzere türü. Kullanırsanız `System.Diagnostics.XmlWriterTraceListener`, yapılandırma dosyasında çıktı dosya konumunu ve adını belirtmeniz gerekir. Bu ayarlayarak yapılır `initializeData` günlük dosyasının adı. Aksi takdirde, sistem bir özel durum oluşturur. Ayrıca varsayılan dosyasına yayar özel bir dinleyici uygulayabilirsiniz.  
  
> [!NOTE]
>  Disk alanı ileti günlüğe kaydetme eriştiği için belirli bir hizmet için diske yazılan iletilerin sayısını sınırlamanız gerekir. İleti sınırına ulaşıldığında, bir izleme bilgileri düzeyinde oluşturulur ve tüm ileti günlüğe kaydetme etkinlikleri durdurun.  
  
 Günlüğe kaydetme düzeyi gibi ek seçenekler, günlük düzeyi ve Seçenekleri bölümünde ele alınmıştır.  
  
 `switchValue` Özniteliği bir `source` yalnızca izleme için geçerlidir. Belirtirseniz bir `switchValue` için öznitelik `System.ServiceModel.MessageLogging` izleme kaynağı olarak izler, herhangi bir etkisi olmaz.  
  
```xml  
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">  
```  
  
 İzleme kaynağı devre dışı bırakmak istiyorsanız, kullanması gereken `logMessagesAtServiceLevel`, `logMalformedMessages`, ve `logMessagesAtTransportLevel` özniteliklerini `messageLogging` öğesi yerine. Bu öznitelikler kümesine `false`. Bu yapılandırma Düzenleyicisi UI arabirimi aracılığıyla önceki kod örneğinde, yapılandırma dosyası kullanarak veya WMI kullanılarak yapılabilir. Yapılandırma Düzenleyicisi aracı hakkında daha fazla bilgi için bkz: [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md). WMI hakkında daha fazla bilgi için bkz: [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
## <a name="logging-levels-and-options"></a>Günlük düzeyleri ve seçenekleri  
 Gelen iletiler için günlüğe kaydetme hemen ileti hizmet düzeyi için kullanıcı kodu büyümeden hemen ileti, biçimlendirilmemiş sonra ve hatalı biçimlendirilmiş iletileri algılandığında gerçekleşir.  
  
 Giden iletiler için günlüğe kaydetme hemen ileti kullanıcı kodu ayrıldığında sonra ve ileti kablo göründükten hemen önce gerçekleşir.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iki farklı düzeylerde, hizmet ve aktarım iletilerini günlüğe kaydeder. Hatalı biçimlendirilmiş iletileri da günlüğe kaydedilir. Üç kategoride birbirinden bağımsızdır ve yapılandırmada ayrı olarak etkinleştirilebilir.  
  
 Ayarlayarak günlük düzeyini denetleyebilirsiniz `logMessagesAtServiceLevel`, `logMalformedMessages`, ve `logMessagesAtTransportLevel` özniteliklerini `messageLogging` öğesi.  
  
### <a name="service-level"></a>Hizmet düzeyi  
 Bu katmanda günlüğe kaydedilen iletileri olan yaklaşık (alma üzerinde) girin veya (gönderme) ayrılma kullanıcı kodu. Filtreler tanımladıysanız, filtrelerle eşleşen iletileri günlüğe kaydedilir. Aksi takdirde, hizmet düzeyinde tüm iletileri günlüğe kaydedilir. Altyapı iletileri (işlemler, eş kanalı ve güvenlik) de güvenilir Mesajlaşma iletileri dışında bu düzeyde günlüğe kaydedilir. Akış iletilerde yalnızca üstbilgileri günlüğe kaydedilir. Ayrıca, bu düzeyde şifresi güvenli iletiler kaydedilir.  
  
### <a name="transport-level"></a>Aktarım düzeyi  
 Bu katmanda günlüğe kaydedilen iletileri kodlanmış veya için veya taşıma hattaki sonra kodunu çözdü hazırsınız demektir. Filtreler tanımladıysanız, filtrelerle eşleşen iletileri günlüğe kaydedilir. Aksi takdirde, Aktarım katmanı tüm iletileri günlüğe kaydedilir. Tüm altyapı iletileri güvenilir Mesajlaşma iletileri de dahil olmak üzere bu katmanda günlüğe kaydedilir. Akış iletilerde yalnızca üstbilgileri günlüğe kaydedilir. Ayrıca, güvenli iletiler IF dışında bu düzeyde HTTPS kullanılan gibi güvenli bir taşıma şifrelenmiş olarak kaydedilir.  
  
### <a name="malformed-level"></a>Hatalı biçimlendirilmiş düzeyi  
 Hatalı biçimlendirilmiş iletiler olan tarafından reddedilen iletiler [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] işleminin herhangi bir aşamada yığını. Hatalı biçimlendirilmiş iletileri olarak kaydediliyor-olduğu: bunu uygun olmayan XML vb. ile olmaları durumunda şifrelenmiş. `maxSizeOfMessageToLog` CDATA olarak kaydedilen iletinin boyutunu tanımlanır. Varsayılan olarak, `maxSizeOfMessageToLog` 256 K eşittir. Bu öznitelik hakkında daha fazla bilgi için diğer seçenekleri bölümüne bakın.  
  
### <a name="other-options"></a>Diğer seçenekleri  
 Günlüğe kaydetme düzeylerini yanı sıra kullanıcı aşağıdaki seçenekleri belirtebilirsiniz:  
  
-   Tüm ileti günlüğe (`logEntireMessage` özniteliği): Bu değer, iletinin tamamını (ileti başlığı ve gövde) günlüğe kaydedilip kaydedilmediğini belirtir. Varsayılan değer `false`, yalnızca üstbilgisi kaydedilir anlamına gelir. Bu ayar, hizmet ve aktarım ileti günlüğe kaydetme düzeylerini etkiler...  
  
-   Günlüğe kaydedilecek en fazla ileti (`maxMessagesToLog` özniteliği): Bu değer günlüğe kaydedilecek ileti sayısı üst sınırını belirtir. Tüm iletileri (hizmet, taşıma ve hatalı biçimlendirilmiş iletileri) Bu kota sayılır. Kotasına ulaşıldığında, bir izleme yayılan ve hiçbir ek ileti günlüğe kaydedilir. Varsayılan değer 10000'dir.  
  
-   Oturum iletisinin en büyük boyutu (`maxSizeOfMessageToLog` özniteliği): Bu değer bayt cinsinden günlüğe kaydedilecek ileti boyut üst sınırını belirtir. Boyut sınırını aşan iletileri günlüğe kaydedilmeyen ve başka bir etkinlik için bu iletiyi gerçekleştirilir. Bu ayar, tüm izleme düzeylerini etkiler. ServiceModel izleme üzerindeyse bir uyarı düzeyi izleme ilk günlük (ServiceModelSend * veya TransportReceive) kullanıcıya bildirmek için noktada yayınlanır. Hatalı biçimlendirilmiş iletileri için varsayılan değer 4 K olsa da hizmet düzeyi ve aktarım düzeyi iletileri için varsayılan değer 256 K ' dir.  
  
    > [!CAUTION]
    >  Karşılaştırılacak hesaplanan ileti boyutu `maxSizeOfMessageToLog` seri hale getirme önce bellekte ileti boyutu. Bu boyut günlüğe kaydedilir ve birçok yerde gerçek boyutundan daha büyük olan ileti dizesi gerçek uzunluğuyla farklı olabilir. Sonuç olarak, iletileri kaydedilebilir değil. Bu bulgusunun belirterek hesabının `maxSizeOfMessageToLog` için öznitelik % 10 beklenen bir ileti boyutundan daha büyük olmalıdır. Ek olarak, hatalı biçimlendirilmiş iletileri oturum açtıysanız, ileti günlükleri tarafından kullanılan gerçek disk alanı ile belirtilen değer boyutunu 5 kata olabilir `maxSizeOfMessageToLog`.  
  
 İzleme dinleyicisi yapılandırma dosyasında tanımlanmış olması durumunda, günlük çıktısı bakılmaksızın belirtilen günlüğe kaydetme düzeyi oluşturulur.  
  
 Bu bölümde açıklanan öznitelikleri gibi ileti günlüğe kaydetme seçeneklerini Windows Yönetim Araçları (WMI) kullanarak çalışma zamanında değiştirilebilir. Bu erişerek yapılabilir [AppDomainInfo](../../../../docs/framework/wcf/diagnostics/wmi/appdomaininfo.md) Boolean bu özellikleri sunar örneği: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`, ve `LogMalformedMessages`. Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırmanıza rağmen ayarlamak bu seçenekleri için `false` yapılandırması, daha sonra bunları değiştirebileceğiniz `true` uygulama çalışırken. Bu ileti günlüğe kaydetme çalışma zamanında etkili bir şekilde sağlar. İleti günlüğe kaydetme, yapılandırma dosyanızda etkinleştirirseniz, benzer şekilde, size, WMI'yı kullanarak çalışma zamanında devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz: [tanılama için Windows Yönetim araçları kullanarak](../../../../docs/framework/wcf/diagnostics/wmi/index.md).  
  
 `source` Bir ileti günlüğü alanında belirtir hangi bağlamda iletisi günlüğe kaydedilir: istek-yanıt ya da hizmet modeli veya aktarım katmanında veya hatalı bir ileti söz konusu olduğunda 1 yönlü isteği için bir istek iletisi gönderme/alma sırasında.  
  
 Hatalı biçimlendirilmiş iletilerde `source` eşittir `Malformed`. Aksi halde, kaynak bağlamına dayalı aşağıdaki değerlere sahip.  
  
 İstek/yanıt  
  
||İsteği Gönder|İsteği alma|Yanıt gönderme|Yanıtın|  
|-|------------------|---------------------|----------------|-------------------|  
|Hizmet modeli katmanı|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Alma<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> Yanıtla|Hizmet<br /><br /> Düzey<br /><br /> Alma<br /><br /> Yanıtla|  
|Aktarım Katmanı|Taşıma<br /><br /> Gönder|Taşıma<br /><br /> Alma|Taşıma<br /><br /> Gönder|Taşıma<br /><br /> Alma|  
  
 Tek yönlü iste  
  
||İsteği Gönder|İsteği alma|  
|-|------------------|---------------------|  
|Hizmet modeli katmanı|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> Veri birimi|Hizmet<br /><br /> Düzey<br /><br /> Alma<br /><br /> Veri birimi|  
|Aktarım Katmanı|Taşıma<br /><br /> Gönder|Taşıma<br /><br /> Alma|  
  
## <a name="message-filters"></a>İleti Filtreleri  
 İleti filtreleri tanımlanmış `messageLogging` yapılandırma öğesinin `diagnostics` yapılandırma bölümü. Bunlar hizmet ve aktarım düzeyinde uygulanır. Bir veya daha fazla filtre tanımlandığında, en az bir filtre ile eşleşen iletileri günlüğe kaydedilir. Hiçbir filtre tanımlanmış olması durumunda, tüm iletileri geçirir.  
  
 Filtreler tam XPath sözdizimini desteklemek ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimsel olarak yanlış bir filtre yapılandırma istisnası ile sonuçlanır.  
  
 Ayrıca filtreleri sağla kullanarak bir güvenlik özelliği `nodeQuota` filtreyle eşleşen incelenmesi XPath DOM düğüm sayısının üst sınırını belirler özniteliği.  
  
 Aşağıdaki örnekte bir filtre yapılandırmak nasıl bir SOAP üstbilgi bölümüne sahip bu kayıtları yalnızca iletileri gösterir.  
  
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
  
 Bir ileti gövdesini filtreleri uygulanamaz. Bir ileti gövdesini işlemek girişimi filtreleri filtreleri listesinden kaldırılır. Bir olay da bu gösteren yayınlanır. Örneğin, aşağıdaki filtre filtre tablosundan kaldırılması.  
  
```xml  
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>  
```  
  
## <a name="configuring-a-custom-listener"></a>Özel bir dinleyici yapılandırma  
 Bu gibi durumlarda, özel bir dinleyici ayrıca ek seçenekleri yapılandırabilirsiniz. Özel bir dinleyici iletileri açmadan önce uygulamaya özgü PII öğelerinden filtreleme yararlı olabilir. Aşağıdaki örnek, bir özel dinleyici yapılandırması gösterir.  
  
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
  
 Bilmeniz gereken, `type` türü için bir koşullu derleme adı özniteliği ayarlanmalıdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<messageLogging >](../../../../docs/framework/configure-apps/file-schema/wcf/messagelogging.md)  
 [Günlüğe İleti Kaydetme](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar](../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)
