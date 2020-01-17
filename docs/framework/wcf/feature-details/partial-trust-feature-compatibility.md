---
title: Kısmi Güven Özelliği Uyumluluğu
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 3e0f1c2f673d4ba603df7da431d10c211cf779ac
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212117"
---
# <a name="partial-trust-feature-compatibility"></a>Kısmi Güven Özelliği Uyumluluğu
Windows Communication Foundation (WCF) kısmen güvenilen bir ortamda çalışırken sınırlı bir işlev alt kümesini destekler. Kısmi güvende desteklenen özellikler, [Desteklenen Dağıtım senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) konusunda açıklandığı gibi belirli bir senaryo kümesi etrafında tasarlanmıştır.  
  
## <a name="minimum-permission-requirements"></a>En düşük Izin gereksinimleri  
 WCF, aşağıdaki standart adlandırılmış izin kümelerinden biri altında çalışan uygulamalardaki özelliklerin bir alt kümesini destekler:  
  
- Orta güven izinleri  
  
- Internet bölgesi izinleri  
  
 Daha kısıtlayıcı izinlerle kısmen güvenilen uygulamalarda WCF kullanılmaya çalışılması, çalışma zamanında güvenlik özel durumlarına neden olabilir.  
  
## <a name="contracts"></a>Sözleşmeler  
 Sözleşmeler kısmi güven altında çalışırken aşağıdaki kısıtlamalara tabidir:  
  
- `[ServiceContract]` arabirimini uygulayan hizmet sınıfı `public` ve `public` oluşturucusuna sahip olmalıdır. `[OperationContract]` yöntemleri tanımlıyorsa, bunların `public`olması gerekir. Bunun yerine bir `[ServiceContract]` arabirimi uygularsa, bu yöntem uygulamaları açık veya `private`olabilir, `[ServiceContract]` arabirimi `public`olur.  
  
- `[ServiceKnownType]` özniteliği kullanılırken, belirtilen yöntem `public`olmalıdır.  
  
- `[MessageContract]` sınıfları ve üyeleri `public`olabilir. `[MessageContract]` sınıfı uygulama derlemesinde tanımlıysa, `internal` ve `internal` üyelere sahip olabilir.  
  
## <a name="system-provided-bindings"></a>Sistem Tarafından Sağlanan Bağlamalar  
 <xref:System.ServiceModel.BasicHttpBinding> ve <xref:System.ServiceModel.WebHttpBinding> kısmi güven ortamında tamamen desteklenir. <xref:System.ServiceModel.WSHttpBinding> yalnızca Aktarım güvenliği modu için desteklenir.  
  
 <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>veya <xref:System.ServiceModel.NetMsmqBinding>gibi HTTP dışındaki aktarımları kullanan bağlamalar, kısmi güven ortamında çalışırken desteklenmez.  
  
## <a name="custom-bindings"></a>Özel Bağlamalar  
 Özel Bağlamalar kısmi güven ortamında oluşturulabilir ve kullanılabilir, ancak bu bölümde belirtilen kısıtlamaların izlenmesi gerekir.  
  
### <a name="transports"></a>Taşımalar  
 Yalnızca <xref:System.ServiceModel.Channels.HttpTransportBindingElement> izin verilen aktarım bağlama öğeleri <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Kodlayıcılar  
 Aşağıdaki kodlayıcılara izin verilir:  
  
- Metin Kodlayıcısı (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
- İkili kodlayıcı (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
- Web Iletisi Kodlayıcısı (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Ileti Iletimi Iyileştirme mekanizması (MTOM) kodlayıcıları desteklenmez.  
  
### <a name="security"></a>Güvenlik  
 Kısmen güvenilir uygulamalar, iletişim güvenliğini sağlamak için WCF 'nin aktarım düzeyi güvenlik özelliklerini kullanabilir. İleti düzeyi güvenlik desteklenmez. Bir bağlamayı ileti düzeyi güvenlik ile kullanmak için yapılandırma, çalışma zamanında bir özel durum ile sonuçlanır.  
  
### <a name="unsupported-bindings"></a>Desteklenmeyen bağlamalar  
 Güvenilir Mesajlaşma, işlemler veya ileti düzeyi güvenlik kullanan bağlamalar desteklenmez.  
  
## <a name="serialization"></a>Serileştirme  
 <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> her ikisi de kısmi güven ortamında desteklenir. Ancak, <xref:System.Runtime.Serialization.DataContractSerializer> kullanımı aşağıdaki koşullara tabidir:  
  
- Tüm seri hale getirilebilir `[DataContract]` türleri `public`olmalıdır.  
  
- `[DataContract]` bir türdeki tüm seri hale getirilebilir `[DataMember]` alanları veya özellikleri ortak ve okuma/yazma olmalıdır. [Salt okunur](https://go.microsoft.com/fwlink/?LinkID=98854) alanların serileştirilmesi ve serisini kaldırma, kısmen güvenilen BIR uygulamada WCF çalıştırılırken desteklenmez.  
  
- `[Serializable]`/ISerializable programlama modeli kısmi güven ortamında desteklenmez.  
  
- Bilinen türler kod veya makine düzeyinde yapılandırma (Machine. config) içinde belirtilmelidir. Bilinen türler güvenlik nedeniyle uygulama düzeyi yapılandırmasında belirtilemez.  
  
- <xref:System.Runtime.Serialization.IObjectReference> uygulayan türler kısmen güvenilen bir ortamda özel durum oluşturur.  
  
 Kısmen güvenilen bir uygulamada güvenli <xref:System.Runtime.Serialization.DataContractSerializer> kullanırken güvenlik hakkında daha fazla bilgi için [kısmi güven En Iyi uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) bölümündeki serileştirme bölümüne bakın.  
  
### <a name="collection-types"></a>Koleksiyon türleri  
 Bazı koleksiyon türleri <xref:System.Collections.Generic.IEnumerable%601> ve <xref:System.Collections.IEnumerable>uygular. Örnek, <xref:System.Collections.Generic.ICollection%601>uygulayan türler içerir. Bu tür türler `GetEnumerator()``public` uygulamasını ve açık bir `GetEnumerator()`uygulamasını uygulayabilir. Bu durumda <xref:System.Runtime.Serialization.DataContractSerializer>, `GetEnumerator()`açık uygulamasını değil `GetEnumerator()``public` uygulamasını çağırır. `GetEnumerator()` uygulamalardan hiçbiri `public` ve tümü açık uygulamalardır <xref:System.Runtime.Serialization.DataContractSerializer> `IEnumerable.GetEnumerator()`çağırır.  
  
 Bir kısmi güven ortamında WCF çalışırken, koleksiyon türleri için `GetEnumerator()` uygulamalarından hiçbiri `public`yoksa veya hiçbiri açık arabirim uygulamaları değilse, bir güvenlik özel durumu oluşturulur.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> ve <xref:System.Collections.Hashtable> gibi birçok .NET Framework koleksiyon türü kısmi güvende <xref:System.Runtime.Serialization.NetDataContractSerializer> tarafından desteklenmez. Bu türlerin `[Serializable]` özniteliği ayarlanmış ve daha önce serileştirme bölümünde belirtildiği gibi, bu öznitelik kısmi güvende desteklenmez. <xref:System.Runtime.Serialization.DataContractSerializer>, koleksiyonlara özel bir şekilde davranır ve bu kısıtlamayı aşmak için, bu kısıtlamayı aşmak için <xref:System.Runtime.Serialization.NetDataContractSerializer> böyle bir mekanizmaya sahip değildir.  
  
 <xref:System.DateTimeOffset> türü kısmi güvende <xref:System.Runtime.Serialization.NetDataContractSerializer> tarafından desteklenmiyor.  
  
 Kısmi güvende çalışırken, bir yedek <xref:System.Runtime.Serialization.NetDataContractSerializer> (<xref:System.Runtime.Serialization.SurrogateSelector> mekanizması kullanılarak) kullanılamaz. Bu kısıtlamanın, bir yedek kullanılarak, serileştirilmek için geçerli olduğunu unutmayın.  
  
## <a name="enabling-common-behaviors-to-run"></a>Ortak davranışları çalıştırmak için etkinleştirme  
 Bir yapılandırma dosyasının [\<Commondavranışları >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) bölümüne eklenen <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliği (aptca) ile işaretlenmeyen hizmet veya uç nokta davranışları, uygulama kısmi güven ortamında çalıştırıldığında ve bu gerçekleştiğinde hiçbir özel durum atılışında çalıştırılmaz. Ortak davranışları çalıştırmaya zorlamak için aşağıdaki seçeneklerden birini yapmanız gerekir:  
  
- Kısmi güven uygulaması olarak dağıtıldığında çalışabilmesi için, <xref:System.Security.AllowPartiallyTrustedCallersAttribute> özniteliğiyle ortak davranışınızı işaretleyin. APTCA tarafından işaretlenmiş derlemelerin çalıştırılmasını engellemek için bilgisayarda bir kayıt defteri girişi ayarlanmayacağınızı unutmayın. .  
  
- Uygulamanın, uygulamayı kısmi güven ortamında çalıştırmak için kod erişimi güvenlik ayarlarını değiştiremediği tam güvenilir bir uygulama olarak dağıtıldığından emin olun. Bunu yapabilirse, davranış çalışmaz ve hiçbir özel durum oluşturulmaz. Bunu sağlamak için, [Caspol. exe (kod erişimi güvenlik Ilkesi aracı)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md)kullanılarak **LevelFinal** seçeneğine bakın.  
  
 Yaygın bir davranış örneği için bkz. [nasıl yapılır: kuruluştaki uç noktaları kilitleme](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Yapılandırma  
 Tek bir özel durum ile, kısmen güvenilen kod yalnızca yerel `app.config` dosyasındaki WCF yapılandırma bölümlerini yükleyebilir. Machine. config dosyasındaki WCF bölümlerine veya bir kök Web. config dosyasına başvuruda bulunan WCF yapılandırma bölümlerinin yüklenmesi için ConfigurationPermission (Kısıtlamasız) gerekir. Bu izin olmadan, yerel yapılandırma dosyası dışındaki WCF yapılandırma bölümlerine (davranışlar, bağlamalar) başvurular, yapılandırma yüklendiğinde bir özel durumla sonuçlanır.  
  
 Bu konunun serileştirme bölümünde açıklandığı gibi, bir özel durum serileştirme için bilinen tür yapılandırmadır.  
  
> [!IMPORTANT]
> Yapılandırma uzantıları yalnızca tam güven altında çalışırken desteklenir.  
  
## <a name="diagnostics"></a>Tanılamalar  
  
### <a name="event-logging"></a>Etkinlikleri Günlüğe Kaydetme  
 Kısmi güven altında sınırlı olay günlüğü desteklenir. Olay günlüğüne yalnızca hizmet etkinleştirme hataları ve izleme/ileti günlüğe kaydetme hataları kaydedilir. Olay günlüğüne aşırı ileti yazılmasını önlemek için bir işlem tarafından günlüğe kaydedilen en fazla olay sayısı 5 ' tir.  
  
### <a name="message-logging"></a>İleti Günlüğe Kaydetme  
 WCF kısmi güven ortamında çalıştırıldığında ileti günlüğe kaydetme çalışmaz. Kısmi güven altında etkinleştirilirse, hizmet etkinleştirmesi başarısız olmaz, ancak hiçbir ileti günlüğe kaydedilmez.  
  
### <a name="tracing"></a>İzleme  
 Kısıtlı izleme işlevselliği, kısmi güven ortamında çalışırken kullanılabilir. Yapılandırma dosyasındaki <`listeners`> öğesinde ekleyebileceğiniz tek türler <xref:System.Diagnostics.TextWriterTraceListener> ve yeni <xref:System.Diagnostics.EventSchemaTraceListener>. Standart <xref:System.Diagnostics.XmlWriterTraceListener> kullanımı tamamlanmamış veya hatalı günlüklere neden olabilir.  
  
 Desteklenen izleme kaynakları şunlardır:  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors> ve <xref:System.IdentityModel.Tokens>.  
  
 Aşağıdaki izleme kaynakları desteklenmez:  
  
- CardSpace  
  
- <xref:System.IO.Log>  

- [System. ServiceModel. Internal. TransactionBridge](https://docs.microsoft.com/previous-versions/aa346556(v=vs.110))]
  
 <xref:System.Diagnostics.TraceOptions> numaralandırmanın aşağıdaki üyeleri belirtilmemelidir:  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 İzlemeyi kısmi güven ortamında kullanırken, uygulamanın İzleme dinleyicisinin çıkışını depolamak için yeterli izinlere sahip olduğundan emin olun. Örneğin, izleme çıkışını bir metin dosyasına yazmak için <xref:System.Diagnostics.TextWriterTraceListener> kullanırken, uygulamanın izleme dosyasına başarıyla yazmak için gerekli dosya dosyası ' na sahip olduğundan emin olun.  
  
> [!NOTE]
> İzleme dosyalarının yinelenen hatalarla taşmasını önlemek için, WCF ilk güvenlik hatasından sonra kaynağın veya eylemin izlenmesini devre dışı bırakır. Her başarısız kaynak erişimi için bir özel durum izlemesi vardır. kaynağa erişmek veya eylemi gerçekleştirmek için ilk kez girişimde bulunuldu.  
  
## <a name="wcf-service-host"></a>WCF hizmet konağı  
 WCF hizmeti ana bilgisayarı kısmi güveni desteklemez. Kısmi güvende bir WCF hizmeti kullanmak istiyorsanız, Visual Studio 'da WCF hizmet kitaplığı proje şablonunu kullanarak hizmetinizi oluşturun. Bunun yerine, Visual Studio 'da, WCF kısmi güveninin desteklendiği bir Web sunucusunda hizmeti barındırabilen WCF hizmeti Web sitesi şablonunu seçerek yeni bir Web sitesi oluşturun.  
  
## <a name="other-limitations"></a>Diğer sınırlamalar  

  WCF, genel olarak, barındırma uygulaması tarafından bu uygulamaya getirilen güvenlik hususları ile sınırlıdır. Örneğin, WCF bir XAML tarayıcı uygulamasında (XBAP) barındırılıyorsa, [Windows Presentation Foundation kısmi güven güvenliği](../../wpf/wpf-partial-trust-security.md)' nde açıklandığı gıbı, XBAP kısıtlamalarına tabidir.  
  
 Kısmi güven ortamında İndigo2 çalıştırılırken aşağıdaki ek özellikler etkinleştirilmemiştir:  
  
- Windows Yönetim Araçları (WMI)  
  
- Olay günlüğü yalnızca kısmen etkinleştirilmiştir ( **Tanılama** bölümünde tartışma bölümüne bakın).  
  
- Performans sayaçları  
  
 Kısmi güven ortamında desteklenmeyen WCF özelliklerinin kullanımı, çalışma zamanında özel durumlara neden olabilir.  
  
## <a name="unlisted-features"></a>Listelenmemiş Özellikler  
 Kısmi güven ortamında çalışırken bir bilgi veya eylem parçasının kullanılamaz olduğunu öğrenmenin en iyi yolu, kaynağa erişmeyi veya `try` bloğunun içindeki eylemi yapmayı denemeniz ve sonra hatanın `catch`. İzleme dosyalarının yinelenen hatalarla taşmasını önlemek için, WCF ilk güvenlik hatasından sonra kaynağın veya eylemin izlenmesini devre dışı bırakır. Her başarısız kaynak erişimi için bir özel durum izlemesi vardır. kaynağa erişmek veya eylemi gerçekleştirmek için ilk kez girişimde bulunuldu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Desteklenen Dağıtım Senaryoları](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)
- [Kısmi Güven En İyi Uygulamaları](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
