---
title: Kısmi Güven Özelliği Uyumluluğu
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 85e34e365d125fe4f00756549ba5bda4311b78f8
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579169"
---
# <a name="partial-trust-feature-compatibility"></a>Kısmi Güven Özelliği Uyumluluğu
Windows Communication Foundation (WCF) kısmen güvenilen bir ortamda çalışırken sınırlı bir işlev alt kümesini destekler. Kısmi güvende desteklenen özellikler, [Desteklenen Dağıtım senaryoları](supported-deployment-scenarios.md) konusunda açıklandığı gibi belirli bir senaryo kümesi etrafında tasarlanmıştır.  
  
## <a name="minimum-permission-requirements"></a>En düşük Izin gereksinimleri  
 WCF, aşağıdaki standart adlandırılmış izin kümelerinden biri altında çalışan uygulamalardaki özelliklerin bir alt kümesini destekler:  
  
- Orta güven izinleri  
  
- Internet bölgesi izinleri  
  
 Daha kısıtlayıcı izinlerle kısmen güvenilen uygulamalarda WCF kullanılmaya çalışılması, çalışma zamanında güvenlik özel durumlarına neden olabilir.  
  
## <a name="contracts"></a>Sözleşmeler  
 Sözleşmeler kısmi güven altında çalışırken aşağıdaki kısıtlamalara tabidir:  
  
- Arabirimi uygulayan hizmet sınıfı, `[ServiceContract]` olmalıdır `public` ve bir oluşturucuya sahip olmalıdır `public` . `[OperationContract]`Yöntemleri tanımlıyorsa, bunlar olmalıdır `public` . Bunun yerine bir arabirim uygularsa `[ServiceContract]` , bu yöntem uygulamaları açık veya `private` arabirimin olması şartıyla açık olabilir `[ServiceContract]` `public` .  
  
- `[ServiceKnownType]`Özniteliği kullanılırken, belirtilen yöntemin olması gerekir `public` .  
  
- `[MessageContract]`sınıflar ve üyeleri olabilir `public` . `[MessageContract]`Sınıf uygulama derlemesinde tanımlıysa, `internal` ve `internal` üyeleri olabilir.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 <xref:System.ServiceModel.BasicHttpBinding>Ve <xref:System.ServiceModel.WebHttpBinding> kısmi güven ortamında tamamen desteklenir. <xref:System.ServiceModel.WSHttpBinding>Yalnızca Aktarım güvenliği modu için desteklenir.  
  
 ,, Veya gibi HTTP dışındaki aktarımları kullanan bağlamalar, <xref:System.ServiceModel.NetTcpBinding> <xref:System.ServiceModel.NetNamedPipeBinding> <xref:System.ServiceModel.NetMsmqBinding> kısmi güven ortamında çalışırken desteklenmez.  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Özel Bağlamalar kısmi güven ortamında oluşturulabilir ve kullanılabilir, ancak bu bölümde belirtilen kısıtlamaların izlenmesi gerekir.  
  
### <a name="transports"></a>Taşımalar  
 Yalnızca ve izin verilen aktarım bağlama öğeleri <xref:System.ServiceModel.Channels.HttpTransportBindingElement> <xref:System.ServiceModel.Channels.HttpsTransportBindingElement> .  
  
### <a name="encoders"></a>Kodlayıcılar  
 Aşağıdaki kodlayıcılara izin verilir:  
  
- Metin Kodlayıcısı ( <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> ).  
  
- İkili kodlayıcı ( <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> ).  
  
- Web Iletisi Kodlayıcısı ( <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement> ).  
  
 Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlayıcıları desteklenmez.  
  
### <a name="security"></a>Güvenlik  
 Kısmen güvenilir uygulamalar, iletişim güvenliğini sağlamak için WCF 'nin aktarım düzeyi güvenlik özelliklerini kullanabilir. İleti düzeyi güvenlik desteklenmez. Bir bağlamayı ileti düzeyi güvenlik ile kullanmak için yapılandırma, çalışma zamanında bir özel durum ile sonuçlanır.  
  
### <a name="unsupported-bindings"></a>Desteklenmeyen bağlamalar  
 Güvenilir Mesajlaşma, işlemler veya ileti düzeyi güvenlik kullanan bağlamalar desteklenmez.  
  
## <a name="serialization"></a>Serileştirme  
 Hem hem de <xref:System.Runtime.Serialization.DataContractSerializer> , <xref:System.Xml.Serialization.XmlSerializer> kısmi güven ortamında desteklenir. Ancak, öğesinin kullanımı <xref:System.Runtime.Serialization.DataContractSerializer> aşağıdaki koşullara tabidir:  
  
- Tüm serileştirilebilir `[DataContract]` türler olmalıdır `public` .  
  
- Bir türdeki tüm seri hale getirilebilir `[DataMember]` alanların veya özelliklerin `[DataContract]` ortak ve okuma/yazma olması gerekir. [Salt okunur](https://go.microsoft.com/fwlink/?LinkID=98854) alanların serileştirilmesi ve serisini kaldırma, kısmen güvenilen BIR uygulamada WCF çalıştırılırken desteklenmez.  
  
- `[Serializable]`/ISerializable programlama modeli kısmi güven ortamında desteklenmez.  
  
- Bilinen türler kod veya makine düzeyinde yapılandırma (Machine. config) içinde belirtilmelidir. Bilinen türler güvenlik nedeniyle uygulama düzeyi yapılandırmasında belirtilemez.  
  
- Uygulayan türler <xref:System.Runtime.Serialization.IObjectReference> kısmen güvenilen bir ortamda özel durum oluşturur.  
  
 Kısmen güvenilen bir uygulamada güvenle kullanırken güvenlik hakkında daha fazla bilgi için [kısmi güven En Iyi uygulamaları](partial-trust-best-practices.md) bölümündeki serileştirme bölümüne bakın <xref:System.Runtime.Serialization.DataContractSerializer> .  
  
### <a name="collection-types"></a>Koleksiyon türleri  
 Bazı koleksiyon türleri hem hem de uygular <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Collections.IEnumerable> . Örnek, uygulayan türler içerir <xref:System.Collections.Generic.ICollection%601> . Bu tür türler, uygulamasının bir `public` uygulamasını `GetEnumerator()` ve açık bir uygulamasını uygulayabilir `GetEnumerator()` . Bu durumda, uygulamasının <xref:System.Runtime.Serialization.DataContractSerializer> `public` `GetEnumerator()` Açık uygulamasını değil, uygulamasını çağırır `GetEnumerator()` . `GetEnumerator()`Uygulamalardan hiçbiri `public` ve hepsi açık uygulamalartadıysanız, öğesini <xref:System.Runtime.Serialization.DataContractSerializer> çağırır `IEnumerable.GetEnumerator()` .  
  
 Bir kısmi güven ortamında WCF çalışırken koleksiyon türleri için, uygulamalardan hiçbiri yoksa `GetEnumerator()` `public` veya hiçbiri açık arabirim uygulamaları değilse, bir güvenlik özel durumu oluşturulur.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 , Ve gibi birçok .NET Framework koleksiyon türü, <xref:System.Collections.Generic.List%601> <xref:System.Collections.ArrayList> <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Hashtable> <xref:System.Runtime.Serialization.NetDataContractSerializer> kısmi güvende içinde desteklenmez. Bu türlerin `[Serializable]` özniteliği kümesi vardır ve daha önce serileştirme bölümünde belirtildiği gibi, bu öznitelik kısmi güvende desteklenmez. , <xref:System.Runtime.Serialization.DataContractSerializer> Koleksiyonları özel bir şekilde davranır ve bu kısıtlamayı aşmak, ancak <xref:System.Runtime.Serialization.NetDataContractSerializer> Bu kısıtlamayı aşmak için böyle bir mekanizması yoktur.  
  
 <xref:System.DateTimeOffset>Tür <xref:System.Runtime.Serialization.NetDataContractSerializer> kısmi güvende tarafından desteklenmiyor.  
  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>Kısmi güvende çalışırken (mekanizması kullanılarak) bir vekil ile birlikte kullanılamaz <xref:System.Runtime.Serialization.SurrogateSelector> . Bu kısıtlamanın, bir yedek kullanılarak, serileştirilmek için geçerli olduğunu unutmayın.  
  
## <a name="enabling-common-behaviors-to-run"></a>Ortak davranışları çalıştırmak için etkinleştirme  
 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>Bir yapılandırma dosyasının bölümüne eklenen öznitelik (APTCA) ile işaretlenmemiş hizmet veya uç nokta davranışları, [\<commonBehaviors>](../../configure-apps/file-schema/wcf/commonbehaviors.md) Uygulama kısmi bir güven ortamında çalıştırıldığında ve bu gerçekleştiğinde hiçbir özel durum atılışında çalıştırılmaz. Ortak davranışları çalıştırmaya zorlamak için aşağıdaki seçeneklerden birini yapmanız gerekir:  
  
- <xref:System.Security.AllowPartiallyTrustedCallersAttribute>Kısmi güven uygulaması olarak dağıtıldığında çalışabilmesi için ortak davranışınızı özniteliğiyle işaretleyin. APTCA tarafından işaretlenmiş derlemelerin çalıştırılmasını engellemek için bilgisayarda bir kayıt defteri girişi ayarlanmayacağınızı unutmayın. .  
  
- Uygulamanın, uygulamayı kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremediği tam güvenilir bir uygulama olarak dağıtıldığından emin olun. Bunu yapabilirse, davranış çalışmaz ve hiçbir özel durum oluşturulmaz. Bunu sağlamak için, [Caspol. exe (kod erişimi güvenlik Ilkesi aracı)](../../tools/caspol-exe-code-access-security-policy-tool.md)kullanılarak **LevelFinal** seçeneğine bakın.  
  
 Yaygın bir davranış örneği için bkz. [nasıl yapılır: kuruluştaki uç noktaları kilitleme](../extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Yapılandırma  
 Tek bir özel durum ile, kısmen güvenilen kod yalnızca yerel dosyadaki WCF yapılandırma bölümlerini yükleyebilir `app.config` . Machine. config dosyasındaki WCF bölümlerine veya bir kök Web. config dosyasına başvuruda bulunan WCF yapılandırma bölümlerinin yüklenmesi için ConfigurationPermission (Kısıtlamasız) gerekir. Bu izin olmadan, yerel yapılandırma dosyası dışındaki WCF yapılandırma bölümlerine (davranışlar, bağlamalar) başvurular, yapılandırma yüklendiğinde bir özel durumla sonuçlanır.  
  
 Bu konunun serileştirme bölümünde açıklandığı gibi, bir özel durum serileştirme için bilinen tür yapılandırmadır.  
  
> [!IMPORTANT]
> Yapılandırma uzantıları yalnızca tam güven altında çalışırken desteklenir.  
  
## <a name="diagnostics"></a>Tanılama  
  
### <a name="event-logging"></a>Etkinlikleri Günlüğe Kaydetme  
 Kısmi güven altında sınırlı olay günlüğü desteklenir. Olay günlüğüne yalnızca hizmet etkinleştirme hataları ve izleme/ileti günlüğe kaydetme hataları kaydedilir. Olay günlüğüne aşırı ileti yazılmasını önlemek için bir işlem tarafından günlüğe kaydedilen en fazla olay sayısı 5 ' tir.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 WCF kısmi güven ortamında çalıştırıldığında ileti günlüğe kaydetme çalışmaz. Kısmi güven altında etkinleştirilirse, hizmet etkinleştirmesi başarısız olmaz, ancak hiçbir ileti günlüğe kaydedilmez.  
  
### <a name="tracing"></a>İzleme  
 Kısıtlı izleme işlevselliği, kısmi güven ortamında çalışırken kullanılabilir. `listeners`Yapılandırma dosyasındaki <> öğesinde, ekleyebileceğiniz tek tür <xref:System.Diagnostics.TextWriterTraceListener> ve yeni <xref:System.Diagnostics.EventSchemaTraceListener> . Standart kullanımı <xref:System.Diagnostics.XmlWriterTraceListener> tamamlanmamış veya hatalı günlüklere neden olabilir.  
  
 Desteklenen izleme kaynakları şunlardır:  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy> , <xref:System.IdentityModel.Selectors> , ve <xref:System.IdentityModel.Tokens> .  
  
 Aşağıdaki izleme kaynakları desteklenmez:  
  
- CardSpace  
  
- <xref:System.IO.Log>  

- [System. ServiceModel. Internal. TransactionBridge](https://docs.microsoft.com/previous-versions/aa346556(v=vs.110))]
  
 Numaralandırmanın aşağıdaki üyeleri <xref:System.Diagnostics.TraceOptions> belirtilmemelidir:  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 İzlemeyi kısmi güven ortamında kullanırken, uygulamanın İzleme dinleyicisinin çıkışını depolamak için yeterli izinlere sahip olduğundan emin olun. Örneğin, <xref:System.Diagnostics.TextWriterTraceListener> izleme çıkışını bir metin dosyasına yazmak için kullanırken, uygulamanın izleme dosyasına başarıyla yazmak için gerekli dosya dosyası ' na sahip olduğundan emin olun.  
  
> [!NOTE]
> İzleme dosyalarının yinelenen hatalarla taşmasını önlemek için, WCF ilk güvenlik hatasından sonra kaynağın veya eylemin izlenmesini devre dışı bırakır. Her başarısız kaynak erişimi için bir özel durum izlemesi vardır. kaynağa erişmek veya eylemi gerçekleştirmek için ilk kez girişimde bulunuldu.  
  
## <a name="wcf-service-host"></a>WCF hizmet ana bilgisayarı  
 WCF hizmeti ana bilgisayarı kısmi güveni desteklemez. Kısmi güvende bir WCF hizmeti kullanmak istiyorsanız, Visual Studio 'da WCF hizmet kitaplığı proje şablonunu kullanarak hizmetinizi oluşturun. Bunun yerine, Visual Studio 'da, WCF kısmi güveninin desteklendiği bir Web sunucusunda hizmeti barındırabilen WCF hizmeti Web sitesi şablonunu seçerek yeni bir Web sitesi oluşturun.  
  
## <a name="other-limitations"></a>Diğer sınırlamalar  

  WCF, genel olarak, barındırma uygulaması tarafından bu uygulamaya getirilen güvenlik hususları ile sınırlıdır. Örneğin, WCF bir XAML tarayıcı uygulamasında (XBAP) barındırılıyorsa, [Windows Presentation Foundation kısmi güven güvenliği](../../wpf/wpf-partial-trust-security.md)' nde açıklandığı gıbı, XBAP kısıtlamalarına tabidir.  
  
 Kısmi güven ortamında İndigo2 çalıştırılırken aşağıdaki ek özellikler etkinleştirilmemiştir:  
  
- Windows Yönetim Araçları (WMI)  
  
- Olay günlüğü yalnızca kısmen etkinleştirilmiştir ( **Tanılama** bölümünde tartışma bölümüne bakın).  
  
- Performans sayaçları  
  
 Kısmi güven ortamında desteklenmeyen WCF özelliklerinin kullanımı, çalışma zamanında özel durumlara neden olabilir.  
  
## <a name="unlisted-features"></a>Listelenmemiş Özellikler  
 Kısmi güven ortamında çalışırken bir bilgi veya eylem parçasının kullanılamaz olduğunu öğrenmenin en iyi yolu, kaynağa erişmeyi veya bir bloğun içinde eylemi yapmayı denemenin `try` yanı sıra `catch` başarısız olur. İzleme dosyalarının yinelenen hatalarla taşmasını önlemek için, WCF ilk güvenlik hatasından sonra kaynağın veya eylemin izlenmesini devre dışı bırakır. Her başarısız kaynak erişimi için bir özel durum izlemesi vardır. kaynağa erişmek veya eylemi gerçekleştirmek için ilk kez girişimde bulunuldu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Desteklenen Dağıtım Senaryoları](supported-deployment-scenarios.md)
- [Kısmi Güven En İyi Uygulamaları](partial-trust-best-practices.md)
