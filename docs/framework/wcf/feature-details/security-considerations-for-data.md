---
title: Veriler için Güvenlik Konuları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
ms.openlocfilehash: 8cb7ee2ea2418602d944c3c08cec2b9279dca3b9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601068"
---
# <a name="security-considerations-for-data"></a>Veriler için Güvenlik Konuları

Windows Communication Foundation (WCF) içindeki verilerle ilgilenirken, bir dizi tehdit kategorisini göz önünde bulundurmanız gerekir. Aşağıdaki tabloda, veri işlemeyle ilgili en önemli tehdit sınıfları listelenmektedir. WCF, bu tehditleri hafifletmek için araçlar sağlar.

Hizmet reddi güvenilir olmayan verileri alırken, veriler, alıcı tarafın bellek, iş parçacıkları, kullanılabilir bağlantılar veya işlemci döngüleri gibi uzun hesaplamalar oluşmasına neden olacak şekilde orantısız bir miktar kaynağa erişmesini sağlayabilir. Bir sunucuya yönelik bir hizmet reddi saldırısı, çökmesine ve diğer, meşru istemcilerden gelen iletileri işleyememesine neden olabilir.

Kötü amaçlı kod yürütme gelen güvenilmeyen veriler, alıcı tarafın kendisine ait olmadığı kodu çalıştırmasına neden olur.

Bilgilerin açıklanması uzak saldırgan, alıcı tarafın taleplerine göre daha fazla bilgi açığa çıkarmasına benzer şekilde isteklerine yanıt vermesini zorlamasına olanak sağlar.

## <a name="user-provided-code-and-code-access-security"></a>Kullanıcı tarafından sağlanmış kod ve kod erişim güvenliği

Kullanıcı tarafından temin edilen Windows Communication Foundation (WCF) altyapı çalıştırma kodu içindeki çeşitli konumlar. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme altyapısı Kullanıcı tarafından belirtilen özellik `set` erişimcileri ve `get` erişimcileri çağırabilir. WCF kanal altyapısı, sınıfının Kullanıcı tarafından sağlanmış türetilmiş sınıflarına da çağrı gösterebilir <xref:System.ServiceModel.Channels.Message> .

Bu, herhangi bir güvenlik açığının mevcut olmadığından emin olmak için kod yazarının sorumluluğundadır. Örneğin, tamsayı türünde bir veri üyesi özelliği olan bir veri sözleşmesi türü oluşturursanız ve `set` erişimci uygulamasında özellik değerini temel alan bir dizi ayırdıysanız, kötü amaçlı bir ileti bu veri üyesine yönelik son derece büyük bir değer içeriyorsa hizmet reddi saldırısı olasılığını açığa çıkarır. Genel olarak, gelen verileri temel alan veya Kullanıcı tarafından belirtilen koddaki uzun işleme dayalı herhangi bir ayırmaktan kaçının (özellikle uzun işleme, daha az sayıda gelen veri olabilir). Kullanıcı tarafından sağlanmış kodun güvenlik analizini gerçekleştirirken, tüm hata durumlarını (yani, özel durumların oluşturulduğu tüm kod dallarını) göz önünde bulundurduğunuzdan emin olun.

Kullanıcı tarafından sağlanmış kodun en son örneği, her işlem için hizmet uygulamanızın içindeki koddur. Hizmet uygulamanızın güvenliği sizin sorumluluğunuzdadır. Yanlışlıkla hizmet reddi açıklarına neden olabilecek güvenli olmayan bir işlem uygulamaları oluşturmak kolaydır. Örneğin, bir dize alan ve adı bu dizeyle başlayan bir veritabanındaki müşterilerin listesini döndüren bir işlem. Büyük bir veritabanıyla çalışıyorsanız ve geçirilmekte olan dize yalnızca tek bir harfle fazlaysa, kodunuz tüm kullanılabilir bellekten daha büyük bir ileti oluşturmayı deneyebilir ve tüm hizmetin başarısız olmasına neden olabilir. ( <xref:System.OutOfMemoryException> .NET Framework bir kurtarılabilir değildir ve her zaman uygulamanızın sonlandırmasına neden olur.)

Çeşitli genişletilebilirlik noktalarına hiçbir kötü amaçlı kod takılı olmadığından emin olmanız gerekir. Bu durum özellikle kısmi güven altında çalışırken, kısmen güvenilen derlemelerin türleriyle ilgilenirken veya kısmen güvenilen kod tarafından kullanılabilir bileşenleri oluştururken ilgilidir. Daha fazla bilgi için sonraki bölümde "kısmi güven tehditleri" bölümüne bakın.

Kısmi güvende çalışırken, veri sözleşmesi serileştirme altyapısının yalnızca veri sözleşmesi programlama modelinin sınırlı bir alt kümesini desteklediğini unutmayın; Örneğin, özel veri üyeleri veya özniteliğini kullanan türler <xref:System.SerializableAttribute> desteklenmez. Daha fazla bilgi için bkz. [kısmi güven](partial-trust.md).

## <a name="avoiding-unintentional-information-disclosure"></a>Yanlışlıkla bilginin açıklanmasını önleme

Güvenliği göz önünde bulundurularak serileştirilebilir türler tasarlarken, bilgilerin açıklanması olası bir konudur.

Aşağıdaki noktaları göz önünde bulundurun:

- <xref:System.Runtime.Serialization.DataContractSerializer>Programlama modeli, serileştirme sırasında tür veya derleme dışındaki özel ve iç verilerin açığa çıkmasına izin verir. Ek olarak, bir türün şekli, şema dışarı aktarma işlemi sırasında açığa çıkabilir. Türün serileştirme projeksiyonunu anladığınızdan emin olun. Ortaya çıkmayı istemiyorsanız, (örneğin, <xref:System.Runtime.Serialization.DataMemberAttribute> bir veri sözleşmesi durumunda özniteliği uygulamadan) serileştirilmesi devre dışı bırakın.

- Aynı türde birden çok serileştirme projeksiyonuna sahip olabileceğini ve kullanımda olan serileştiriciye bağlı olduğunu unutmayın. Aynı tür, ile <xref:System.Runtime.Serialization.DataContractSerializer> birlikte kullanıldığında ve başka bir veri kümesiyle birlikte kullanıldığında bir veri kümesini açığa çıkabilir <xref:System.Xml.Serialization.XmlSerializer> . Yanlışlıkla yanlış serileştirici kullanılması bilgilerin açığa çıkmasına neden olabilir.

- <xref:System.Xml.Serialization.XmlSerializer>Eski uzak yordam çağrısı (RPC)/Encoded modunun kullanımı, gönderme tarafındaki nesne grafiğinin şeklini istenmeden alma tarafına gösterebilir.

## <a name="preventing-denial-of-service-attacks"></a>Hizmet reddi saldırılarını engelleme

### <a name="quotas"></a>Kotalar

Alıcı tarafın önemli miktarda bellek ayırmasına neden olma olasılığı, olası bir hizmet reddi saldırıdır. Bu bölüm, büyük iletilerden kaynaklanan bellek tüketimi sorunlarını ele alırken diğer saldırılar meydana gelebilir. Örneğin, iletiler bir orantısız miktarı işlem süresi kullanıyor olabilir.

Hizmet reddi saldırıları genellikle kotalar kullanılarak azaltılmıştır. Bir kota aşıldığında, <xref:System.ServiceModel.QuotaExceededException> normalde bir özel durum oluşturulur. Kota olmadan kötü amaçlı bir ileti, kullanılabilir tüm belleğe erişilmesine, bir <xref:System.OutOfMemoryException> özel duruma veya tüm kullanılabilir yığınlara erişilmesine neden olabilir ve buna yol açar <xref:System.StackOverflowException> .

Kota aşıldı senaryosu kurtarılabilir; çalışan bir hizmette karşılaşılırsa, şu anda işlenen ileti atılır ve hizmet çalışmaya devam eder ve daha fazla ileti işler. Ancak, bellek dışı ve yığın taşması senaryoları, .NET Framework her yerde kurtarılamaz; hizmet böyle özel durumlarla karşılaşırsa sonlandırır.

WCF 'de kotalar ön tahsisi içermez. Örneğin, <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> Kota (çeşitli sınıflarda bulunan) 128 KB olarak ayarlandıysa, her ileti için 128 KB 'nin otomatik olarak ayrıldığı anlamına gelmez. Ayrılan gerçek miktar, gerçek gelen ileti boyutuna bağlıdır.

Birçok kota, aktarım katmanında kullanılabilir. Bunlar, kullanımdaki belirli aktarım kanalı tarafından zorlanan kotalardır (HTTP, TCP, vb.). Bu konu, bu kotaların bazılarını ele alırken, bu kotalar [Aktarım kotalarıyla](transport-quotas.md)ayrıntılı olarak açıklanmıştır.

### <a name="hashtable-vulnerability"></a>Hashtable güvenlik açığı

Veri sözleşmeleri diyez tabloları veya koleksiyonlar içerdiğinde bir güvenlik açığı oluşur. Bu sorun, çok sayıda değerin aynı karma değeri oluşturabileceği bir Hashtable 'a çok sayıda değer eklenirse oluşur. Bu, DOS saldırısı olarak kullanılabilir.  Bu güvenlik açığı, MaxReceivedMessageSize bağlama kotasının ayarlanarak azaltılabilir. Bu tür saldırıları engellemek için bu kota ayarlanırken dikkatli olunmalıdır. Bu kota, WCF iletisi boyutunun üst sınırını koyar. Ayrıca, veri sözleşmelerinizi kullanarak tablolularıyla veya koleksiyonlar kullanmaktan kaçının.

## <a name="limiting-memory-consumption-without-streaming"></a>Bellek tüketimini akış olmadan sınırlandırma

Büyük iletiler etrafında güvenlik modeli, akışın kullanımda olup olmamasına bağlıdır. Temel, akışlı olmayan bir durumda, mesajların belleği arabelleğe alınır. Bu durumda, <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> <xref:System.ServiceModel.Channels.TransportBindingElement> en büyük ileti boyutunu erişecek şekilde sınırlayarak büyük iletilere karşı korumak için sistem tarafından belirtilen bağlamalarda veya üzerinde bulunan kotayı kullanın. Bir hizmetin aynı anda birden çok ileti işliyor olabileceğini ve bu durumda bunların hepsi bellekte olduğunu unutmayın. Bu tehdidi azaltmak için daraltma özelliğini kullanın.

Ayrıca `MaxReceivedMessageSize` , ileti başına bellek tüketimine bir üst sınır yerleştirmediğini, ancak bunu sabit bir faktör içinde sınırlandırmadığını unutmayın. Örneğin, `MaxReceivedMessageSize` 1 MB ve 1 MB 'lık bir ileti alınıp sonra seri durumdan çıkarılmışsa, seri durumdan çıkarılan nesne grafiğini içermesi için ek bellek gerekir ve bu da 1 MB 'tan fazla toplam bellek tüketimi elde edilir. Bu nedenle, çok fazla gelen veriler olmadan önemli miktarda bellek tüketimine neden olabilecek serileştirilebilir türler oluşturmaktan kaçının. Örneğin, 50 isteğe bağlı veri üyesi alanları ve ek 100 özel alanları olan "MyContract" veri sözleşmesi "" XML yapımı ile oluşturulabilir \<MyContract/> . Bu XML, 150 alanları için belleğe erişilmeye sonuçlanıyor. Veri üyelerinin varsayılan olarak isteğe bağlı olduğunu unutmayın. Böyle bir tür bir dizinin parçasıysa sorun oluşur.

`MaxReceivedMessageSize`Tüm hizmet reddi saldırılarını engellemek için tek başına yeterli değildir. Örneğin, seri hale getirici, iç içe geçmiş bir nesne grafiğinin serisini kaldırmak için (bir başka nesne içeren bir nesne, ancak başka bir nesneyi içeren bir nesne) gelen bir ileti tarafından kaldırılabilir. Hem <xref:System.Runtime.Serialization.DataContractSerializer> hem de <xref:System.Xml.Serialization.XmlSerializer> çağrı yöntemleri, bu tür grafiklerin serisini kaldırmak için iç içe bir yoldur. Yöntem çağrılarının derin iç içe geçirilmesi kurtarılamaz bir sonuç verebilir <xref:System.StackOverflowException> . Bu tehdit, <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> konusunun devamındaki "XML güvenli kullanımı" bölümünde açıklandığı gibi, XML iç içe geçme düzeyini sınırlamak üzere kota ayarlanarak azalmıştır.

Ek kotalar `MaxReceivedMessageSize` , IKILI XML kodlaması kullanılırken özellikle önemlidir. İkili kodlamanın kullanılması, sıkıştırmaya biraz eşdeğerdir: gelen iletideki küçük bir bayt grubu çok fazla veri temsil edebilir. Bu nedenle, sınıra bir ileti ekleme bile `MaxReceivedMessageSize` tam genişletilmiş biçimde daha fazla bellek alabilir. XML 'e özgü bu tehditleri azaltmak için, bu konunun devamındaki "XML güvenli kullanımı" bölümünde anlatıldığı gibi tüm XML okuyucu kotaları doğru ayarlanmalıdır.

## <a name="limiting-memory-consumption-with-streaming"></a>Bellek tüketimini akış ile sınırlama

Akış sırasında `MaxReceivedMessageSize` hizmet reddi saldırılarına karşı korumak için küçük bir ayar kullanabilirsiniz. Ancak, akışta daha karmaşık senaryolar mümkündür. Örneğin, bir dosya karşıya yükleme hizmeti kullanılabilir tüm bellekten daha büyük dosyaları kabul eder. Bu durumda, ' yi `MaxReceivedMessageSize` son derece büyük bir değere ayarlayın, neredeyse hiçbir verinin bellekte arabelleğe alınmadığını ve ileti doğrudan diske akışını bekliyor. Kötü amaçlı bir ileti, WCF 'yi bu durumda akışa almak yerine bu verileri arabelleğe alarak zorlayabilir `MaxReceivedMessageSize`

Bu tehdidi azaltmak için, arabelleğe almayı sınırlayan çeşitli WCF veri işleme bileşenlerinde belirli Kota ayarları vardır. Bunların en önemlisi, `MaxBufferSize` çeşitli taşıma bağlama öğelerinde ve standart bağlamalarda bulunan özelliktir. Akışta, bu kotanın ileti başına ayırmak istediğiniz en fazla bellek miktarını hesaba katmak üzere ayarlanması gerekir. ' De olduğu gibi `MaxReceivedMessageSize` , ayar bellek tüketimine mutlak bir en yüksek değer yerleştirmez, ancak yalnızca sabit bir faktör içinde bu değeri kısıtlar. Ayrıca, ' de olduğu gibi `MaxReceivedMessageSize` , aynı anda birden çok ileti işleme olasılığının farkında olun.

### <a name="maxbuffersize-details"></a>MaxBufferSize ayrıntıları

`MaxBufferSize`Özelliği, toplu arabelleğe alma WCF 'nin her birini sınırlandırır. Örneğin, WCF her zaman SOAP üst bilgilerini ve SOAP hatalarını ve bir Ileti Iletimi Iyileştirme mekanizması (MTOM) iletisindeki doğal okuma düzeninde olmayan tüm MIME parçalarını arabelleğe alır. Bu ayar tüm bu durumlarda arabelleğe alma miktarını sınırlandırır.

WCF bu `MaxBufferSize` değeri, arabelleği olabilecek çeşitli bileşenlere geçirerek gerçekleştirir. Örneğin, sınıfın bazı <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> aşırı yüklemeleri <xref:System.ServiceModel.Channels.Message> bir `maxSizeOfHeaders` parametre alır. WCF, `MaxBufferSize` SOAP üst bilgisi arabelleğe alma miktarını sınırlamak için değeri bu parametreye geçirir. Sınıfı doğrudan kullanılırken bu parametrenin ayarlanması önemlidir <xref:System.ServiceModel.Channels.Message> . Genel olarak, WCF 'de kota parametreleri alan bir bileşen kullanırken, bu parametrelerin güvenlik etkilerine ilişkin etkilerini anlamak ve doğru şekilde ayarlamak önemlidir.

MTOM ileti Kodlayıcısı da bir ayara sahiptir `MaxBufferSize` . Standart bağlamaları kullanırken, bu otomatik olarak aktarım düzeyi `MaxBufferSize` değerine ayarlanır. Ancak, özel bir bağlama oluşturmak için MTOM ileti Kodlayıcısı bağlama öğesi kullanılırken, `MaxBufferSize` akış kullanıldığında özelliği güvenli bir değere ayarlamanız önemlidir.

## <a name="xml-based-streaming-attacks"></a>XML tabanlı akış saldırıları

`MaxBufferSize`Hala, WCF 'nin akış beklenirken arabelleğe alma işlemine zorlanamadığından emin olmak için yeterli değildir. Örneğin, WCF XML okuyucuları her zaman yeni bir öğeyi okumaya Başlarken tüm XML öğesi başlangıç etiketini arabelleğe alın. Bu işlem, ad alanlarının ve özniteliklerin düzgün şekilde işlenmesini sağlayacak şekilde yapılır. `MaxReceivedMessageSize`Büyük olacak şekilde yapılandırıldıysa (örneğin, doğrudan diske büyük dosya akışı senaryosunu etkinleştirmek için), tüm ileti gövdesinin büyük BIR XML öğesi başlangıç etiketi olduğu durumlarda kötü amaçlı bir ileti oluşturulabilir. Bir ile sonuçları okumaya çalışır <xref:System.OutOfMemoryException> . Bu, bu konunun ilerleyen kısımlarında "XML güvenli kullanımı" bölümünde ele alınan XML okuyucu kotaları kullanılarak tamamen azaltılan, XML tabanlı birçok hizmet reddi saldırısından biridir. Akış sırasında, bu kotaların tümünü ayarlamak özellikle önemlidir.

### <a name="mixing-streaming-and-buffering-programming-models"></a>Akış ve arabelleğe alma programlama modellerini karıştırma

Aynı hizmette akış ve akış olmayan programlama modellerini karıştırarak birçok olası saldırı oluşur. İki işlem içeren bir hizmet sözleşmesi olduğunu varsayalım: biri bir alır <xref:System.IO.Stream> ve başka bir özel türün dizisini alır. Ayrıca, `MaxReceivedMessageSize` ilk işlemin büyük akışları işlemesini sağlamak için büyük bir değere ayarlandığını varsayalım. Ne yazık ki bu, büyük iletilerin artık ikinci işleme de gönderilebileceği anlamına gelir ve seri hale getirici, işlem çağrılmadan önce, bellekteki verileri bir dizi olarak arabelleğe alır. Bu, olası bir hizmet reddi saldırıdır: kota, seri `MaxBufferSize` hale getiricinin birlikte çalıştığı ileti gövdesinin boyutunu sınırlamaz.

Bu nedenle, aynı sözleşmede akış tabanlı ve akış olmayan işlemleri karıştırmaktan kaçının. İki programlama modelini kesinlikle karıştırdıysanız, aşağıdaki önlemleri kullanın:

- <xref:System.Runtime.Serialization.IExtensibleDataObject>Özelliğini olarak ayarlayarak özelliği kapatın <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> <xref:System.ServiceModel.ServiceBehaviorAttribute> `true` . Bu, yalnızca sözleşmenin bir parçası olan üyelerin seri durumdan çıkarılmasını sağlar.

- <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A>Öğesinin özelliğini <xref:System.Runtime.Serialization.DataContractSerializer> güvenli bir değere ayarlayın. Bu kota, <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliğinde veya yapılandırma aracılığıyla da kullanılabilir. Bu kota, bir seri kaldırma bölümünde Serisi kaldırılan nesne sayısını sınırlar. Normalde, bir ileti sözleşmesinin her bir işlem parametresi veya ileti gövdesi bölümü bir bölümde seri durumdan çıkarılmış olur. Dizilerin serisi kaldırılırken, her dizi girişi ayrı bir nesne olarak sayılır.

- Tüm XML okuyucu kotalarını güvenli değerlere ayarlayın. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>Akış olmayan işlemlerde, ve ' a dikkat edin <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> ve dizeleri önleyin.

- Bilinen türlerin listesini gözden geçirin ve bunlardan herhangi birinin herhangi bir zamanda örneklendirildiğini aklınızda bulundurun (Bu konunun ilerleyen kısımlarında yer alan "Istenmeyen türlerin yüklenmesini koruma" bölümüne bakın).

- <xref:System.Xml.Serialization.IXmlSerializable>Çok miktarda veriyi arabelleğe alan arabirimi uygulayan herhangi bir tür kullanmayın. Bu tür türleri bilinen türler listesine eklemeyin.

- <xref:System.Xml.XmlElement> <xref:System.Xml.XmlNode> <xref:System.Byte> Bir sözleşmede uygulayan, diziler, diziler veya türler kullanmayın <xref:System.Runtime.Serialization.ISerializable> .

- <xref:System.Xml.XmlElement> <xref:System.Xml.XmlNode> <xref:System.Byte> Bilinen türler listesinde öğesini uygulayan, diziler, diziler veya türler kullanmayın <xref:System.Runtime.Serialization.ISerializable> .

Akış olmayan işlem ' i kullandığında önceki önlemler geçerlidir <xref:System.Runtime.Serialization.DataContractSerializer> . , Kota korumasına sahip olmadığından, aynı hizmette akış ve akış olmayan programlama modellerini hiçbir şekilde karıştırmayın <xref:System.Xml.Serialization.XmlSerializer> <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> .

### <a name="slow-stream-attacks"></a>Yavaş akış saldırıları

Akış hizmeti reddi saldırılarının bir sınıfı, bellek tüketimi içermez. Bunun yerine, saldırı yavaş bir göndereni veya veri alıcısını içerir. Verilerin gönderilmesi veya alınması beklenirken, iş parçacıkları ve kullanılabilir bağlantılar gibi kaynaklar tükenmiştir. Bu durum kötü amaçlı bir saldırının veya yavaş bir ağ bağlantısındaki meşru bir gönderenden/alıcının sonucu olarak ortaya çıkabilir.

Bu saldırıları azaltmak için taşıma zaman aşımlarını doğru olarak ayarlayın. Daha fazla bilgi için bkz. [Aktarım kotaları](transport-quotas.md). İkinci olarak, `Read` `Write` WCF 'de akışlarla çalışırken hiçbir zaman zaman uyumlu veya işlem kullanmayın.

## <a name="using-xml-safely"></a>XML 'i güvenle kullanma

> [!NOTE]
> Bu bölüm XML hakkında olsa da, bilgiler JavaScript Nesne Gösterimi (JSON) belgeleri için de geçerlidir. Kotalar, [JSON ve XML arasında eşleme](mapping-between-json-and-xml.md)kullanarak benzer şekilde çalışır.

### <a name="secure-xml-readers"></a>Güvenli XML okuyucuları

XML bilgi kümesi, WCF 'deki tüm ileti işlemenin temelini oluşturur. Güvenilmeyen bir kaynaktan XML verileri kabul edildiğinde, azaltılmalıdır olması gereken birkaç hizmet reddi saldırısı olasılığı vardır. WCF, özel, güvenli XML okuyucuları sağlar. Bu okuyucular, WCF 'de standart kodlamalardan biri (metin, ikili veya MTOM) kullanılırken otomatik olarak oluşturulur.

Bu okuyucular üzerindeki bazı güvenlik özellikleri her zaman etkindir. Örneğin, okuyucular asla bir hizmet reddi saldırısı kaynağı olan ve meşru SOAP iletilerinde hiçbir şekilde görünmemesi gereken belge türü tanımlarını (DTD 'Ler) işlemez. Diğer güvenlik özellikleri, aşağıdaki bölümde açıklanan, yapılandırılması gereken okuyucu kotalarını içerir.

Doğrudan XML okuyucularıyla (kendi özel kodlayıcıınızı yazarken veya sınıfla doğrudan çalışırken <xref:System.ServiceModel.Channels.Message> ) çalışırken, güvenilmeyen verilerle çalışma şansı olduğunda her zaman WCF güvenli okuyucularını kullanın. , Veya sınıfındaki statik fabrika yöntemi aşırı yüklemelerinin birini çağırarak güvenli okuyucular oluşturun <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A> <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A> <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> <xref:System.Xml.XmlDictionaryReader> . Bir okuyucu oluştururken güvenli kota değerlerini geçirin. `Create`Yöntem aşırı yüklerini çağırmayın. Bunlar bir WCF okuyucu oluşturmaz. Bunun yerine, bu bölümde açıklanan güvenlik özellikleriyle korunmayan bir okuyucu oluşturulur.

### <a name="reader-quotas"></a>Okuyucu kotaları

Güvenli XML okuyucuları için beş yapılandırılabilir kota vardır. Bunlar normalde, `ReaderQuotas` kodlama bağlama öğelerinde veya standart bağlamalarda özelliği kullanılarak veya <xref:System.Xml.XmlDictionaryReaderQuotas> okuyucu oluştururken geçirilen bir nesne kullanılarak yapılandırılır.

#### <a name="maxbytesperread"></a>MaxBytesPerRead

Bu kota, `Read` öğe başlangıç etiketi ve özniteliklerini okurken tek bir işlemde okunan bayt sayısını sınırlar. (Akış olmayan durumlarda, öğe adının kendisi kotaya karşı sayılmaz.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A>aşağıdaki nedenlerle önemlidir:

- Okuma sırasında, öğe adı ve öznitelikleri her zaman bellekte arabelleğe alınır. Bu nedenle, akış beklendiğinde aşırı arabelleğe almayı engellemek için bu kotayı akış modunda doğru şekilde ayarlamanız önemlidir. Gerçekleşen `MaxDepth` gerçek arabelleğe alma miktarı hakkında daha fazla bilgi için kota bölümüne bakın.

- Öznitelik adlarının benzersizlik için denetlenmesi gerektiğinden, çok fazla XML özniteliği orantısız işleme süresi kullanabilir. `MaxBytesPerRead`Bu tehdidi azaltır.

#### <a name="maxdepth"></a>MaxDepth

Bu kota, XML öğelerinin en fazla iç içe geçme derinliğini sınırlandırır. Örneğin, " \<A> \<B> \<C/> \</B> \</A> " belgesinin iç içe geçmiş derinliği üç. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>Aşağıdaki nedenlerle önemlidir:

- `MaxDepth`ile etkileşimde `MaxBytesPerRead` bulunur: okuyucu, her zaman geçerli öğe ve tüm üst öğelerinden verileri bellekte tutar, böylece okuyucunun maksimum bellek tüketimi bu iki ayar ürünüyle orantılıdır.

- Derin iç içe geçmiş bir nesne grafiğinin serisi kaldırılırken, seri hale getirici yığının tamamına erişmeye zorlanır ve kurtarılamaz bir değer oluşturur <xref:System.StackOverflowException> . Hem hem de için içe geçen XML iç içe ve nesne arasında doğrudan bağıntı bulunur <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> . `MaxDepth`Bu tehdidi azaltmak için kullanın.

#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount

Bu kota, okuyucunun *NameTable*boyutunu sınırlandırır. NameTable, bir XML belgesi işlenirken karşılaşılan belirli dizeleri (ad alanları ve ön ekler gibi) içerir. Bu dizelerin bellekte ara belleğe alındığından, akış beklendiğinde aşırı arabelleğe almayı engellemek için bu kotayı ayarlayın.

#### <a name="maxstringcontentlength"></a>MaxStringContentLength

Bu kota, XML okuyucunun döndürdüğü en büyük dize boyutunu sınırlandırır. Bu kota, XML okuyucusu içindeki bellek tüketimini, ancak okuyucu kullanan bileşende sınırlamaz. Örneğin,, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli hale getirilmiş bir okuyucu kullandığında <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> , bu kotadan daha büyük dizelerin serisini kaldırmaz. <xref:System.Xml.XmlDictionaryReader>Sınıfı doğrudan kullanıldığında, tüm yöntemler bu kotaya uymaz, ancak yalnızca, yöntemi gibi dizeleri okumak için tasarlanan Yöntemler <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> . <xref:System.Xml.XmlReader.Value%2A>Okuyucudaki özelliği bu kotadan etkilenmez ve bu nedenle bu kotanın sağladığı koruma gerekli olduğunda kullanılmamalıdır.

#### <a name="maxarraylength"></a>MaxArrayLength

Bu kota, bayt dizileri dahil olmak üzere XML okuyucunun döndürdüğü temel elemanların bir dizisinin maksimum boyutunu sınırlandırır. Bu kota, XML okuyucusu üzerinde bellek tüketimini sınırlamaz, ancak okuyucu kullanan herhangi bir bileşende. Örneğin,, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli hale getirilmiş bir okuyucu kullandığında <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> , bu kotadan daha büyük olan bayt dizilerinin serisini kaldırmaz. Tek bir sözleşmede akış ve arabellekli programlama modellerini karıştırmaya çalışırken bu kotayı ayarlamanız önemlidir. <xref:System.Xml.XmlDictionaryReader>Sınıfı doğrudan kullanırken, yalnızca belirli temel türlerin (örneğin,) yalnızca rastgele boyutu dizileri okumak için özel olarak tasarlanan yöntemleri, bu kotanın dikkate alınması gerektiğini aklınızda bulundurun <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A> .

## <a name="threats-specific-to-the-binary-encoding"></a>Ikili kodlamaya özgü tehditler

İkili XML kodlaması WCF, bir *Sözlük dizeleri* özelliği içerir. Büyük bir dize yalnızca birkaç bayt kullanılarak kodlanmayabilir. Bu, önemli ölçüde performans artışı sağlar, ancak hafiflemesinin azaltılması gereken yeni hizmet reddi tehditleri sunar.

İki tür sözlük vardır: *statik* ve *dinamik*. Statik sözlük, ikili kodlamada kısa bir kod kullanılarak gösterilebilen uzun dizelerin yerleşik bir listesidir. Bu dizeler listesi okuyucu oluşturulduğunda ve değiştirilemediği zaman sabittir. Statik sözlükte WCF 'nin varsayılan olarak kullandığı dizelerin hiçbiri, önemli bir hizmet reddi tehdidi oluşturma konusunda yeterince büyük değildir, ancak yine de sözlük genişletme saldırısında kullanılabilir. Kendi statik sözlüğünüzü sağladığınız Gelişmiş senaryolarda, büyük sözlük dizeleri oluştururken dikkatli olun.

Dinamik sözlükler özelliği, iletilerin kendi dizelerini tanımlamasına ve bunları kısa kodlarla ilişkilendirilmesine izin verir. Bu dizeden koda eşlemeler tüm iletişim oturumu sırasında bellekte tutulur, örneğin sonraki iletiler dizelerin yeniden gönderilmesini gerektirmez ve önceden tanımlanmış kodlardan yararlanabilir. Bu dizeler rastgele uzunlukta olabilir ve bu nedenle statik sözlükten daha ciddi bir tehdit oluşturabilir.

Azaltılması gereken ilk tehdit, dinamik sözlüğün (dizeden koda eşleme tablosu) çok büyük hale gelmesine olanak sağlar. Bu sözlük birkaç ileti kursu üzerine genişletilebilir ve bu nedenle `MaxReceivedMessageSize` yalnızca her bir ileti için ayrı olarak uygulandığı için kota hiçbir koruma gerektirmez. Bu nedenle, içinde <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> sözlüğün boyutunu sınırlayan ayrı bir özellik bulunur <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> .

Diğer kotaların aksine bu kota, ileti yazarken de geçerlidir. İleti okunurken aşılırsa, `QuotaExceededException` her zamanki gibi oluşturulur. İleti yazılırken aşılırsa, kotanın aşılmasına neden olan dizeler, Dinamik sözlükler özelliği kullanılmadan olduğu gibi yazılır.

### <a name="dictionary-expansion-threats"></a>Sözlük genişletme tehditleri

Sözlük genişletmesinden sonra, ikili özel saldırıların önemli bir sınıfı. İkili biçimdeki küçük bir ileti, dize sözlükleri özelliğinin yoğun bir şekilde kullanılmasını sağlayan tam olarak genişletilmiş metin biçiminde çok büyük bir ileti açabilir. Dinamik sözlük dizeleri için genişleme faktörü, <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> Tüm sözlüğün en büyük boyutunu aştığından, kota tarafından sınırlandırılır.

<xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength` Ve `MaxArrayLength` özellikleri yalnızca bellek tüketimini sınırlar. Bellek kullanımı zaten sınırlı olduğundan, akış olmayan kullanımdaki tehditleri hafifletmek genellikle gerekmez `MaxReceivedMessageSize` . Ancak, `MaxReceivedMessageSize` ön genişletme baytlarını sayar. İkili kodlama kullanımda olduğunda, bellek tüketimi büyük olasılıkla `MaxReceivedMessageSize` yalnızca bir faktörle sınırlı olabilir <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> . Bu nedenle, ikili kodlama kullanılırken her zaman okuyucu kotaları (özellikle) ayarlanması önemlidir <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A> .

İkili kodlama ile birlikte kullanıldığında, <xref:System.Runtime.Serialization.DataContractSerializer> `IExtensibleDataObject` bir sözlük genişletme saldırısı bağlamak için arabirim kötüye kullanılabilir. Bu arabirim temelde, sözleşmenin bir parçası olmayan rastgele veriler için sınırsız depolama alanı sağlar. Kotalar, bir sorun ortaya çıkaran gibi yeterince düşük bir şekilde ayarlanmıyorsa `MaxSessionSize` `MaxReceivedMessageSize` , `IExtensibleDataObject` ikili kodlamayı kullanırken özelliği devre dışı bırakın. `IgnoreExtensionDataObject`Özelliği özniteliğinde olarak ayarlayın `true` `ServiceBehaviorAttribute` . Alternatif olarak, `IExtensibleDataObject` arabirimini uygulamayın. Daha fazla bilgi için bkz. [Ileri uyumlu veri sözleşmeleri](forward-compatible-data-contracts.md).

### <a name="quotas-summary"></a>Kotalar Özeti

Aşağıdaki tabloda kotalar hakkında rehberlik özetlenmektedir.

|Koşul|Ayarlanacak önemli kotalar|
|---------------|-----------------------------|
|Akış veya akış küçük iletileri, metin veya MTOM kodlaması yok|`MaxReceivedMessageSize`, `MaxBytesPerRead` ve`MaxDepth`|
|Akış veya akış küçük iletileri, ikili kodlama|`MaxReceivedMessageSize`, `MaxSessionSize` , ve tümü`ReaderQuotas`|
|Büyük ileti, metin veya MTOM kodlamasını akışa alma|`MaxBufferSize`ve tümü`ReaderQuotas`|
|Büyük iletileri akışa alma, ikili kodlama|`MaxBufferSize`, `MaxSessionSize` , ve tümü`ReaderQuotas`|

- Aktarım düzeyi zaman aşımları her zaman ayarlanmalıdır ve büyük veya küçük iletiler akışı yapıp görmediğine bakılmaksızın, akış kullanımda olduğunda zaman uyumlu okuma/yazma işlemleri kullanmayın.

- Bir kota hakkında şüpheli olduğunda, açık bırakmak yerine güvenli bir değere ayarlayın.

## <a name="preventing-malicious-code-execution"></a>Kötü amaçlı kod yürütmeyi önler

Aşağıdaki genel tehdit sınıfları kodu yürütebilir ve istenmeyen etkilere sahip olabilir:

- Seri hale getirici, kötü amaçlı, güvenli olmayan veya güvenliğe duyarlı bir tür yükler.

- Gelen bir ileti, seri hale getiricinin, olağan dışı sonuçlara sahip olacak şekilde normal bir şekilde güvenli türde bir örnek oluşturmasına neden olur.

Aşağıdaki bölümlerde bu tehdit sınıfları daha fazla ele alınmaktadır.

## <a name="datacontractserializer"></a>DataContractSerializer

(Hakkında güvenlik bilgileri için <xref:System.Xml.Serialization.XmlSerializer> ilgili belgelere bakın.) İçin güvenlik modeli, <xref:System.Xml.Serialization.XmlSerializer> <xref:System.Runtime.Serialization.DataContractSerializer> ile benzerdir ve genellikle ayrıntılarda farklılık gösterir. Örneğin, <xref:System.Xml.Serialization.XmlIncludeAttribute> özniteliği özniteliği yerine tür içerme için kullanılır <xref:System.Runtime.Serialization.KnownTypeAttribute> . Ancak, öğesine özgü bazı tehditler <xref:System.Xml.Serialization.XmlSerializer> Bu konunun ilerleyen kısımlarında ele alınmıştır.

### <a name="preventing-unintended-types-from-being-loaded"></a>Istenmeyen türlerin yüklenmesini önler

İstenmeden türlerin yüklenmesi, türün kötü amaçlı olup olmadığı veya yalnızca güvenliğe duyarlı yan etkileri olan önemli sonuçlara sahip olabilir. Bir tür, açıktan yararlanma güvenlik açığı içerebilir, kurucuya da sınıf oluşturucusunda güvenliğe duyarlı eylemler gerçekleştirebilir, hizmet reddi saldırılarını kolaylaştıran büyük bir bellek parmak izine sahip olabilir veya kurtarılamaz özel durumlar oluşturabilir. Türler, türü yüklendikten hemen sonra ve herhangi bir örnek oluşturulmadan önce çalışan sınıf oluşturuculara sahip olabilir. Bu nedenlerden dolayı, seri hale getiricinin yükleyebileceği tür kümesini denetlemek önemlidir.

, <xref:System.Runtime.Serialization.DataContractSerializer> Gevşek olarak bağlanmış bir şekilde seri hale getirir. Ortak dil çalışma zamanı (CLR) türünü ve gelen verilerden derleme adlarını hiçbir şekilde okumazlar. Bu, öğesinin davranışına benzerdir, ancak,, <xref:System.Xml.Serialization.XmlSerializer> ve ' nin davranışından farklıdır <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Gevşek bir güvenlik derecesi, uzak saldırgan yalnızca iletideki türü adlandırarak, yüklenecek rastgele bir tür belirtemediği için bir güvenlik derecesi sunar.

<xref:System.Runtime.Serialization.DataContractSerializer>Her zaman sözleşmeye göre beklenen bir tür yüklemeye izin verilir. Örneğin, bir veri sözleşmesinin türünde bir veri üyesi varsa `Customer` , <xref:System.Runtime.Serialization.DataContractSerializer> `Customer` Bu veri üyesini serileştirtiğinde türü yüklemesine izin verilir.

Ayrıca, çok <xref:System.Runtime.Serialization.DataContractSerializer> biçimliliği destekler. Veri üyesi olarak bildirilebilecek <xref:System.Object> , ancak gelen veriler bir örnek içeriyor olabilir `Customer` . Bu, yalnızca `Customer` tür "bilinen" Bu mekanizmalardan biri aracılığıyla seri hale getirici 'e "bilindiğinde" yapılabilir.

- <xref:System.Runtime.Serialization.KnownTypeAttribute>bir türe uygulanan öznitelik.

- `KnownTypeAttribute`bir tür listesi döndüren bir yöntemi belirten öznitelik.

- `ServiceKnownTypeAttribute`özniteliğe.

- `KnownTypes`Yapılandırma bölümü.

- Serileştirici doğrudan kullanılıyorsa, oluşturma sırasında açıkça kendisine geçirilen bilinen türlerin listesi <xref:System.Runtime.Serialization.DataContractSerializer> .

Bu mekanizmaların her biri, seri hale getiricinin yükleyemekte olduğu daha fazla tür sunarak yüzey alanını artırır. Bilinen türler listesine kötü amaçlı veya istenmeyen türlerin eklenmemesini sağlamak için bu mekanizmaların her birini denetleyin.

Bilinen bir tür kapsam içinde olduğunda, bu, herhangi bir zamanda yüklenebilir ve anlaşma gerçekten onu kullanıyor olsa bile, türün örnekleri oluşturulabilir. Örneğin, yukarıdaki mekanizmalardan birini kullanarak "MyDangerousType" türünün bilinen türler listesine eklendiğini varsayalım. Bunun anlamı:

- `MyDangerousType`yüklenir ve sınıf oluşturucusu çalışır.

- Bir veri sözleşmesinin dize veri üyesine serisi kaldırılırken bile kötü amaçlı bir ileti bir örneğinin oluşturulmasına neden olabilir `MyDangerousType` . İçindeki `MyDangerousType` özellik ayarlayıcıları gibi kod çalıştırılabilir. Bu yapıldıktan sonra, seri hale getirici bu örneği dize veri üyesine atamayı dener ve bir özel durumla başarısız olur.

Bilinen türlerin bir listesini döndüren veya bir listeyi doğrudan oluşturucuya geçirirken bir yöntemi yazarken <xref:System.Runtime.Serialization.DataContractSerializer> , listeyi hazırlayan kodun güvenli olduğundan ve yalnızca güvenilir veriler üzerinde çalıştığından emin olun.

Yapılandırmada bilinen türleri belirtirken, yapılandırma dosyasının güvenli olduğundan emin olun. Yapılandırmada her zaman tanımlayıcı adlar kullanın (türün bulunduğu imzalı derlemenin ortak anahtarını belirterek), ancak yüklenecek türün sürümünü belirtmeyin. Tür yükleyicisi, mümkünse en son sürümü otomatik olarak seçer. Yapılandırmada belirli bir sürümü belirtirseniz, aşağıdaki riski çalıştırırsınız: bir tür, gelecekteki bir sürümde düzeltilebilecek bir güvenlik güvenlik açığına sahip olabilir, ancak yapılandırmada açık bir şekilde belirtildiğinden, savunmasız sürüm hala yüklenir.

Çok sayıda bilinen türün başka bir sonucu vardır:, <xref:System.Runtime.Serialization.DataContractSerializer> uygulama etki alanında serileştirme ve seri durumdan çıkarma gereken her tür için bir giriş içeren bir serileştirme/seri hale getirme kodu önbelleği oluşturur. Bu önbellek, uygulama etki alanı çalıştığı sürece hiçbir zaman temizlenmez. Bu nedenle, bir uygulamanın birçok bilinen türü kullandığını algılayan bir saldırgan bu türlerin serisini kaldırma, önbelleğin orantısız büyük miktarda belleği kullanmasına neden olabilir.

### <a name="preventing-types-from-being-in-an-unintended-state"></a>Türlerin ISTENMEDEN bir durumda olmasını önlemek

Bir tür, Zorlanmış olması gereken iç tutarlılık kısıtlamalarına sahip olabilir. Seri durumdan çıkarma sırasında bu kısıtlamaların kesilmesini önlemek için dikkatli olunmalıdır.

Aşağıdaki bir tür örneği, bir spaceckft üzerindeki Airlock 'un durumunu temsil eder ve hem iç hem de dış kapıların aynı anda açık olmadığı kısıtlamayı zorlar.

[!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
[!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]

Bir saldırgan bunun gibi kötü amaçlı bir ileti gönderebilir ve bu, kısıtlamaları ve nesneyi geçersiz duruma getirmeye karşı istenmeyen ve öngörülemeyen sonuçlara yol açabilir.

```xml
<SpaceStationAirlock>
    <innerDoorOpen>true</innerDoorOpen>
    <outerDoorOpen>true</outerDoorOpen>
</SpaceStationAirlock>
```

Bu durumun aşağıdaki noktalara dikkat ederek kaçınılabilir:

- <xref:System.Runtime.Serialization.DataContractSerializer>Çoğu sınıfı seri hale geldiğinde, oluşturucular çalışmaz. Bu nedenle, oluşturucuda gerçekleştirilen herhangi bir durum yönetimine güvenmeyin.

- Nesnenin geçerli bir durumda olduğundan emin olmak için geri çağırmaları kullanın. Özniteliği ile işaretlenen geri çağırma <xref:System.Runtime.Serialization.OnDeserializedAttribute> işlemi, seri durumdan çıkarma tamamlandıktan sonra çalıştığı ve genel durumu İnceleme ve düzeltme şansı varsa özellikle yararlıdır. Daha fazla bilgi için bkz. [Sürüm dayanıklı serileştirme geri çağırmaları](version-tolerant-serialization-callbacks.md).

- Veri anlaşması türlerini, özellik ayarlayıcılarının çağrılması gereken belirli bir sıraya göre tasarlamayın.

- Özniteliğiyle işaretlenmiş eski türleri kullanarak dikkatli yapın <xref:System.SerializableAttribute> . Bunların birçoğu yalnızca güvenilir verilerle kullanılmak üzere .NET Framework uzaktan iletişim için tasarlanmıştır. Bu öznitelikle işaretlenen mevcut türler, durum güvenliği göz önünde bulundurularak tasarlanmayabilir.

- <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> <xref:System.Runtime.Serialization.DataMemberAttribute> Durum güvenliği açısından verilerin varlığını güvence altına almak için özniteliğinin özelliğine güvenmeyin. Veriler her zaman, `null` `zero` veya olabilir `invalid` .

- Güvenilmeyen bir veri kaynağından Serisi kaldırılan bir nesne grafiğine hiçbir şekilde güvenmez. Tek tek her nesne tutarlı bir durumda olabilir, ancak nesne grafı bir bütün olarak olmayabilir. Ayrıca, nesne grafik koruma modu devre dışı olsa bile, serisi kaldırılan grafikte aynı nesneye birden fazla başvuru olabilir veya döngüsel başvurular olabilir. Daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).

### <a name="using-the-netdatacontractserializer-securely"></a>NetDataContractSerializer 'ı güvenli kullanma

, <xref:System.Runtime.Serialization.NetDataContractSerializer> Türlerine sıkı biçimde kullanan bir serileştirme altyapısıdır. Bu, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve ' a benzerdir <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> . Diğer bir deyişle, gelen verilerden .NET Framework derlemeyi ve tür adını okuyarak hangi türün örneklendirilecek olduğunu belirler. WCF 'nin bir parçası olsa da, bu serileştirme altyapısını takma yöntemi değildir; özel kod yazılması gerekir. , `NetDataContractSerializer` Öncelikle .NET Framework uzaktan iletişim IÇIN WCF 'e geçiş kolaylığı sağlar. Daha fazla bilgi için [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md)bölümündeki ilgili bölüme bakın.

İletinin kendisi herhangi bir tür yüklenebildiğinden, <xref:System.Runtime.Serialization.NetDataContractSerializer> mekanizma doğal olarak güvenli değildir ve yalnızca güvenilir verilerle kullanılmalıdır. Yalnızca güvenli türlerin yüklenmesine izin veren güvenli, tür sınırlaması bir tür bağlayıcı yazarak güvenli hale getirmek mümkündür ( <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> özelliğini kullanarak).

Güvenilen verilerle birlikte kullanıldığında, gelen veriler, özellikle özelliği olarak ayarlandıysa, yüklenecek türü yeterince belirleyebilir <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> . Uygulamanın dizinine veya genel derleme önbelleğine erişimi olan herkes, yüklenmesi beklenen kötü amaçlı bir türü yerine getirebilir. İzinleri doğru şekilde ayarlayarak uygulamanızın dizininin ve genel derleme önbelleğinin güvenliğinin her zaman emin olun.

Genel olarak, örneğinize kısmen güvenilen kod erişimine izin verirseniz `NetDataContractSerializer` veya yedek seçiciyi ( <xref:System.Runtime.Serialization.ISurrogateSelector> ) veya seri hale getirme cildi () kontrol ediyorsanız <xref:System.Runtime.Serialization.SerializationBinder> , kod serileştirme/seri kaldırma işlemi üzerinde harika bir denetim uygulayabilir. Örneğin, rastgele türler ekleyebilir, bilgilerin açığa çıkmasına, sonuçta ortaya çıkan nesne grafı veya serileştirilmiş verilerle oynanmasına ya da sonuç olarak seri hale getirilmiş akış taşmasına yol açabilir.

İle ilgili başka bir güvenlik, `NetDataContractSerializer` kötü amaçlı kod yürütme tehdidi değil, hizmet reddine neden olur. Kullanırken `NetDataContractSerializer` , her zaman <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> kotayı güvenli bir değer olarak ayarlayın. Boyutu yalnızca bu kotayla sınırlı olan bir nesne dizisini ayıran küçük bir kötü amaçlı ileti oluşturmak kolaydır.

### <a name="xmlserializer-specific-threats"></a>XmlSerializer 'a özgü tehditler

<xref:System.Xml.Serialization.XmlSerializer>Güvenlik modeli, ile benzerdir <xref:System.Runtime.Serialization.DataContractSerializer> . Ancak, birkaç tehdit için benzersizdir <xref:System.Xml.Serialization.XmlSerializer> .

, <xref:System.Xml.Serialization.XmlSerializer> Çalışma zamanında *serileştirme derlemeleri* oluşturur ve bunları seri hale getirir ve onları yeniden çıkarır; bu derlemeler geçici dosyalar dizininde oluşturulur. Başka bir işlem veya kullanıcının bu dizine erişim hakları varsa, bu, rastgele kodla serileştirme/seri kaldırma kodunun üzerine yazabilir. <xref:System.Xml.Serialization.XmlSerializer>Ardından, serileştirme/seri durumdan çıkarma kodu yerine bu kodu güvenlik bağlamını kullanarak çalıştırır. Bunun oluşmasını engellemek için izinlerin geçici dosyalar dizininde doğru ayarlandığından emin olun.

<xref:System.Xml.Serialization.XmlSerializer>Ayrıca, çalışma zamanında oluşturmak yerine önceden oluşturulmuş serileştirme derlemelerinin kullanıldığı bir moda sahiptir. Bu mod <xref:System.Xml.Serialization.XmlSerializer> uygun bir serileştirme derlemesini her bulabileceği zaman tetiklenir. <xref:System.Xml.Serialization.XmlSerializer>Serileştirme derlemesinin seri hale getirilen türleri içeren derlemeyi imzalamak için kullanılan anahtarla imzalanmış olup olmadığını denetler. Bu, kötü amaçlı derlemelerden serileştirme derlemeleri olarak yürütülen koruma sunar. Ancak, serileştirilebilir türlerinizi içeren derleme imzalanmamışsa, <xref:System.Xml.Serialization.XmlSerializer> Bu denetimi gerçekleştiremez ve doğru ada sahip herhangi bir derlemeyi kullanır. Bu, kötü amaçlı kod çalışmasını mümkün hale getirir. Yalnızca serileştirilebilir türlerinizi içeren derlemeleri veya kötü amaçlı derlemelerin giriş durumunu engellemek için uygulamanızın dizinine ve genel derleme önbelleğine erişimi sıkı bir şekilde denetleyin.

<xref:System.Xml.Serialization.XmlSerializer>Hizmet reddi saldırısına tabi olabilir. <xref:System.Xml.Serialization.XmlSerializer>Bir `MaxItemsInObjectGraph` kotası yoktur (üzerinde olduğu gibi <xref:System.Runtime.Serialization.DataContractSerializer> ). Bu nedenle, yalnızca ileti boyutuyla sınırlı olan, rastgele bir nesne miktarını serileştirir.

### <a name="partial-trust-threats"></a>Kısmi güven tehditleri

Kısmi güvenle çalışan kodla ilgili tehditlere ilişkin aşağıdaki kaygılara dikkat edin. Bu tehditler, kötü amaçlı kısmen güvenilen kodun yanı sıra diğer saldırı senaryolarıyla birlikte kötü amaçlı kısmen güvenilen kod içerir (örneğin, belirli bir dizeyi oluşturan ve serisini kaldırma kısmen güvenilen kod).

- Herhangi bir serileştirme bileşeni kullanırken, tüm serileştirme senaryosu sizin onay kapsamı içinde olsa bile, bu kullanımdan önce hiçbir izni hiçbir zaman onaylama, ancak güvenilmeyen herhangi bir veri veya nesne ile ilgilenmeyin. Bu tür kullanımlar güvenlik açıklarına neden olabilir.

- Kısmen güvenilen kodun, serileştirme süreci üzerinde, genişletilebilirlik noktaları (yedeklerin kapıları), serileştirildiği türler veya diğer yollarla denetimi olduğu durumlarda, kısmen güvenilen kod seri hale getiricinin büyük miktarda verinin serileştirilmiş akışa çıkış olmasına neden olabilir ve bu da bu akışın alıcısından hizmet reddi (DoS) oluşmasına neden olabilir. DoS tehditleri açısından duyarlı olan bir hedef için tasarlanan verileri serileştirdiyseniz kısmen güvenilen türler serileştirmeyin veya kısmen güvenilen kod denetimi serileştirmesine izin vermeyin.

- Örneğiniz için kısmen güvenilen kod erişimine izin verirseniz <xref:System.Runtime.Serialization.DataContractSerializer> veya [veri sözleşmesinin yedeklerin kapılarını](../extending/data-contract-surrogates.md)kontrol ediyorsanız, serileştirme/seri kaldırma işlemi üzerinde çok fazla denetim uygulanabilir. Örneğin, rastgele türler ekleyebilir, bilgilerin açığa çıkmasına, sonuçta ortaya çıkan nesne grafı veya serileştirilmiş verilerle oynanmasına ya da sonuç olarak seri hale getirilmiş akış taşmasına yol açabilir. Eşdeğer <xref:System.Runtime.Serialization.NetDataContractSerializer> tehdit, "NetDataContractSerializer güvenli kullanımı" bölümünde açıklanmaktadır.

- <xref:System.Runtime.Serialization.DataContractAttribute>Öznitelik bir türe uygulanmışsa (veya olarak işaretlenen tür olarak işaretlenmiş <xref:System.SerializableAttribute> ancak yoksa <xref:System.Runtime.Serialization.ISerializable> ), tüm oluşturucular genel olmayan veya taleplerine göre korunsa bile, seri hale getirici böyle bir türün bir örneğini oluşturabilir.

- Seri durumdan çıkarılacak veriler güvenilir olmadığından ve bilinen tüm türlerin güvendiğiniz türler olduğundan emin değilseniz, seri durumdan çıkarma sonucuna hiçbir şekilde güvenmeyin. Bilinen türlerin, kısmi güvende çalışırken uygulama yapılandırma dosyasından yüklenmediğini (ancak bilgisayar yapılandırma dosyasından yüklendiğini) unutmayın.

- <xref:System.Runtime.Serialization.DataContractSerializer>Kısmen güvenilen koda eklenen bir yedek içeren bir örnek geçirirseniz, kod o vekil üzerinde değiştirilebilir tüm ayarları değiştirebilir.

- Seri durumdan çıkarılmış bir nesne için, XML okuyucu (veya içindeki veriler) kısmen güvenilen koddan geliyorsa, sonuçta elde edilen seri durumdan çıkarılmış nesneyi güvenilmeyen veriler olarak değerlendirin.

- <xref:System.Runtime.Serialization.ExtensionDataObject>Türün ortak üyesi olmaması aslında, içindeki verilerin güvenli olduğu anlamına gelmez. Örneğin, ayrıcalıklı bir veri kaynağından bazı verilerin bulunduğu bir nesne olarak seri durumdan çıkardıysanız ve bu nesneyi kısmen güvenilen koda verirseniz, kısmen güvenilen kod `ExtensionDataObject` nesneyi serileştirerek içindeki verileri okuyabilir. <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> `true` Ayrıcalıklı bir veri kaynağından, daha sonra kısmen güvenilen koda geçirilen bir nesneye ne zaman seri durumdan çıkarılırken, öğesini olarak ayarlamayı göz önünde bulundurun.

- <xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> tam güvende özel, korunan, iç ve ortak üyelerin serileştirmesini destekler. Ancak kısmi güvende yalnızca ortak üyeler seri hale getirilebilir. Bir <xref:System.Security.SecurityException> uygulama genel olmayan bir üyeyi serileştirmek istediğinde, oluşturulur.

    İç veya korumalı iç üyelerin kısmi güvende serileştirilmesine izin vermek için <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> derleme özniteliğini kullanın. Bu öznitelik, bir derlemenin iç üyelerinin diğer bir derlemede görünür olduğunu bildirmesine izin verir. Bu durumda, iç üyelerinin serileştirilmesi isteyen bir derleme, iç üyelerinin System. Runtime. Serialization. dll ' ye görünür olduğunu bildirir.

    Bu yaklaşımın avantajı, yükseltilmiş kod oluşturma yolu gerektirmemelidir.

    Aynı zamanda, iki önemli olumsuz de vardır.

    Birinci dezavantajı, özniteliğin kabul etme özelliğinin <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> bütünleştirilmiş kod genelinde bir özelliktir. Diğer bir deyişle, yalnızca belirli bir sınıfın iç üyeleri seri hale getirilebilir olduğunu belirtemezsiniz. Kuşkusuz, belirli bir iç üyeyi seri hale getirmeniz gerekmez, yalnızca bu üyeye bir öznitelik eklememeyi seçebilirsiniz <xref:System.Runtime.Serialization.DataMemberAttribute> . Benzer şekilde, bir geliştirici, hafif görünürlük sorunları ile özel veya korumalı bir üye oluşturmak da tercih edebilir.

    İkinci dezavantajı, hala özel veya korumalı üyeleri desteklemezler.

    Kısmi güvende özniteliğin kullanımını göstermek için <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> aşağıdaki programı göz önünde bulundurun:

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]

    Yukarıdaki örnekte, `PermissionsHelper.InternetZone` <xref:System.Security.PermissionSet> kısmi güven için öğesine karşılık gelir. Artık, özniteliği olmadan <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> uygulama başarısız olur, <xref:System.Security.SecurityException> genel olmayan üyelerin kısmi güvende serileştirilmediğini belirten bir.

    Ancak, kaynak dosyaya aşağıdaki satırı eklediğimiz takdirde program başarıyla çalıştırılır.

    [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]

## <a name="other-state-management-concerns"></a>Diğer durum yönetimi konuları

Nesne durumu yönetimiyle ilgili diğer konular aşağıda yer alınır:

- Akış temelli programlama modelini bir akış taşımasıyla kullanırken ileti geldiğinde ileti işleme oluşur. İletiyi gönderen, akışın ortasında Gönder işlemini iptal edebilir ve daha fazla içerik bekleniyorsa kodunuzu öngörülemeyen bir durumda bırakır. Genel olarak, akışın tamamlanmamakta olmaması ve akışın durdurulduğu durumlarda geri alınamaz bir akış tabanlı işlemde herhangi bir iş gerçekleştirmeyin. Bu durum, akış gövdesinden sonra bir iletinin hatalı biçimlendirilmiş olabileceği durumlar için de geçerlidir (örneğin, SOAP Zarfı için bir bitiş etiketi eksik olabilir veya ikinci bir ileti gövdesi olabilir).

- Özelliği kullanmak `IExtensibleDataObject` gizli verilerin oluşturulmasına neden olabilir. Güvenilmeyen bir kaynaktan veri sözleşmeleri içeren verileri kabul ediyorsanız `IExtensibleObjectData` ve daha sonra iletilerin imzalandığı bir güvenli kanalda yeniden yaydıysanız, hiçbir şeyi bildiğiniz veriler için büyük olasılıkla vouching olursunuz. Ayrıca, gönderdiğiniz genel durum hem bilinen hem de bilinmeyen veri parçalarını hesaba aldıysanız geçersiz olabilir. Uzantı verisi özelliğini seçerek `null` veya özelliği seçmeli olarak devre dışı bırakarak bu durumdan kaçının `IExtensibleObjectData` .

## <a name="schema-import"></a>Şemayı Içeri aktarma

Normalde, türleri oluşturmak için şemayı içeri aktarma işlemi yalnızca tasarım zamanında gerçekleşir, örneğin, bir Web hizmetindeki [ServiceModel meta veri yardımcı programı Aracı (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) , bir istemci sınıfı oluşturmak için. Ancak, daha Gelişmiş senaryolarda, çalışma zamanında şemayı işleyebilirsiniz. Bunu yapmanın, hizmet reddi risklerine maruz bırakacağına dikkat edin. Bazı şemanın içeri aktarılması uzun zaman alabilir. <xref:System.Xml.Serialization.XmlSerializer>Şemalar muhtemelen güvenilmeyen bir kaynaktan geliyorsa, bu senaryolarda hiçbir şekilde şema içeri aktarma bileşenini kullanmayın.

## <a name="threats-specific-to-aspnet-ajax-integration"></a>ASP.NET AJAX tümleştirmesine özgü tehditler

Kullanıcı veya uyguladığı zaman <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> <xref:System.ServiceModel.Description.WebHttpBehavior> , WCF hem XML hem de JSON iletilerini kabul edebilecek bir uç nokta gösterir. Ancak, hem XML okuyucu hem de JSON okuyucusu tarafından kullanılan tek bir okuyucu kotaları kümesi vardır. Bazı Kota ayarları bir okuyucu için uygun olabilir ancak diğeri için çok büyük olabilir.

Uygularken `WebScriptEnablingBehavior` , kullanıcının uç noktada bir JavaScript proxy 'si sunma seçeneği vardır. Aşağıdaki güvenlik sorunları göz önünde bulundurulmalıdır:

- Hizmet hakkındaki bilgiler (işlem adları, parametre adları vb.), JavaScript proxy 'si incelenerek elde edilebilir.

- JavaScript uç noktası kullanılırken, hassas ve özel bilgiler istemci Web tarayıcısı önbelleğinde tutulabilir.

## <a name="a-note-on-components"></a>Bileşenlere bir göz

WCF esnek ve özelleştirilebilir bir sistemdir. Bu konunun içeriklerinin çoğu, en yaygın WCF kullanımı senaryolarına odaklanmaktadır. Ancak, WCF bileşenleri oluşturmak için birçok farklı yol vardır. Her bileşeni kullanmanın güvenlik etkilerine ilişkin etkileri anlamak önemlidir. Özellikle:

- XML okuyucuları kullanmanız gerektiğinde, <xref:System.Xml.XmlDictionaryReader> sınıfının diğer okuyucuların aksine sağladığı okuyucuları kullanın. Güvenli okuyucular <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A> ,, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A> veya yöntemleri kullanılarak oluşturulur <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> . <xref:System.Xml.XmlReader.Create%2A>Yöntemini kullanmayın. Okuyucuları her zaman güvenli kotalar ile yapılandırın. WCF 'deki serileştirme motorları yalnızca WCF 'den güvenli XML okuyucuları ile birlikte kullanıldığında güvenlidir.

- , <xref:System.Runtime.Serialization.DataContractSerializer> Güvenilir olmayan verileri seri durumdan çıkarmak için kullanırken, her zaman <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> özelliği ayarlayın.

- Bir ileti oluştururken, `maxSizeOfHeaders` `MaxReceivedMessageSize` yeterli koruma sunmıyorsa parametresini ayarlayın.

- Kodlayıcı oluştururken, ve gibi ilgili kotaları her zaman yapılandırın `MaxSessionSize` `MaxBufferSize` .

- Bir XPath ileti filtresi kullanırken, <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> filtrenin ziyaret ettığı XML düğümü miktarını sınırlamak için öğesini ayarlayın. Çok sayıda düğüm ziyaret etmeden hesaplanması uzun süren XPath ifadeleri kullanmayın.

- Genel olarak, kota kabul eden herhangi bir bileşeni kullanırken, güvenlik etkilerini anlayın ve güvenli bir değere ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.XmlDictionaryReader>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Veri Anlaşması Bilinen Türler](data-contract-known-types.md)
