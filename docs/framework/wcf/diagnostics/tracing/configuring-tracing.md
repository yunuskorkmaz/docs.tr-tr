---
title: İzlemeyi Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: 8702091c185ba3d4956d3bd5d13ca191c12fce82
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59162887"
---
# <a name="configuring-tracing"></a>İzlemeyi Yapılandırma
Bu konuda nasıl izlemeyi etkinleştirmek, izlemeleri ve küme izleme düzeylerini kümesi Etkinlik izleme ve uçtan uca izleme bağıntı desteklemek için yayma yaymak için izleme kaynakları yapılandırabilir ve izlemeleri erişmek için izleme dinleyicilerine ayarlama açıklanmaktadır.  
  
 Üretim veya hata ayıklama ortamında izleme ayarları önerileri için başvurmak [izleme ve ileti günlüğe kaydetme için önerilen ayarlar](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  Windows 8'de izleme günlükleri oluşturmak, uygulamanın, uygulama yükseltilmiş (yönetici olarak çalıştır) çalıştırmanız gerekir.  
  
## <a name="enabling-tracing"></a>İzlemeyi etkinleştirme  
 Windows Communication Foundation (WCF) aşağıdaki tanılama izleme verilerini çıkarır:  
  
-   Özel durumlar, uyarılar ve diğer önemli işlem yüküyle olayları izlemeler işlem çağrıları gibi uygulamaların tüm bileşenleri arasında işlem kilometre taşları için kod.  
  
-   Windows hata olaylarını izleme özelliği yanlış olduğunda. Bkz: [olay günlüğü](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 WCF izleme üzerine kurulmuştur <xref:System.Diagnostics>. İzlemeyi kullanmak için yapılandırma dosyası veya kod iz kaynakları tanımlamanız gerekir. WCF her WCF derleme için bir izleme kaynağı tanımlar. `System.ServiceModel` İzleme kaynağı en genel WCF izleme kaynağı ve WCF iletişim yığını kullanıcı kodu girme/bırakmak için taşıma girme/bırakarak genelinde işleme kilometre taşları kaydeder. `System.ServiceModel.MessageLogging` İzleme kaynağı sistem üzerinden akan tüm iletileri kaydeder.  
  
 İzleme varsayılan olarak etkin değildir. İzlemeyi etkinleştirmek için bir izleme dinleyicisi oluşturun ve yapılandırmada dışında "Kapalı" Seçili iz kaynağı için izleme düzeyi; Aksi takdirde, WCF, tüm izlemeleri oluşturmaz. Dinleyici belirtmezseniz, izleme otomatik olarak devre dışı bırakıldı. Dinleyici tanımlanır, ancak hiçbir düzeyi belirtilen düzeyi "Off olarak" izleme yok yayıldığını anlamına gelir. varsayılan olarak ayarlanır.  
  
 WCF genişletilebilirlik noktaları gibi özel işlemi invokers kullanırsanız, kendi izlemeleri yayma. WCF genişletilebilirlik noktası uygularsanız, artık varsayılan yol standart izlemelerinde gönderebilir olmasıdır. Yayan izlemeleri tarafından el ile izleme desteği uygulamaz, beklediğiniz izlemeleri göremeyebilirsiniz.  
  
 Uygulama yapılandırma dosyasını düzenleyerek izlemeyi yapılandırabilirsiniz — ya da Web.config barındırılan Web uygulamaları veya Appname.exe.config şirket içinde barındırılan uygulamalar için. Bu düzen örneği verilmiştir. Bu ayarlar hakkında daha fazla bilgi için "Yapılandırma izleme dinleyicileri için tüketen Traces" bölümüne bakın.  
  
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
>  Visual Studio'da bir WCF Hizmeti projesinin yapılandırma dosyasını düzenlemek için uygulamanın yapılandırma dosyasını sağ tıklatın — ya da Web.config barındırılan Web uygulamaları veya şirket içinde barındırılan bir uygulamada için Appname.exe.config **Çözüm Gezgini** . Ardından **WCF yapılandırmasını Düzenle** bağlam menüsü öğesi. Böylece [Yapılandırma Aracı (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), bir grafik kullanıcı arabirimi kullanarak WCF hizmetleri için yapılandırma ayarlarını değiştirmenizi sağlar.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Yapılandırma izleme kaynakları izlemeleri yayma  
 WCF her derleme için bir izleme kaynağı tanımlar. Bir derlemenin içinde oluşturulan izlemeleri, bu kaynak için tanımlanan dinleyicileri tarafından erişilir. Aşağıdaki izleme kaynakları tanımlanır:  
  
-   System.ServiceModel: WCF işlem, herhangi bir zamanda tüm aşamaları oturum yapılandırmasını okuma, bir ileti aktarım işlenir, kullanıcı kodu ve benzeri güvenlik işleme, bir ileti gönderilir.  
  
-   System.ServiceModel.MessageLogging: Sistem üzerinden akan tüm iletileri günlüğe kaydeder.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Ortak günlük File System (CLFS) için .NET Framework arabirimi için günlüğe kaydetme.  
  
-   System.Runtime.Serialization: Nesneleri okumak veya yazılan günlükleri.  
  
-   CardSpace.  
  
 Yapılandırma aşağıdaki örnekte gösterildiği gibi her izleme kaynağı aynı (paylaşılan) dinleyici kullanmak için yapılandırabilirsiniz.  
  
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
  
 Ayrıca, kullanıcı kodu izlemeleri yayma almak için aşağıdaki örnekte, gösterildiği gibi kullanıcı tanımlı izleme kaynakları ekleyebilirsiniz.  
  
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
  
 Kullanıcı tanımlı iz kaynakları oluşturma hakkında daha fazla bilgi için bkz. [genişletme izleme](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>İzleme dinleyicilerine izlemeleri kullanmak için yapılandırma  
 Çalışma zamanında, WCF veri işleyen dinleyiciler için izleme verilerini akışları. WCF için çeşitli ön tanımlı dinleyiciler sağlar <xref:System.Diagnostics>, çıkış için kullandıkları biçimde farklıdır. Özel bir dinleyici türleri de ekleyebilirsiniz.  
  
 Kullanabileceğiniz `add` adını ve kullanmak istediğiniz İzleme dinleyicisi türünü belirtmek için. Bizim örnek yapılandırma, biz dinleyicisi adlı `traceListener` ve standart .NET Framework İzleme dinleyicisi eklenen (`System.Diagnostics.XmlWriterTraceListener`) olarak kullanılacak istiyoruz türü. İzleme dinleyicilerine her kaynak için herhangi bir sayıda ekleyebilirsiniz. Dosya İzle İzleme dinleyicisi yayar, yapılandırma dosyasında çıktı dosyasının konumunu ve adını belirtmeniz gerekir. Bu ayarı gerçekleştirilir `initializeData` bu dinleyici için dosyanın adı. Bir dosya adı belirtmezseniz, rastgele dosya adı kullanılan dinleyici türüne göre oluşturulur. Varsa <xref:System.Diagnostics.XmlWriterTraceListener> olan kullanıldığında, bir dosya adı uzantısı ile oluşturulur. Özel bir dinleyici uygularsanız, bu öznitelik bir dosya adı dışındaki başlatma verilerini almak için kullanabilirsiniz. Örneğin, bu öznitelik için bir veritabanı tanımlayıcı belirtebilirsiniz.  
  
 İzlemeleri Kablodaki, örneğin, uzak bir veritabanına göndermek için bir özel İzleme dinleyicisi yapılandırabilirsiniz. Bir uygulama dağıtıcı izleme günlüklerini uzak makinede uygun erişim denetimini uygulamalıdır.  
  
 İzleme dinleyicisi programlı olarak da yapılandırabilirsiniz. Daha fazla bilgi için [nasıl yapılır: İzleme dinleyicileri oluşturma ve başlatma](https://go.microsoft.com/fwlink/?LinkId=94648) ve [özel TraceListener oluşturma](https://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Çünkü `System.Diagnostics.XmlWriterTraceListener` olduğu değil iş parçacığı açısından güvenli, iz kaynakları yalnızca izlemeleri alırken kilitleyin. Kaynak çakışması ortaya çıkabilir, bu dinleyici kullanacak şekilde yapılandırılmış bir izleme kaynağına izleme birçok iş parçacığı çıkış olduğunda, bir önemli bir performans sorunu oluşur. Bu sorunu gidermek için iş parçacığı açısından güvenlidir özel bir dinleyici uygulamalıdır.  
  
## <a name="trace-level"></a>İzleme düzeyi  
 İzleme düzeyini tarafından denetlenir `switchValue` izleme kaynağı ayarlama. Kullanılabilir izleme düzeylerini, aşağıdaki tabloda açıklanmıştır.  
  
|İzleme düzeyi|İzlenen olaylarını yapısı|İçerik izlenen olay|İzlenen olayları|Hedef kullanıcı|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Kapalı|Yok|Yok|Yayılan izleme yok.|Yok|  
|Kritik|"Negatif" olayları: beklenmeyen bir işleme veya bir hata koşulunu belirten olaylar.||Aşağıdakiler dahil olmak üzere işlenmeyen özel durumlar günlüğe kaydedilir:<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (CLR herhangi ThreadAbortExceptionHandler çağırır)<br />-StackOverflowException (yakalanamaz)<br />-ConfigurationErrorsException<br />-SEHException<br />-Uygulama başlatma hataları<br />-İşlem hızla başarısız olayları<br />-Sistem kilitlendi<br />-Zehirli iletileri: ileti uygulamanın başarısız olmasına neden izler.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Hata|"Negatif" olayları: beklenmeyen bir işleme veya bir hata koşulunu belirten olaylar.|Beklenmeyen işlem gerçekleştirilmedi. Uygulamanın beklendiği gibi bir görevi gerçekleştirmek mümkün değildi. Ancak, uygulama hala çalışır durumda.|Tüm özel durumlar günlüğe kaydedilir.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Uyarı|"Negatif" olayları: beklenmeyen bir işleme veya bir hata koşulunu belirten olaylar.|Olası bir sorunu oluştu veya, uygulama hala işlevlerini doğru oluşabilir. Ancak, bu düzgün çalışması devam.|-Uygulama, azaltma ayarlarını izin verilenden daha fazla istekte alıyor.<br />-En fazla yapılandırılmış kapasitesi dolmak üzere alıcı kuyruğudur.<br />-Zaman aşımı süresini aştı.<br />-Credentials reddedilir.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Bilgiler|"Pozitif" olayları: başarılı kilometre taşları işaretleme olayları|Başarılı ve önemli kilometre taşları uygulama yürütme, uygulamanın düzgün şekilde ya da olmasın çalıştığından bağımsız olarak.|Genel olarak, izleme ve tanılama sistem durumu, performans ölçüm veya profil oluşturma için faydalı iletileri üretilir. Gibi bilgileri kapasite planlama ve performans yönetimi için kullanabilirsiniz:<br /><br /> -Kanal oluşturulur.<br />-Uç noktası dinleyicisi oluşturulur.<br />-İleti girer/aktarım bırakır.<br />-Güvenlik belirteci alınır.<br />-Yapılandırma ayarı okuyun.|Yöneticiler<br /><br /> Uygulama geliştiricileri<br /><br /> Ürün geliştiriciler.|  
|Ayrıntılı|"Pozitif" olayları: başarılı kilometre taşları işaretleme olayları.|Kullanıcı kodu ve bakım için düşük düzey olaylar gönderilir.|Genel olarak, bu düzey en iyileştirme hata ayıklama veya uygulama için kullanabilirsiniz.<br /><br /> -Anlaşılan ileti üst bilgisi.|Yöneticiler<br /><br /> Uygulama geliştiricileri<br /><br /> Ürün geliştiriciler.|  
|ActivityTracing||Akış olaylarını işleme etkinlikleri ve bileşenleri arasında.|Bu düzey, Yöneticiler ve geliştiriciler uygulamalarını aynı uygulama etki alanında bağıntısını kurmanızı sağlar:<br /><br /> -İzlemelerini başlatma/durdurma gibi etkinlik sınırlar.<br />-İzlemeleri aktarımları.|Tümü|  
|Tümü||Uygulama düzgün çalışmayabilir. Tüm olaylar gönderilir.|Önceki tüm olaylar.|Tümü|  
  
 Ayrıntı düzeylerinden kritik için üst üste, diğer bir deyişle, her izleme düzeyi kapalı düzeyi dışında yukarıdaki tüm düzeyleri içerir. Örneğin, uyarı düzeyinde dinleyen bir dinleyici kritik, hata ve uyarı izlemelerini alır. Tümü düzeyi ayrıntılı olaylarına kritik ve etkinlik izleme olaylarını içerir.  
  
> [!CAUTION]
>  Bilgi ve Verbose ActivityTracing düzeylerini, makinedeki tüm kullanılabilir kaynakları kullandıysanız, ileti işleme hızı olumsuz şekilde etkileyebilecek izlemeleri çok oluşturun.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Etkinlik izleme ve bağıntı için yayma işlemi yapılandırma  
 `activityTracing` İçin belirtilen değer `switchValue` özniteliği etkinlik sınırlar ve uç noktaları içinde aktarımları izlemeleri yayan etkinlik izlemeyi etkinleştirmek için kullanılır.  
  
> [!NOTE]
>  WCF'de belirli genişletilebilirlik özellikleri kullandığınızda alabilirsiniz bir <xref:System.NullReferenceException> Etkinlik izleme etkin olduğunda. Bu sorunu gidermek için uygulamanızın yapılandırma dosyasını denetleyin ve emin `switchValue` izleme kaynak olarak ayarlanmazsa özniteliğinin `activityTracing`.  
  
 `propagateActivity` Öznitelik, etkinlik ileti Exchange'de katılan diğer uç noktalarına yayılan olup olmadığını gösterir. Bu değer ayarlayarak `true`, herhangi iki uç nokta tarafından oluşturulan izleme dosyaları almak ve nasıl bir dizi başka bir uç noktada izlemeleri izlemelerini bir uç nokta üzerinde bir dizi aktarılan gözlemleyin.  
  
 Etkinlik izleme ve yayma hakkında daha fazla bilgi için bkz. [yayma](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Her ikisi de `propagateActivity` ve `ActivityTracing` Boole değerleri için System.ServiceModel TraceSource uygulayın. `ActivityTracing` Değeri WCF veya kullanıcı tanımlı olanlar da dahil olmak üzere tüm izleme kaynağı için de geçerlidir.  
  
 Kullanamazsınız `propagateActivity` özniteliği kullanıcı tanımlı izleme kaynakları ile. Kullanıcı kodu etkinlik kimliği yayma için ServiceModel ayarlamayın emin `ActivityTracing`, ServiceModel ilgili sorun yaşamaya devam ederken `propagateActivity` özniteliğini `true`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Nasıl yapılır: Oluşturma ve izleme dinleyicilerini başlatma](https://go.microsoft.com/fwlink/?LinkId=94648)
- [Özel TraceListener oluşturma](https://go.microsoft.com/fwlink/?LinkId=96239)
