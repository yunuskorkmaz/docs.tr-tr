---
title: Kısmi Güven Özelliği Uyumluluğu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
caps.latest.revision: 75
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 20cb6c1cd7a3b06b57bce02d5c3caacc7e2e42b7
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/27/2018
---
# <a name="partial-trust-feature-compatibility"></a>Kısmi Güven Özelliği Uyumluluğu
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kısmen güvenilen bir ortamda çalışan sınırlı işlevlerinin bir alt kümesini destekler. Kısmi güvende desteklenen özellikler senaryoları belirli bir dizi açıklandığı şekilde tasarlanmış [desteklenen dağıtım senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) konu.  
  
## <a name="minimum-permission-requirements"></a>Minimum izin gereksinimleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] özelliklerinin bir kısmı ya da aşağıdaki standart adlandırılmış izin kümeleri altında çalışan uygulamaları destekler:  
  
-   Orta güven izinleri  
  
-   Internet bölgesi izinleri  
  
 Kullanılmaya çalışılıyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] daha kısıtlayıcı izinler ile kısmen güvenilir uygulamalar çalışma zamanında güvenlik özel durumlarda neden olabilir.  
  
## <a name="contracts"></a>Sözleşmeler  
 Sözleşmeler, kısmi güven altında çalışırken aşağıdaki kısıtlamalar geçerlidir:  
  
-   Uygulayan hizmet sınıfı `[ServiceContract]` arabirimi olmalıdır `public` ve bir `public` Oluşturucusu. Bunu tanımlıyorsa `[OperationContract]` yöntemleri, bunlar olmalıdır `public`. Bunun yerine uyguluyorsa bir `[ServiceContract]` arabirimi, bu yöntem uygulamalarını olabilir açık veya `private`, koşuluyla `[ServiceContract]` arabirimi `public`.  
  
-   Kullanırken `[ServiceKnownType]` özniteliği, belirtilen yöntemi olmalıdır `public`.  
  
-   `[MessageContract]` sınıflar ve üyeleri olabilir `public`. Varsa `[MessageContract]` sınıfı olabilir Uygulama derlemesinde tanımlanan `internal` ve `internal` üyeleri.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 <xref:System.ServiceModel.BasicHttpBinding> Ve <xref:System.ServiceModel.WebHttpBinding> bir kısmi güven ortamda tam olarak desteklenir. <xref:System.ServiceModel.WSHttpBinding> Yalnızca Aktarım güvenlik modu için desteklenir.  
  
 HTTP dışında taşımalar gibi kullandığınız bağlamaları <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>, veya <xref:System.ServiceModel.NetMsmqBinding>, kısmi güven Ortamı'nda çalışırken desteklenmez.  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Özel bağlamalar oluşturulabilir ve bir kısmi güven ortamında kullanılan, ancak bu bölümde belirtilen kısıtlamaları izlemeniz gerekir.  
  
### <a name="transports"></a>Taşımalar  
 İzin verilen tek öğeler aktarım bağlama <xref:System.ServiceModel.Channels.HttpTransportBindingElement> ve <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Kodlayıcılar  
 Aşağıdaki kodlayıcılar izin verilir:  
  
-   Metin Kodlayıcı (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   İkili kodlama (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   Web ileti Kodlayıcı (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 İleti iletim en iyi duruma getirme mekanizmasını (MTOM) kodlayıcılar desteklenmez.  
  
### <a name="security"></a>Güvenlik  
 Kısmen güvenilir uygulamalar kullanabilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]'s aktarım düzeyinde iletişimin güvenliğini sağlamak için güvenlik özellikleri. İleti düzeyi güvenlik desteklenmez. Çalışma zamanında bir özel durum iletisi düzeyi güvenlik kullanmak için bir bağlama yapılandırma sonuçlanır.  
  
### <a name="unsupported-bindings"></a>Desteklenmeyen bağlamaları  
 Güvenilir Mesajlaşma, işlemler veya ileti düzeyi güvenlik bağlamaları desteklenmez.  
  
## <a name="serialization"></a>Serileştirme  
 Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> bir kısmi güven ortamında desteklenir. Ancak, kullanım <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabi olan:  
  
-   Tüm serileştirilebilir `[DataContract]` türleri olmalıdır `public`.  
  
-   Tüm serileştirilebilir `[DataMember]` alanları veya özelliklerinde bir `[DataContract]` türü ortak ve gerekir okuma/yazma. Seri hale getirme ve seri durumdan çıkarma işlemi [readonly](http://go.microsoft.com/fwlink/?LinkID=98854) çalıştırırken alanları desteklenmiyor [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmen güvenilen uygulamada.  
  
-   `[Serializable]` /ISerializable programlama modeli bir kısmi güven ortamında desteklenmez.  
  
-   Bilinen türler, kod veya makine düzeyinde yapılandırma (machine.config) belirtilmelidir. Bilinen türler güvenlik nedenleriyle uygulama düzeyi yapılandırmasında belirtilemez.  
  
-   Türleri uygulayan <xref:System.Runtime.Serialization.IObjectReference> kısmen güvenilen bir ortamda bir özel durum.  
  
 Seri hale getirme bölümüne bakın [kısmi güven en iyi yöntemler](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) kullanırken güvenliği hakkında daha fazla bilgi için <xref:System.Runtime.Serialization.DataContractSerializer> güvenli bir uygulamada kısmen güvenilir.  
  
### <a name="collection-types"></a>Koleksiyon türleri  
 Bazı koleksiyon türleri her ikisini de uygulamak <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.IEnumerable>. Örnekler uygulama türleri <xref:System.Collections.Generic.ICollection%601>. Gibi türler uygulayabileceğiniz bir `public` uyarlamasını `GetEnumerator()`ve açık uygulaması `GetEnumerator()`. Bu durumda, <xref:System.Runtime.Serialization.DataContractSerializer> çağırır `public` uyarlamasını `GetEnumerator()`ve açık uyarlamasını `GetEnumerator()`. Hiçbiri `GetEnumerator()` uygulamalarıdır `public` ve tüm açık, ardından uygulamalarıdır <xref:System.Runtime.Serialization.DataContractSerializer> çağırır `IEnumerable.GetEnumerator()`.  
  
 Koleksiyon için türleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir kısmi güven ortamında hiçbiri çalışan `GetEnumerator()` uygulamalarıdır `public`, veya bunların hiçbiri açık arabirim uygulamaları olan ve sonra bir güvenlik özel durum.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Birçok .NET Framework koleksiyon türleri gibi <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Hashtable> tarafından desteklenmeyen <xref:System.Runtime.Serialization.NetDataContractSerializer> kısmi güvende. Bu tür sahip `[Serializable]` özniteliği olarak ayarlanmış ve bu özniteliğin serileştirme bölümünde daha önce belirtildiği gibi kısmi güvende desteklenmiyor. <xref:System.Runtime.Serialization.DataContractSerializer> Özel bir yolla koleksiyonları değerlendirir ve bu nedenle bu kısıtlamaya alabilir ancak <xref:System.Runtime.Serialization.NetDataContractSerializer> bu kısıtlamayı aşmak için bu tür mekanizması vardır.  
  
 <xref:System.DateTimeOffset> Türü tarafından desteklenmiyor <xref:System.Runtime.Serialization.NetDataContractSerializer> kısmi güvende.  
  
 Bir yedek kullanılamaz <xref:System.Runtime.Serialization.NetDataContractSerializer> (kullanarak <xref:System.Runtime.Serialization.SurrogateSelector> mekanizması) kısmi güvende çalıştırırken. Bu kısıtlama serileştirme değil için bir yedek kullanarak için geçerli olduğunu unutmayın.  
  
## <a name="enabling-common-behaviors-to-run"></a>Çalıştırmak ortak davranışları etkinleştirme  
 Hizmet veya uç nokta davranışları işaretlenmemiş ile <xref:System.Security.AllowPartiallyTrustedCallersAttribute> eklenir (APTCA) özniteliği [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) uygulama kısmi güvende çalıştığında, bir yapılandırma dosyası bölümünü çalıştırmak değil ortam ve hiçbir özel durum oluşur böyle bir durumda. Ortak davranışları çalışan zorlamak için aşağıdaki seçeneklerden birini yapmanız gerekir:  
  
-   Ortak davranışı ile işaretle <xref:System.Security.AllowPartiallyTrustedCallersAttribute> bir kısmi güven uygulaması olarak dağıtıldığında çalışabilmesi özniteliği. Bir kayıt defteri girdisi bilgisayarda APTCA işaretlenmiş derlemeleri çalışmasını engellemek için ayarlanabilir unutmayın. biçimindeki telefon numarasıdır.  
  
-   Uygulama kullanıcılar bir kısmi güven ortamında uygulamayı çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremez tam güvenilir bir uygulama olarak dağıtılırsa emin olun. Bunu yapmak, davranışı çalışmaz ve hiçbir özel durum oluşur. Bunu sağlamak için bkz: **levelfinal** seçeneği kullanılarak [Caspol.exe (kod erişim güvenliği ilke aracı)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Bir ortak davranışı örneği için bkz: [nasıl yapılır: Lock aşağı Enterprise uç noktalarını](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Yapılandırma  
 Bunun tek istisnası kısmen güvenilen kod yalnızca yükleyebilir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yerel yapılandırma bölümlerinin `app.config` dosya. Yüklemek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma bölümler bu başvuruyu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bölümleri machine.config veya kök web.config dosyasında ConfigurationPermission(Unrestricted) gerektirir. Bu izin olmadan başvurular [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapılandırma yüklendiğinde bir özel durum yerel yapılandırma dosyası sonuçlarında dışında yapılandırma bölümlerinin (davranışları, bağlamaları).  
  
 Bir özel durum bilinen türü seri hale getirme, bu konunun serileştirme bölümünde açıklandığı gibi yapılandırmadır.  
  
> [!IMPORTANT]
>  Yapılandırma uzantıları yalnızca tam güven altında çalışırken desteklenir.  
  
## <a name="diagnostics"></a>Tanılamalar  
  
### <a name="event-logging"></a>Etkinlikleri Günlüğe Kaydetme  
 Sınırlı olay günlüğü altında kısmi güven desteklenir. Etkinleştirme hataları yalnızca hizmet ve izleme/ileti günlüğe kaydetme hatalarının olay günlüğüne kaydedilir. En fazla bir işlem tarafından günlüğe olayları olay günlüğüne aşırı iletileri yazılmasını engellemek için 5, sayısıdır.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 Günlük kaydı olduğunda çalışmaz ileti [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmi güven bir ortamda çalıştırılabilir. Kısmi güven altında etkinleştirilirse, hizmeti etkinleştirme başlayabildiğinden, ancak hiçbir ileti günlüğe kaydedilir.  
  
### <a name="tracing"></a>İzleme  
 Kısıtlı izleme işlevselliği, kısmi güven ortamında çalışan olduğunda kullanılabilir. İçinde <`listeners`> öğesi yapılandırma dosyasında ekleyebileceğiniz yalnızca türleridir <xref:System.Diagnostics.TextWriterTraceListener> ve yeni <xref:System.Diagnostics.EventSchemaTraceListener>. Standart kullanımını <xref:System.Diagnostics.XmlWriterTraceListener> eksik veya hatalı günlüklerinde neden olabilir.  
  
 Desteklenen izleme kaynakları şunlardır:  
  
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
  
 İzleme bir kısmi güven ortamında kullanırken, uygulama İzleme dinleyicisi çıktısını depolamak için yeterli izinlere sahip olduğundan emin olun. Örneğin, kullanırken <xref:System.Diagnostics.TextWriterTraceListener> İzleme çıktısı bir metin dosyasına yazma için uygulama başarıyla izleme dosyaya yazmak için gerekli gerekli FileIOPermission olduğundan emin olun.  
  
> [!NOTE]
>  İzleme dosyaları yinelenen hatalarla taşmasını önlemek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kaynak ya da ilk güvenlik hatasından sonra işlem izlemeyi devre dışı bırakır. Kaynağa erişim veya eylemi gerçekleştirmek için bir girişimde ilk kez her başarısız kaynak erişimi için bir özel durum izleme yoktur.  
  
## <a name="wcf-service-host"></a>WCF hizmet konağı  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet ana bilgisayarı, kısmi güven desteklemez. Kullanmak istiyorsanız bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmet kısmi güvende, kullanmayın [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] hizmetinizi oluşturmak için Visual Studio'da hizmet kitaplığı proje şablonu. Bunun yerine, Visual Studio'da oluşturma seçerek yeni bir Web sitesi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir Web sunucusunda hizmetinde barındırabilir Hizmet Web sitesi şablonu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kısmi güven desteklenir.  
  
## <a name="other-limitations"></a>Diğer sınırlamaları  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] genellikle üzerine barındırma uygulaması tarafından uygulanan güvenlik konuları sınırlıdır. Örneğin, varsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] barındırılan bir XAML tarayıcısı uygulaması (XBAP içinde), XBAP sınırlamalara tabi açıklandığı gibi olmasından [Windows Presentation Foundation kısmi güven Security](http://go.microsoft.com/fwlink/?LinkId=89138).  
  
 İndigo2 bir kısmi güven ortamında çalıştırırken aşağıdaki ek özellikler etkin değil:  
  
-   Windows Yönetim Araçları (WMI)  
  
-   Olay günlüğü yalnızca kısmen etkin (tartışmada bkz **tanılama** bölümü).  
  
-   Performans sayaçları  
  
 Kullanımı [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir kısmi güven ortamında desteklenmeyen özellikler çalışma zamanında özel durumlara neden olabilir.  
  
## <a name="unlisted-features"></a>Listede bulunmayan özellikleri  
 Kısmi güven ortamında çalışan kaynağa erişim veya bir işlem içinde denemek için olduğunda bir bilgi veya eylem kullanılamaz bulmak için en iyi yolu bir `try` bloğu ve ardından `catch` hatası. İzleme dosyaları yinelenen hatalarla taşmasını önlemek için [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kaynak ya da ilk güvenlik hatasından sonra işlem izlemeyi devre dışı bırakır. Kaynağa erişim veya eylemi gerçekleştirmek için bir girişimde ilk kez her başarısız kaynak erişimi için bir özel durum izleme yoktur.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Desteklenen Dağıtım Senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 [Kısmi Güven En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
