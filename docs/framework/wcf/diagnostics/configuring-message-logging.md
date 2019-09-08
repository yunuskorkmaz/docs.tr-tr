---
title: İleti Günlüğe Kaydetmeyi Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: db538634dccf22fb954ccf0827909e5cf3563f77
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70798168"
---
# <a name="configuring-message-logging"></a>İleti Günlüğe Kaydetmeyi Yapılandırma

Bu konu, farklı senaryolar için ileti günlüğe kaydetmeyi nasıl yapılandırabileceğinizi açıklamaktadır.

## <a name="enabling-message-logging"></a>Ileti günlüğe kaydetmeyi etkinleştirme

Windows Communication Foundation (WCF) varsayılan olarak iletileri günlüğe eklemez. İleti günlüğe kaydetmeyi etkinleştirmek için `System.ServiceModel.MessageLogging` izleme kaynağına bir izleme dinleyicisi eklemeniz ve yapılandırma dosyasındaki `<messagelogging>` öğenin özniteliklerini ayarlamanız gerekir.

Aşağıdaki örnek, günlüğü nasıl etkinleştireceğinizi ve ek seçenekler belirtmenizi gösterir.

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

İleti günlüğe kaydetme ayarları hakkında daha fazla bilgi için bkz. [izleme ve Ileti günlüğe kaydetme Için önerilen ayarlar](./tracing/recommended-settings-for-tracing-and-message-logging.md).

Kullanmak istediğiniz dinleyicinin adını ve türünü belirtmek için'ikullanabilirsiniz.`add` Örnek yapılandırmada, dinleyici "Messages" olarak adlandırılır ve standart .NET Framework İzleme dinleyicisini (`System.Diagnostics.XmlWriterTraceListener`) kullanılacak tür olarak ekler. `System.Diagnostics.XmlWriterTraceListener`Kullanıyorsanız, yapılandırma dosyasında çıkış dosyasının konumunu ve adını belirtmeniz gerekir. Bu, günlük dosyasının adı `initializeData` ayarlanarak yapılır. Aksi takdirde, sistem bir özel durum oluşturur. Günlükleri varsayılan bir dosyaya yayan özel bir dinleyici da uygulayabilirsiniz.

> [!NOTE]
> İleti günlüğe kaydetme disk alanına eriştiği için belirli bir hizmet için diske yazılan ileti sayısını sınırlamanız gerekir. İleti sınırına ulaşıldığında, bilgi düzeyindeki bir izleme oluşturulur ve tüm ileti günlüğü etkinlikleri durur.

Günlüğe kaydetme düzeyi ve ek seçenekler, günlük düzeyi ve seçenekler bölümünde ele alınmıştır.

`switchValue` Öğesininözniteliği`source` yalnızca izleme için geçerlidir. İzleme`System.ServiceModel.MessageLogging` kaynağı için aşağıdaki `switchValue` gibi bir öznitelik belirtirseniz, hiçbir etkisi olmaz.

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
```

İzleme kaynağını devre dışı bırakmak istiyorsanız, `logMessagesAtServiceLevel`bunun yerine `messageLogging` öğesinin, `logMalformedMessages`ve `logMessagesAtTransportLevel` özniteliklerini kullanmanız gerekir. Tüm bu öznitelikleri olarak `false`ayarlamanız gerekir. Bu, önceki kod örnekteki yapılandırma dosyası kullanılarak, yapılandırma Düzenleyicisi Kullanıcı arabirimi arabiriminden veya WMI kullanılarak yapılabilir. Yapılandırma Düzenleyicisi aracı hakkında daha fazla bilgi için bkz. [yapılandırma Düzenleyicisi aracı (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md). WMI hakkında daha fazla bilgi için bkz. [Tanılama için Windows Yönetim araçları kullanma](./wmi/index.md).

## <a name="logging-levels-and-options"></a>Günlük düzeyleri ve Seçenekler

Gelen iletilerde, ileti oluşturulduktan hemen sonra ileti, hizmet düzeyindeki Kullanıcı koduna girmeden ve hatalı biçimlendirilmiş iletiler algılandığında anında gerçekleşir.

Giden iletiler için günlüğe kaydetme, ileti, kullanıcı kodundan ayrıldıktan hemen sonra ve ileti kablodan geçmeden hemen önce gerçekleşir.

WCF, iletileri iki farklı düzeyde, hizmette ve aktarımda günlüğe kaydeder. Hatalı biçimlendirilmiş iletiler de günlüğe kaydedilir. Üç kategori birbirinden bağımsızdır ve yapılandırmada ayrı olarak etkinleştirilebilir.

`logMessagesAtServiceLevel` Öğesinin,`logMalformedMessages` ve`logMessagesAtTransportLevel` özniteliklerini ayarlayarak günlüğe kaydetme düzeyini kontrol edebilirsiniz. `messageLogging`

### <a name="service-level"></a>Hizmet düzeyi

Bu katmanda günlüğe kaydedilen iletiler, Kullanıcı kodu girmek için (alma sırasında) veya ayrılmaya (gönderme sırasında). Filtreler tanımlanmışsa, yalnızca filtrelerle eşleşen iletiler günlüğe kaydedilir. Aksi takdirde, hizmet düzeyindeki tüm iletiler günlüğe kaydedilir. Altyapı iletileri (işlemler, eş kanal ve güvenlik), güvenilir mesajlaşma iletileri dışında bu düzeyde de günlüğe kaydedilir. Akışlı iletilerde yalnızca üstbilgiler günlüğe kaydedilir. Ayrıca, güvenli iletilerin şifresi bu düzeyde çözülür.

### <a name="transport-level"></a>Aktarım düzeyi

Bu katmanda günlüğe kaydedilen iletiler, hattaki taşıma için veya sonrasında kodlanacak veya kodu çözülecek şekilde hazırlanmaya yöneliktir. Filtreler tanımlanmışsa, yalnızca filtrelerle eşleşen iletiler günlüğe kaydedilir. Aksi halde, aktarım katmanındaki tüm iletiler günlüğe kaydedilir. Tüm altyapı iletileri, güvenilir mesajlaşma iletileri de dahil olmak üzere bu katmanda günlüğe kaydedilir. Akışlı iletilerde yalnızca üstbilgiler günlüğe kaydedilir. Ayrıca, HTTPS gibi güvenli bir aktarım kullanılması dışında, güvenli iletiler bu düzeyde şifreli olarak kaydedilir.

### <a name="malformed-level"></a>Hatalı biçimlendirilmiş düzey

Hatalı biçimlendirilmiş iletiler, herhangi bir işleme aşamasında WCF yığını tarafından reddedilen iletilerdir. Hatalı biçimlendirilmiş iletiler, olarak kaydedilir: Bu durumda, uygun olmayan XML ile, vb. için şifrelenir. `maxSizeOfMessageToLog`CDATA olarak günlüğe kaydedilecek iletinin boyutu tanımlanır. Varsayılan olarak, `maxSizeOfMessageToLog` 256k ' e eşittir. Bu öznitelik hakkında daha fazla bilgi için diğer seçenekler bölümüne bakın.

### <a name="other-options"></a>Diğer seçenekler

Kullanıcı, günlük düzeylerine ek olarak aşağıdaki seçenekleri belirtebilir:

- Tüm iletiyi Kaydet (`logEntireMessage` öznitelik): Bu değer, iletinin tamamının (ileti üst bilgisi ve gövdesi) günlüğe kaydedilip kaydedilmeyeceğini belirtir. Varsayılan değer `false`, yani yalnızca üstbilginin günlüğe kaydedildiği anlamına gelir. Bu ayar, hizmet ve aktarım iletisi günlük düzeylerini etkiler.

- Günlüğe kaydedilecek en fazla ileti`maxMessagesToLog` (öznitelik): Bu değer, günlüğe kaydedilecek en fazla ileti sayısını belirtir. Tüm iletiler (hizmet, aktarım ve hatalı biçimlendirilmiş iletiler) bu kotanın altında sayılır. Kotaya ulaşıldığında, bir izleme yayınlanır ve başka bir ileti günlüğe kaydedilmez. Varsayılan değer 10000 ' dir.

- Günlüğe kaydedilecek iletinin en büyük boyutu (`maxSizeOfMessageToLog` öznitelik): Bu değer, bayt cinsinden günlüğe kaydedilecek en büyük ileti boyutunu belirtir. Boyut sınırını aşan iletiler günlüğe kaydedilmez ve bu ileti için başka bir etkinlik gerçekleştirilmez. Bu ayar tüm izleme düzeylerini etkiler. ServiceModel izleme açık ise, kullanıcıya bildirimde bulunan ilk günlük noktasında (ServiceModelSend * veya TransportReceive) bir uyarı düzeyi izleme yayınlanır. Hizmet düzeyi ve aktarım düzeyi iletileri için varsayılan değer 256K, ancak hatalı biçimlendirilmiş iletiler için varsayılan değer 4K olur.

  > [!CAUTION]
  > Karşılaştırma `maxSizeOfMessageToLog` için hesaplanan ileti boyutu, Serileştirmeden önce bellekteki ileti boyutudur. Bu boyut, günlüğe kaydedilen ileti dizesinin gerçek uzunluğundan farklı olabilir ve birçok durumda gerçek boyuttan daha büyük olur. Sonuç olarak, iletiler günlüğe kaydedilmez. Bu olguyu, `maxSizeOfMessageToLog` beklenen ileti boyutundan% 10 daha büyük olacak özniteliği belirterek yapabilirsiniz. Ayrıca, hatalı biçimlendirilmiş iletiler günlüğe kaydedilir, ileti günlükleri tarafından kullanılan gerçek disk alanı, tarafından `maxSizeOfMessageToLog`belirtilen değerin boyutunun 5 katı olabilir.

Yapılandırma dosyasında bir izleme dinleyicisi tanımlanmazsa, belirtilen günlüğe kaydetme düzeyinden bağımsız olarak günlüğe kaydetme çıkışı oluşturulmaz.

Bu bölümde açıklanan öznitelikler gibi ileti günlüğü seçenekleri, Windows Yönetim Araçları (WMI) kullanılarak çalışma zamanında değiştirilebilir. Bu, bu Boole özelliklerini sunan [AppDomainInfo](./wmi/appdomaininfo.md) örneğine erişerek yapılabilir: `LogMessagesAtServiceLevel`, `LogMessagesAtTransportLevel`ve `LogMalformedMessages`. Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri `false` yapılandırma bölümünde ayarlarsanız, daha sonra uygulamanın çalıştığı zaman olarak `true` değiştirebilirsiniz. Bu, çalışma zamanında ileti günlüğe kaydetmeyi etkili bir şekilde sunar. Benzer şekilde, yapılandırma dosyanızda ileti günlüğünü etkinleştirirseniz, WMI kullanarak çalışma zamanında devre dışı bırakabilirsiniz. Daha fazla bilgi için bkz. [Tanılama için Windows Yönetim araçları kullanma](./wmi/index.md).

İleti `source` günlüğündeki alan, iletinin hangi bağlamda günlüğe kaydedileceğini belirtir: istek iletisi gönderirken/alırken, istek-yanıt veya 1 yönlü istek, hizmet modeli veya aktarım katmanında veya hatalı biçimlendirilmiş bir ileti durumunda.

Hatalı biçimlendirilmiş iletilerde `source` `Malformed`eşittir. Aksi takdirde, kaynak, bağlamı temel alarak aşağıdaki değerlere sahiptir.

Istek/yanıt için

||Istek gönder|Istek al|Yanıt gönder|Yanıt al|
|-|------------------|---------------------|----------------|-------------------|
|Hizmet modeli katmanı|Hizmet<br /><br /> Düzey<br /><br /> Send<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Receive<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Send<br /><br /> Döndürüp|Hizmet<br /><br /> Düzey<br /><br /> Receive<br /><br /> Döndürüp|
|Aktarım katmanı|Aktarım<br /><br /> Send|Aktarım<br /><br /> Receive|Aktarım<br /><br /> Send|Aktarım<br /><br /> Receive|

Tek yönlü Istek için

||Istek gönder|Istek al|
|-|------------------|---------------------|
|Hizmet modeli katmanı|Hizmet<br /><br /> Düzey<br /><br /> Send<br /><br /> Inın|Hizmet<br /><br /> Düzey<br /><br /> Receive<br /><br /> Inın|
|Aktarım katmanı|Aktarım<br /><br /> Send|Aktarım<br /><br /> Receive|

## <a name="message-filters"></a>İleti Filtreleri

İleti filtreleri `messageLogging` `diagnostics` yapılandırma bölümünün yapılandırma öğesinde tanımlanmıştır. Bunlar hizmet ve Aktarım düzeyinde uygulanır. Bir veya daha fazla filtre tanımlandığında yalnızca filtrelerden en az biriyle eşleşen mesajlar günlüğe kaydedilir. Hiçbir filtre tanımlanmamışsa, tüm iletiler geçer.

Filtreler tam XPath söz dizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimi yanlış bir filtre, yapılandırma özel durumuyla sonuçlanır.

Filtreler ayrıca, XPath Dom içindeki filtreyle eşleşecek `nodeQuota` şekilde incelenebilir maksimum düğüm sayısını sınırlayan özniteliği kullanarak bir güvenlik özelliği de sağlar.

Aşağıdaki örnek, yalnızca bir SOAP üstbilgisi bölümüne sahip iletileri kaydeden bir filtrenin nasıl yapılandırılacağını gösterir.

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

Filtreler bir iletinin gövdesine uygulanamaz. Bir iletinin gövdesini işlemeyi deneyen filtreler, filtreler listesinden kaldırılır. Bunu belirten bir olay da yayılır. Örneğin, aşağıdaki filtre filtre tablosundan kaldırılacak.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Özel bir dinleyici yapılandırma

Ayrıca, ek seçeneklerle özel bir dinleyici de yapılandırabilirsiniz. Özel bir dinleyici, günlüğe kaydedilmeden önce iletilerden uygulamaya özgü PII öğelerini filtrelemede yararlı olabilir. Aşağıdaki örnek, özel bir dinleyici yapılandırmasını gösterir.

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

`type` Özniteliğin, türün nitelenmiş derleme adına ayarlanması gerektiğini bilmelisiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [\<messageLogging >](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Günlüğe İleti Kaydetme](message-logging.md)
- [İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar](./tracing/recommended-settings-for-tracing-and-message-logging.md)
