---
title: İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 5ced4f3a3a5e83564703db88b28ee2b3c6eeb1a0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185715"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
Bu konu, WebHost kullanırken hassas bilgilerin maruz kalmalarını nasıl koruyabileceğinizi ve yararlı ipuçlarını açıklar.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>WebHost ile Özel İzleme Dinleyicisi Kullanma  
 Kendi izleme dinleyicinizi yazıyorsanız, Web tarafından barındırılan bir hizmet durumunda izlemelerin kaybolabileceği olasılığının farkında olmalısınız. WebHost yeniden dönüştürdüğünde, yinelenen bir işlem devralırken canlı işlemi kapatır. Ancak, iki işlem yine de dinleyici türüne bağlı bir süre için aynı kaynağa erişimi olmalıdır. Bu durumda, `XmlWriterTraceListener` ikinci işlem için yeni bir izleme dosyası oluşturur; Windows olay izleme aynı oturum içinde birden çok işlemi yönetir ve aynı dosyaya erişim sağlar. Kendi dinleyiciniz benzer işlevler sağlamazsa, dosya iki işlem tarafından kilitlendiğinde izlemeler kaybolabilir.  
  
 Özel izleme dinleyicisinin, örneğin kablodaki izlemeleri ve iletileri uzak bir veritabanına gönderebileceğini de unutmayın. Bir uygulama dağıtıcısı olarak, uygun erişim denetimi ile özel dinleyici yapılandırmanız gerekir. Ayrıca, uzak konumda açığa çıkabilen herhangi bir kişisel bilgi üzerinde güvenlik kontrolü uygulamalısınız.  
  
## <a name="logging-sensitive-information"></a>Hassas Bilgileri Günlüğe Kaydetme  
 İleti kapsam dayken izlemeler ileti üstbilgileri içerir. İzleme etkinleştirildiğinde, bir sorgu dizesi gibi uygulamaya özgü üstbilgilerdeki kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görülebilir. Uygulama dağıtıcı, yapılandırma ve izleme dosyaları üzerinde erişim denetimini zorlamakiçin sorumludur. Bu tür bilgilerin görünür olmasını istemiyorsanız, izleme günlüğünü paylaşmak istiyorsanız izlemeyi devre dışı bırakmanız veya verilerin bir kısmını filtrelemeniz gerekir.  
  
 Aşağıdaki ipuçları, izleme dosyasının içeriğinin istemeden açığa çıkarOlmasını önlemenize yardımcı olabilir:  
  
- Günlük dosyalarının hem WebHost'ta hem de kendi barındırma senaryolarında Access Control Lists (ACL) tarafından korunduğundan emin olun.  
  
- Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin. Örneğin, .xml dosya uzantısı güvenli bir seçim değildir. Servis edilebilen uzantıların listesini görmek için IIS yönetim kılavuzunu kontrol edebilirsiniz.  
  
- Web tarayıcısı kullanan harici bir taraf tarafından erişmesini önlemek için WebHost vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, kullanıcı adı ve parola gibi anahtarlar ve kişisel olarak tanımlanabilir bilgiler (PII) izlemelerde ve günlüğe kaydedilmiş iletilerde günlüğe kaydedilmez. Ancak bir makine yöneticisi, `enableLoggingKnownPII` Machine.config `machineSettings` dosyasının öğesindeki özniteliği kullanarak makinede çalışan uygulamaların bilinen kişisel olarak tanımlanabilir bilgileri (PII) aşağıdaki gibi günlüğe kaydetmesini sağlayabilir:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 `<machineSettings enableLoggingKnownPii="Boolean"/>` Öğe Machine.config dosyasının dışında varsa, sistem <xref:System.Configuration.ConfigurationErrorsException>bir .  
  
 Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında etkili dir. Her iki öznitelik de `true`'' de ayarlandığında, bir olay başlangıçta günlüğe kaydedilir. Bir olay, ayarlanmış `logKnownPii` `true` ancak `enableLoggingKnownPii` . `false`  
  
 KIŞISEL bilgiler hakkında daha fazla bilgi [için, KIŞISEL Güvenlik Kilitleme](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) örneğine bakın.  
  
 Makine yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır. Kişisel günlük etkinse, güvenlik anahtarları ve KIŞISEL bilgiler günlüğe kaydedilir. Devre dışı bırakılmışsa, duyarlı ve uygulamaya özgü veriler ileti üstbilgileri ve gövdelerinde günlüğe kaydedilir. Gizlilik ve kişisel bilgilerin açığa çıkarılmaktan korunması konusunda daha kapsamlı bir tartışma için [Bkz.](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480490(v=msdn.10))  
  
 Ayrıca, ileti gönderenin IP adresi bağlantı yönelimli taşımalar için bağlantı başına bir kez ve aksi takdirde gönderilen ileti başına bir kez günlüğe kaydedilir. Bu gönderenin rızası olmadan yapılır. Ancak, bu günlüğe kaydetme yalnızca, canlı hata ayıklama dışında varsayılan veya önerilen izleme düzeyleri olmayan Bilgi veya Verbose izleme düzeylerinde gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
