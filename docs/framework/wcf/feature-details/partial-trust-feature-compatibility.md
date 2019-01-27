---
title: Kısmi Güven Özelliği Uyumluluğu
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 404fe1a7fb14f28d264d4a97981eade8404141ee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564736"
---
# <a name="partial-trust-feature-compatibility"></a>Kısmi Güven Özelliği Uyumluluğu
Kısmen güvenilen bir ortamda çalışan işlevselliğin sınırlı bir alt kümesinde Windows Communication Foundation (WCF) destekler. Kısmi güvende desteklenen özellikler bölümünde anlatıldığı gibi belirli senaryoları birtakım geçici olarak tasarlanmıştır [desteklenen dağıtım senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) konu.  
  
## <a name="minimum-permission-requirements"></a>En düşük izin gereksinimleri  
 WCF ya da aşağıdaki standart adlandırılmış izin kümelerinin altında çalışan uygulamalar, özelliklerin bir alt kümesini destekler:  
  
-   Orta güven izinleri  
  
-   Internet bölgesi izinleri  
  
 Kısmen güvenilir uygulamaların daha kısıtlayıcı izinlerle WCF kullanmayı denemeden güvenlik özel durumlar çalışma zamanında neden olabilir.  
  
## <a name="contracts"></a>Sözleşmeler  
 Sözleşmeler, kısmi güven altında çalışırken aşağıdaki kısıtlamalar şunlardır:  
  
-   Uygulayan bir hizmet sınıfı `[ServiceContract]` arabirimi olmalıdır `public` ve bir `public` Oluşturucusu. Tanımlıyorsa `[OperationContract]` olmalıdır bu yöntem, `public`. Bunun yerine uyguluyorsa bir `[ServiceContract]` arabirimi, bu yöntem uygulamaları açık veya `private`, koşuluyla `[ServiceContract]` arabirimi `public`.  
  
-   Kullanırken `[ServiceKnownType]` öznitelik, belirtilen metot olmalı `public`.  
  
-   `[MessageContract]` sınıfları ve üyeleri olabilir `public`. Varsa `[MessageContract]` sınıfı olabilir Uygulama derlemesinde tanımlanan `internal` ve `internal` üyeleri.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 <xref:System.ServiceModel.BasicHttpBinding> Ve <xref:System.ServiceModel.WebHttpBinding> kısmi güven ortamında tam olarak desteklenir. <xref:System.ServiceModel.WSHttpBinding> Yalnızca Transport güvenlik modunu desteklenir.  
  
 Dışındaki HTTP taşımaları gibi kullandığınız bağlamaları <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>, veya <xref:System.ServiceModel.NetMsmqBinding>, kısmi güven ortamında çalıştırırken desteklenmez.  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Özel bağlamalar oluşturulabilir ve kısmi güven ortamında kullanılan, ancak bu bölümde belirtilen kısıtlamalara uymalıdır.  
  
### <a name="transports"></a>Taşımalar  
 Yalnızca izin verilen öğeler aktarım bağlama <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Kodlayıcılar  
 Aşağıdaki kodlayıcılarda izin verilir:  
  
-   Metin Kodlayıcı (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   İkili Kodlayıcı (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   Web ileti Kodlayıcı (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 İleti Aktarım en iyi duruma getirme mekanizması (MTOM) kodlayıcılarda desteklenmez.  
  
### <a name="security"></a>Güvenlik  
 Kısmen güvenilen uygulamalar, iletişimin güvenliğini sağlamak için WCF'ın aktarım düzeyi güvenlik özelliklerini kullanabilirsiniz. İleti düzeyi güvenlik desteklenmez. İleti düzeyi güvenliği kullanmak için bir bağlama yapılandırma çalışma zamanında bir özel durum sonuçlanır.  
  
### <a name="unsupported-bindings"></a>Desteklenmeyen bağlamalar  
 Güvenilir Mesajlaşma, işlemler veya ileti düzeyi güvenlik kullanan bağlamaları desteklenmez.  
  
## <a name="serialization"></a>Serileştirme  
 Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> kısmi güven ortamında desteklenir. Ancak, kullanım <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabi olan:  
  
-   Tüm serileştirilebilir `[DataContract]` türleri olmalıdır `public`.  
  
-   Tüm serileştirilebilir `[DataMember]` alanlar ve özellikler bir `[DataContract]` türü genel olmalıdır ve okuma/yazma. Serileştirme ve seri durumundan çıkarma [salt okunur](https://go.microsoft.com/fwlink/?LinkID=98854) WCF kısmen güvenilen bir uygulamada çalışırken alanları desteklenmiyor.  
  
-    `[Serializable]` /ISerializable programlama modeli, kısmi güven ortamında desteklenmez.  
  
-   Bilinen türler, kod veya makine düzeyinde yapılandırma (machine.config) belirtilmelidir. Uygulama düzeyinde yapılandırma güvenlik nedenleriyle, bilinen türleri belirtilemez.  
  
-   Türleri uygulayan <xref:System.Runtime.Serialization.IObjectReference> kısmen güvenilen bir ortamda özel durum.  
  
 Serileştirme bölümüne bakın [kısmi güven en iyi uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) kullanırken güvenliği hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.DataContractSerializer> kısmen güvenilen bir uygulama içinde güvenli bir şekilde.  
  
### <a name="collection-types"></a>Koleksiyon türleri  
 Bazı koleksiyon türleri her ikisini de uygulamak <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.IEnumerable>. Örnekler uygulayan türler <xref:System.Collections.Generic.ICollection%601>. Bu türler uygulayabilirsiniz bir `public` uygulaması `GetEnumerator()`, açık uygulaması `GetEnumerator()`. Bu durumda, <xref:System.Runtime.Serialization.DataContractSerializer> çağırır `public` uygulaması `GetEnumerator()`ve açık uyarlamasını `GetEnumerator()`. Hiçbiri `GetEnumerator()` uygulamalarıdır `public` ve ardından tümü açık uygulamaları <xref:System.Runtime.Serialization.DataContractSerializer> çağırır `IEnumerable.GetEnumerator()`.  
  
 WCF hiçbiri bir kısmi güven ortamında çalışıyorsa, koleksiyon türleri için `GetEnumerator()` uygulamalarıdır `public`, veya bunların hiçbiri açık arabirim uygulamalarıdır ve sonra bir güvenlik özel durumu oluşturulur.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Çoğu .NET Framework koleksiyon türleri gibi <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Hashtable> tarafından desteklenmeyen <xref:System.Runtime.Serialization.NetDataContractSerializer> kısmi güven. Bu tür sahip `[Serializable]` özniteliğini ayarlayın ve Serileştirme bölümünde daha önce belirtildiği gibi bu öznitelik kısmi güvende desteklenmiyor. <xref:System.Runtime.Serialization.DataContractSerializer> Koleksiyonlar, özel bir şekilde davranır ve bu nedenle bu kısıtlamayı çözmek elde edebilirsiniz ancak <xref:System.Runtime.Serialization.NetDataContractSerializer> bu kısıtlama aşmak için bu tür mekanizması vardır.  
  
 <xref:System.DateTimeOffset> Türü tarafından desteklenmiyor <xref:System.Runtime.Serialization.NetDataContractSerializer> kısmi güven.  
  
 Bir yedek kullanılamaz <xref:System.Runtime.Serialization.NetDataContractSerializer> (kullanarak <xref:System.Runtime.Serialization.SurrogateSelector> mekanizması) kısmi güvende çalışan. Bu kısıtlama için serileştirme değil, bir yedek kullanarak geçerli olduğunu unutmayın.  
  
## <a name="enabling-common-behaviors-to-run"></a>Çalıştırılacak ortak davranışları etkinleştirme  
 Hizmet veya uç nokta davranışları işaretlenmemiş ile <xref:System.Security.AllowPartiallyTrustedCallersAttribute> eklenen özniteliği (APTCA) [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) kısmi güvende uygulama çalışırken, bir yapılandırma dosyası bölümünü çalıştırmak değil Bu durumda ortam ve hiçbir özel durum oluşturulur. Ortak davranışları çalışmasını zorunlu kılmak için aşağıdaki seçeneklerden birini yapmanız gerekir:  
  
-   Ortak davranışınızı işaretlemek <xref:System.Security.AllowPartiallyTrustedCallersAttribute> kısmen güvenilen uygulamada dağıtıldığında çalıştırabileceği şekilde onlara özniteliği. Bir kayıt defteri girişi bilgisayarda APTCA işaretli derlemeler çalışmasını önlemek için ayarlanabilir unutmayın. biçimindeki telefon numarasıdır.  
  
-   Uygulamanın tam olarak güvenilen bir uygulama kullanıcılar, uygulamayı bir kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremez dağıtılması durumunda emin olun. Bunu yapmak, davranışı çalışmaz ve hiçbir özel durum. Bunu sağlamak için bkz: **levelfinal** seçeneği kullanılarak [Caspol.exe (kod erişimi güvenliği ilke aracı)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Bir ortak davranışı örneği için bkz [nasıl yapılır: Enterprise uç noktalarını kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Yapılandırma  
 Bunun tek istisnası kısmen güvenilen kod yalnızca yerel WCF yapılandırma bölümlerini yükleyebilir `app.config` dosya. WCF bölümleri machine.config veya bir kök başvuru WCF yapılandırma bölümlerini yüklenecek ConfigurationPermission(Unrestricted) web.config dosyası gerektirir. Yapılandırma yüklendiğinde WCF yapılandırma bölümlerine (davranışları, bağlamaları) yerel yapılandırma dosyası sonuçları bir özel durum dışında bu izin olmadan başvuruyor.  
  
 Bunun tek istisnası bilinen türü seri hale getirme, bu konunun serileştirme bölümünde anlatıldığı gibi yapılandırmadır.  
  
> [!IMPORTANT]
>  Yapılandırma uzantıları yalnızca tam güven altında çalışırken desteklenir.  
  
## <a name="diagnostics"></a>Tanılamalar  
  
### <a name="event-logging"></a>Etkinlikleri Günlüğe Kaydetme  
 Sınırlı bir olay günlüğü, kısmi güven altında desteklenir. Yalnızca etkinleştirme hataları hizmet ve izleme/ileti günlük kaydı hataları olay günlüğüne kaydedilir. Bir işlem tarafından günlüğe kaydedilen olayların sayısı, aşırı iletileri olay günlüğüne yazma önlemek için 5 ise.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 Kısmi güven ortamında WCF çalıştırıldığında ileti günlüğe kaydetmeyi çalışmaz. Kısmi güven altında etkinleştirilirse, bu hizmeti etkinleştirme başarısız olmaz, ancak hiçbir ileti günlüğe kaydedilir.  
  
### <a name="tracing"></a>İzleme  
 Kısmi güven ortamında çalıştırırken kısıtlı izleme işlevselliği kullanılabilir. İçinde <`listeners`> öğesi yapılandırma dosyasında ekleyebileceğiniz tek türleridir <xref:System.Diagnostics.TextWriterTraceListener> ve yeni <xref:System.Diagnostics.EventSchemaTraceListener>. Standart kullanımını <xref:System.Diagnostics.XmlWriterTraceListener> eksik veya yanlış günlüklerinde neden olabilir.  
  
 Desteklenen iz kaynakları şunlardır:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, ve <xref:System.IdentityModel.Tokens>.  
  
 Aşağıdaki izleme kaynakları desteklenmez:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://msdn.microsoft.com/library/system.servicemodel.internal.transactionbridge.aspx)]
  
 Aşağıdaki üyeleri <xref:System.Diagnostics.TraceOptions> numaralandırma belirtilmemelidir:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 İzleme bir kısmi güven ortamında kullanırken, uygulama İzleme dinleyicisi çıktısını depolamak için yeterli izinlere sahip olduğundan emin olun. Örneğin, kullanırken <xref:System.Diagnostics.TextWriterTraceListener> izleme çıktısına bir metin dosyasına yazmak için uygulamanın gerekli FileIOPermission başarıyla izleme dosyasına yazmak için gerekli olduğundan emin olun.  
  
> [!NOTE]
>  Yinelenen hata izleme dosyaları taşmasını önlemek için kaynağın veya ilk güvenlik hatasından sonra işlem izleme WCF devre dışı bırakır. Kaynağa erişim veya bir eylem gerçekleştirmek için bir girişimde ilk kez her başarısız kaynağa erişim için bir özel durum izleme yoktur.  
  
## <a name="wcf-service-host"></a>WCF hizmet konağı  
 WCF hizmet konağı, kısmi güven desteklemez. Bir WCF hizmetini kısmi güven kullanmak istiyorsanız, WCF hizmet kitaplığı proje şablonu Visual Studio'da hizmetinizi oluşturmak için kullanmayın. Bunun yerine, kısmi güven WCF desteklenen bir Web sunucusu hizmeti barındıran WCF Hizmeti Web site şablonunu seçerek Visual Studio'da yeni bir Web sitesi oluşturun.  
  
## <a name="other-limitations"></a>Diğer sınırlamalar  
 WCF üzerine barındırma uygulama tarafından uygulanan güvenlik konuları için genellikle sınırlıdır. WCF bir XAML tarayıcı uygulaması (XBAP) barındırılıyorsa, bu örneğin, XBAP sınırlamalara tabi açıklandığı olduğu [Windows Presentation Foundation kısmi güven güvenliği](https://go.microsoft.com/fwlink/?LinkId=89138).  
  
 İndigo2 bir kısmi güven ortamında çalıştırırken aşağıdaki ek özellikleri etkin değil:  
  
-   Windows Yönetim Araçları (WMI)  
  
-   Olay günlüğü yalnızca kısmen etkinleştirildi (içindeki tartışmalara bakın **tanılama** bölümü).  
  
-   Performans sayaçları  
  
 Kısmi güven ortamında desteklenmez WCF özelliklerinin kullanımını özel durumlar çalışma zamanında neden olabilir.  
  
## <a name="unlisted-features"></a>Listede bulunmayan özellikleri  
 Kısmi güven ortamında çalışan kaynağa erişmek veya içinde eylemi uygulamak denemek olduğunda bilgilerini veya bu eylemi bir parça kullanılamaz bulmak için en iyi yolu bir `try` blok ve ardından `catch` hatası. Yinelenen hata izleme dosyaları taşmasını önlemek için kaynağın veya ilk güvenlik hatasından sonra işlem izleme WCF devre dışı bırakır. Kaynağa erişim veya bir eylem gerçekleştirmek için bir girişimde ilk kez her başarısız kaynağa erişim için bir özel durum izleme yoktur.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Desteklenen Dağıtım Senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)
- [Kısmi Güven En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
