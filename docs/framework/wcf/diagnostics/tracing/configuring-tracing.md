---
title: "İzlemeyi Yapılandırma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
caps.latest.revision: "53"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3beeaec1ed9982fc49f6bf81e2717db862e7882f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-tracing"></a>İzlemeyi Yapılandırma
Bu konuda nasıl izlemeyi etkinleştirmek, izlemeleri ve kümesi izleme düzeyleri, kümesi Etkinlik izleme ve uçtan uca izleme bağıntı desteklemek için yayma yaymak üzere izleme kaynakları yapılandırabilir ve izlemeleri erişmek için izleme dinleyicileri ayarlama açıklanmaktadır.  
  
 Üretim veya hata ayıklama ortamında izleme ayarları önerileri için bkz [izleme ve ileti günlüğe kaydetme için önerilen ayarları](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  Windows 8'de izleme günlükleri oluşturmak, uygulamanız için sırayla, uygulama yükseltilmiş (yönetici olarak çalıştır) çalıştırmanız gerekir.  
  
## <a name="enabling-tracing"></a>İzlemeyi etkinleştirme  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]Aşağıdaki Tanılama izleme verilerini çıkarır:  
  
-   Özel durumlar, uyarılar ve diğer önemli bir işleme olayları işlem kilometre taşları gibi işlem çağrıları uygulamalarının tüm bileşenleri arasında izlemelerini kodu.  
  
-   Windows hata olaylarını izleme özelliği düzgün olduğunda. Bkz: [olay günlüğü](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]İzleme üstünde oluşturulan <xref:System.Diagnostics>. İzlemeyi kullanmak için yapılandırma dosyası veya kod izleme kaynakları tanımlamanız gerekir. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]her biri için bir izleme kaynağını tanımlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] derleme. `System.ServiceModel` İzleme kaynağıdır en genel [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] izleme kaynağını ve kayıtları arasında kilometre taşları işleme [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] iletişimi yığınından kullanıcı kodu girme/bırakmak için Aktarım girme ve çıkılıyor. `System.ServiceModel.MessageLogging` İzleme kaynağını sistem üzerinden akan tüm iletileri kaydeder.  
  
 İzleme varsayılan olarak etkin değildir. İzlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturmak ve yapılandırmada dışında "Kapalı" Seçili izleme kaynağı için izleme düzeyi; Aksi takdirde, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] herhangi izlemeleri oluşturmaz. Dinleyici belirtmezseniz, izleme otomatik olarak devre dışı bırakıldı. Dinleyici tanımlı, ancak hiçbir düzeyi belirtilen düzeyi "Kapalı için" hiçbir izleme yayınlanır anlamı varsayılan olarak ayarlanır.  
  
 Kullanırsanız [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] özel işlem invokers gibi genişletilebilirlik noktaları kendi izleri yayma. Genişletilebilirlik noktanız uygulamak, bunun nedeni, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] artık varsayılan yolda standart izleri yayma. Verme izlemeler tarafından el ile izleme desteği uygulamaz, beklediğiniz izlemeleri göremeyebilirsiniz.  
  
 Uygulama yapılandırma dosyasını düzenleyerek izlemeyi yapılandırabilirsiniz — her iki Web.config Web barındırılan uygulamalar veya Appname.exe.config kendini barındıran uygulamalar için. Aşağıdakiler, bu tür düzenleme bir örnektir. Bu ayarlar hakkında daha fazla bilgi için "Yapılandırma izleme dinleyicileri için tüketen izlemeleri" bölümüne bakın.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Yapılandırma dosyasını düzenlemek için bir [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] hizmet projesinde [!INCLUDE[vs_current_short](../../../../../includes/vs-current-short-md.md)], uygulamanın yapılandırma dosyasına sağ tıklayın — ya da Web.config Web barındırılan uygulamalar veya kendi kendini barındıran uygulamada Appname.exe.config  **Çözüm Gezgini**. Ardından **WCF yapılandırmasını Düzenle** bağlam menüsü öğesini. Bu başlatır [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), yapılandırma ayarlarını değiştirmenizi sağlayan [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] bir grafik kullanıcı arabirimini kullanarak hizmetleri.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>İzlemeler yaymak üzere izleme kaynaklarını yapılandırma  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]İzleme kaynağı her derlemesi için tanımlar. Bir derlemenin içinde oluşturulan izlemeleri, bu kaynak için tanımlanan dinleyicileri tarafından erişilir. Aşağıdaki izleme kaynakları tanımlanmıştır:  
  
-   System.ServiceModel: tüm aşamalarında günlüklerini [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] işleme yapılandırma salt okunur olduğunda, bir ileti taşımasına işlenir, kullanıcı kodu ve benzeri işleme, güvenlik bir ileti gönderilir.  
  
-   System.ServiceModel.MessageLogging: sistem üzerinden akan tüm iletileri günlüğe kaydeder.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Ortak günlük File System (CLFS) için .NET Framework arabirimin günlüğü.  
  
-   System.Runtime.Serialization: nesneleri okunabilir veya yazılabilir olduğunda günlüğe kaydedilir.  
  
-   CardSpace.  
  
 Aşağıdaki yapılandırma örnekte gösterildiği gibi her izleme kaynağı aynı (paylaşılan) dinleyici kullanmak için yapılandırabilirsiniz.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Ayrıca, kullanıcı kodu izleri yayma için aşağıdaki örnekte, gösterildiği gibi kullanıcı tanımlı izleme kaynakları ekleyebilirsiniz.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]İzleme kaynakları kullanıcı tanımlı oluşturmak için bkz: [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>İzleme dinleyicileri izlemeleri kullanmak için yapılandırma  
 Çalışma zamanında [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] akışları izleme verileri işleyen dinleyicileri verileri. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]birçok önceden tanımlı dinleyiciler için sağlar <xref:System.Diagnostics>, çıktı için kullandıkları biçiminde farklı. Özel dinleyicisi türleri de ekleyebilirsiniz.  
  
 Kullanabileceğiniz `add` adını ve kullanmak istediğiniz İzleme dinleyicisi türünü belirtmek için. Bizim örnek yapılandırma biz dinleyicisi adlı `traceListener` ve standart .NET Framework İzleme dinleyicisi eklenir (`System.Diagnostics.XmlWriterTraceListener`) istiyoruz kullanılacak türü. İzleme dinleyicileri her kaynağı için herhangi bir sayıda ekleyebilirsiniz. Dosya İzle İzleme dinleyicisi yayar, yapılandırma dosyasında çıktı dosya konumunu ve adını belirtmeniz gerekir. Bu ayarlayarak yapılır `initializeData` bu dinleyici dosyasının adı. Bir dosya adı belirtmezseniz, rasgele bir dosya adı kullanılan dinleyicisi türüne göre oluşturulur. Varsa <xref:System.Diagnostics.XmlWriterTraceListener> olan kullanıldığında, bir dosya adı uzantısı ile oluşturulur. Özel bir dinleyici uygularsanız, bu öznitelik bir dosya adı dışında başlatma veri almak için kullanabilirsiniz. Örneğin, bu öznitelik için bir veritabanı tanımlayıcı belirtebilirsiniz.  
  
 İzlemeler hattaki, örneğin, uzak bir veritabanına göndermek için bir özel İzleme dinleyicisi yapılandırabilirsiniz. Bir uygulama dağıtıcı uzak makinede izleme günlükleri uygun erişim denetimini zorunlu.  
  
 İzleme dinleyicisi programlı olarak da yapılandırabilirsiniz. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Nasıl yapılır: oluşturma ve başlatma izleme dinleyicileri](http://go.microsoft.com/fwlink/?LinkId=94648) ve [özel TraceListener oluşturma](http://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Çünkü `System.Diagnostics.XmlWriterTraceListener` olan değil iş parçacığı, izleme kaynağı kaynakları özel olarak izlemeleri alırken kilitlemek. Kaynak çakışması ortaya çıkabilir, bu dinleyiciyi kullanmak üzere yapılandırılmış bir izleme kaynağına izlemeleri birçok iş parçacığı çıkış olduğunda, bir önemli performans sorunu sonuçlanır. Bu sorunu gidermek için iş parçacığı özel bir dinleyici uygulamanız gerekir.  
  
## <a name="trace-level"></a>İzleme düzeyi  
 İzleme düzeyini tarafından denetlenen `switchValue` izleme kaynağını ayarlama. Kullanılabilir izleme düzeyleri aşağıdaki tabloda açıklanmıştır.  
  
|İzleme düzeyi|İzlenen olayların yapısı|İzlenen olayların içeriği|İzlenen olayları|Kullanıcı hedef|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Kapalı|Yok|Yok|Hiçbir izlemeleri gösterilen.|Yok|  
|Kritik|"Negatif" olayları: beklenmeyen bir işlem veya bir hata koşulu belirten olaylar.||İşlenmeyen özel durumlar aşağıdakiler de dahil olmak üzere kaydedilir:<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (CLR herhangi ThreadAbortExceptionHandler çağırır)<br />-StackOverflowException (yakalanan olamaz)<br />-ConfigurationErrorsException<br />-SEHException<br />-Uygulama başlatma hataları<br />-Failfast olayları<br />-Sistem kilitlendi<br />-Zehirli ileti: uygulamanın başarısız olmasına neden izlemeleri iletisi.|Yöneticiler<br /><br /> Uygulama geliştiricilerinin|  
|Hata|"Negatif" olayları: beklenmeyen bir işlem veya bir hata koşulu belirten olaylar.|Beklenmeyen işlem gerçekleştirilmedi. Uygulamanın beklendiği gibi bir görevi gerçekleştirmek mümkün değildi. Ancak, uygulama hala çalışır durumda.|Tüm özel durumları günlüğe kaydedilir.|Yöneticiler<br /><br /> Uygulama geliştiricilerinin|  
|Uyarı|"Negatif" olayları: beklenmeyen bir işlem veya bir hata koşulu belirten olaylar.|Olası bir sorun oluştu veya, uygulama hala işlevleri doğru oluşabilir. Ancak, bunu düzgün çalışması devam.|-Uygulama azaltma ayarlarının izin verilenden daha fazla isteklerini alıyor.<br />-Alıcı kuyruk kapasitesinin üst sınırına yapılandırılmış ' dir.<br />-Zaman aşımını aştı.<br />-Kimlik bilgilerini reddetti.|Yöneticiler<br /><br /> Uygulama geliştiricilerinin|  
|Bilgiler|"Pozitif" olayları: başarılı kilometre taşları işaretlemek olayları|Başarılı ve önemli kilometre taşları uygulama yürütmenin uygulama değil veya düzgün çalışıyor.|Genel olarak, ileti izleme ve sistem durumu Tanılama, performansını ölçmek veya profil oluşturma için yararlı üretilir. İçin kapasite planlama ve performans yönetimi gibi bilgileri kullanabilirsiniz:<br /><br /> -Kanalları oluşturulur.<br />-Bitiş noktası dinleyicileri oluşturulur.<br />-İleti girer/taşıma bırakır.<br />-Güvenlik belirteci alınır.<br />-Yapılandırma ayarı okuyun.|Yöneticiler<br /><br /> Uygulama geliştiricilerinin<br /><br /> Ürün geliştiriciler.|  
|Ayrıntılı|"Pozitif" olayları: başarılı kilometre taşları işaretlemek olaylar.|Kullanıcı kodu ve bakım için düşük düzey olayları gösterilen.|Genel olarak, bu düzey hata ayıklama veya uygulama iyileştirme için kullanabilirsiniz.<br /><br /> -İleti üstbilgisi anlaşıldı.|Yöneticiler<br /><br /> Uygulama geliştiricilerinin<br /><br /> Ürün geliştiriciler.|  
|ActivityTracing||İşlem etkinlikleri ve bileşenler arasındaki akış olaylar.|Bu düzey, Yöneticiler ve geliştiriciler uygulamalar aynı uygulama etki alanındaki ilişkilendirmenize olanak sağlar:<br /><br /> -Başlat/Durdur gibi etkinlik sınırları izlemelerini.<br />-Aktarımları için izlemeleri.|Tümü|  
|Tümü||Uygulama düzgün çalışmayabilir. Tüm olayları gösterilen.|Tüm önceki olayları.|Tümü|  
  
 Ayrıntı düzeylerinden kritik için diğer üstünde yığılma, diğer bir deyişle, her izleme düzeyi Off düzeyi dışında yukarıdaki tüm düzeyleri içerir. Örneğin, uyarı düzeyinde dinleme dinleyici kritik, hata ve uyarı izlemeleri alır. Tüm düzey ayrıntılı olaylarına kritik ve etkinlik izleme olaylarını içerir.  
  
> [!CAUTION]
>  Bilgi ve Verbose ActivityTracing düzeyleri çok fazla makinedeki tüm kullanılabilir kaynakları kullandıysanız, ileti işleme olumsuz yönde etkileyebilir izlerini oluşturur.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Etkinlik izleme ve yayma bağıntı için yapılandırma  
 `activityTracing` İçin belirtilen değer `switchValue` özniteliği etkinlik sınırları ve uç noktaları içinde aktarımları için izlemeleri yayar etkinlik izlemeyi etkinleştirmek için kullanılır.  
  
> [!NOTE]
>  Belirli genişletilebilirlik özellikleri kullandığınızda [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], get bir <xref:System.NullReferenceException> Etkinlik izleme etkin olduğunda. Bu sorunu gidermek için uygulamanızın yapılandırma dosyasını denetleyin ve emin `switchValue` izleme kaynağınız ayarlanmazsa özniteliğinin `activityTracing`.  
  
 `propagateActivity` Öznitelik, etkinlik ileti Exchange'de katılmak diğer uç noktalar olarak yayıldığı olup olmadığını gösterir. Bu değer ayarlayarak `true`, iki uç nokta tarafından oluşturulan izleme dosyaları alabilir ve nasıl başka bir uç noktada izlemeleri kümesi için bir uç noktada izlemeleri kümesi aktarılan inceleyin.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]Etkinlik izleme ve yayma, bkz: [yayma](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Her ikisi de `propagateActivity` ve `ActivityTracing` Boole değerleri System.ServiceModel TraceSource uygulayın. `ActivityTracing` Değeri herhangi bir izleme kaynağını için de geçerlidir dahil olmak üzere [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] veya kullanıcı tanımlı olanlar.  
  
 Kullanamazsınız `propagateActivity` özniteliği kullanıcı tanımlı izleme kaynakları ile. Kullanıcı kodu etkinlik kimliği yayma için ServiceModel ayarlamayın emin olun `ActivityTracing`, ServiceModel yaşamaya sırasında `propagateActivity` özniteliği kümesine `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Nasıl yapılır: İzleme Dinleyicileri Oluşturma ve Başlatma](http://go.microsoft.com/fwlink/?LinkId=94648)  
 [Özel TraceListener oluşturma](http://go.microsoft.com/fwlink/?LinkId=96239)
