---
title: İzlemeyi Yapılandırma
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: d8b216bf5497cf2a1faa2fa24ba1d8b3102f6f10
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185746"
---
# <a name="configuring-tracing"></a>İzlemeyi Yapılandırma
Bu konu, izleme izlemeyi, izleme kaynaklarını izleme ve izleme düzeyleri ayarlamak için nasıl yapılandırabileceğinizi, etkinlik izlemeve yayılmayı uçlardan uca izleme bağındırMasını desteklemek için nasıl ayarlayabileceğinizi ve izleme dinleyicilerini izleme izine göre nasıl ayarlaabileceğinizi açıklar.  
  
 Üretim veya hata ayıklama ortamında ki ayarları izleme önerileri [için, İzleme ve İleti Günlüğe Kaydetme için Önerilen Ayarlar'a](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md)bakın.  
  
> [!IMPORTANT]
> Windows 8'de, uygulamanızın izleme günlükleri oluşturabilmesi için uygulamanızı yükseltilmiş (Yönetici olarak çalıştır) çalıştırmanız gerekir.  
  
## <a name="enabling-tracing"></a>İzlemeyi Etkinleştirme  
 Windows Communication Foundation (WCF), tanılama izleme için aşağıdaki verileri sağlar:  
  
- İşlem çağrıları, kod özel durumları, uyarılar ve diğer önemli işleme olayları gibi uygulamaların tüm bileşenlerindeki işlem kilometre taşlarını izler.  
  
- İzleme özelliği arızalandığında Windows hatası olayları. [Bkz. Olay Günlüğü.](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
  
 WCF izleme üstüne inşa <xref:System.Diagnostics>edilmiştir. İzlemeyi kullanmak için, yapılandırma dosyasında veya koddaki izleme kaynaklarını tanımlamanız gerekir. WCF, her WCF derlemesi için bir izleme kaynağı tanımlar. `System.ServiceModel` İzleme kaynağı en genel WCF izleme kaynağıdır ve WCF iletişim yığınında taşımadan kullanıcı kodu girme/bırakma işlemine kadar işleme kilometre taşlarını kaydeder. İzleme `System.ServiceModel.MessageLogging` kaynağı, sistemde akan tüm iletileri kaydeder.  
  
 İzleme varsayılan olarak etkinleştirildi. İzlemeyi etkinleştirmek için, bir izleme dinleyicisi oluşturmanız ve yapılandırmada seçili izleme kaynağı için "Kapalı" dışında bir izleme düzeyi ayarlamanız gerekir; aksi takdirde, WCF herhangi bir iz oluşturmaz. Bir dinleyici belirtmezseniz, izleme otomatik olarak devre dışı bırakılır. Bir dinleyici tanımlanır, ancak düzey belirtilmemişse, düzey varsayılan olarak "Kapalı" olarak ayarlanır, bu da hiçbir izlemenin yayımlanmadığı anlamına gelir.  
  
 Özel işlem çağrıçlayıcıları gibi WCF genişletilebilirlik noktaları kullanıyorsanız, kendi izlemelerinizi yaysanız gerekir. Bunun nedeni, bir genişletilebilirlik noktası uygularsanız, WCF'nin varsayılan yolda standart izlemeleri artık yakılamamasının dır. İzler yayarak manuel izleme desteği uygulamazsanız, beklediğiniz izleri göremeyebilirsiniz.  
  
 Uygulamanın yapılandırma dosyasını düzenleyerek izlemeyi yapılandırabilirsiniz(Web tarafından barındırılan uygulamalar için Web.config veya kendi barındırılan uygulamalar için Appname.exe.config). Aşağıda bu tür bir edit e-posta verilmiştir. Bu ayarlar hakkında daha fazla bilgi için "İzleme Dinleyicilerini İzlemeyi İzlemek için Yapılandırma" bölümüne bakın.  
  
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
> Visual Studio'daki bir WCF hizmet projesinin yapılandırma dosyasını düzenlemek için, uygulamanın yapılandırma dosyasına (Web barındırılan uygulamalar için Web.config veya **Solution Explorer'da**kendi barındırılan uygulama için Appname.exe.config) sağ tıklayın. Ardından **WCF Yapılandırma** bağlamını edit menü öğesini seçin. Bu, grafik sel kullanıcı arabirimi kullanarak WCF hizmetleri için yapılandırma ayarlarını değiştirmenizi sağlayan [Configuration Editor Aracını (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)başlatır.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>İz Kaynaklarını İz Yayıştacak Şekilde Yapılandırma  
 WCF her derleme için bir izleme kaynağı tanımlar. Bir derleme içinde oluşturulan izlemeler, o kaynak için tanımlanan dinleyiciler tarafından erişilir. Aşağıdaki izleme kaynakları tanımlanır:  
  
- System.ServiceModel: WCF işlemenin tüm aşamalarını kaydeder, yapılandırma okunduğunda, bir ileti taşımada, güvenlik işlemlerinde işlenir, kullanıcı kodunda bir ileti gönderilir, vesaire.  
  
- System.ServiceModel.MessageLogging: Sistem üzerinden akan tüm iletileri kaydeder.  
  
- System.IdentityModel.  
  
- System.ServiceModel.Activation.  
  
- System.IO.Log: .NET Framework arabiriminin Ortak Günlük Dosya Sistemine (CLFS) giriş ibaresi.  
  
- System.Runtime.Serialization: Nesneler okunduğunda veya yazıldığında günlükler.  
  
- Cardspace.  
  
 Aşağıdaki yapılandırma örneğinde belirtildiği gibi, her izleme kaynağını aynı (paylaşılan) dinleyiciyi kullanacak şekilde yapılandırabilirsiniz.  
  
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
  
 Ayrıca, kullanıcı kodu izlemeleri yatmak için aşağıdaki örnekte gösterildiği gibi kullanıcı tanımlı izleme kaynakları ekleyebilirsiniz.  
  
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
  
 Kullanıcı tanımlı izleme kaynakları oluşturma hakkında daha fazla bilgi için [bkz.](../../../../../docs/framework/wcf/samples/extending-tracing.md)  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>İzleme Dinleyicilerini İzlemeYi Tüketecek Şekilde Yapılandırma  
 Çalışma zamanında WCF, verileri işleyen dinleyicilere izleme verileri aktarıyor. WCF, çıktı için <xref:System.Diagnostics>kullandıkları biçimde farklılık gösteren birkaç önceden tanımlanmış dinleyici sağlar. Özel dinleyici türleri de ekleyebilirsiniz.  
  
 Kullanmak istediğiniz `add` izleme dinleyicisinin adını ve türünü belirtmek için kullanabilirsiniz. Örnek yapılandırmamızda Dinleyici'yi adlandırdık `traceListener` ve standart .NET Framework`System.Diagnostics.XmlWriterTraceListener`trace dinleyicisini ( ) kullanmak istediğimiz tür olarak ekledik. Her kaynak için istediğiniz sayıda izleme dinleyicisi ekleyebilirsiniz. İzleme dinleyicisi izlemeyi bir dosyaya yayırsa, çıktı dosyası konumunu ve adını yapılandırma dosyasında belirtmeniz gerekir. Bu, o `initializeData` dinleyici için dosyanın adına ayarlayarak yapılır. Bir dosya adı belirtmezseniz, kullanılan dinleyici türüne göre rasgele bir dosya adı oluşturulur. <xref:System.Diagnostics.XmlWriterTraceListener> Kullanılırsa, uzantısı olmayan bir dosya adı oluşturulur. Özel bir dinleyici uygularsanız, bu özniteliği dosya adı dışındaki başlatma verilerini almak için de kullanabilirsiniz. Örneğin, bu öznitelik için bir veritabanı tanımlayıcısı belirtebilirsiniz.  
  
 Örneğin, kablodaki izlemeleri uzak bir veritabanına gönderecek şekilde özel bir izleme dinleyicisi yapılandırabilirsiniz. Uygulama dağıtıcı olarak, uzak makinedeki izleme günlükleri üzerinde uygun erişim denetimini zorlamanız gerekir.  
  
 Ayrıca, izleme dinleyicisini programlı olarak yapılandırabilirsiniz. Daha fazla bilgi için [bkz: İzleme Dinleyicileri Oluşturma ve Başlatma](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md) ve [Özel İzleme Dinleyicisi Oluşturma.](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)  
  
> [!CAUTION]
> `System.Diagnostics.XmlWriterTraceListener` İş parçacığı güvenli olmadığından, izleme kaynağı yalnızca izlemeleri çıkarırken kaynakları kilitleyebilir. Bu dinleyiciyi kullanmak üzere yapılandırılan bir izleme kaynağına çok sayıda iş parçacığı çıkışı izlendiğinde, kaynak çekişmesi oluşabilir ve bu da önemli bir performans sorununa neden olabilir. Bu sorunu gidermek için, iş parçacığı güvenli özel bir dinleyici uygulamanız gerekir.  
  
## <a name="trace-level"></a>İzleme Düzeyi  
 İzleme düzeyi, izleme kaynağının `switchValue` ayarı tarafından denetlenir. Kullanılabilir izleme düzeyleri aşağıdaki tabloda açıklanmıştır.  
  
|İzleme Düzeyi|İzlenen Olayların Doğası|İzlenen Olayların İçeriği|İzlenen Etkinlikler|Kullanıcı Hedefi|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Kapalı|Yok|Yok|Hiçbir iz yayılmadım.|Yok|  
|Kritik|"Negatif" olaylar: beklenmeyen bir işleme veya hata durumunu gösteren olaylar.||Aşağıdakiler de dahil olmak üzere işlenmemiş özel durumlar günlüğe kaydedilir:<br /><br /> - OutOfMemoryException<br />- ThreadAbortException (CLR herhangi bir ThreadAbortExceptionHandler çağırır)<br />- StackOverflowException (yakalanamaz)<br />- YapılandırmaHatalarıÖzel Durum<br />- SEHException<br />- Uygulama başlangıç hataları<br />- Failfast olaylar<br />- Sistem askıda<br />- Zehirli iletiler: uygulamanın başarısız lığa neden olan ileti izlemeleri.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Hata|"Negatif" olaylar: beklenmeyen bir işleme veya hata durumunu gösteren olaylar.|Beklenmeyen işlem gerçekleşti. Uygulama beklendiği gibi bir görev gerçekleştirmek mümkün değildi. Ancak, uygulama hala çalışır durumda.|Tüm özel durumlar günlüğe kaydedilir.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Uyarı|"Negatif" olaylar: beklenmeyen bir işleme veya hata durumunu gösteren olaylar.|Olası bir sorun oluştu veya oluşabilir, ancak uygulama hala düzgün çalışıyor. Ancak, düzgün çalışmaya devam etmeyebilir.|- Uygulama, azaltma ayarlarının izin verdiğinden daha fazla istek alıyor.<br />- Alıcı sıra, en yüksek yapılandırılmış kapasitesine yakındır.<br />- Zaman aşımı aşıldı.<br />- Kimlik bilgileri reddedilir.|Yöneticiler<br /><br /> Uygulama geliştiricileri|  
|Bilgi|"Olumlu" olaylar: başarılı kilometre taşlarını işaretleyen olaylar|Uygulamanın düzgün çalışıp çalışmadığına bakılmaksızın, uygulama yürütmenin önemli ve başarılı kilometre taşları.|Genel olarak, sistem durumunu izlemek ve tanılama, performans veya profil oluşturma için yararlı iletiler oluşturulur. Bu bilgileri kapasite planlama ve performans yönetimi için kullanabilirsiniz:<br /><br /> - Kanallar oluşturulur.<br />- Endpoint dinleyiciler oluşturulur.<br />- İleti taşımaya girer/ayrılır.<br />- Güvenlik belirteci alınır.<br />- Yapılandırma ayarı okunur.|Yöneticiler<br /><br /> Uygulama geliştiricileri<br /><br /> Ürün geliştiricileri.|  
|Ayrıntılı|"Olumlu" olaylar: başarılı kilometre taşlarını işaretleyen olaylar.|Hem kullanıcı kodu hem de servis için düşük düzeyli olaylar yayılır.|Genel olarak, hata ayıklama veya uygulama optimizasyonu için bu düzeyi kullanabilirsiniz.<br /><br /> - Anlaşılmış ileti üstbilgi.|Yöneticiler<br /><br /> Uygulama geliştiricileri<br /><br /> Ürün geliştiricileri.|  
|Aktivite Yarışı||İşleme etkinlikleri ve bileşenler arasındaki akış olayları.|Bu düzey, yöneticilerin ve geliştiricilerin uygulamaları aynı uygulama etki alanında ilişkilendirmesine olanak tanır:<br /><br /> - Başlat/durdur gibi etkinlik sınırları için izler.<br />- Transferler için izler.|Tümü|  
|Tümü||Uygulama düzgün çalışabilir. Tüm olaylar yayılır.|Önceki tüm olaylar.|Tümü|  
  
 Verbose'den Kritik'e kadar olan düzeyler üst üste yığılmış, yani her izleme düzeyi Kapalı seviye dışında üstündeki tüm düzeyleri içerir. Örneğin, Uyarı düzeyinde dinleyen bir dinleyici Kritik, Hata ve Uyarı izlemelerini alır. Tüm düzey, Verbose'dan Kritik ve Etkinlik izleme olaylarını içerir.  
  
> [!CAUTION]
> Bilgi, Verbose ve ActivityTracing düzeyleri, makinedeki tüm kullanılabilir kaynakları kullandıysanız ileti çıktısını olumsuz etkileyebilecek çok sayıda izleme oluşturur.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Korelasyon için Etkinlik İzleme ve YayılmaYı Yapılandırma  
 Öznitelik `activityTracing` için `switchValue` belirtilen değer, etkinlik sınırları ve uç noktalar içinde aktarımlar için izleme ler yayan etkinlik izlemesini etkinleştirmek için kullanılır.  
  
> [!NOTE]
> WCF'de belirli genişletilebilirlik özelliklerini kullandığınızda, <xref:System.NullReferenceException> etkinlik izleme etkinleştirildiğinde bir şey elde edebilirsiniz. Bu sorunu gidermek için, uygulamanızın yapılandırma dosyasını `switchValue` denetleyin ve izleme kaynağınızın `activityTracing`özniteliğinin ayarlanmadığından emin olun.  
  
 Öznitelik, `propagateActivity` etkinliğin ileti alışverişine katılan diğer uç noktalara yayılıp yayılmaması gerektiğini gösterir. Bu değeri `true`, herhangi iki uç nokta tarafından oluşturulan izleme dosyalarını alabilir ve bir uç noktadaki izleme kümesinin başka bir uç noktadaki bir dizi iz kümesine nasıl aktığını gözlemleyebilirsiniz.  
  
 Etkinlik izleme ve yayılma hakkında daha fazla bilgi için [bkz.](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md)  
  
 Hem `propagateActivity` `ActivityTracing` de Boolean değerleri System.ServiceModel TraceSource için geçerlidir. Bu `ActivityTracing` değer, WCF veya kullanıcı tanımlı olanlar da dahil olmak üzere herhangi bir izleme kaynağı için de geçerlidir.  
  
 Özniteliği kullanıcı `propagateActivity` tanımlı izleme kaynaklarıyla kullanamazsınız. Kullanıcı kodu etkinliği kimliği yayılımı için ServiceModel'i ayarlamadığınızdan `propagateActivity` emin olun, `true`servicemodel `ActivityTracing`özniteliği hala .'a ayarlanmışken.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [İzleme](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Yönetim ve Tanılama](../../../../../docs/framework/wcf/diagnostics/index.md)
- [Nasıl yapılır: İzleme Dinleyicileri Oluşturma ve Başlatma](../../../debug-trace-profile/how-to-create-and-initialize-trace-listeners.md)
- [Özel TraceListener Oluşturma](https://docs.microsoft.com/archive/msdn-magazine/2006/april/clr-inside-out-extending-system-diagnostics)
