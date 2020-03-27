---
title: İleti Günlüğe Kaydetmeyi Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- message logging [WCF]
ms.assetid: 0ff4c857-8f09-4b85-9dc0-89084706e4c9
ms.openlocfilehash: 283f43239d6cf5aea5ea668397a52313ff526e2a
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80345194"
---
# <a name="configuring-message-logging"></a>İleti Günlüğe Kaydetmeyi Yapılandırma

Bu konu, farklı senaryolar için ileti günlüğe kaydetmeyi nasıl yapılandırabileceğinizi açıklar.

## <a name="enabling-message-logging"></a>İleti Günlüğe Kaydetmeyi Etkinleştirme

Windows Communication Foundation (WCF) iletileri varsayılan olarak günlüğe kaydetmez. İleti günlüğe kaydetmeyi etkinleştirmek için, `System.ServiceModel.MessageLogging` izleme kaynağına bir `<messagelogging>` izleme dinleyicisi eklemeniz ve yapılandırma dosyasındaki öğe için öznitelikleri ayarlamanız gerekir.

Aşağıdaki örnekte, günlüğe kaydetmenin nasıl etkinleştirilen ve ek seçenekler belirtin.

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

İleti günlüğe kaydetme ayarları hakkında daha fazla bilgi için, [İzleme ve İleti Günlüğe Kaydetme için Önerilen Ayarlar'a](./tracing/recommended-settings-for-tracing-and-message-logging.md)bakın.

Kullanmak istediğiniz `add` dinleyicinin adını ve türünü belirtmek için kullanabilirsiniz. Örnek yapılandırmada Dinleyiciye "iletiler" adı verilir ve kullanılacak tür olarak`System.Diagnostics.XmlWriterTraceListener`standart .NET Framework izleme dinleyicisi ( ) ekler. Kullanıyorsanız, `System.Diagnostics.XmlWriterTraceListener`yapılandırma dosyasında çıktı dosyası konumunu ve adını belirtmeniz gerekir. Bu, günlük `initializeData` dosyasının adına ayarlayarak yapılır. Aksi takdirde, sistem bir özel durum atar. Ayrıca, varsayılan bir dosyaya günlük ler yakan özel bir dinleyici de uygulayabilirsiniz.

> [!NOTE]
> İleti günlüğü disk alanına eriştiğinden, belirli bir hizmet için diske yazılan ileti lerin sayısını sınırlaştırmıştırmıştır. İleti sınırına ulaşıldığında, Bilgi düzeyinde bir izleme üretilir ve tüm ileti günlüğe kaydetme etkinlikleri durur.

Günlük düzeyi ve ek seçenekler, Günlük Düzeyi ve Seçenekler bölümünde tartışılır.

A'nın `switchValue` `source` özniteliği yalnızca izleme için geçerlidir. İzleme kaynağı `switchValue` için aşağıdaki gibi bir öznitelik belirtirseniz, bunun bir etkisi yoktur. `System.ServiceModel.MessageLogging`

```xml
<source name="System.ServiceModel.MessageLogging" switchValue="Verbose">
</source>
```

İzleme kaynağını devre dışı kılmış olmak istiyorsanız, `logMessagesAtServiceLevel` `logMalformedMessages`bunun `logMessagesAtTransportLevel` yerine öğenin özniteliklerini ve özniteliklerini `messageLogging` kullanmalısınız. Tüm bu öznitelikleri `false`' ye ayarlamanız gerekir. Bu, önceki kod örneğindeki yapılandırma dosyasını kullanarak, Configuration Editor UI arabirimi üzerinden veya WMI kullanılarak yapılabilir. Configuration Editor aracı hakkında daha fazla bilgi için [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)bakın. WMI hakkında daha fazla bilgi için, [tanılama için Windows Yönetim Araçları kullanma'ya](./wmi/index.md)bakın.

## <a name="logging-levels-and-options"></a>Günlük Düzeyleri ve Seçenekleri

Gelen iletiler için günlüğe kaydetme, ileti oluşturulduktan hemen sonra, ileti hizmet düzeyinde ki kullanıcı koduna gelmeden hemen önce ve hatalı biçimlendirilmiş iletiler algılandığında gerçekleşir.

Giden iletiler için günlüğe kaydetme, ileti kullanıcı kodundan ayrıldıktan hemen sonra ve ileti kabloya girmeden hemen önce gerçekleşir.

WCF iletileri iki farklı düzeyde, hizmet ve taşıma da kaydeder. Hatalı biçimlendirilmiş iletiler de günlüğe kaydedilir. Üç kategori birbirinden bağımsızdır ve yapılandırmada ayrı olarak etkinleştirilebilir.

Öğenin `logMessagesAtServiceLevel`, ve `logMalformedMessages` `logMessagesAtTransportLevel` özniteliklerini ayarlayarak günlüğe kaydetme düzeyini denetleyebilirsiniz. `messageLogging`

### <a name="service-level"></a>Hizmet Düzeyi

Bu katmanda günlüğe kaydedilen iletiler, kullanıcı kodunu girmek (almak üzere) veya ayrılmak üzeredir. Filtreler tanımlanmışsa, yalnızca filtrelerle eşleşen iletiler günlüğe kaydedilir. Aksi takdirde, hizmet düzeyindeki tüm iletiler günlüğe kaydedilir. Güvenilir İleti iletileri dışında altyapı iletileri (hareketler, eş kanal ve güvenlik) de bu düzeyde günlüğe kaydedilir. Akışlı iletilerde yalnızca üstbilgi günlüğe kaydedilir. Buna ek olarak, güvenli iletiler bu düzeyde şifresi çözülür kaydedilir.

### <a name="transport-level"></a>Ulaşım Seviyesi

Bu katmanda günlüğe kaydedilen iletiler, kablo üzerinde veya taşıma dan sonra kodlanacak veya çözülmeye hazırdır. Filtreler tanımlanmışsa, yalnızca filtrelerle eşleşen iletiler günlüğe kaydedilir. Aksi takdirde, aktarım katmanındaki tüm iletiler günlüğe kaydedilir. Güvenilir ileti iletileri de dahil olmak üzere tüm altyapı iletileri bu katmanda günlüğe kaydedilir. Akışlı iletilerde yalnızca üstbilgi günlüğe kaydedilir. Ayrıca, HTTPS gibi güvenli bir aktarım kullanılmadığı dışında, güvenli iletiler bu düzeyde şifrelenmişolarak kaydedilir.

### <a name="malformed-level"></a>Hatalı Biçimlendirilmiş Seviye

Hatalı biçimlendirilmiş iletiler, işlemin herhangi bir aşamasında WCF yığını tarafından reddedilen iletilerdir. Hatalı biçimlendirilmiş iletiler olduğu gibi günlüğe kaydedilir: eğer öyleyse, uygun olmayan XML ile şifrelenir, ve saire. `maxSizeOfMessageToLog`cdata olarak günlüğe kaydedilecek iletinin boyutunu tanımlamıştır. Varsayılan olarak, `maxSizeOfMessageToLog` 256K eşittir. Bu öznitelik hakkında daha fazla bilgi için Diğer Seçenekler bölümüne bakın.

### <a name="other-options"></a>Diğer Seçenekler

Günlüğe kaydetme düzeylerine ek olarak, kullanıcı aşağıdaki seçenekleri belirtebilir:

- Tüm İletiyi`logEntireMessage` (öznitelik) günlüğe kaydedin: Bu değer, iletinin tamamının (ileti üstbilgisi ve gövdesi) günlüğe kaydedilip günlüğe kaydolmadığını belirtir. Varsayılan değer, `false`yalnızca üstbilginin günlüğe kaydedildiği anlamına gelir. Bu ayar hizmet ve aktarım ileti günlüğe kaydetme düzeylerini etkiler...

- Günlüğe kaydolacak`maxMessagesToLog` maksimum iletiler (öznitelik): Bu değer, günlüğe kaydolacak en fazla ileti sayısını belirtir. Tüm iletiler (hizmet, aktarım ve yanlış biçimlendirilmiş iletiler) bu kotaya dahil edilir. Kotaya ulaşıldığında, bir izleme yayımlanır ve ek ileti günlüğe kaydedilir. Varsayılan değer 10000'dir.

- Günlük için iletinin`maxSizeOfMessageToLog` maksimum boyutu (öznitelik): Bu değer, bayt oturum açmak için iletilerin maksimum boyutunu belirtir. Boyut sınırını aşan iletiler günlüğe kaydedilmez ve bu ileti için başka bir etkinlik gerçekleştirilmez. Bu ayar tüm izleme düzeylerini etkiler. ServiceModel izleme sayılmalı, kullanıcıyı bilgilendirmek için ilk günlüğe kaydetme noktasından (ServiceModelSend* veya TransportReceive) bir Uyarı düzeyi izleme saçar. Hizmet düzeyi ve aktarım düzeyi iletileri için varsayılan değer 256K iken, hatalı biçimlendirilmiş iletilerin varsayılan değeri 4K'dır.

  > [!CAUTION]
  > Karşılaştırmak için hesaplanan ileti `maxSizeOfMessageToLog` boyutu, serileştirmeden önce bellekteki ileti boyutudur. Bu boyut, günlüğe kaydedilen ileti dizesinin gerçek uzunluğundan farklı olabilir ve birçok durumda gerçek boyuttan daha büyüktür. Sonuç olarak, iletiler günlüğe kaydedilemeyebilir. Bu gerçeği, özniteliğinin `maxSizeOfMessageToLog` beklenen ileti boyutundan %10 daha büyük olduğunu belirterek açıklayabilirsiniz. Ayrıca, hatalı biçimlendirilmiş iletiler günlüğe kaydedilirse, ileti günlükleri tarafından kullanılan gerçek disk alanı, belirtilen `maxSizeOfMessageToLog`değerin 5 katına kadar olabilir.

Yapılandırma dosyasında izleme dinleyicisi tanımlanmamışsa, belirtilen günlük düzeyine bakılmaksızın günlüğe kaydetme çıktısı oluşturulmaz.

Bu bölümde açıklanan öznitelikler gibi ileti günlüğe kaydetme seçenekleri, Windows Yönetim Araçları (WMI) kullanılarak çalışma zamanında değiştirilebilir. Bu [AppDomainInfo](./wmi/appdomaininfo.md) örneğine erişerek yapılabilir, hangi bu Boolean `LogMessagesAtServiceLevel` `LogMessagesAtTransportLevel`özellikleri `LogMalformedMessages`ortaya çıkarır: , , ve . Bu nedenle, ileti günlüğe kaydetme için bir izleme dinleyicisi yapılandırırsanız, ancak bu seçenekleri `false` yapılandırmada ayarlarsanız, bunları daha sonra uygulama çalışırken değiştirebilirsiniz. `true` Bu, çalışma zamanında ileti günlüğe kaydetmeyi etkin bir şekilde sağlar. Benzer şekilde, yapılandırma dosyanızda ileti günlüğe kaydetmeyi etkinleştiriseniz, WMI kullanarak çalışma zamanında devre dışı kalabilirsiniz. Daha fazla bilgi için [bkz.](./wmi/index.md)

İleti `source` günlüğündeki alan, iletinin hangi bağlamda günlüğe kaydedildiğini belirtir: istek iletisi gönderirken/alırken, istek-yanıt veya tek yönlü istek için, hizmet modelinde veya aktarım katmanında veya yanlış biçimlendirilmiş bir ileti durumunda.

Yanlış biçimlendirilmiş iletiler için, `source` 'ye `Malformed`eşittir. Aksi takdirde, kaynak bağlamı temel alan aşağıdaki değerlere sahiptir.

İstek/Yanıt Için

||İstek Gönder|İstek Alma|Yanıt Gönder|Yanıt Al|
|-|------------------|---------------------|----------------|-------------------|
|Hizmet Modeli katmanı|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Al<br /><br /> İstek|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> Yanıtla|Hizmet<br /><br /> Düzey<br /><br /> Al<br /><br /> Yanıtla|
|Taşıma katmanı|Aktarım<br /><br /> Gönder|Aktarım<br /><br /> Al|Aktarım<br /><br /> Gönder|Aktarım<br /><br /> Al|

Tek Yönlü İstek İçin

||İstek Gönder|İstek Alma|
|-|------------------|---------------------|
|Hizmet Modeli katmanı|Hizmet<br /><br /> Düzey<br /><br /> Gönder<br /><br /> Datagram|Hizmet<br /><br /> Düzey<br /><br /> Al<br /><br /> Datagram|
|Taşıma katmanı|Aktarım<br /><br /> Gönder|Aktarım<br /><br /> Al|

## <a name="message-filters"></a>İleti Filtreleri

İleti filtreleri yapılandırma `messageLogging` bölümünün yapılandırma `diagnostics` öğesinde tanımlanır. Bunlar servis ve taşıma düzeyinde uygulanır. Bir veya daha fazla filtre tanımlandığında, yalnızca filtrelerden en az biriyle eşleşen iletiler günlüğe kaydedilir. Filtre tanımlanmamışsa, tüm iletiler geçer.

Filtreler tam XPath sözdizimini destekler ve yapılandırma dosyasında göründükleri sırada uygulanır. Sözdizimi olarak yanlış filtre yapılandırma özel durumuyla sonuçlanır.

Filtreler ayrıca, xpath DOM'daki filtreyle eşleşecek şekilde incelenebilen maksimum düğüm sayısını sınırlayan özniteliği kullanarak `nodeQuota` bir güvenlik özelliği de sağlar.

Aşağıdaki örnek, yalnızca SOAP üstbilgi bölümü olan iletileri kaydeden bir filtrenin nasıl yapılandırılabildiğini gösterir.

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

Filtreler iletinin gövdesine uygulanamaz. İletigövdesini işlemeye çalışan filtreler filtreler listesinden kaldırılır. Bunu gösteren bir olay da yayılır. Örneğin, aşağıdaki filtre filtre tablosundan kaldırılır.

```xml
<add xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">/s:Envelope/s:Body[contains(text(), "Hello")]</add>
```

## <a name="configuring-a-custom-listener"></a>Özel Dinleyici Yapılandırma

Ayrıca, özel bir dinleyiciyi ek seçeneklerle yapılandırabilirsiniz. Özel bir dinleyici, günlüğe kaydetmeden önce iletilerden uygulamaya özgü KIŞISEL öğeleri filtrelemede yararlı olabilir. Aşağıdaki örnek, özel bir dinleyici yapılandırmasını gösterir.

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

Özniteliğin `type` türün nitelikli bir derleme adı olarak ayarlanmasını gerektiğini unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [\<mesajGünlük>](../../configure-apps/file-schema/wcf/messagelogging.md)
- [Günlüğe İleti Kaydetme](message-logging.md)
- [İzleme ve İletileri Günlüğe Kaydetme için Önerilen Ayarlar](./tracing/recommended-settings-for-tracing-and-message-logging.md)
