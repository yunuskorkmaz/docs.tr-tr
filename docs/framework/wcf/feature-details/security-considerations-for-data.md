---
title: Veriler için Güvenlik Konuları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
ms.openlocfilehash: 13e596ea64fc62ed6280e74636243619178ce069
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990892"
---
# <a name="security-considerations-for-data"></a>Veriler için Güvenlik Konuları

Windows Communication Foundation (WCF) verilerle ilgilenirken, bir dizi tehdit kategorileri dikkate almanız gerekir. Veri işleme ile ilgili en önemli tehdit sınıfları aşağıdaki tabloda listelenmektedir. WCF bu tehditleri azaltmak için araçlar sağlar.

Güvenilir olmayan verileri alırken, hizmet reddi, verileri uzun hesaplamalar neden olarak orantısız miktarda bellek, iş parçacıkları, kullanılabilir bağlantılar veya işlemci döngülerinin gibi çeşitli kaynaklara erişim için alma tarafında neden olabilir. Bir sunucuya karşı bir hizmet reddi saldırısı kilitlenme ve yasal, diğer istemcilerinden gelen iletileri işleyemez neden olabilir.

Gelen kodu çalıştırmak için alma tarafında veri neden güvenilmeyen kötü amaçlı kod yürütme, istediniz değil.

Bilgilerin açığa çıkması uzak saldırgan, amaçlayan daha fazla bilgi ifşa şekilde kendi isteklerini yanıtlamak için alıcı tarafın zorlar.

## <a name="user-provided-code-and-code-access-security"></a>Kullanıcı tarafından sağlanan kodu ve kod erişimi güvenliği

Bir Windows Communication Foundation (WCF) altyapı basamak sayısı, kullanıcı tarafından sağlanan kodu çalıştırın. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme motoruna kullanıcı tarafından sağlanan özellik çağırıp `set` erişimcileri ve `get` erişimcileri. WCF kanalı altyapı da kullanıcı tarafından sağlanan türetilen sınıflara çağırabilir <xref:System.ServiceModel.Channels.Message> sınıfı.

Hiçbir güvenlik açıklarını bulunduğundan emin olmak için bir kod yazar sorumluluğundadır. Örneğin, oluşturursanız, bir veri anlaşması türü Tamsayı türünde ve içinde bir veri üyesi özelliği ile `set` erişimci uygulama özellik değerine göre bir dizi ayırmak, bir kötü amaçlı, hizmet reddi saldırısı olasılığını kullanıma sunma ileti, bu veri üyesi için son derece büyük bir değer içeriyor. Genel olarak, herhangi bir ayırma göre gelen verileri veya kullanıcı tarafından sağlanan kodu işleme (özellikle uzun işleme küçük bir gelen veri miktarına göre neden olabilir) uzun kaçının. Kullanıcı tarafından sağlanan kod güvenlik analizi gerçekleştirirken, tüm hata koşulları (burada özel durumlar diğer bir deyişle, tüm kod dallarını) de dikkate alınması gereken emin olun.

Son kullanıcı tarafından sağlanan kod örneği, hizmet uygulamanız için her bir işlem içinde kodudur. Hizmet uygulamanızın güvenlik sizin sorumluluğunuzdur. Yanlışlıkla hizmet reddi güvenlik açıklarına neden olabilir, güvenli olmayan işlem uygulamaları oluşturmak kolay bir işlemdir. Örneğin, o dizeyi bir dize alır ve müşterilerin listesini veritabanından adını döndürür. bir işlem başlatır. Büyük bir veritabanı ile çalışıyorsanız ve yalnızca tek bir harftir geçirilen bir dize ise, kodunuzun tüm hizmetin başarısız olmasına neden olan tüm kullanılabilir belleği daha büyük bir ileti oluşturma girişiminde bulunabilir. (Bir <xref:System.OutOfMemoryException> içinde kurtarılamaz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve her zaman, uygulamanızın sonlandırılmasıyla sonuçlanır.)

Kötü amaçlı bir kodun için çeşitli genişletilebilirlik noktaları takılı emin olmanız gerekir. Bu kısmen güvenilen derlemelerden türleriyle ilgili ya da kısmen güvenilen kod tarafından kullanılabilir bileşenleri oluşturma kısmi güven altında çalışırken özellikle geçerlidir. Daha fazla bilgi için "Kısmi güven tehditleri" bir sonraki bölüme bakın.

Kısmi güvende çalışan, veri sözleşme seri hale getirme altyapısı veri sözleşme programlama modelinin - Örneğin, özel veri üyeleri yalnızca sınırlı bir alt destekler veya türleri kullanarak unutmayın <xref:System.SerializableAttribute> öznitelik desteklenmez. Daha fazla bilgi için [kısmi güven](../../../../docs/framework/wcf/feature-details/partial-trust.md).

## <a name="avoiding-unintentional-information-disclosure"></a>Yanlışlıkla bilgilerin açığa çıkması kaçınma

Güvenlikten ödün Serializable türler tasarlarken, bilgi ifşası olası bir konudur.

Aşağıdaki noktaları göz önünde bulundurun:

- <xref:System.Runtime.Serialization.DataContractSerializer> Türün veya derlemenin serileştirme sırasında dışında özel ve iç verilerin açığa programlama modeli sağlar. Ayrıca, bir tür şeklini şema dışarı aktarma sırasında sunulabilir. Türün seri hale getirme projeksiyon anladığınızdan emin olun. Kullanıma sunulan herhangi bir şey istemiyorsanız, seri hale getirme devre dışı bırak (örneğin, uygulanmıyor tarafından <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği bir veri anlaşması söz konusu olduğunda).

- Aynı türde kullanımda seri hale getirici bağlı olarak birden fazla seri hale getirme projeksiyonlar olabileceğini unutmayın. Aynı türü ile kullanıldığında veri kümesi getirebilir <xref:System.Runtime.Serialization.DataContractSerializer> ve başka bir dizi ile kullanıldığında veri <xref:System.Xml.Serialization.XmlSerializer>. Yanlışlıkla yanlış seri hale getirici kullanarak, bilgi açığa çıkmasına neden olabilir.

- Kullanarak <xref:System.Xml.Serialization.XmlSerializer> içinde eski uzak yordam çağrısı (RPC) / kodlanmış modu alıcı tarafına Gönderen tarafında Nesne grafiğini şekli yanlışlıkla açığa.

## <a name="preventing-denial-of-service-attacks"></a>Hizmet reddi saldırılarını önleme

### <a name="quotas"></a>Kotalar

Önemli miktarda bellek ayırmak için alma tarafında neden olası bir hizmet reddi saldırısını olur. Bu bölümde büyük iletilerden kaynaklanan bellek tüketimi sorunlar yoğunlaşır olsa da, diğer saldırıları ortaya çıkabilir. Örneğin, ileti işleme süresi orantısız miktarda kullanabilir.

Hizmet reddi saldırılarını kullanarak kotalar genellikle azalır. Bir sınır aşıldığında, bir <xref:System.ServiceModel.QuotaExceededException> özel durumu normal olarak oluşturulur. Kotası olmadan, sonuçta kötü amaçlı bir ileti erişilmek üzere tüm kullanılabilir bellek neden bir <xref:System.OutOfMemoryException> özel durum ya da erişilebilmesi için kullanılabilir tüm yığınları içinde elde edilen bir <xref:System.StackOverflowException>.

Kota aşıldı senaryo kurtarılamaz.; çalışan bir hizmette, aldıysanız, o anda işlenmekte olan ileti atılır ve hizmet çalışmaya devam eder ve daha fazla iletileri işler. Bellek yetersiz ve yığın taşması senaryoları, ancak herhangi bir yerindeki kurtarılabilir değildir [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; bu tür özel durumların karşılaşırsa, hizmet sonlandırır.

Wcf'de kotaları tüm ön ayırması içermeyen. Örneğin, varsa <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kota (çeşitli sınıflarında bulunur), 128 KB olarak ayarlanır, 128 KB, her ileti için otomatik olarak tahsis edilen gelmez. Ayrılan gerçek gerçek gelen ileti boyutuna bağlıdır.

Birçok kotalarını, aktarım katmanında kullanılabilir. Bu, belirli taşıma kanalının (HTTP, TCP vb.) kullanımda tarafından uygulanan kotalar vardır. Bu konuda bu kotalar bazıları ele alınmıştır, ancak bu kotalar ayrıntılı olarak açıklanan [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md).

### <a name="hashtable-vulnerability"></a>Hashtable güvenlik açığı

Veri sözleşmeleri hashtable'da veya koleksiyonları içerdiğinde bir güvenlik açığı var. Çok sayıda değeri bir karma tablosunda eklediyseniz burada bu değerleri çok sayıda aynı karma değeri üretmek sorun oluşur. Bu bir DOS saldırısı kullanılabilir.  Bu güvenlik açığını MaxReceivedMessageSize bağlama kota ayarlayarak azaltılabilir. Bu tür saldırıları önlemek için bu kota ayarlarken dikkatli olunması gerekir. Bu kota, üst sınır WCF ileti boyutuna göre yerleştirir. Ayrıca, veri sözleşmelerinizi hashtable'da veya koleksiyonları kullanmaktan kaçının.

## <a name="limiting-memory-consumption-without-streaming"></a>Akış olmadan bellek tüketimini sınırlamak

Güvenlik modeli büyük iletiler çevresinde akış kullanımda olmasına göre değişir. Temel, akışa olmayan durumda belleğe iletiler arabelleğe alınır. Bu durumda <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kotası <xref:System.ServiceModel.Channels.TransportBindingElement> veya erişmek için en büyük ileti boyutunu sınırlayarak büyük iletiler karşı korumak için sistem tarafından sağlanan bağlamalar. Bir hizmet birden çok ileti aynı anda işliyor olabilir, bu durumda tüm bellekte olduklarını unutmayın. Bu tehdidi azaltmak için azaltma özelliğini kullanın.

Ayrıca `MaxReceivedMessageSize` bir üst sınır, ileti başına bellek tüketimi yerleştirmez ancak için sabit bir faktör içinde sınırlar. Örneğin, varsa `MaxReceivedMessageSize` 1 MB ve 1 MB'lık bir ileti alındığında ve ardından seri durumdan, ek bellek toplam bellek tüketimini kutusu üzerinde 1 MB kaynaklanan seri durumdan çıkarılmış Nesne grafiği içerecek biçimde gereklidir. Bu nedenle, önemli bellek tüketimi kadar gelen veri olmadan sonuçlanabilir, seri hale getirilebilir türler oluşturmamaya özen gösterin. Örneğin, "MyContract" 50 isteğe bağlı veri üyesi alanları ve ek bir 100 özel alanlar XML oluşturucuyla örneği bir veri anlaşması "\<MyContract / >". Bu XML 150 alanlar için erişilen bellek sonuçlanır. Veri üyeleri varsayılan olarak isteğe bağlı olduğunu unutmayın. Böyle bir türü bir dizinin parçası olduğunda sorun karmaşıklaşır.

`MaxReceivedMessageSize` tek başına tüm hizmet reddi saldırılarını önlemek yeterli değil. Örneğin, seri durumdan çıkarıcı bir iç içe geçmiş Nesne grafiği (henüz başka bir vb. içeren başka bir nesne içeren bir nesne) seri durumdan çıkarılacak gelen iletiyi tarafından zorlanabilir. Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> yöntemleri gibi grafikler seri durumdan çıkarılacak iç içe geçmiş bir şekilde çağırın. Yöntem çağrılarının derin iç içe geçme kurtarılamaz bir neden <xref:System.StackOverflowException>. Bu tehdit ayarlayarak kalktıktan <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> kota, XML iç içe geçme düzeyini "Güvenle XML kullanarak" bölümünde bu konunun ilerleyen bölümlerinde açıklandığı gibi sınırlamak için.

Ek kotalar ayarını `MaxReceivedMessageSize` ikili XML encoding kullanıldığında özellikle önemlidir. İkili kodlama kullanılarak sıkıştırma biraz eşdeğer: çok fazla veri bayt gelen iletideki küçük bir grubu temsil edebilir. Bu nedenle, bir ileti içine sığdırma bile `MaxReceivedMessageSize` sınırı sürebilir çok daha fazla bellek tam olarak genişletilmiş biçiminde. Bu tür özel XML tehditleri azaltmak için tüm XML okuyucusu kotalar "Güvenle XML kullanarak" bölümünde bu konunun ilerleyen bölümlerinde açıklandığı gibi doğru şekilde ayarlanması gerekir.

## <a name="limiting-memory-consumption-with-streaming"></a>Bellek tüketimi akış ile sınırlama

Akış, bir küçük kullanabilir `MaxReceivedMessageSize` hizmet reddi saldırılarına karşı korumaya yönelik ayarı. Ancak, daha karmaşık senaryolarda, akış ile mümkündür. Örneğin, bir dosya karşıya yükleme hizmeti, tüm kullanılabilir bellekten daha büyük dosyaları kabul eder. Bu durumda, `MaxReceivedMessageSize` son derece büyük bir değere doğrudan diske akışları neredeyse hiçbir veri bellek ve iletiyi arabelleğe alınıp bekleniyor. Kötü amaçlı bir ileti şekilde WCF yerine bu durumda, akış verilerini arabelleğe zorlayabilirsiniz varsa `MaxReceivedMessageSize` artık tüm kullanılabilir bellek erişim iletiye karşı korur.

Bu tehdidi azaltmak için belirli bir kota ayarları, çeşitli WCF veri işleme bileşenlerini sınırı arabelleğe alma mevcut. Bunların en önemlisi `MaxBufferSize` çeşitli aktarım bağlama öğeleriyle ve standart bağlamalar özelliği. Akış, bu kota en fazla ileti ettiğinizi bellek miktarını dikkate alarak ayarlamanız gerekir. Olduğu gibi `MaxReceivedMessageSize`, ayar bir mutlak en büyük bellek tüketimi koymaz, ancak yalnızca için sabit bir faktör içinde sınırlar. Ayrıca, olarak ile `MaxReceivedMessageSize`, birden çok ileti aynı anda işlenmekte olan olasılığını unutmayın.

### <a name="maxbuffersize-details"></a>MaxBufferSize ayrıntıları

`MaxBufferSize` Sınırlar arabelleğe alma WCF mu herhangi bir toplu özellik. Örneğin, WCF her zaman bir ileti aktarım en iyi duruma getirme mekanizması (MTOM) iletisi doğal okuma düzeninde olmaması bulunan herhangi bir MIME bölümü yanı sıra SOAP üstbilgileri ve SOAP hataları arabelleğe alır. Bu ayar tüm durumlarda arabelleğe alma miktarını sınırlar.

WCF gerçekleştirir bu geçirerek `MaxBufferSize` arabellek çeşitli bileşenleri için değer. Örneğin, bazı <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> , aşırı <xref:System.ServiceModel.Channels.Message> sınıfındaki oluşturucuların bir `maxSizeOfHeaders` parametresi. WCF geçirir `MaxBufferSize` SOAP üstbilgi arabelleğe alma tutarını sınırlamak için bu parametre için değer. Bu parametreyi kullanırken ayarlamak önemlidir <xref:System.ServiceModel.Channels.Message> doğrudan sınıf. Genel olarak, bir bileşen kota parametreleri alan WCF'de kullanırken, bu parametreleri güvenlik etkilerini anlamanıza ve doğru şekilde ayarlanması önemlidir.

MTOM ileti Kodlayıcı de sahip bir `MaxBufferSize` ayarı. Standart bağlamaları kullanırken, bu aktarım düzeyi için otomatik olarak ayarlanır `MaxBufferSize` değeri. Ancak, MTOM ileti Kodlayıcı bağlama öğesi, özel bir bağlama oluşturmak için kullanırken ayarlamak önemlidir `MaxBufferSize` güvenli bir değere akışı yapılırken kullanılır.

## <a name="xml-based-streaming-attacks"></a>XML-tabanlı akış saldırıları

`MaxBufferSize` tek başına WCF akış beklendiğinde arabelleğe içine zorlanamıyor emin olmak yeterli değil. Örneğin, WCF XML okuyucular her zaman tüm XML öğenin başlangıç etiketinde yeni bir öğe okunacak başlatırken arabellek. Bu ad alanları ve özniteliklerini düzgün bir şekilde işlenir böylece gerçekleştirilir. Varsa `MaxReceivedMessageSize` yapılandırılır (doğrudan disk büyük dosya senaryo akış etkinleştirmek için örneğin,) büyük olması için kötü amaçlı bir ileti tüm ileti gövdesi, büyük bir XML öğesi başlangıç etiketi bulunduğu oluşturulabilir. Dosyayı okuma girişimi sonuçlanır bir <xref:System.OutOfMemoryException>. Bu, tüm XML okuyucusu kotaları, bu konunun ilerleyen bölümlerindeki "Güvenle XML kullanarak" bölümünde açıklanan kullanılarak azaltılabilir sayıda olası XML tabanlı hizmet reddi saldırı biridir. Akış, tüm bu kotalar ayarlamak özellikle önemlidir.

### <a name="mixing-streaming-and-buffering-programming-models"></a>Akış ve programlama modellerini arabelleğe alma karıştırma

Birçok olası saldırıları, akış ve akış dışı programlama modelleri aynı hizmetteki karıştırma alanından ortaya çıkar. Bir hizmet sözleşmesini iki işlem ile olduğunu varsayın: alır bir <xref:System.IO.Stream> ve başka bazı özel bir tür dizisini alır. Ayrıca varsayın `MaxReceivedMessageSize` büyük akışları işlemek ilk işlemi etkinleştirmek için büyük bir değere ayarlanır. Ne yazık ki, bu işlemi çağrılmadan önce büyük iletiler şimdi de ikinci işlem ve bellek seri durumdan çıkarıcının arabellekler verileri bir dizi olarak gönderilmesini anlamına gelir. Olası bir hizmet reddi saldırısını budur: `MaxBufferSize` kota, ileti gövdesi boyutu sınırlamaz olduğu seri durumdan çıkarıcı ile çalışır.

Bu nedenle, aynı sözleşme akış tabanlı ve veri akışı işlemlerinde karıştırmayın. Kesinlikle iki programlama modellerini karıştırmak gerekir, aşağıdaki önlemleri kullanın:

- Devre dışı <xref:System.Runtime.Serialization.IExtensibleDataObject> özelliğini ayarlayarak <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliği <xref:System.ServiceModel.ServiceBehaviorAttribute> için `true`. Bu sözleşmenin bir parçası olan üyeleri seri sağlar.

- Ayarlama <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> özelliği <xref:System.Runtime.Serialization.DataContractSerializer> güvenli bir değer. Bu kota de kullanılabilir <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği veya yapılandırma yoluyla. Bu kota, bir seri durumundan çıkarma bölümde durumdan nesne sayısını sınırlar. Normalde, her işlem parametresi veya ileti Gövde bölümünün bir ileti anlaşması içinde bir bölümde seri durumda. Her dizi girişi, diziler seri durumdan çıkarılırken zaman ayrı bir nesne kabul edilir.

- Tüm XML okuyucusu kotalar güvenli değerlere ayarlayın. Dikkat <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, ve <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> ve akış dışı işlemler dizelerde kaçının.

- Bilinen türler, herhangi bir zamanda herhangi biri oluşturulabilir aklınızda tutma listesini gözden geçirin (Bu konunun ilerleyen bölümlerindeki "Önleme istenmeyen türleri gelen yüklenme" bölümüne bakın).

- Uygulayan türler kullanmayın <xref:System.Xml.Serialization.IXmlSerializable> çok fazla veri arabellek arabirimi. Bu türler, bilinen türler listesine eklemeyin.

- Kullanmayın <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> diziler <xref:System.Byte> diziler veya türleri uygulayan <xref:System.Runtime.Serialization.ISerializable> sözleşmesindeki.

- Kullanmayın <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> diziler <xref:System.Byte> diziler veya türleri uygulayan <xref:System.Runtime.Serialization.ISerializable> bilinen türler listesine.

Akış işlemi kullandığında önceki önlemler uygulamak <xref:System.Runtime.Serialization.DataContractSerializer>. Akış dışı programlama modelleri aynı hizmetini kullanıyorsanız ve hiç akış karıştırmak <xref:System.Xml.Serialization.XmlSerializer>, korumasını olmadığından <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> kota.

### <a name="slow-stream-attacks"></a>Yavaş Stream saldırıları

Akış hizmet reddi saldırılarını sınıfının bellek tüketimi gerektirmez. Bunun yerine, saldırı yavaş gönderen veya alıcı veri içerir. Gönderilen veya alınan verilerin beklenirken, iş parçacıkları ve kullanılabilir ağ bağlantıları gibi kaynakları tükendi. Bu durum kötü amaçlı saldırı sonucunda ya da yasal bir gönderen/alıcı yavaş ağ bağlantısı üzerinde meydana gelebilecek.

Bu saldırıları azaltmak için Aktarım zaman aşımları doğru şekilde ayarlayın. Daha fazla bilgi için [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md). İkincisi, hiçbir zaman zaman uyumlu kullanmayın `Read` veya `Write` WCF akış ile çalışırken operations.

## <a name="using-xml-safely"></a>XML kullanarak güvenli bir şekilde

> [!NOTE]
> Bu bölüm hakkında daha fazla XML olsa da, bilgi JavaScript nesne gösterimi (JSON) belgeler için de geçerlidir. Kotalar kullanarak benzer şekilde, iş [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).

### <a name="secure-xml-readers"></a>XML okuyucular güvenliğini sağlama

XML bilgi kümesi tüm ileti işleme WCF'de temelini oluşturur. XML verilerini birkaç olasılık mevcut azaltılması gereken hizmet reddi saldırısı güvenilmeyen bir kaynaktan kabul ederken. WCF özel, güvenli XML okuyucular sağlar. Bu okuyucular, standart Kodlamalar birini WCF (metin, ikili veya MTOM) kullanırken otomatik olarak oluşturulur.

Bazı güvenlik özellikleri bu okuyucular her zaman etkindir. Örneğin, okuyucular, olası bir hizmet reddi saldırılarını kaynağı olan ve hiçbir zaman yasal SOAP iletilerini görünmesi gereken belge türü tanımları (DTD'ler) hiçbir zaman işleyin. Yapılandırılmalıdır, okuyucu kotalar aşağıdaki bölümde açıklanan diğer güvenlik özellikleri içerir.

Doğrudan XML okuyucularıyla çalışırken (gibi kendi özel bir kodlayıcı yazarken veya doğrudan ile çalışırken <xref:System.ServiceModel.Channels.Message> sınıfı), bir güvenilir olmayan verileri ile çalışma olasılığı olduğunda WCF güvenli okuyucular her zaman kullanın. Güvenli okuyucular çağıran bir statik fabrika tarafından yöntemi aşırı yüklemeleri oluşturma <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, veya <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> üzerinde <xref:System.Xml.XmlDictionaryReader> sınıfı. Bir okuyucu oluşturulurken güvenli kota değerlerini geçirirsiniz. Çağırmayın `Create` yöntemi aşırı yüklemeleri. Bu, bir WCF okuyucu oluşturmayın. Bunun yerine, bu bölümde açıklanan güvenlik özellikleri tarafından korunmayan bir okuyucu oluşturulur.

### <a name="reader-quotas"></a>Okuyucu kotaları

Güvenli XML okuyucular beş yapılandırılabilir kotalar vardır. Bunlar kullanarak normal şekilde yapılandırılır `ReaderQuotas` özelliği kodlama bağlama öğeleri veya standart bağlamaları veya kullanılarak bir <xref:System.Xml.XmlDictionaryReaderQuotas> bir okuyucusu oluşturulurken nesnesi geçirildi.

#### <a name="maxbytesperread"></a>MaxBytesPerRead

Bu kotayı tek bir okunan bayt sayısını sınırlayan `Read` etiketini ve onun özniteliklerini öğe okurken işlemi başlatın. (Akış olmayan durumlarda, öğe adı kotaya dahil edilmez.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> aşağıdaki nedenlerle önemlidir:

- Her zaman, okunan, öğe adı ve özniteliklerini bellekte arabelleğe alınır. Bu nedenle, akış modunda akış beklendiğinde aşırı arabelleğe almayı önlemek için bu kotayı doğru şekilde ayarlanması önemlidir. Bkz: `MaxDepth` gerçekleşmeden gerçek miktarını arabelleğe alma hakkında bilgi için kota bölümüne.

- Benzersizlik için denetlenecek öznitelik adları olduğundan çok fazla XML özniteliklere sahip orantısız işleme zamanı kullanıyor olabilir. `MaxBytesPerRead` Bu tehdidi azaltır.

#### <a name="maxdepth"></a>MaxDepth

Bu kota, XML öğeleri en fazla iç içe geçme derinliği sınırlar. Örneğin, belge "\<A >\<B >\<C / >\</B >\</A >" üç iç içe geçme derinliği vardır. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A> Aşağıdaki nedenlerle önemlidir:

- `MaxDepth` etkileşime `MaxBytesPerRead`: en yüksek bellek tüketimi Okuyucu için bu iki ayar çarpımını orantılı, bu nedenle okuyucu her zaman veri bellekte geçerli öğenin ve tüm alt öğelerinden tutar.

- Bir iç içe geçmiş Nesne grafiği işlenirken, seri durumdan çıkarıcı tüm yığını erişip kurtarılamaz bir throw zorlanır <xref:System.StackOverflowException>. XML iç içe geçirme ve nesnenin iç içe her ikisi için de arasında doğrudan bağıntı var. <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer>. Kullanım `MaxDepth` bu tehdidi azaltmak için.

#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount

Bu kota boyutu okuyucunun sınırlar *ad tablosu*. Ad tablosu, bir XML belgesi işleme sırasında karşılaşılan belirli dizeleri (örneğin, ad alanlarını ve önekleri) içerir. Bu dizeler bellekte arabelleğe alınan gibi akış beklendiğinde aşırı arabelleğe almayı önlemek için bu kotayı ayarlayın.

#### <a name="maxstringcontentlength"></a>MaxStringContentLength

Bu kota, XML okuyucusu döndüren maksimum dize boyutu sınırlar. Bu kota, XML okuyucusu bellek tüketimini sınırlamaz, ancak okuyucu kullanan bileşen. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, dizeleri bu kotayı daha büyük serisini değil. Kullanırken <xref:System.Xml.XmlDictionaryReader> doğrudan bu kota, ancak yalnızca dizeleri gibi okumak için özel olarak tasarlanmış yöntemleri tüm yöntemleri saygı sınıf <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> yöntemi. <xref:System.Xml.XmlReader.Value%2A> Okuyucu özelliği bu kota tarafından etkilenmez ve bu kotayı sağlar koruma gerekli olduğunda, bu nedenle kullanılmamalıdır.

#### <a name="maxarraylength"></a>MaxArrayLength

Bu kota, bir XML okuyucusu döndüren bayt dizileri de dahil olmak üzere temel elemanlar dizisinde en büyük boyutu sınırlar. Bu kota, XML okuyucusu bellek tüketimini sınırlamaz, ancak okuyucu kullanarak hangi bileşeni. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, bayt dizileri bu kotayı daha büyük serisini değil. Tek bir sözleşmede akış ve arabelleğe alınan programlama modellerini karıştırmak çalışırken bu kota ayarlamak önemlidir. Aklınızda kullanırken <xref:System.Xml.XmlDictionaryReader> doğrudan, yalnızca rastgele boyutunu belirli ilkel türler, dizileri gibi okumak için özel olarak tasarlanmış yöntemleri sınıf <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, bu kotayı uyup.

## <a name="threats-specific-to-the-binary-encoding"></a>İkili kodlama için özel tehditler

WCF destekler kodlama ikili XML'si içeren bir *sözlük dizeleri* özelliği. Büyük bir dize kullanarak yalnızca birkaç bayt kodlanmış. Bu, önemli ölçüde performans kazanımı sağlar, ancak azaltılması gereken yeni hizmet reddi tehditlerine tanıtır.

Sözlükler iki tür vardır: *statik* ve *dinamik*. Statik sözlükte ikili kodlama kısa bir kod kullanılarak temsil edilebilir uzun dizeler yerleşik bir listesidir. Bu dize listesi sabit okuyucu oluşturulduğunda ve değiştirilemez. WCF varsayılan olarak kullandığı statik sözlükte dizeleri hiçbiri, sözlük genişletme saldırısını hala kullanılabilir olsa da önemli bir hizmet reddi tehdit teşkil yeterli büyüklükte değil. Statik sözlüğünüz Burada sağladığınız Gelişmiş senaryolarda büyük sözlük dizeleri giriş oluştururken dikkatli olun.

Dinamik sözlük özelliği, kendi dizeleri tanımlayın ve kısa kodları ile ilişkilendirmek iletileri sağlar. Sonraki ileti dizelerini yeniden başlatmanız gerekmez ve önceden tanımlanmış kodlarını kullanabilir Bu dize kod eşlemeleri tüm iletişimin oturumu sırasında bellekte tutulur. Bu dizeler rastgele uzunlukta olması ve bu nedenle statik sözlükte olanlardan daha ciddi bir tehdit teşkil olabilir.

Azaltılması gereken ilk tehdit çok büyük boyutlu hale gelmesini dinamik sözlüğün (dize kod eşlemesinin tablo) bir olasılıktır. Bu sözlük birkaç ileti kursunda genişletilebilir ve böylece `MaxReceivedMessageSize` kota yalnızca her ileti için ayrı olarak uygulandığından koruma sunar. Bu nedenle, ayrı <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> özelliği var. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> , sözlük boyutu sınırlar.

Diğer çoğu kotalar, bu kotayı iletiler yazarken geçerlidir. Bir ileti okurken aşılırsa `QuotaExceededException` zamanki oluşturulur. Bir ileti yazarken aşılırsa kotanın aşılmasına neden herhangi bir dize olarak yazılır-, dinamik sözlük özelliği olmadan kullanmaktır.

### <a name="dictionary-expansion-threats"></a>Sözlük genişletme tehditler

İkili özgü saldırı önemli sınıfı sözlük genişletme ortaya çıkar. Dize sözlükleri özellik kapsamlı kullanımını yaparsa küçük bir ikili biçimini iletisinde tam olarak genişletilmiş metin biçiminde çok büyük bir iletiye kapatabilir. Dinamik sözlük dizeleri için genişletme faktörü sınırlıdır <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> kotası, hiçbir dinamik sözlük dizesinde tüm sözlük en büyük boyutu aştığından.

<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, Ve `MaxArrayLength` özellikleri yalnızca bellek tüketimini sınırlamak. Bellek kullanımı tarafından zaten sınırlı olduğundan tüm tehditleri akışa olmayan kullanımı gerekmez normalde `MaxReceivedMessageSize`. Ancak, `MaxReceivedMessageSize` öncesi genişletme bayt sayısı. İkili kodlama kullanımda olmadığında bellek tüketimi potansiyel olarak ötesine geçip `MaxReceivedMessageSize`, yalnızca faktörüyle sınırlı <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Bu nedenle, her zaman tüm okuyucu kotalar ayarlamak önemlidir (özellikle <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) kullanırken ikili kodlama.

İle birlikte ikili kodlama kullanırken <xref:System.Runtime.Serialization.DataContractSerializer>, `IExtensibleDataObject` arabirimi yanlış bir sözlük genişletme saldırısı. Bu arabirim, temelde sözleşmesinin bir parçası değil, rastgele veriler için sınırsız depolama sağlar. Kotalar yaratmayacağı ayarlanamaz, şekilde `MaxSessionSize` çarpılmasıyla `MaxReceivedMessageSize` değil bir sorun teşkil, devre dışı bırakma `IExtensibleDataObject` özelliğini kullanırken ikili kodlama. Ayarlama `IgnoreExtensionDataObject` özelliğini `true` üzerinde `ServiceBehaviorAttribute` özniteliği. Alternatif olarak, uygulamayın `IExtensibleDataObject` arabirimi. Daha fazla bilgi için [İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).

### <a name="quotas-summary"></a>Kotalar özeti

Aşağıdaki tabloda kotaları hakkında kılavuz bilgileri özetlenmektedir.

|Koşul|Önemli kotalar ayarlamak için|
|---------------|-----------------------------|
|Akış veya küçük iletileri, metin veya MTOM kodlama akış|`MaxReceivedMessageSize`, `MaxBytesPerRead`, ve `MaxDepth`|
|Akış veya küçük iletileri, ikili akış kodlama|`MaxReceivedMessageSize`, `MaxSessionSize`ve tüm `ReaderQuotas`|
|Akış büyük iletiler, metin ya da MTOM kodlama|`MaxBufferSize` ve tüm `ReaderQuotas`|
|Akış büyük iletiler, ikili kodlama|`MaxBufferSize`, `MaxSessionSize`ve tüm `ReaderQuotas`|

- Aktarım düzeyi zaman aşımları, her zaman ayarlanmalıdır ve akış olup büyük veya küçük ileti akışı bağımsız olarak kullanımda olduğunda hiçbir zaman zaman uyumlu okuma/yazma kullanın.

- Emin olamadığınız durumlarda bir kota hakkında güvenli bir değer yerine açık bırakarak ayarlayın.

## <a name="preventing-malicious-code-execution"></a>Kötü amaçlı kod yürütmesini engelleme

Aşağıdaki genel sınıfları tehdit kod yürütebilir ve sahip istenmeyen etkilere:

- Kötü amaçlı, güvenli olmayan veya güvenlik açısından duyarlı bir türü seri durumdan çıkarıcı yükler.

- Normalde güvenli bir tür gibi olarak bir örneğini oluşturmak seri durumdan çıkarıcının gelen iletiyi neden olan bir şekilde istenmeyen sonuçları.

Aşağıdaki bölümlerde bu sınıfların tehditleri daha ayrıntılı açıklanmaktadır.

## <a name="datacontractserializer"></a>DataContractSerializer

(Güvenlik hakkında bilgi için <xref:System.Xml.Serialization.XmlSerializer>, ilgili belgelerine bakın.) İçin güvenlik modeli <xref:System.Xml.Serialization.XmlSerializer> ilkesindekine benzer <xref:System.Runtime.Serialization.DataContractSerializer>ve çoğunlukla ayrıntıları farklıdır. Örneğin, <xref:System.Xml.Serialization.XmlIncludeAttribute> yerine türü eklemek için kullanılan öznitelik <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği. Ancak, bazı tehditler için benzersiz <xref:System.Xml.Serialization.XmlSerializer> bu konunun ilerleyen bölümlerinde ele alınmıştır.

### <a name="preventing-unintended-types-from-being-loaded"></a>Tür istenmeyen yüklenmesini engelleyen

Tür istenmeyen yüklenirken önemli sonuçlar olabilir, bu türü kötü amaçlı ya da yalnızca güvenlik açısından duyarlı bir yan etkisi yok. Bir tür açıklardan güvenlik açığı içeren, kendi oluşturucu veya sınıf oluşturucusu içinde güvenlik duyarlı eylemleri gerçekleştirmek, hizmet reddi saldırılarını kolaylaştıran veya kurtarılamaz bir özel durum oluşturabildiğini varsaymasını büyük bellek ayak izine sahip. Türleri türü yüklendikten hemen sonra ve herhangi bir örneği oluşturulmadan önce çalıştıran sınıf oluşturucuları olabilir. Bu nedenlerle, seri durumdan çıkarıcı yükleyebilir türleri denetlemek önemlidir.

<xref:System.Runtime.Serialization.DataContractSerializer> Gevşek bir şekilde seri durumdan çıkarır. Hiçbir ortak dil çalışma zamanı (CLR) türü ve derleme adları gelen verileri okur. Bu davranıştır benzer <xref:System.Xml.Serialization.XmlSerializer>, ancak davranışından farklıdır <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Uzak saldırgan bu tür iletisinde adlandırarak yüklemek için rastgele bir tür belirttiğinden gevşek bağlantı güvenliği, derecesini tanıtır.

<xref:System.Runtime.Serialization.DataContractSerializer> Sözleşmenin göre şu anda beklenen bir tür yüklemeyi her zaman izin verilir. Örneğin, bir veri anlaşması türü veri üyesine sahip `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> yüklenmesine izin `Customer` yazın, bu veri üyesi seri durumdan çıkarır.

Ayrıca, <xref:System.Runtime.Serialization.DataContractSerializer> çok biçimlilik destekler. Bir veri üyesi olarak bildirilebilir <xref:System.Object>, ancak gelen veri içerebilir bir `Customer` örneği. Bu yalnızca `Customer` türü sağlandıktan "bilinen" için seri durumdan çıkarıcı bu mekanizmalardan biri yoluyla:

- <xref:System.Runtime.Serialization.KnownTypeAttribute> öznitelik bir türe uygulandı.

- `KnownTypeAttribute` türlerinin bir listesini döndüren bir yöntem belirten özniteliği.

- `ServiceKnownTypeAttribute` özniteliği.

- `KnownTypes` Yapılandırma bölümü.

- Geçirilecek açıkça bilinen türlerinin bir listesini <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirici doğrudan kullanıyorsanız, oluşturma sırasında.

Bu mekanizmaların her biri, seri durumdan çıkarıcı yükleyebilir ve daha fazla türdeki sunarak yüzey alanını artırır. Hiçbir kötü amaçlı veya istenmeyen türü bilinen türler listesine eklendiğinden emin olmak için Bu mekanizmaların her biri denetler.

Bilinen türü kapsamında olduğunda, dilediğiniz zaman yüklenebilir ve gerçekte kullandığı sözleşmeye engelliyor olsa bile tür örneklerinin oluşturulabilir. Örneğin, "MyDangerousType" Yukarıdaki mekanizmalarını kullanarak bilinen türler listesine eklenen türü varsayalım. Bunun anlamı:

- `MyDangerousType` yüklenir ve kendi sınıf oluşturucu döngülerinden.

- Hatta bir dize veri üyesi olan bir veri anlaşması seri durumdan çıkarılırken zaman kötü amaçlı bir ileti örneği yine de neden olabilir `MyDangerousType` oluşturmak için. Kod `MyDangerousType`, özellik ayarlayıcılarına gibi çalışabilir. Bunu yaptıktan sonra seri durumdan çıkarıcı bu örneğin dize veri üyesine atamak ve bir özel durumla başarısız dener.

Bilinen türlerinin bir listesini döndüren bir yöntem yazarken veya bir liste doğrudan geçerken <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusu, listenin hazırlar kod güvenlidir ve yalnızca güvenilen veriler üzerinde çalışıyor olun.

Yapılandırmada bilinen türleri belirtme yapılandırma dosyası güvenli olduğundan emin olun. Güçlü adlar (tür bulunduğu imzalanmış derlemenin ortak anahtar belirterek), her zaman yapılandırmasında kullanmasına rağmen türün yüklenecek sürümü belirtmez. Yükleyici türü en son sürümü, mümkünse otomatik olarak seçer. Belirli bir sürüm yapılandırması belirtirseniz, aşağıdaki risk çalıştırın: Bir türe gelecekte yayımlanacak bir sürümde giderilen bir güvenlik açığına sahip olabilir, ancak savunmasız sürüm yapılandırmasında açıkça belirtilmediği için yine de yükler.

Çok fazla bilinen türüne sahip olan başka bir klona sahiptir: <xref:System.Runtime.Serialization.DataContractSerializer> Seri hale getirmek ve seri durumdan gerekir her tür için bir giriş ile uygulama etki alanındaki bir önbellek serileştirme/seri durumundan çıkarma kod oluşturur. Bu önbellek, uygulama etki alanı çalıştığı sürece hiçbir zaman kaldırılır. Bu nedenle, bir uygulamanın birçok bilinen türleri kullandığı farkındadır bir saldırganın bir orantısız miktarda bellek kullanmak önbellek neden tüm bu tür, seri durumundan çıkarma neden olabilir.

### <a name="preventing-types-from-being-in-an-unintended-state"></a>Tür istenmeyen bir durumda olmasını önleyen

Bir tür uygulanmasını gerektiren iç tutarlılık kısıtlamaları olabilir. Bu kısıtlamalar seri durumundan çıkarma sırasında bozmayı önlemek için dikkatli olunması gerekir.

Aşağıdaki örnek bir türün bir spacecraft üzerinde bir hava kilidi durumunu temsil eder ve hem iç hem de dış kapılar aynı anda açılamıyor kısıtlamayı zorlar.

[!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
[!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]

Bir saldırganın gibi bu, kötü amaçlı bir ileti gönderebilir, kısıtlamaları geçici olarak almak ve sahip geçersiz bir durum nesnesi alınırken istenmeyen ve beklenmeyen sonuçlar.

```xml
<SpaceStationAirlock>
    <innerDoorOpen>true</innerDoorOpen>
    <outerDoorOpen>true</outerDoorOpen>
</SpaceStationAirlock>
```

Bu durum, aşağıdaki noktaları farkına varmadan tarafından önlenebilir:

- Zaman <xref:System.Runtime.Serialization.DataContractSerializer> çoğu sınıf, Oluşturucular çalıştırma seri durumdan çıkarır. Bu nedenle, oluşturucuda yapılan herhangi bir durumu yönetim güvenmeyin.

- Geri çağırmaları nesne geçerli bir durumda olduğundan emin olmak için kullanın. Geri çağırma ile işaretlenen <xref:System.Runtime.Serialization.OnDeserializedAttribute> seri durumundan çıkarma tamamlandı ve incelemek ve genel durumu düzeltmek için bir fırsat sonra çalıştığından özniteliği özellikle yararlıdır. Daha fazla bilgi için [sürüme dayanıklı serileştirme geri çağırmaları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).

- Veri sözleşmesi türleri hangi özellik ayarlayıcı çağrılmalıdır belirli bir sıraya üzerinde yararlanmayı tasarlamayın.

- Eski türleri ile işaretlenen kullanarak ilgileniriz <xref:System.SerializableAttribute> özniteliği. Çoğu ile çalışmak üzere tasarlanmış [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uzaktan iletişim için güvenilir verilerle kullanın. Varolan türleri bu özniteliği ile işaretlenmiş ile durum güvenlik düşünülerek tasarlanmıştır değil.

- Güvenmeyin <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği <xref:System.Runtime.Serialization.DataMemberAttribute> durumu güvenliği açısından kadar veri sağlamak için özniteliği. Verileri her zaman olabilir `null`, `zero`, veya `invalid`.

- Hiçbir zaman ilk önce doğrulamadan bir güvenilmeyen bir veri kaynağından bir nesne grafiğinin seri durumdan güven. Her ayrı nesneyi tam olmayabilir tutarlı bir duruma, ancak nesne grafiğini olabilir. Ayrıca, Nesne grafiği koruma modu devre dışı bırakılmış olsa bile, seri durumdan çıkarılmış grafik aynı nesneye birden çok başvuruya sahip veya döngüsel başvurulara sahip. Daha fazla bilgi için [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).

### <a name="using-the-netdatacontractserializer-securely"></a>NetDataContractSerializer güvenli bir şekilde kullanma

<xref:System.Runtime.Serialization.NetDataContractSerializer> Türlerine sıkı eşleştirme kullanan bir seri hale getirme altyapısı. Bu benzer <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Diğer bir deyişle, okuyarak örneklemek için tür belirler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gelen veri derlemesi ve tür adı. WCF bir parçası olmasına rağmen bu serileştirme motoruna takma, sağlanan bir yolu yoktur; özel kod için yazılmış olmalıdır. `NetDataContractSerializer` Geçiş dışında öncelikli olarak kolaylaştırmak için sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] WCF için uzaktan iletişim. Daha fazla bilgi için bkz ilgili bölümde [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).

İleti, her türlü yüklenebilir, işaret edebilir çünkü <xref:System.Runtime.Serialization.NetDataContractSerializer> mekanizması doğası gereği güvenli değil ve yalnızca güvenilir verilerle kullanılmalıdır. Güvenli yalnızca güvenli türler yüklemeye izin veren bir güvenli, tür sınırlaması türü bağlayıcı yazarak hale mümkündür (kullanarak <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> özelliği).

Bile güvenilir verilerle kullanıldığında, gelen veri yeterince türü yüklemek için özellikle de belirtebilir <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> özelliği <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Uygulamanın dizine veya genel derleme önbelleği erişimi olan herkes, kötü amaçlı bir türü yüklemek için gereken bir yerine yerine kullanabilirsiniz. Her zaman doğru izinleri ayarlayarak uygulamanızın dizinine ve Genel Derleme Önbelleği güvenlik emin olun.

Genel olarak kısmen güvenilen kod erişime izin verirseniz, `NetDataContractSerializer` örneği veya aksi halde vekil seçici denetimi (<xref:System.Runtime.Serialization.ISurrogateSelector>) veya serileştirme Bağlayıcısı (<xref:System.Runtime.Serialization.SerializationBinder>), kod üzerinde denetim büyük ölçüde madde Serileştirme/seri durumdan çıkarma işlemi. Örneğin, bunu rastgele türler ekleme, bilginin açığa çıkmasına neden, elde edilen Nesne grafiği veya serileştirilmiş veriler ile değiştirmesine veya sonuç seri hale getirilmiş akış taşması.

İle ilgili başka bir güvenlik sorunu `NetDataContractSerializer` hizmeti, kötü amaçlı kod yürütme tehdit reddi. Kullanırken `NetDataContractSerializer`, her zaman ayarlanan <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> kotası için güvenli bir değer. Tarafından bu kota boyutu sınırlı nesne dizisini ayırır küçük, kötü amaçlı bir ileti oluşturmak daha kolaydır.

### <a name="xmlserializer-specific-threats"></a>XmlSerializer özgü tehditler

<xref:System.Xml.Serialization.XmlSerializer> Güvenlik modeli benzer <xref:System.Runtime.Serialization.DataContractSerializer>. Ancak, birkaç tehditler için benzersiz <xref:System.Xml.Serialization.XmlSerializer>.

<xref:System.Xml.Serialization.XmlSerializer> Oluşturur *serileştirme derlemelerinin* gerçekten serileştirir ve seri durumdan çıkarır; kodu içeren çalışma zamanında bu derlemeleri bir geçici dosyalar dizininde oluşturulur. Başka bir işlem veya kullanıcı bu dizine erişim hakkı varsa, serileştirme/seri durumundan çıkarma kod ile rastgele kod yazabilir. <xref:System.Xml.Serialization.XmlSerializer> Sonra güvenlik bağlamı, serileştirme/seri kaldırma yerine kodla bu kod çalışır. İzinleri, bunu önlemek için geçici dosyalar dizini üzerinde doğru şekilde ayarlandığından emin olun.

<xref:System.Xml.Serialization.XmlSerializer> Ayrıca hangi kullandığı önceden oluşturulan serileştirme derlemeleri çalışma zamanında üretmek yerine bir moda sahiptir. Bu mod tetiklenen her <xref:System.Xml.Serialization.XmlSerializer> uygun serileştirme derlemesi bulabilirsiniz. <xref:System.Xml.Serialization.XmlSerializer> Seri hale getirme derlemesi türleri serileştirilen içeren derleme imzalamak için kullanılan aynı anahtarla oturumu olup olmadığını denetler. Serileştirme bütünleştirilmiş kodları gösterebilecek kötü amaçlı derlemelerden koruma sunar. Serializable türler içeren derleme değilse, ancak, imzalı <xref:System.Xml.Serialization.XmlSerializer> doğru ada sahip derlemeler kullanır ve bu denetimi gerçekleştiremezsiniz. Kötü amaçlı kod çalıştıran bu mümkün kılar. Her zaman, serializable türler içeren derlemeler oturum veya uygulamanızın dizinine ve kötü amaçlı derlemelerin giriş önlemek için Genel Derleme Önbelleği erişimi sıkı bir şekilde denetlemenizi sağlar.

<xref:System.Xml.Serialization.XmlSerializer> Bir hizmet reddi saldırısı tabi olabilir. <xref:System.Xml.Serialization.XmlSerializer> Sahip olmadığı bir `MaxItemsInObjectGraph` kota (kullanılabilir olduğu <xref:System.Runtime.Serialization.DataContractSerializer>). Bu nedenle, nesneler, yalnızca ileti boyutuyla sınırlı miktarda bir rastgele çıkarır.

### <a name="partial-trust-threats"></a>Kısmi güven tehditler

Kısmi güven ile çalışan kod için ilgili tehditleri ile ilgili aşağıdaki sorunlar unutmayın. Bu tehditler, diğer saldırı senaryoları (belirli bir dizeyi ve ardından seri durumdan çıkarılırken oluşturan örneğin kısmen güvenilen kodu) ile birlikte kötü amaçlı kod kısmen güvenilen yanı sıra kötü amaçlı kısmen güvenilen kod içerir.

- Hiçbir zaman herhangi bir seri hale getirme bileşeni kullanırken, bu tür bir kullanımdan önce herhangi bir izni bile, onay kapsamında tüm serileştirme senaryodur ve herhangi bir güvenilir olmayan verileri veya nesneleri ile ilgili olmayan onay. Konusu kullanımları, güvenlik açıklarına neden olabilir.

- Kısmen güvenilen kod genişletilebilirlik noktaları (yedekleri) serileştirilmekte olan tür veya başka bir yolla yoluyla seri hale getirme işlemi üzerinde denetime sahip olduğu durumlarda kısmen güvenilen kod büyük miktarda çıktısını almak seri hale getirici neden olabilir Hizmet Reddi (DoS) bu akışın alıcısına neden olabilecek serileştirilmiş akış verileri. DoS tehditlere karşı duyarlı bir hedef yönelik verileri seri hale getirme değil kısmen güvenilen türleri serileştirmek veya aksi kısmen güvenilen kod denetim serileştirme izin.

- Kısmen güvenilen kod erişime izin verirseniz, <xref:System.Runtime.Serialization.DataContractSerializer> örneği veya aksi halde denetim [veri anlaşması yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), serileştirme/seri durumdan çıkarma işlemi üzerinde denetim büyük ölçüde çalışma. Örneğin, bunu rastgele türler ekleme, bilginin açığa çıkmasına neden, elde edilen Nesne grafiği veya serileştirilmiş veriler ile değiştirmesine veya sonuç seri hale getirilmiş akış taşması. Eşdeğer <xref:System.Runtime.Serialization.NetDataContractSerializer> tehdit "Kullanarak NetDataContractSerializer güvenli bir şekilde" bölümünde açıklanmıştır.

- Varsa <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği bir türe uygulandı (veya türü olarak işaretlenmiş <xref:System.SerializableAttribute> ancak <xref:System.Runtime.Serialization.ISerializable>), seri durumdan çıkarıcı, genel olmayan ya da talepleri tarafından korunan tüm oluşturucular olsa bile, böyle bir türü örneği oluşturabilirsiniz.

- Hiçbir zaman seri durumundan çıkarma sonucu verileri seri durumdan güvenilir değilse ve tüm bilinen türler güvendiğiniz türleri olan güvenin. Bilinen türler uygulama yapılandırma dosyasından yüklenen değildir (ancak bilgisayar yapılandırma dosyasından yüklenir) unutmayın kısmi güvende çalışan.

- Geçirirseniz bir <xref:System.Runtime.Serialization.DataContractSerializer> örneği ile bir vekil eklenen kısmen güvenilen kod için kod, tüm bu yedek değiştirilebilir ayarlarını değiştirebilirsiniz.

- Bir seri durumdan çıkarılmış nesne için XML okuyucusu (veya veri sıralamadaki) gelen kısmen güvenilen koddan elde edilen seri durumdan çıkarılmış nesne güvenilir olmayan verileri işle.

- Olgu, <xref:System.Runtime.Serialization.ExtensionDataObject> türünde hiçbir Genel üyeler içerdiği verilerin güvenli olduğunu gelmez. Örneğin, bazı verilerin bulunduğu, kısmen güvenilen kod, nesne sonra elle bir nesneye bir ayrıcalıklı veri kaynağından seri durumdan, kısmen güvenilen kod verileri okuyabilir `ExtensionDataObject` nesneyi seri hale getirme tarafından. Ayarlamayı düşünün <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> için `true` ne zaman ayrıcalıklı bir veri kaynağından daha sonraki bir nesnede seri durumdan çıkarılırken izin ver geçirilen kısmen güvenilen kodu.

- <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tam güvende seri hale getirilmesini özel, korumalı, dahili ve genel üyeleri destekler. Ancak, yalnızca Genel üyeler kısmi güvende serileştirilebilir. A <xref:System.Security.SecurityException> uygulamanın genel olmayan üye bir'seri hale getirme girişiminde bulunursa oluşturulur.

    İç izin vermek veya kısmi güvende seri hale için iç korumalı üyeler <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> derleme özniteliği. Bu öznitelik, iç üyelerini bazı diğer derlemeye görünür olduğunu bildirmek bir derleme sağlar. Bu durumda, iç üyelerini seri olmasını isteyen bir derleme iç üyelerini System.Runtime.Serialization.dll için görünür olduğunu bildirir.

    Bu yaklaşımın avantajı, bir yükseltilmiş kod oluşturma yolu gerektirmez olmasıdır.

    Aynı anda iki ana dezavantajları vardır.

    İlk dezavantajı, katılım özelliğidir <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> derleme genelinde bir özniteliktir. Diğer bir deyişle, yalnızca belirli bir sınıfı serileştirilmiş iç üyeleri olduğunu belirtemezsiniz. Elbette, yine de belirli bir iç üyeyi basitçe değil ekleyerek serileştirilecek değil seçebileceğiniz bir <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği bu üye için. Benzer şekilde, bir geliştirici, özel veya korumalı, hafif görünürlük kaygıları yerine bir üye iç yapmak de seçebilirsiniz.

    İkinci dezavantajı, hala özel veya korumalı üyeler desteklemediğini ' dir.

    Kullanımını göstermek için <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> kısmi güvende öznitelik, aşağıdaki program göz önünde bulundurun:

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]

    Yukarıdaki örnekte `PermissionsHelper.InternetZone` karşılık gelen <xref:System.Security.PermissionSet> kısmi güven için. Şimdi, olmadan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> özniteliği, uygulama başarısız olur, özel durum atma bir <xref:System.Security.SecurityException> gösteren genel olmayan üyelere kısmi güvende serileştirilemiyor.

    Ancak, aşağıdaki satırı için kaynak dosyası eklerseniz program başarıyla çalışır.

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]

## <a name="other-state-management-concerns"></a>Diğer durum yönetimi konuları

Nesne durumu yönetimi ile ilgili bazı sorunları söz şunlardır:

- Akış tabanlı programlama modeli ile bir akış aktarma kullanırken, bir ileti gelirse iletisinin işlenmesi oluşur. İletiyi gönderen, daha fazla içerik bekleniyorsa kodunuzu beklenmeyen bir durumda bırakır. akış ortasında gönderme işlemini iptal. Genel olarak, eksiksiz olmasının akışta güvenmeyin ve herhangi bir iş akışı geri iptal edildi durumunda, alınamaz akış tabanlı bir işlemde gerçekleştirmeyin. Bu durum burada bir ileti olabilir hatalı biçimlendirilmiş akış gövdeden sonra durum için de geçerlidir (örneğin, SOAP Zarfı için bir bitiş etiketi eksik olabilir veya ikinci bir ileti gövdesi olabilir).

- Kullanarak `IExtensibleDataObject` özellik derleyicisindeki hassas verileri neden olabilir. Güvenilmeyen bir kaynaktan gelen veriler ile veri sözleşmeleri içine kabul ettiğiniz, `IExtensibleObjectData` ve daha sonra bu iletileri oturumunuz nereden güvenli bir kanal üzerinde yeniden yayma, büyük olasılıkla bildiğiniz bir şey hakkında veriler için özgün olduğunu belgelemekten. Ayrıca, genel durumu gönderdiğiniz veri bilinen ve bilinmeyen parçalarını dikkate alın, geçersiz olabilir. Ya da seçmeli olarak uzantısı data özelliğini ayarlayarak bu durumdan kaçınmak `null` veya seçmeli olarak devre dışı bırakarak `IExtensibleObjectData` özelliği.

## <a name="schema-import"></a>Şema içeri aktarma

Normalde, türleri oluşturmak için Şemayı içeri aktarma işlemi yalnızca tasarım zamanında, örneğin, kullanırken gerçekleşir [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci sınıfı oluşturmak için bir Web hizmeti. Ancak, daha gelişmiş senaryolarda, çalışma zamanında şema işleyebilir. Bunun yapılması hizmet reddi riskleri kullanıma sunabileceğiniz dikkat edin. Bazı şema içeri aktarılacak uzun sürebilir. Hiçbir zaman kullanmayın <xref:System.Xml.Serialization.XmlSerializer> şema içeri aktarma bileşen şemaları büyük olasılıkla güvenilmeyen bir kaynaktan gelip gelmediğine senaryolarda.

## <a name="threats-specific-to-aspnet-ajax-integration"></a>ASP.NET AJAX tümleştirme özgü tehditler

Kullanıcı ne zaman uygulayan <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> veya <xref:System.ServiceModel.Description.WebHttpBehavior>, WCF, hem XML hem de JSON iletileri kabul edebilen bir uç noktasını kullanıma sunar. Ancak, hem XML okuyucusu ve JSON okuyucu tarafından kullanılan okuyucu kotaları, yalnızca bir dizi yoktur. Bazı kota ayarları bir okuyucu için uygun ancak diğer çok büyük olabilir.

Uygularken `WebScriptEnablingBehavior`, kullanıcı uç noktasında bir JavaScript proxy'si kullanıma sunmak için olanağına sahiptir. Aşağıdaki güvenlik sorunları dikkate alınmalıdır:

- JavaScript proxy'si inceleyerek (işlem adları, parametre adları vb.) hizmeti hakkında bilgi elde edilebilir.

- JavaScript uç noktası kullanırken, hassas ve özel bilgileri istemci Web tarayıcısının önbelleğine saklanması gerekir.

## <a name="a-note-on-components"></a>Not bileşenleri

WCF esnek ve özelleştirilebilir bir sistemdir. Bu konunun içeriği en yaygın WCF kullanım senaryoları üzerinde odaklanın. Ancak, birçok farklı şekilde WCF sağlayan bileşenleri oluşturmak mümkündür. Her bir bileşenini kullanarak güvenlik etkilerini anlamak önemlidir. Özellikle:

- XML okuyucular kullanmalısınız okuyucular kullanarak <xref:System.Xml.XmlDictionaryReader> sınıfı, aksine başka bir okuyucu sağlar. Güvenli okuyucular kullanılarak oluşturulur <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, veya <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> yöntemleri. Kullanmayın <xref:System.Xml.XmlReader.Create%2A> yöntemi. Her zaman okuyucular güvenli kotaları yapılandırın. Yalnızca WCF güvenli XML okuyucular ile kullanıldığında, WCF serileştirme motorlarında güvenlidir.

- Kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> potansiyel olarak güvenilir olmayan verileri seri durumdan çıkarılacak her zaman ayarlamak <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> özelliği.

- Bir ileti oluştururken şu ayarları yapın `maxSizeOfHeaders` parametresi varsa `MaxReceivedMessageSize` yeterli koruma sağlamaz.

- Bir kodlayıcı oluştururken, her zaman ilgili kotalar gibi yapılandırma `MaxSessionSize` ve `MaxBufferSize`.

- Bir XPath İleti Filtresi kullanırken ayarlayın <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> filtre ziyaret eder XML düğümüyle miktarını sınırlamak için. Birçok düğüm ziyaret etmenize gerek kalmadan işlem uzun sürebilir XPath ifadeleri kullanmayın.

- Genel olarak, bir kota kabul eden herhangi bir bileşeni kullanırken, kendi güvenlik etkilerini anlamak ve güvenli bir değere ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.XmlDictionaryReader>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Veri Anlaşması Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
