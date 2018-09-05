---
title: İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
ms.date: 03/30/2017
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ccb16a0996386f3518bc52e95c1892c56e8bbad2
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43512631"
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
Bu konuda, WebHost kullanırken faydalı ipuçları yanı sıra açıklanmasını hassas bilgileri nasıl Koruyabileceğiniz açıklanmaktadır.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>WebHost ile Özel İzleme dinleyicisi kullanma  
 Kendi İzleme dinleyicisi yazıyorsanız, bir Web servisinin söz konusu olduğunda izlemeleri kaybolabilir geliştiriciyi olmalıdır. WebHost geri dönüştürüldüğünde, yinelenen devralıyor ancak Canlı işlemi kapatır. Ancak, iki işlem dinleyici türde bağımlı bir süre için hala aynı kaynağa erişimi olmalıdır. Bu durumda, `XmlWriterTraceListener` Windows olay izleme aynı oturumunda birden çok işlem yönetir ve aynı dosyaya erişim sunar; ikinci işlem için yeni bir izleme dosyası oluşturur. Kendi dinleyici benzer işlevleri sağlamıyorsa, dosyanın iki işlem tarafından kilitli değilken izlemeleri kaybolabilir.  
  
 Özel İzleme dinleyicisi izlemeleri ve iletileri kablo, örneğin, bir uzak veritabanına gönderebildiğini farkında olmalıdır. Bir uygulama dağıtıcı uygun erişim denetimi ile özel dinleyicileri yapılandırmanız gerekir. Ayrıca, uzak konumu gösterilen herhangi bir kişisel bilgi denetimde güvenlik uygulamanız gerekir.  
  
## <a name="logging-sensitive-information"></a>Hassas bilgi günlük kaydı  
 Kapsam içinde bir ileti olduğunda ileti üstbilgileri izlemelerini içerir. İzleme etkin olduğunda, uygulamaya özgü üstbilgiler, sorgu dizesi gibi kişisel bilgileri; ve kredi kartı numarası gibi bilgileri gövde, günlüklerde görünür hale gelebilir. Uygulama dağıtıcısı, yapılandırma ve izleme dosyaları üzerinde erişim denetimi uygulamaktan sorumludur. Bu tür bilgilerin görünür olmasını istemiyorsanız, izlemeyi devre dışı bırakmak veya verilerin bir kısmını izleme günlükleri paylaşmak istiyorsanız filtre gerekir.  
  
 Aşağıdaki ipuçları bir izleme dosyası içeriğini istenmeden açıklanmasını önlemenize yardımcı olabilir:  
  
-   Günlük dosyaları tarafından erişim denetim listeleri (ACL) WebHost ve barındırma senaryolarında korunan emin olun.  
  
-   Bir Web isteği sunularak kolayca sunulamayan bir dosya uzantısı'nı seçin. Örneğin, .xml dosya uzantısı güvenli bir seçenek değil. Sunulabilecek uzantıların listesini görmek için IIS Yönetim kılavuzuna bakabilirsiniz.  
  
-   Bir Web tarayıcısı kullanılarak harici bir tarafça erişilmesini önlemek için WebHost vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, anahtarları ve kullanıcı adı ve parola gibi kişisel bilgileri (PII) izlemeleri günlüğe kaydedilmez ve iletileri günlüğe. Bir makine yöneticisinin ancak kullanabilirsiniz `enableLoggingKnownPII` özniteliğini `machineSettings` makine üzerinde çalışan uygulamalar, bilinen kişisel bilgileri (PII) aşağıdaki gibi oturum izin vermek için Machine.config dosyasının öğesi:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Varsa `<machineSettings enableLoggingKnownPii="Boolean"/>` öğesi Machine.config dosyasının dışında var, sistem oluşturur bir <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Uygulama başlatıldığında veya yeniden değişiklikleri etkili olur. Her iki öznitelik ayarlandığında başlangıçta bir olay kaydedilir `true`. Bir olay, ayrıca kaydedilir `logKnownPii` ayarlanır `true` ancak `enableLoggingKnownPii` olduğu `false`.  
  
 PII günlüğe kaydetme hakkında daha fazla bilgi için bkz. [PII güvenlik kilidi](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) örnek.  
  
 Makine Yöneticisi ve uygulama dağıtıcı aşırı bu iki anahtar kullanırken dikkatli. PII günlüğe kaydetme etkinleştirilmişse, güvenlik anahtarları ve PII günlüğe kaydedilir. Etkinleştirilirse, hala ileti üstbilgileri ve gövdeleri hassas ve uygulamaya özgü veriler günlüğe kaydedilir. Gizlilik ve açıklanmasını PII koruma hakkında daha kapsamlı bir açıklama için bkz: [kullanıcı gizliliğini](https://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Ayrıca, iletiyi gönderenin IP adresi, bir kez bağlantı tabanlı aktarımlar için bağlantı başına ve bir kez aksi gönderilen ileti başına kaydedilir. Bu gönderen rızası gerçekleştirilir. Ancak, bu günlük yalnızca, varsayılan olmayan ya da önerilen izlemenin düzeylerin, üretimde dışında hata ayıklama Canlı bilgi veya ayrıntılı izleme düzeyleri gerçekleşir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
