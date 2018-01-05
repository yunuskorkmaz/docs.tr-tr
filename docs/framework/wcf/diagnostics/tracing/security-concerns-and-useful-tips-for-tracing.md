---
title: "İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88bc2880-ecb9-47cd-9816-39016a07076f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4c6916333d1efa99ba1c4a9d75d80be2193e8698
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-concerns-and-useful-tips-for-tracing"></a>İzleme için Güvenlikle İlgili Noktalar ve Faydalı İpuçları
Bu konuda, hem de WebHost kullanırken yararlı ipuçları açıklanmasını hassas bilgileri nasıl koruyabilirim açıklanmaktadır.  
  
## <a name="using-a-custom-trace-listener-with-webhost"></a>Özel İzleme dinleyicisi WebHost ile kullanma  
 Kendi İzleme dinleyicisi yazıyorsanız, izlemeleri Web barındırılan hizmet durumunda kaybolabilir olasılığı haberdar olmanız gerekir. WebHost dönüştürüldüğünde yinelenen devreye girer ederken dinamik işlemi kapatır. Ancak, iki işlem dinleyicisi türüne bağlıdır süre için hala aynı kaynağa erişim izni olmalıdır. Bu durumda, `XmlWriterTraceListener` Windows olay izleme aynı oturumunda birden çok işlem yönetir ve aynı dosyaya erişim verir ancak ikinci işlem için; yeni bir izleme dosyası oluşturur. Kendi dinleyicisi benzer işlevler sağlamıyorsa, dosyanın iki işlem tarafından kilitli olduğunda izlemeleri kaybolabilir.  
  
 Özel İzleme dinleyicisi izlemeleri ve iletileri hattaki, örneğin, uzak bir veritabanına gönderebildiğini farkında olmalıdır. Bir uygulama dağıtıcı uygun erişim denetimi ile özel dinleyicileri yapılandırmanız gerekir. Ayrıca, uzak konumda verilebilen herhangi bir kişisel bilgi güvenlik denetimi uygulamalısınız.  
  
## <a name="logging-sensitive-information"></a>Hassas bilgileri günlüğe kaydetme  
 Bir ileti kapsamda olduğunda izlemeleri ileti üstbilgilerini içerir. İzleme etkinleştirildiğinde, uygulamaya özgü üstbilgiler, sorgu dize gibi kişisel bilgilerinizi; ve kredi kartı numarası gibi bilgileri gövde, günlüklerde görünür hale gelebilir. Erişim denetimini yapılandırma ve izleme dosyaları uygulama için uygulama dağıtıcı sorumludur. Bu tür bilgilerin görünür olmasını istemiyorsanız, izlemeyi devre dışı bırakmak veya izleme günlüklerini paylaşmak istiyorsanız verilerin bir kısmını filtre gerekir.  
  
 Aşağıdaki ipuçları bir izleme dosyası içeriğini istenmeden açıklanmasını önlemeye yardımcı olabilir:  
  
-   Tarafından erişim denetim listeleri (ACL) hem de WebHost ve kendi kendini barındıran senaryoları korunan dosyaları günlük emin olun.  
  
-   Web isteği kullanarak kolayca sunulamıyor bir dosya uzantısı seçin. Örneğin, .xml dosya uzantısı güvenli bir seçenek değil. Sunulabilecek uzantıların listesini görmek için IIS Yönetim kılavuzuna bakabilirsiniz.  
  
-   Bir Web tarayıcısı kullanılarak harici bir tarafça erişilmesini önlemek için WebHost vroot genel dizininin dışında olması gereken günlük dosyası konumu için mutlak bir yol belirtin.  
  
 Varsayılan olarak, anahtarları ve kullanıcı adı ve parola gibi kişisel bilgileri (PII) içindeki oturum açmadığı ve iletileri günlüğe. Bir Makine Yöneticisi, ancak kullanabilirsiniz `enableLoggingKnownPII` özniteliğini `machineSettings` makinede çalışan uygulamaların bilinen kişisel bilgileri (PII) gibi oturum izin vermek için Machine.config dosyasının öğesi:  
  
```xml  
<configuration>  
   <system.ServiceModel>  
      <machineSettings enableLoggingKnownPii="Boolean"/>  
   </system.ServiceModel>  
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
            <add name="xml" />  
         </listeners>  
      </source>  
  </sources>  
</system.diagnostics>  
```  
  
 Varsa `<machineSettings enableLoggingKnownPii="Boolean"/>` öğesi dışında Machine.config dosyasının var, sistem oluşturur bir <xref:System.Configuration.ConfigurationErrorsException>.  
  
 Uygulama başlatıldığında veya yeniden başlatır değişiklikler etkili olur. Her iki öznitelik ayarlandığında bir olay başlangıçta kaydedilir `true`. Bir olay, ayrıca kaydedilir `logKnownPii` ayarlanır `true` ancak `enableLoggingKnownPii` olan `false`.  
  
 PII günlüğe kaydetme hakkında daha fazla bilgi için bkz: [PII güvenlik kilidi](../../../../../docs/framework/wcf/samples/pii-security-lockdown.md) örnek.  
  
 Makine Yöneticisi ve bu iki anahtar kullanıldığında, uygulama dağıtıcı son derece dikkatli olun çalışma. PII günlüğe kaydetme işlemi etkinleştirilmişse, güvenlik anahtarlarını ve PII günlüğe kaydedilir. Devre dışı ise, hala ileti üstbilgilerini ve gövdeleri hassas ve uygulamaya özgü veriler günlüğe kaydedilir. Gizlilik ve maruz kalma PII koruma daha kapsamlı bir açıklama için bkz: [kullanıcı gizliliği](http://go.microsoft.com/fwlink/?LinkID=94647).  
  
 Ayrıca, IP adresi iletiyi gönderenin kez bağlantı yönelimli taşıma için bağlantısı ve başına bir kez aksi gönderilen ileti günlüğe kaydedilir. Bu gönderen izniniz olmadan gerçekleştirilir. Ancak, bu günlük yalnızca, varsayılan olmayan ya da izleme düzeylerini üretim, önerilen dışında hata ayıklama Canlı bilgi veya ayrıntılı izleme düzeyde oluşur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
