---
title: İzlemeyi Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: bc23aff2f049f205d02e2fb1b5f8798c7f6a9931
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044229"
---
# <a name="configuring-tracing"></a>İzlemeyi Yapılandırma
Bu konu, izlemeyi nasıl etkinleştirebileceğinizi, izleme kaynaklarını, izlemeleri yaymak ve izleme düzeylerini ayarlamayı, Etkinlik izlemeyi ve yaymayı, uçtan uca izleme bağıntısını destekleyecek şekilde ayarlamayı ve izleme dinleyicilerini izlemelere erişim için ayarlamayı açıklar.  
  
 Üretim veya hata ayıklama ortamındaki izleme ayarları önerileri için [izleme ve Ileti günlüğe kaydetme Için önerilen ayarlar](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)bölümüne bakın.  
  
> [!IMPORTANT]
> Windows 8 ' de uygulamanızın izleme günlükleri oluşturması için uygulamanızı yükseltilmiş (yönetici olarak çalıştır) çalıştırmalısınız.  
  
## <a name="enabling-tracing"></a>Izlemeyi etkinleştirme  
 Windows Communication Foundation (WCF) Tanılama izleme için aşağıdaki verileri verir:  
  
- İşlem çağrıları, kod özel durumları, uyarılar ve diğer önemli işleme olayları gibi uygulamaların tüm bileşenleri genelinde işlem kilometre taşları için izlemeler.  
  
- İzleme özelliğinin düzgün çalışmamasına zaman Windows hata olayları. [Olay günlüğüne](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)bakın.  
  
 WCF izleme, üzerine <xref:System.Diagnostics>kurulmuştur. İzlemeyi kullanmak için yapılandırma dosyasında veya kodda izleme kaynakları tanımlamanız gerekir. WCF, her WCF derlemesi için bir izleme kaynağı tanımlar. `System.ServiceModel` İzleme kaynağı en genel WCF izleme kaynağıdır ve işlem kilometre taşlarını WCF iletişim yığınında, Kullanıcı kodunu girmeye/bırakarak taşıma/bırakma işleminden sonra kaydeder. İzleme `System.ServiceModel.MessageLogging` kaynağı, sistem üzerinden akan tüm iletileri kaydeder.  
  
 İzleme varsayılan olarak etkin değildir. İzlemeyi etkinleştirmek için, bir izleme dinleyicisi oluşturmanız ve yapılandırmada seçili izleme kaynağı için "off" dışında bir izleme düzeyi ayarlamanız gerekir. Aksi takdirde, WCF hiçbir izleme üretmez. Bir dinleyici belirtmezseniz, izleme otomatik olarak devre dışıdır. Bir dinleyici tanımlanmışsa, ancak düzey belirtilmemişse, varsayılan olarak düzey "off" olarak ayarlanır; bu da hiçbir izlemenin yayılmayacağı anlamına gelir.  
  
 Özel işlem invokers gibi WCF genişletilebilirlik noktalarını kullanırsanız, kendi izlemelerinizi yaymalısınız. Bunun nedeni, bir genişletilebilirlik noktası uyguladığınızda WCF 'nin varsayılan yolda standart izlemeleri artık yaymayacağı bir yoldur. İzlemeleri yayarak el ile izleme desteği uygulamadıysanız, beklediğinizi izlemelerinizi göremeyebilirsiniz.  
  
 Uygulamanın yapılandırma dosyasını düzenleyerek izlemeyi yapılandırabilirsiniz: Web 'de barındırılan uygulamalar için Web. config veya şirket içinde barındırılan uygulamalar için AppName. exe. config. Aşağıda bu tür bir düzenleme örneği verilmiştir. Bu ayarlar hakkında daha fazla bilgi için, "Izlemeleri kullanmak için Izleme dinleyicileri yapılandırma" bölümüne bakın.  
  
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
> Visual Studio 'da bir WCF hizmeti projesinin yapılandırma dosyasını düzenlemek için uygulamanın yapılandırma dosyasına (Web 'de barındırılan uygulamalar için Web. config veya **Çözüm Gezgini**içindeki şirket içinde barındırılan uygulama için AppName. exe. config ' e tıklayın. Ardından, **WCF yapılandırma bağlamını Düzenle** menü öğesini seçin. Bu, bir grafik kullanıcı arabirimi kullanarak WCF Hizmetleri için yapılandırma ayarlarını değiştirmenize olanak sağlayan [yapılandırma Düzenleyicisi aracını (SvcConfigEditor. exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)başlatır.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Izlemeleri yayma için Izleme kaynaklarını yapılandırma  
 WCF her derleme için bir izleme kaynağı tanımlar. Bir derlemede oluşturulan izlemelere bu kaynak için tanımlanan dinleyiciler tarafından erişilir. Aşağıdaki izleme kaynakları tanımlanmıştır:  
  
- System. ServiceModel: Yapılandırma her değiştiğinde WCF işlemenin tüm aşamalarını günlüğe kaydeder, aktarım sırasında bir ileti işlenir, güvenlik işleme, Kullanıcı kodunda bir ileti gönderilir ve bu şekilde devam eder.  
  
- System. ServiceModel. MessageLogging: Sistem üzerinden akan tüm iletileri günlüğe kaydeder.  
  
- System. IdentityModel.  
  
- System. ServiceModel. Activation.  
  
- System. ıO. log: .NET Framework arabirimi için Ortak Günlük Dosya Sistemi (CLFS) günlüğe kaydediliyor.  
  
- System. Runtime. Serialization: Nesneler okunmakta veya yazıldığında günlüğe kaydedilir.  
  
- Rağmen.  
  
 Aşağıdaki yapılandırma örneğinde gösterildiği gibi, her bir izleme kaynağını aynı (paylaşılan) dinleyiciye kullanacak şekilde yapılandırabilirsiniz.  
  
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
  
 Ayrıca, Kullanıcı kodu izlemelerini göstermek için aşağıdaki örnekte gösterildiği gibi Kullanıcı tanımlı izleme kaynakları ekleyebilirsiniz.  
  
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
  
 Kullanıcı tanımlı izleme kaynakları oluşturma hakkında daha fazla bilgi için bkz. [Izlemeyi genişletme](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Izlemeleri kullanmak için Izleme dinleyicileri yapılandırma  
 Çalışma zamanında, WCF akışları verileri işleyen dinleyicilerine veri izler. WCF, için daha <xref:System.Diagnostics>önceden tanımlanmış birkaç dinleyici sağlar ve bu, çıktı için kullandıkları biçimde farklılık gösterir. Ayrıca, özel dinleyici türleri ekleyebilirsiniz.  
  
 Kullanmak istediğiniz izleme dinleyicisinin adını ve türünü belirtmek için'ikullanabilirsiniz.`add` Örnek yapılandırmanızda, dinleyiciyi `traceListener` adlandırdık ve kullanmak istediğimiz tür olarak standart .NET Framework Trace Listener (`System.Diagnostics.XmlWriterTraceListener`) ekledik. Her kaynak için herhangi bir sayıda izleme dinleyicisi ekleyebilirsiniz. İzleme dinleyicisi izlemeyi bir dosyaya yayıyorsa, yapılandırma dosyasında çıkış dosyasının konumunu ve adını belirtmeniz gerekir. Bu, bu dinleyicinin dosya `initializeData` adına ayarlanarak yapılır. Bir dosya adı belirtmezseniz, kullanılan dinleyici türü temel alınarak rastgele bir dosya adı oluşturulur. <xref:System.Diagnostics.XmlWriterTraceListener> Kullanılıyorsa, uzantısı olmayan bir dosya adı oluşturulur. Özel bir dinleyici uygularsanız, bu özniteliği bir dosya adı dışında başlatma verisi almak için de kullanabilirsiniz. Örneğin, bu öznitelik için bir veritabanı tanımlayıcısı belirtebilirsiniz.  
  
 Örneğin, uzak bir veritabanına izleme izlemek için özel bir izleme dinleyicisi yapılandırabilirsiniz. Bir uygulama dağıtıcı olarak, uzak makinedeki izleme günlüklerinde doğru erişim denetimini zorunlu kılabilirsiniz.  
  
 Ayrıca, bir izleme dinleyicisini programlı bir şekilde yapılandırabilirsiniz. Daha fazla bilgi için [nasıl yapılır: İzleme dinleyicileri](https://go.microsoft.com/fwlink/?LinkId=94648) oluşturma ve başlatma ve [özel bir TraceListener oluşturma](https://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
> `System.Diagnostics.XmlWriterTraceListener` , İş parçacığı açısından güvenli olmadığından izleme kaynağı, izlemeleri çıktıları sırasında kaynakları özel olarak kilitleyebilir. Birçok iş parçacığı çıkışı, bu dinleyiciyi kullanmak üzere yapılandırılmış bir izleme kaynağına izlenirse, kaynak çakışması oluşabilir ve bu durum önemli bir performans sorununa neden olur. Bu sorunu çözmek için, iş parçacığı açısından güvenli olan özel bir dinleyici uygulamalısınız.  
  
## <a name="trace-level"></a>İzleme düzeyi  
 İzleme düzeyi izleme kaynağı `switchValue` ayarıyla denetlenir. Kullanılabilir izleme düzeyleri aşağıdaki tabloda açıklanmıştır.  
  
|İzleme düzeyi|Izlenen olayların doğası|Izlenen olayların içeriği|İzlenen Olaylar|Kullanıcı hedefi|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Kapalı|Yok|Yok|Hiçbir izleme yayılmadı.|Yok|  
|Kritik|"Negatif" olaylar: beklenmeyen bir işleme veya bir hata koşulunu belirten olaylar.||Aşağıdakiler dahil işlenmemiş özel durumlar günlüğe kaydedilir:<br /><br /> -OutOfMemoryException<br />-Threadadbortexception (CLR herhangi bir Threadavbortexceptionhandler çağırır)<br />-StackOverflowException (yakalanamaz)<br />-ConfigurationErrorsException<br />-Şehir özel durumu<br />-Uygulama başlatma hataları<br />-FailFast olayları<br />-Sistem askıda kalıyor<br />-Poison iletileri: uygulamanın başarısız olmasına neden olan ileti izlemeleri.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Hata|"Negatif" olaylar: beklenmeyen bir işleme veya bir hata koşulunu belirten olaylar.|Beklenmeyen işlem gerçekleşti. Uygulama beklenen şekilde bir görev gerçekleştiremedi. Ancak uygulama hala çalışır durumda kalır.|Tüm özel durumlar günlüğe kaydedilir.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Uyarı|"Negatif" olaylar: beklenmeyen bir işleme veya bir hata koşulunu belirten olaylar.|Olası bir sorun oluştu ya da olabilir, ancak uygulama hala doğru şekilde çalışır. Ancak, düzgün şekilde çalışmaya devam edemeyebilir.|-Uygulama, azaltma ayarlarının izin verenden daha fazla istek alıyor.<br />-Alma kuyruğu en yüksek yapılandırılmış kapasiteye yaklaştı.<br />-Zaman aşımı aşıldı.<br />-Kimlik bilgileri reddedilir.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Bilgiler|"Olumlu" olaylar: başarılı kilometre taşlarını işaretleyen olaylar|Uygulamanın düzgün çalışıp çalışmadığını bağımsız olarak uygulama yürütmenin önemli ve başarılı kilometre taşları.|Genel olarak, sistem durumunu izleme ve tanılamaya yönelik olarak, performans veya profil oluşturma ölçme için yararlı iletiler oluşturulur. Kapasite planlama ve performans yönetimi için bu bilgileri kullanabilirsiniz:<br /><br /> -Kanallar oluşturulur.<br />-Uç nokta dinleyicileri oluşturulur.<br />-İleti taşımayı giriyor/bırakıyor.<br />-Güvenlik belirteci alındı.<br />-Yapılandırma ayarı okundu.|Yöneticiler<br /><br /> Uygulama geliştiricileri<br /><br /> Ürün geliştiricileri.|  
|Ayrıntılı|"Olumlu" olaylar: başarılı kilometre taşlarını işaretleyen olaylar.|Hem Kullanıcı kodu hem de bakım için düşük düzey olaylar yayınlanır.|Genel olarak, hata ayıklama veya uygulama iyileştirmesi için bu düzeyi kullanabilirsiniz.<br /><br /> -Anlamış ileti üstbilgisi.|Yöneticiler<br /><br /> Uygulama geliştiricileri<br /><br /> Ürün geliştiricileri.|  
|ActivityTracing||İşlem etkinlikleri ve bileşenleri arasındaki akış olayları.|Bu düzey, yöneticilerin ve geliştiricilerin aynı uygulama etki alanındaki uygulamaları ilişkilendirmelerine olanak tanır:<br /><br /> -Başlat/Durdur gibi etkinlik sınırları için izlemeler.<br />-Aktarımlar için izlemeler.|Tümü|  
|Tümü||Uygulama düzgün çalışmayabilir. Tüm olaylar yayınlanır.|Önceki tüm olaylar.|Tümü|  
  
 Ayrıntılıdan kritik ' e kadar olan düzeyler birbirlerinin üzerine yığılır, diğer bir deyişle, her bir izleme düzeyi, kapalı düzeyi hariç tüm seviyeleri içerir. Örneğin, uyarı düzeyini dinleyen bir dinleyici, kritik, hata ve uyarı izlemelerini alır. Tüm düzey, ayrıntıdan kritik ve etkinlik izleme olaylarına kadar olan olayları içerir.  
  
> [!CAUTION]
> Bilgi, ayrıntılı ve ActivityTracing düzeyleri, makinedeki tüm kullanılabilir kaynakları kullandıysanız ileti aktarım hızını olumsuz yönde etkileyebilecek çok sayıda izleme oluşturur.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Bağıntı için etkinlik Izlemeyi ve yaymayı yapılandırma  
 Öznitelik için belirtilen değer, etkinlik sınırları ve uç noktalar içindeki aktarımlar için izlemeleri veren Etkinlik izlemeyi etkinleştirmek için kullanılır. `activityTracing` `switchValue`  
  
> [!NOTE]
> WCF 'de belirli genişletilebilirlik özelliklerini kullandığınızda, <xref:System.NullReferenceException> etkinlik izlemenin ne zaman etkinleştirildiğini görebilirsiniz. Bu sorunu gidermek için, uygulamanızın yapılandırma dosyasını denetleyin ve izleme kaynağınıza ait `switchValue` özniteliğin olarak `activityTracing`ayarlı olmadığından emin olun.  
  
 `propagateActivity` Özniteliği, etkinliğin ileti değişimine katılan diğer uç noktalara yayılıp yaymayacağını gösterir. Bu değeri olarak `true`ayarlarsanız, herhangi iki uç nokta tarafından oluşturulan izleme dosyalarını alabilir ve bir uç noktada bir izleme kümesinin başka bir uç noktasındaki izleme kümesine akışını gözlemleyebilirsiniz.  
  
 Etkinlik izleme ve yayma hakkında daha fazla bilgi için bkz. [yayma](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Hem hem de `propagateActivity` BooleandeğerleriSystem.ServiceModelTraceSourceiçingeçerlidir.`ActivityTracing` `ActivityTracing` Değer aynı zamanda WCF veya Kullanıcı tanımlı olanlar dahil olmak üzere tüm izleme kaynakları için de geçerlidir.  
  
 `propagateActivity` Özniteliği Kullanıcı tanımlı izleme kaynakları ile kullanamazsınız. Kullanıcı kodu etkinlik kimliği yayılması için ServiceModel `ActivityTracing`' ı ayarladığınızdan, hala ServiceModel `propagateActivity` özniteliği olarak `true`ayarlanmış olduğundan emin olun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Nasıl yapılır: Izleme dinleyicileri oluşturma ve başlatma](https://go.microsoft.com/fwlink/?LinkId=94648)
- [Özel bir TraceListener oluşturma](https://go.microsoft.com/fwlink/?LinkId=96239)
