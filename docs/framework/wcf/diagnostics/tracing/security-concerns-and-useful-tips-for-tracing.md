---
title: İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
ms.openlocfilehash: 91a1b4bab3ac47f41821ad69228310c3993cf037
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90555048"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
Bu konu başlığı altında, gizli bilgilerin sunulanlarından nasıl koruyabileceğiniz ve WebHost kullanırken yararlı olan ipuçları açıklanmaktadır.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>WebHost ile özel bir Izleme dinleyicisi kullanma  
 Kendi izleme dinleyicinizi yazıyorsanız, izlemelerin Web 'de barındırılan bir hizmette kaybolması ihtimaline dikkat etmeniz gerekir. WebHost geri dönüştürüldüğünde canlı işlemi kapatır ve yinelenen bir işlem sürer. Ancak, iki işlemin bir süredir aynı kaynağa erişimi olması gerekir, bu da dinleyici türüne bağımlıdır. Bu durumda, `XmlWriterTraceListener` ikinci işlem için yeni bir izleme dosyası oluşturur; Windows olay izleme aynı oturum içinde birden çok işlemi yönetir ve aynı dosyaya erişim sağlar. Kendi dinleyiciniz benzer işlevler sağlamıyorsa, dosya iki işlem tarafından kilitlendiğinde izlemeler kaybolabilir.  
  
 Ayrıca, özel bir İzleme dinleyicisinin, uzak bir veritabanına, örneğin, uzak bir veritabanına izleme ve mesaj gönderebildiği farkında olmanız gerekir. Bir uygulama dağıtıcı olarak, uygun erişim denetimiyle özel dinleyicileri yapılandırmanız gerekir. Ayrıca, uzak konumda açığa çıkarılabilen herhangi bir kişisel bilgi için güvenlik denetimi de uygulamalısınız.  
  
## <a name="logging-sensitive-information"></a>Gizli bilgileri günlüğe kaydetme  
 İzlemeler, bir ileti kapsamda olduğunda ileti üst bilgileri içerir. İzleme etkin olduğunda, bir sorgu dizesi gibi uygulamaya özgü üst bilgilerde kişisel bilgiler; ve kredi kartı numarası gibi gövde bilgileri günlüklerde görünür hale gelebilir. Uygulama dağıtıcı, yapılandırma ve izleme dosyalarında erişim denetimini zormaktan sorumludur. Bu tür bilgilerin görünmesini istemiyorsanız, izleme günlüklerini paylaşmak istiyorsanız izlemeyi devre dışı bırakmanız veya verilerin bir kısmını filtrelemeniz gerekir.  
  
 Aşağıdaki ipuçları, bir izleme dosyasının içeriğinin istenmeden gösterilmesini önlemeye yardımcı olabilir:  
  
- Günlük dosyalarının hem WebHost hem de Self-Host senaryolarında Access Control listeleriyle (ACL) korunduğundan emin olun.  
  
- Web isteği kullanılarak kolayca sunulamayan bir dosya uzantısı seçin. Örneğin,. xml dosya uzantısı güvenli bir seçenek değildir. Hizmet verilen uzantıların bir listesini görmek için IIS Yönetim Kılavuzu ' na bakabilirsiniz.  
  
- Bir Web tarayıcısı kullanarak bir dış tarafın erişmesini engellemek için, WebHost vroot ortak dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, Kullanıcı adı ve parola gibi anahtarlar ve kişisel bilgiler (PII), izlemelerde ve günlüğe kaydedilen iletilerde günlüğe kaydedilmez. Ancak Makine Yöneticisi, `enableLoggingKnownPII` `machineSettings` makinede çalışan uygulamaların bilinen kişisel olarak tanımlanabilen BILGILERI (PII) şu şekilde günlüğe kaydetmek için Machine.config dosyasının öğesindeki özniteliğini kullanabilir:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
</configuration>
```  
  
 Daha sonra bir uygulama dağıtıcısı, `logKnownPii` aşağıdaki gıbı PII günlüğünü etkinleştirmek için App.config ya da Web.config dosyasında özniteliğini kullanabilir:  
  
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
  
 Yalnızca her iki ayar de `true` PII günlüğü etkin olduğunda. İki anahtar birleşimi, her bir uygulama için bilinen PII 'yi günlüğe kaydetme esnekliğini sağlar.  
  
 Bir yapılandırma dosyasında iki veya daha fazla özel kaynak belirtirseniz, yalnızca ilk kaynağın özniteliklerinin okunup okunduğuna dikkat edin. Diğerleri yok sayılır. Diğer bir deyişle, aşağıdaki App.config, dosya, PII her iki kaynak için de PII günlüğü, ikinci kaynak için açık olarak etkinleştirilmiş olsa da bu şekilde günlüğe kaydedilmez.  
  
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
  
 `<machineSettings enableLoggingKnownPii="Boolean"/>`Öğe Machine.config dosyanın dışında varsa, sistem bir oluşturur <xref:System.Configuration.ConfigurationErrorsException> .  
  
 Değişiklikler yalnızca uygulama başlatıldığında veya yeniden başlatıldığında geçerli olur. Her iki öznitelik olarak ayarlandığında bir olay başlangıçta günlüğe kaydedilir `true` . Bir olay, `logKnownPii` olarak ayarlanmışsa günlüğe kaydedilir `true` `enableLoggingKnownPii` `false` .  
  
 PII günlüğü hakkında daha fazla bilgi için bkz. [PII güvenlik kilitleme](../../samples/pii-security-lockdown.md) örneği.  
  
 Makine Yöneticisi ve uygulama dağıtıcı, bu iki anahtarı kullanırken çok dikkatli olmalıdır. PII günlüğü etkinse, güvenlik anahtarları ve PII günlüğe kaydedilir. Devre dışıysa, hassas ve uygulamaya özgü veriler hala ileti üstbilgilerinde ve gövdede günlüğe kaydedilir. Gizlilikle ilgili daha kapsamlı bir tartışma ve PII 'nin gösterilmesini sağlama hakkında daha fazla bilgi için bkz. [Kullanıcı gizliliği](/previous-versions/dotnet/articles/aa480490(v=msdn.10)).  
  
 Buna ek olarak, ileti göndericisinin IP adresi bağlantı yönelimli aktarımlar için bağlantı başına bir kez günlüğe kaydedilir ve aksi takdirde ileti başına bir kez gönderilir. Bu, gönderen onay olmadan yapılır. Ancak, bu günlük yalnızca, canlı hata ayıklama haricinde, üretim ortamında varsayılan veya önerilen izleme düzeyleri olmayan bilgi veya ayrıntılı izleme düzeylerinde oluşur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](index.md)
