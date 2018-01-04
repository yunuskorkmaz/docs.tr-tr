---
title: "Veriler için Güvenlik Konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7eb98da-4a93-4692-8b59-9d670c79ffb2
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: bb7a40bc38a3fdf3f7be2b31e30e768e26be2d15
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="security-considerations-for-data"></a>Veriler için Güvenlik Konuları
Verilerle ilgilenirken [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], tehdit kategori sayısı dikkate almanız gerekir. Aşağıdaki tabloda veri işleme ile ilgili en önemli tehdit sınıflar listelenir. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bu tehditleri azaltmak için araçlar sağlar.  
  
 Hizmet reddi  
 Güvenilmeyen veri alırken, verileri uzun hesaplamalar neden olarak orantısız miktarda bellek, iş parçacıkları, kullanılabilir bağlantıları veya işlemci döngülerinin gibi çeşitli kaynak erişmek alma tarafı neden olabilir. Bir sunucuya karşı bir hizmet reddi saldırısı kilitlenmesine ve diğer, yasal istemcilerinden gelen iletileri işleyemiyor neden.  
  
 Kötü amaçlı kod yürütme  
 Gelen güvenilmeyen veri onu istemediğiniz kodu çalıştırmak alma tarafı neden olur.  
  
 Bilgilerin açığa çıkmasına  
 Uzak saldırgan için oranla daha fazla bilgi ifşa şekilde kendi isteklerini yanıtlamak için alıcı taraf zorlar.  
  
## <a name="user-provided-code-and-code-access-security"></a>Kullanıcı tarafından sağlanan kod ve kod erişimi güvenliği  
 İçinde basamak sayısını [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] altyapı kullanıcı tarafından sağlanan kodu çalıştırın. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme motoruna kullanıcı tarafından sağlanan özellik çağrısı `set` erişimciler ve `get` erişimciler. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Kanal altyapısının çağırıp kullanıcı tarafından sağlanan türetilmiş sınıfları <xref:System.ServiceModel.Channels.Message> sınıfı.  
  
 Hiçbir güvenlik açıkları var olduğundan emin olmak için kod yazar sorumluluğundadır. Örneğin, oluşturursanız, bir veri sözleşmesi türü Tamsayı türünde ve içinde veri üyesi özelliğiyle `set` erişimci uygulama tahsis özellik değerine dayalı bir dizi, bir hizmet reddi saldırısı olasılığı bir kötü amaçlı olmadığını kullanıma ileti, bu veri üyesi için son derece büyük bir değer içeriyor. Genel olarak, tüm ayırmaları gelen veri göre veya uzun (özellikle uzun işleme küçük gelen veri miktarına göre kaynaklanabilir varsa) kullanıcı tarafından sağlanan kodda işleme kaçının. Kullanıcı tarafından sağlanan kod güvenlik analizi gerçekleştirirken, tüm hata durumları (burada özel durumlar diğer bir deyişle, tüm kod dalları) de göz önüne almanız gereken emin olun.  
  
 Son kullanıcı tarafından sağlanan kod, hizmet uygulamanızı her bir işlemin içinde kod örneğidir. Hizmet uygulamanızın güvenlik bilgilerinizi sorumluluğundadır. Yanlışlıkla güvenlik açıkları hizmet reddine neden güvensiz işlemi uygulamaları oluşturmak kolaydır. Örneğin, o dizeyi bir dize alır ve müşterilerin listesini veritabanından adını döndürür. bir işlem başlatır. Büyük bir veritabanı ile çalışıyorsanız ve geçirilen dize yalnızca tek bir harf ise, kodunuzu bir ileti tüm hizmetinin başarısız olmasına neden olan tüm kullanılabilir belleği daha büyük oluşturma girişiminde bulunabilir. (Bir <xref:System.OutOfMemoryException> içinde kurtarılamaz [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] ve her zaman, uygulamanızın sonlandırılmasıyla sonuçlanır.)  
  
 Kötü amaçlı kod çeşitli genişletilebilirlik noktaları prize takılı olduğundan emin olun. Kısmen güvenilen derlemelerden türleriyle ilgilenme veya kısmen güvenilen kod tarafından kullanılabilir bileşenler oluşturma kısmi güven altında çalışırken özellikle ilgili budur. Daha fazla bilgi için "Kısmi güven tehditleri" sonraki bölümüne bakın.  
  
 Kısmi güvende çalıştırırken veri sözleşmesi seri hale getirme altyapısı ve veri modelinin sözleşme programlama - Örneğin, özel veri üyeleri için sınırlı bir alt destekler veya kullanarak türleri unutmayın <xref:System.SerializableAttribute> öznitelik desteklenmez. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Kısmi güven](../../../../docs/framework/wcf/feature-details/partial-trust.md).  
  
## <a name="avoiding-unintentional-information-disclosure"></a>Yanlışlıkla bilgilerin açığa çıkmasına önleme  
 Seri hale getirilebilir türler göz önünde bulundurularak ile tasarlarken, bilgi açıklama olası bir konudur.  
  
 Aşağıdaki noktaları göz önünde bulundurun:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Programlama modeli, tür veya derleme seri hale getirme sırasında dışında özel ve iç veri riskini olanak sağlar. Ayrıca, bir türü şeklini şema dışa aktarma sırasında gösterilebilir. Tür serileştirme projeksiyon anladığınızdan emin olun. Kullanıma sunulan herhangi bir şey istemiyorsanız, seri hale getirme devre dışı bırakın (örneğin, uygulayarak değil <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği bir veri sözleşmesi söz konusu olduğunda).  
  
-   Aynı türde kullanımda seri hale getirici bağlı olarak birden fazla seri hale getirme tahminleri olabilir unutmayın. Aynı türde bir kullanıldığında veri kümesi getirebilir <xref:System.Runtime.Serialization.DataContractSerializer> ve başka bir kullanıldığında veri kümesini <xref:System.Xml.Serialization.XmlSerializer>. Yanlışlıkla yanlış seri hale getirici kullanarak bilgi açığa çıkmasına neden olabilir.  
  
-   Kullanarak <xref:System.Xml.Serialization.XmlSerializer> (RPC) eski uzak yordam çağrısı / kodlanmış modu, alma tarafı için Gönderen tarafında nesne grafiğinin şekli kasıtsız olarak kullanıma.  
  
## <a name="preventing-denial-of-service-attacks"></a>Hizmet reddi saldırılarını önleme  
  
### <a name="quotas"></a>Kotalar  
 Olası bir hizmet reddi saldırısı önemli miktarda bellek ayırmak alma tarafı neden olur. Bu bölümde büyük iletilerden doğan bellek tüketimi sorunları yoğunlaşır olsa da, diğer saldırılara ortaya çıkabilir. Örneğin, iletileri işleme süresi orantısız miktarda kullanabilir.  
  
 Hizmet reddi saldırılarını genellikle kotaları kullanan azalır. Bir kota aşıldığında bir <xref:System.ServiceModel.QuotaExceededException> özel normal durum. Kota kötü amaçlı bir ileti erişilebilmesi tüm kullanılabilir bellek sonuçta neden olabilir bir <xref:System.OutOfMemoryException> özel durum ya da erişilebilmesi için tüm kullanılabilir yığınları, sonuçta ortaya çıkan bir <xref:System.StackOverflowException>.  
  
 Kurtarılabilir kotası aşıldı senaryodur; çalışan bir hizmette, aldıysanız, işlenmekte olan iletisi göz ardı edilir ve hizmet çalıştıran tutar ve başka ileti işler. Bellek yetersiz ve yığın taşması senaryoları, ancak herhangi bir yerinde kurtarılabilir olmayan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]; bu tür özel durumlar karşılaşırsa hizmeti sonlandırır.  
  
 Kotalarda [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tüm ön ayırma içermeyen. Örneğin, varsa <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kota (çeşitli sınıflarında bulunur) 128 KB olarak ayarlanır, 128 KB otomatik olarak her ileti için ayrılan gelmez. Ayrılmış gerçek gerçek gelen ileti boyutuna bağlıdır.  
  
 Birçok kotalarını aktarım katmanında kullanılabilir. Kota kullanımı (HTTP, TCP vb.) belirli aktarım kanalda tarafından uygulanmıyor bunlar. Bu konuda bu kotalar bazıları açıklanmaktadır, ancak bu kotalar ayrıntılı olarak açıklanmıştır [taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md).  
  
### <a name="hashtable-vulnerability"></a>Hashtable güvenlik açığı  
 Veri sözleşmeleri hashtable'da veya koleksiyonları içeren bir güvenlik açığı bulunmaktadır. Çok sayıda değerleri bir karma tablosunda eklediyseniz, bu değerleri çok sayıda aynı karma değeri üretmek sorun oluşur. Bu bir DOS saldırısı kullanılabilir.  Bu güvenlik açığından MaxRecievedMessageSize bağlama kota ayarlayarak azaltılabilir. Bu tür saldırıları önlemek için bu kota ayarlarken dikkatli olunması gerekir. Bu kota WCF ileti boyutu üst sınırını koyar. Ayrıca, hashtable'da veya koleksiyonlar veri sözleşmelerinizi kullanmaktan kaçının.  
  
## <a name="limiting-memory-consumption-without-streaming"></a>Akış olmadan sınırlama bellek tüketimi  
 Güvenlik modeli büyük iletileri çevresinde akış kullanımda olmasına bağlıdır. Temel, akışı olmayan durumda iletileri belleğe arabelleğe alınmamış. Bu durumda, kullanarak <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A> kota <xref:System.ServiceModel.Channels.TransportBindingElement> veya erişmek için maksimum ileti boyutu sınırlayarak büyük iletileri karşı korumak için sistem tarafından sağlanan bağlamalar. Bir hizmet birden çok ileti aynı anda işliyor olabilir, bu durumda tüm bellekte olduklarını unutmayın. Bu tehdidi azaltmak için azaltma özelliğini kullanın.  
  
 Ayrıca `MaxReceivedMessageSize` bir üst sınır ileti başına bellek tüketimi üzerinde yerleştirmez, ancak kendisine içinde sabit bir faktör sınırlar. Örneğin, varsa `MaxReceivedMessageSize` 1 MB'tır ve 1 MB ileti aldı ve ardından seri durumdan çıkarılmış, ek bellek toplam bellek tüketimi iyi üzerinde 1 MB kaynaklanan seri durumdan çıkarılmış Nesne grafiği içeren için gereklidir. Bu nedenle, gelen kadar veri olmadan önemli bellek kullanımına neden olabilir seri hale getirilebilir türler oluşturmamaya özen gösterin. Örneğin, 50 isteğe bağlı verileri üye ve bir ek 100 özel alanları ile "MyContract" ile XML yapım örneği bir veri sözleşmesi "\<MyContract / >". Bu XML 150 alanlar için erişilen bellek sonuçlanır. Veri üyeleri varsayılan olarak isteğe bağlı olduğunu unutmayın. Bu tür bir türü bir dizi parçası olduğunda sorun araya geldiğinde.  
  
 `MaxReceivedMessageSize`tek başına tüm hizmet reddi saldırılarını önlemek yeterli değil. Örneğin, seri durumdan çıkarıcının (henüz başka bir vb. içeren başka bir nesne içeren bir nesne) bir iç içe nesne grafiğinin seri durumdan çıkarılacak gelen ileti tarafından zorlanabilir. Hem <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer> iç içe geçmiş bir şekilde böyle grafikleri seri durumdan yöntemlerini çağırın. Yöntem çağrıları derin iç içe geçmiş bir kurtarılamaz neden <xref:System.StackOverflowException>. Bu tehdit ayarlayarak azaltıldığından <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement.MaxDepth%2A> konunun devamındaki "Güvenle XML kullanarak" bölümünde açıklandığı gibi XML iç içe geçme düzeyi sınırlamak için kota.  
  
 Ek kotalar ayarını `MaxReceivedMessageSize` ikili XML kodlama kullanılarak, özellikle önemlidir. İkili kodlama kullanılarak eşdeğerdir sıkıştırma biraz: gelen ileti baytlarının miktarını küçük bir grup çok miktarda veri temsil edebilir. Bu nedenle, bir ileti içine sığdırma bile `MaxReceivedMessageSize` sınırı sürebilir çok daha fazla bellek tam olarak genişletilmiş biçiminde. Bu tür XML özgü tehditleri azaltmak için tüm XML okuyucusu kotalar bu konunun devamındaki "Güvenle XML kullanarak" bölümünde açıklandığı gibi doğru şekilde ayarlanması gerekir.  
  
## <a name="limiting-memory-consumption-with-streaming"></a>Akış ile sınırlama bellek tüketimi  
 Akış, küçük bir kullanabilir `MaxReceivedMessageSize` hizmet reddi saldırılarına karşı korumak için ayarı. Ancak, daha karmaşık senaryolarda akış ile mümkün değildir. Örneğin, bir dosya karşıya yükleme hizmeti, tüm kullanılabilir bellekten daha büyük dosyaları kabul eder. Bu durumda, ayarlamak `MaxReceivedMessageSize` son derece büyük bir değere doğrudan diske akışları neredeyse hiç veri bellek ve iletiyi arabelleğe alınıp bekleniyor. Kötü amaçlı bir ileti şekilde zorlayabilirsiniz varsa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bu durumda, akış yerine arabellek verilere `MaxReceivedMessageSize` artık tüm kullanılabilir bellek erişme iletiye karşı korur.  
  
 Bu tehdidi azaltmak için belirli kota ayarları çeşitli mevcut [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] arabelleğe alma sınırı veri işleme bileşenleri. Bunlardan en önemli `MaxBufferSize` çeşitli aktarım bağlama öğeleriyle ve standart bağlamaları özelliği. Akış, bu kota en fazla ileti başına ayrılacak istekli bellek miktarı dikkate alarak ayarlamanız gerekir. İle `MaxReceivedMessageSize`, ayar mutlak bir en yüksek bellek tüketimine ilişkin koymaz ancak yalnızca kendisine içinde sabit bir faktör sınırlar. Ayrıca, olarak ile `MaxReceivedMessageSize`, aynı anda işlenmekte olan birden fazla ileti olasılığını unutmayın.  
  
### <a name="maxbuffersize-details"></a>MaxBufferSize ayrıntıları  
 `MaxBufferSize` Özelliği sınırlar herhangi toplu arabelleğe alma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yapar. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] her zaman bir ileti iletim en iyi duruma getirme mekanizmasını (MTOM) iletisi doğal okuma sırada olmaması için bulunan tüm MIME bölümler yanı sıra SOAP üstbilgileri ve SOAP hataları arabelleğe alır. Bu ayar, tüm bu durumlarda arabelleğe alma miktarını sınırlar.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Bunu geçirerek gerçekleştirir `MaxBufferSize` arabellek çeşitli bileşenler için değer. Örneğin, bazı <xref:System.ServiceModel.Channels.Message.CreateMessage%2A> , overloads <xref:System.ServiceModel.Channels.Message> sınıfı Al bir `maxSizeOfHeaders` parametresi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]geçirir `MaxBufferSize` SOAP üstbilgi arabelleğe alma miktarını sınırlamak için bu parametre için değer. Kullanırken bu parametreyi ayarlayın önemlidir <xref:System.ServiceModel.Channels.Message> doğrudan sınıfı. Bir bileşenin kullanırken genel olarak, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kota parametreleri alan bu parametreleri güvenlik etkilerini anlamak ve doğru bir şekilde ayarlamak önemlidir.  
  
 MTOM ileti Kodlayıcı de sahip bir `MaxBufferSize` ayarı. Standart bağlamaları kullanırken, bu aktarım düzeyi için otomatik olarak ayarlanır `MaxBufferSize` değeri. Ancak, özel bağlama oluşturmak için MTOM ileti Kodlayıcı bağlama öğesi kullanırken ayarlamak önemli olduğunu `MaxBufferSize` özelliği akış olduğunda güvenli bir değeri için kullanılır.  
  
## <a name="xml-based-streaming-attacks"></a>XML tabanlı akış saldırıları  
 `MaxBufferSize`tek başına emin olmak yeterli değil [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] akış beklendiğinde arabelleğe alma içine zorlanamaz. Örneğin, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML okuyucular yeni bir öğe okumak başlatırken tüm XML öğenin başlangıç etiketinde her zaman arabellek. Ad alanları ve öznitelikleri düzgün bir şekilde işlenir böylece bu yapılır. Varsa `MaxReceivedMessageSize` yapılandırılmış (senaryo akış doğrudan disk büyük bir dosya etkinleştirmek için örneğin,) büyük olması için kötü amaçlı bir ileti burada tüm ileti gövdesi büyük bir XML öğenin başlangıç etiketinde yapılandırılmıştır. Dosyayı okuma girişimi sonuçlanan bir <xref:System.OutOfMemoryException>. Bu, tüm XML okuyucusu kotaları, bu konunun devamındaki "Güvenle XML kullanarak" bölümünde açıklanan kullanılarak azaltılabilir birçok olası XML tabanlı hizmet reddi saldırıları biridir. Akış, tüm bu kotalar ayarlamak özellikle önemlidir.  
  
### <a name="mixing-streaming-and-buffering-programming-models"></a>Akış ve programlama modelleri arabelleğe alma karıştırma  
 Olası saldırıların çoğu, akış ve akış dışı programlama modelleri aynı hizmet karıştırma kaynaklanır. Bir hizmet sözleşmesini iki işlem ile olduğunu varsayın: alır bir <xref:System.IO.Stream> ve başka bazı özel türünün dizisini alır. Ayrıca varsayın `MaxReceivedMessageSize` geniş akışlar işleme ilk işlemini etkinleştirmek için büyük bir değere ayarlayın. Ne yazık ki, bu işlemi çağrılmadan önce büyük iletileri artık ikinci bir işlem de ve seri durumdan çıkarıcının arabellekleri verilere bellekte bir dizi olarak gönderilip gönderilmediğini anlamına gelir. Olası bir hizmet reddi saldırısı budur: `MaxBufferSize` kota ileti gövdesi boyutunu sınırlamaz olduğu seri durumdan çıkarıcının ile çalışır.  
  
 Bu nedenle, aynı sözleşme akış tabanlı ve akışı olmayan işlemlerinde karıştırma kaçının. İki programlama modeli kesinlikle karışık gerekir, aşağıdaki önlemleri kullanın:  
  
-   Kapatma <xref:System.Runtime.Serialization.IExtensibleDataObject> ayarlayarak özelliği <xref:System.ServiceModel.ServiceBehaviorAttribute.IgnoreExtensionDataObject%2A> özelliği <xref:System.ServiceModel.ServiceBehaviorAttribute> için `true`. Bu sözleşmenin parçası olan üyeleri seri sağlar.  
  
-   Ayarlama <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> özelliği <xref:System.Runtime.Serialization.DataContractSerializer> güvenli bir değer. Bu kota de kullanılabilir <xref:System.ServiceModel.ServiceBehaviorAttribute> özniteliği veya yapılandırma yoluyla. Bu kota bir seri durumdan çıkarma bölüm serisi nesne sayısını sınırlar. Normalde, her işlem parametresi ya da ileti gövdesi bölümünde bir ileti sözleşmesi içinde bir bölüm serisi. Diziler çıkarılırken her dizi girişi ayrı bir nesne sayılır.  
  
-   Tüm XML okuyucusu kotalar güvenli değerlere ayarlayın. Dikkat <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>, <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, ve <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A> ve akış dışı işlemleri dizelerde kaçının.  
  
-   Bilinen türler, bunları herhangi biri herhangi bir zamanda oluşturulabilir aklınızda tutma listesini gözden geçirin (Bu konunun devamındaki "Önleme istenmeyen türleri gelen yükleniyor" bölümüne bakın).  
  
-   Uygulama türleri kullanmayın <xref:System.Xml.Serialization.IXmlSerializable> çok miktarda veri arabellek arabirimi. Bu tür türleri bilinen türleri listesine eklemeyin.  
  
-   Kullanmayın <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> diziler <xref:System.Byte> diziler veya türleri uygulayan <xref:System.Runtime.Serialization.ISerializable> sözleşmesindeki.  
  
-   Kullanmayın <xref:System.Xml.XmlElement>, <xref:System.Xml.XmlNode> diziler <xref:System.Byte> diziler veya türleri uygulayan <xref:System.Runtime.Serialization.ISerializable> bilinen türleri listesinde.  
  
 Akış dışı işlemi kullandığında önceki önlemler uygulamak <xref:System.Runtime.Serialization.DataContractSerializer>. Hiçbir zaman akış karıştırmak ve akış dışı programlama modelleri aynı hizmette kullanıyorsanız <xref:System.Xml.Serialization.XmlSerializer>, korumasını olmadığından <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior.MaxItemsInObjectGraph%2A> kota.  
  
### <a name="slow-stream-attacks"></a>Yavaş akış saldırıları  
 Akış hizmet reddi saldırılarını sınıfının bellek tüketimi gerektirmez. Bunun yerine, saldırı bir yavaş veya vericinin veri içerir. Gönderilen veya alınan verilerin beklerken, iş parçacıkları ve kullanılabilir bağlantıları gibi kaynakları tükendi. Bu durum kötü amaçlı saldırı sonucunda ya da yasal bir gönderici/alıcı bir yavaş ağ bağlantısı üzerinde meydana gelebilecek.  
  
 Bu saldırıları azaltmak için Aktarım zaman aşımlarını doğru olarak ayarlayın. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Taşıma kotaları](../../../../docs/framework/wcf/feature-details/transport-quotas.md). İkincisi, hiçbir zaman zaman uyumlu kullanmak `Read` veya `Write` akış ile çalışırken işlemleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-xml-safely"></a>XML kullanarak güvenli bir şekilde  
  
> [!NOTE]
>  Bu bölümde XML hakkında olsa da, bilgi JavaScript nesne gösterimi (JSON) belgeleri için de geçerlidir. Kullanarak kotaları benzer şekilde, iş [arasında eşleme JSON ve XML](../../../../docs/framework/wcf/feature-details/mapping-between-json-and-xml.md).  
  
### <a name="secure-xml-readers"></a>XML okuyucular güvenli  
 XML bilgi tüm ileti işlenirken temelini [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. XML verilerini azaltılması gereken olasılıklar mevcut hizmet reddi saldırısı sayısı güvenilmeyen bir kaynaktan kabul ederken. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]özel, güvenli XML okuyucu sağlar. Bu okuyucular standart kodlamaları birini kullanırken otomatik olarak oluşturulan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] (metin, ikili veya MTOM).  
  
 Bazı güvenlik özelliklerini bu okuyucular her zaman etkindir. Örneğin, okuyucular hiçbir zaman olası bir hizmet reddi saldırılarını kaynağı olan ve hiçbir zaman yasal SOAP iletilerinde görünmesi gereken belge tür tanımları (DTD) işler. Diğer güvenlik özellikleri yapılandırılmalıdır, okuyucu kotalar sonraki bölümde açıklanan içerir.  
  
 Doğrudan XML okuyucularıyla çalışırken (gibi kendi özel Kodlayıcı yazarken veya doğrudan ile çalışırken <xref:System.ServiceModel.Channels.Message> sınıfı), her zaman kullanmak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] güvenilmeyen verilerle çalışma şansı olduğunda okuyucular güvenli. Güvenli okuyucular statik Fabrika arama biri tarafından yöntemi aşırı oluşturma <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, veya <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> üzerinde <xref:System.Xml.XmlDictionaryReader> sınıfı. Bir okuyucusu oluşturulurken güvenli kota değerlerini geçirin. Çağırmayın `Create` yöntemi aşırı. Bunlar oluşturmayın bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] okuyucu. Bunun yerine, bu bölümde açıklanan güvenlik özellikleri tarafından korunmayan bir okuyucu oluşturulur.  
  
### <a name="reader-quotas"></a>Okuyucu kotaları  
 Güvenli XML okuyucular beş yapılandırılabilir kotalar vardır. Bunlar normalde kullanılarak yapılandırılmış olan `ReaderQuotas` özelliğini kodlama bağlama öğeleri veya standart bağlamaları veya kullanarak bir <xref:System.Xml.XmlDictionaryReaderQuotas> bir okuyucusu oluşturulurken nesnesi geçirildi.  
  
#### <a name="maxbytesperread"></a>MaxBytesPerRead  
 Bu kota tek bir okunan bayt sayısını sınırlar `Read` etiketini ve onun özniteliklerini öğesi okunurken işlemi başlatın. (Akışı dışı durumlarda, öğe adını kota karşı sayılmaz.) <xref:System.Xml.XmlDictionaryReaderQuotas.MaxBytesPerRead%2A> aşağıdaki nedenlerle önemlidir:  
  
-   Okunmakta zaman öğe adı ve öznitelikleri her zaman bellekte arabelleğe alınmış. Bu nedenle, bu kota doğru akış beklendiğinde aşırı arabelleğe almayı önlemek için modu akış ayarlamak önemlidir. Bkz: `MaxDepth` gerçekleşir kota bölüm gerçek miktarını arabelleğe alma hakkında bilgi için.  
  
-   Öznitelik adları için benzersizlik denetlenecek olduğundan çok fazla XML özniteliklere sahip orantısız işleme zamanı kullanabilir. `MaxBytesPerRead`Bu tehdidi azaltır.  
  
#### <a name="maxdepth"></a>MaxDepth  
 Bu kota en fazla iç içe geçirme derinliği XML öğelerinin sınırlar. Örneğin, belge "\<A >\<B >\<C / >\</B >\</A >" üç iç içe geçirme derinliği sahiptir. <xref:System.Xml.XmlDictionaryReaderQuotas.MaxDepth%2A>Aşağıdaki nedenlerle önemlidir:  
  
-   `MaxDepth`ile etkileşime giren `MaxBytesPerRead`: okuyucu en fazla bellek tüketimi bu iki ayar ürününe orantılı şekilde okuyucu her zaman veri geçerli öğe ve tüm alt öğelerinden bellekte saklar.  
  
-   İç içe nesne grafiğinin seri durumdan çıkarılırken, seri durumdan çıkarıcının tüm yığın erişmek ve kurtarılamaz bir throw zorlanır <xref:System.StackOverflowException>. XML iç içe geçme ve nesne iç içe geçme her ikisi arasında doğrudan bir ilişki var. <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Xml.Serialization.XmlSerializer>. Kullanım `MaxDepth` bu tehdidi azaltmak için.  
  
#### <a name="maxnametablecharcount"></a>MaxNameTableCharCount  
 Bu kota okuyucunun boyutunu sınırlar *ad tablosu*. Ad tablosu bir XML belgesi işleme sırasında karşılaşılan belirli dizeleri (örneğin, ad alanlarını ve önekleri) içerir. Bu dizeler bellekte arabelleğe gibi akış beklendiğinde aşırı arabelleğe almayı önlemek için bu kotayı ayarlayın.  
  
#### <a name="maxstringcontentlength"></a>MaxStringContentLength  
 Bu kota XML okuyucusu döndürür en çok dize boyutu sınırlar. Bu kota XML okuyucusu bellek tüketimini sınırlamaz ancak okuyucu kullanarak bileşeni. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>, dizeleri Bu kota büyük serisi yok. Kullanırken <xref:System.Xml.XmlDictionaryReader> doğrudan bu kota, ancak yalnızca dizeleri gibi okumak için özellikle tasarlanmış yöntemlerini tüm yöntemleri saygı sınıfı <xref:System.Xml.XmlDictionaryReader.ReadContentAsString%2A> yöntemi. <xref:System.Xml.XmlReader.Value%2A> Okuyucu özelliği bu kota tarafından etkilenmez ve bu kota sağlar koruma gerekli olduğunda, bu nedenle kullanılmamalıdır.  
  
#### <a name="maxarraylength"></a>MaxArrayLength  
 Bu kota bir temel bayt dizileri de dahil olmak üzere XML okuyucuyu döndürür elemanlar dizisinde en büyük boyutu sınırlar. Bu kota XML okuyucusu bellek tüketimini sınırlamaz ancak okuyucu kullanarak hangi bileşeni. Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> ile güvenli bir okuyucu kullanan <xref:System.Xml.XmlDictionaryReaderQuotas.MaxArrayLength%2A>, bayt dizileri Bu kota büyük serisi yok. Bu kota tek bir sözleşmede akış ve arabelleğe alınan programlama modelleri karışık çalışılırken ayarlamak önemlidir. Aklınızda kullanırken <xref:System.Xml.XmlDictionaryReader> doğrudan, yalnızca belirli ilkel türler, rasgele boyutunu dizileri gibi okumak için özellikle tasarlanmış yöntemlerini sınıf <xref:System.Xml.XmlDictionaryReader.ReadInt32Array%2A>, bu kota saygılı olun.  
  
## <a name="threats-specific-to-the-binary-encoding"></a>İkili kodlama için tehditleri özel  
 İkili kodlama XML [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] destekler içeren bir *sözlük dizeleri* özelliği. Büyük bir dize, yalnızca birkaç bayt kullanılarak kodlanmış. Bu, önemli ölçüde performans artışı sağlar, ancak azaltılması gereken yeni hizmet reddi tehditleri tanıtır.  
  
 Sözlük iki tür vardır: *statik* ve *dinamik*. Statik sözlük ikili kodlama kısa bir kod kullanılarak temsil edilebilir uzun dizeleri yerleşik bir listesidir. Bu dize listesi okuyucu oluşturulduğunda ve değiştirilemez düzeltilmiştir. Statik sözlük dizelerde hiçbiri, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] bir sözlük genişletme saldırısında hala kullanılabilir olsa da varsayılan olarak kullandığı önemli bir hizmet reddi tehdit teşkil yeterli büyüklükte. Kendi statik sözlük Burada sağladığınız Gelişmiş senaryolarda büyük sözlük dizeleri giriş dikkatli olun.  
  
 Dinamik sözlük özelliği, kendi dizeleri tanımlayın ve bunları kısa kodlarıyla ilişkilendirmek iletilerine izin verir. Bu dize kod eşlemeleri sonraki iletiler dizeleri yeniden başlatmanız gerekmez ve önceden tanımlanmış kodları kullanabilir, bellekte tüm iletişimin oturumu sırasında tutulur. Bu dizeler rastgele uzunlukta olması ve bu nedenle statik sözlükte olandan daha ciddi bir tehdit teşkil olabilir.  
  
 Azaltılması gereken ilk çok büyük boyutlu hale dinamik sözlük (dize kod eşlemesinin tablo) olasılığını tehlike. Bu sözlük birkaç iletileri süresince genişletilmiş ve bu nedenle `MaxReceivedMessageSize` kota yalnızca her ileti için ayrı ayrı uygulandığından koruma sunar. Bu nedenle, ayrı <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> özelliği var. <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> sözlük boyutu sınırlar.  
  
 Diğer çoğu kotaları, bu kota iletileri yazılırken uygulanır. Bir ileti okunurken aşılırsa `QuotaExceededException` her zamanki gibi oluşturulur. Bir ileti yazarken aşılırsa kotanın aşılmasına neden herhangi bir dizesi olarak yazılan-, dinamik sözlük özelliği olmadan kullanmaktır.  
  
### <a name="dictionary-expansion-threats"></a>Sözlük genişletme tehditleri  
 İkili özgü saldırı önemli sınıfı sözlük genişletme ortaya çıkar. Dize sözlükler özellik kapsamlı kullanımını yaparsa ikili biçimde küçük bir ileti tam olarak genişletilmiş metin biçiminde çok büyük bir iletiye kapatabilir. Dinamik sözlük dizeleri için genişletme faktörü sınırlıdır <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A> kota, hiç dinamik sözlük dizesi tüm sözlük en büyük boyutunu aştığından.  
  
 <xref:System.Xml.XmlDictionaryReaderQuotas.MaxNameTableCharCount%2A>, `MaxStringContentLength`, Ve `MaxArrayLength` özellikleri yalnızca bellek tüketimini sınırlamak. Bunlar bellek kullanımı zaten tarafından sınırlı olduğundan akışı olmayan kullanımı tüm tehditlerin azaltılmasına gerekmez normalde `MaxReceivedMessageSize`. Ancak, `MaxReceivedMessageSize` öncesi genişletme bayt sayısı. İkili kodlama kullanımda olduğunda, bellek tüketimi olası sunmamızı `MaxReceivedMessageSize`, yalnızca faktörüyle sınırlı <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement.MaxSessionSize%2A>. Bu nedenle, her zaman tüm okuyucu kotalar ayarlamak önemlidir (özellikle <xref:System.Xml.XmlDictionaryReaderQuotas.MaxStringContentLength%2A>) ikili kodlama kullanırken.  
  
 İle birlikte ikili kodlama kullanırken <xref:System.Runtime.Serialization.DataContractSerializer>, `IExtensibleDataObject` arabirimi kötüye sözlük genişletme saldırısı. Bu arabirim, sınırsız depolama sözleşmenin parçası olmayan rastgele veriler için temelde sağlar. Kotalar yeterince düşük ayarlanamaz, şekilde `MaxSessionSize` çarpılmasıyla `MaxReceivedMessageSize` yok bir sorun teşkil, devre dışı `IExtensibleDataObject` ikili kodlama kullanırken özelliği. Ayarlama `IgnoreExtensionDataObject` özelliğine `true` üzerinde `ServiceBehaviorAttribute` özniteliği. Alternatif olarak, uygulamayan `IExtensibleDataObject` arabirimi. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][İleri uyumlu veri sözleşmeleri](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="quotas-summary"></a>Kotalar özeti  
 Kotalar ilgili yönergeleri aşağıdaki tabloda özetlenmiştir.  
  
|Koşul|Önemli kotalar ayarlamak için|  
|---------------|-----------------------------|  
|Akış veya küçük iletileri, metin ya da MTOM kodlama akış|`MaxReceivedMessageSize`, `MaxBytesPerRead`, ve`MaxDepth`|  
|Akış veya küçük iletileri, ikili akış kodlama|`MaxReceivedMessageSize`, `MaxSessionSize`ve tüm`ReaderQuotas`|  
|Akış büyük iletiler, metin ya da MTOM kodlama|`MaxBufferSize`ve tüm`ReaderQuotas`|  
|Akış büyük iletiler, ikili kodlama|`MaxBufferSize`, `MaxSessionSize`ve tüm`ReaderQuotas`|  
  
-   Aktarım düzeyinde zaman aşımlarını her zaman ayarlamanız gerekir ve akış olup büyük veya küçük iletileri akış bağımsız olarak kullanımda olduğunda eşzamanlı okuma/yazma hiçbir zaman kullanın.  
  
-   Zaman şüpheli bir kota hakkında güvenli bir değer yerine açık bırakarak ayarlayın.  
  
## <a name="preventing-malicious-code-execution"></a>Kötü amaçlı kod yürütmeyi engelleme  
 Aşağıdaki genel sınıfları tehditleri kod yürütmek ve sahip istenmeyen etkiler:  
  
-   Kötü amaçlı, güvenli olmayan veya güvenlik açısından duyarlı türü seri durumdan çıkarıcının yükler.  
  
-   Gelen ileti gibi normal olarak güvenli bir türünün bir örneği oluşturmak seri durumdan çıkarıcının neden olan bir şekilde istenmeyen sonuçları.  
  
 Aşağıdaki bölümlerde bu sınıfların tehditleri daha ayrıntılı ele alınmıştır.  
  
## <a name="datacontractserializer"></a>DataContractSerializer  
 (Güvenlik bilgileri için <xref:System.Xml.Serialization.XmlSerializer>, ilgili belgelerine bakın.) İçin güvenlik modeli <xref:System.Xml.Serialization.XmlSerializer> olarak benzer <xref:System.Runtime.Serialization.DataContractSerializer>ve çoğunlukla ayrıntıları farklıdır. Örneğin, <xref:System.Xml.Serialization.XmlIncludeAttribute> yerine türü eklemek için kullanılan öznitelik <xref:System.Runtime.Serialization.KnownTypeAttribute> özniteliği. Ancak, bazı tehditler için benzersiz <xref:System.Xml.Serialization.XmlSerializer> bu konunun ilerleyen bölümlerinde ele alınmaktadır.  
  
### <a name="preventing-unintended-types-from-being-loaded"></a>İstenmeyen türleri yüklenmesini engelleme  
 Tür kötü amaçlı veya yalnızca güvenlik açısından duyarlı yan etkileri sahip olup olmadığını istenmeyen türleri yüklenirken önemli sonuçları olabilir. Bir tür yararlanma güvenlik açığı içeren, kendi oluşturucunun ya da sınıf oluşturucu güvenlik açısından duyarlı eylemler gerçekleştirmek, hizmet reddi saldırılarını kolaylaştıran veya kurtarılamaz bir özel durum atabilir büyük bellek parmak izine sahip. Türleri türü yüklendikten hemen sonra ve hiç örneği oluşturulmadan önce çalıştıran sınıf oluşturucular olabilir. Bu nedenlerle, seri durumdan çıkarıcının yükleyebilir türleri kümesini denetlemek önemlidir.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Geniş bağlı şekilde seri durumdan çıkarır. Bu asla ortak dil çalışma zamanı (CLR) türü ve derleme adları gelen verileri okur. Bu davranışı için benzer <xref:System.Xml.Serialization.XmlSerializer>, ancak davranışından farklıdır <xref:System.Runtime.Serialization.NetDataContractSerializer>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Uzak bir saldırgana yalnızca bu tür iletisi adlandırılmasıyla yüklemek için rasgele bir tür belirttiğinden gevşek bağlantı güvenliği, derecesini tanıtır.  
  
 <xref:System.Runtime.Serialization.DataContractSerializer> Göre sözleşmesi şu anda beklenen bir türü yüklemek için her zaman izin verilir. Örneğin, bir veri sözleşmesi türünün veri üyesi varsa `Customer`, <xref:System.Runtime.Serialization.DataContractSerializer> yüklemesine izin `Customer` bu veri üyesi çıkarır zaman yazın.  
  
 Ayrıca, <xref:System.Runtime.Serialization.DataContractSerializer> çok biçimlilik destekler. Bir veri üyesi olarak bildirilmelidir <xref:System.Object>, ancak gelen veri içerebilir bir `Customer` örneği. Bu mümkündür yalnızca `Customer` türü yapılmadı "bilinen" kaldırıcı bu mekanizmalardan biri yoluyla:  
  
-   <xref:System.Runtime.Serialization.KnownTypeAttribute>bir türe uygulanan öznitelik.  
  
-   `KnownTypeAttribute`türlerinin bir listesini döndüren bir yöntem belirten özniteliği.  
  
-   `ServiceKnownTypeAttribute`özniteliği.  
  
-   `KnownTypes` Yapılandırma bölümü.  
  
-   Geçirilecek açıkça bilinen türlerinin bir listesini <xref:System.Runtime.Serialization.DataContractSerializer> seri hale getirici doğrudan kullanıyorsanız, oluşturma sırasında.  
  
 Bu mekanizmaların her biri, yüzey alanını seri durumdan çıkarıcının yükleyebilir ve daha fazla türleri sunarak artırır. Kötü amaçlı veya istenmeyen türü yok bilinen türleri listesine eklendiğinden emin olmak için Bu mekanizmaların her biri kontrol eder.  
  
 Bilinen bir türe kapsamda eklendiğinde, dilediğiniz zaman yüklenebilir ve gerçekte kullanarak sözleşme engelliyor olsa bile türdeki örneklerin oluşturulabilir. Örneğin, "MyDangerousType" Yukarıdaki mekanizmalardan biri kullanılarak bilinen türleri listesine eklenir türü varsayalım. Bunun anlamı:  
  
-   `MyDangerousType`yüklenir ve kendi sınıf oluşturucu döngülerinden.  
  
-   Bile bir dize veri üyesi olan bir veri sözleşmesi seri durumdan çıkarılırken, kötü amaçlı bir ileti örneği hala neden olabilir `MyDangerousType` oluşturmak için. Kod `MyDangerousType`, özellik ayarlayıcıları gibi çalışabilir. Bu yapıldıktan sonra bu örneğin dize veri üyesini atamak ve bir özel durumla başarısız seri durumdan çıkarıcının çalışır.  
  
 Bilinen türlerinin bir listesini döndüren bir yöntem yazarken veya bir liste doğrudan geçirilirken <xref:System.Runtime.Serialization.DataContractSerializer> oluşturucusu, listenin hazırlar kod güvenli ve güvenilir veriler üzerinde çalışıyor.  
  
 Bilinen türler yapılandırmasında belirtiliyorsa, yapılandırma dosyasını güvenli olduğundan emin olun. Tanımlayıcı adlar (tür bulunduğu imzalı derleme ortak anahtarını belirterek) yapılandırmada her zaman kullanın, ancak yük türü sürümü belirtmeyin. Türü yükleyicisi en son sürümünü mümkünse otomatik olarak seçer. Belirli bir sürüm yapılandırmasında belirtirseniz, aşağıdaki riski: sonraki bir sürümde sabit bir güvenlik açığı bir türe sahip olabilir, ancak yapılandırmasında açıkça belirtildiğinden savunmasız sürüm hala yükler.  
  
 Çok fazla bilinen türlerine sahip olan başka bir sonucu: <xref:System.Runtime.Serialization.DataContractSerializer> serileştirme ve seri durumdan gerekir her tür için bir girdi ile uygulama etki alanındaki bir önbellek serileştirme/seri durumdan çıkarma kod oluşturur. Bu önbellek, uygulama etki alanı çalıştığı sürece hiçbir zaman temizlenir. Bu nedenle, uygulama birçok bilinen türler kullanan farkındadır bir saldırgan önbellek orantısız büyük miktarda bellek tüketmesine neden olan tüm bu tür, seri durumdan çıkarma neden olabilir.  
  
### <a name="preventing-types-from-being-in-an-unintended-state"></a>İstenmeyen bir durumda olmasını türleri önleyen  
 Bir tür zorlanmış olmalıdır iç tutarlılık sınırlamaları olabilir. Seri durumdan çıkarma sırasında bu kısıtlamaların çiğnemekten kaçınmak için dikkatli olunması gerekir.  
  
 Aşağıdaki örnekte bir türde bir spacecraft üzerinde bir hava kilidi durumunu temsil eder ve hem iç hem de dış kapı aynı anda açık olamayacağını kısıtlamayı zorlar.  
  
 [!code-csharp[DataContractAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#3)]
 [!code-vb[DataContractAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#3)]  
  
 Bir saldırgan kısıtlamaları alma ve olabilir geçersiz bir durum nesnesi alma gibi bu, kötü amaçlı bir ileti gönderebilir istenmeyen ve beklenmeyen sonuçlara.  
  
```xml  
<SpaceStationAirlock>  
    <innerDoorOpen>true</innerDoorOpen>  
    <outerDoorOpen>true</outerDoorOpen>  
</SpaceStationAirlock>  
```  
  
 Bu durum, aşağıdaki noktaları farkına tarafından önlenebilir:  
  
-   Zaman <xref:System.Runtime.Serialization.DataContractSerializer> çoğu sınıf, çalışmıyor oluşturucular seri durumdan çıkarır. Bu nedenle, oluşturucuda yapılan herhangi bir durum Yönetim güvenmeyin.  
  
-   Geri aramalar nesne geçerli bir durumda olduğundan emin olmak için kullanın. Geri çağırma işaretlenmiş <xref:System.Runtime.Serialization.OnDeserializedAttribute> özniteliği olduğundan özellikle yararlı seri durumdan çıkarma işlemi tamamlandıktan ve inceleyin ve genel durumu düzeltmek için bir fırsat sonra çalışır. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Sürüm toleranslı seri hale getirme geri çağrıları](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).  
  
-   Hangi özelliği ayarlayıcılar çağrılmalıdır belirli bir sıraya üzerinde yararlanmayı veri sözleşmesi tasarım türleri değil.  
  
-   Eski türler ile işaretlenen kullanarak ilgilenebilmek <xref:System.SerializableAttribute> özniteliği. Bunların çoğu, çalışmak için tasarlanmış [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] uzaktan iletişim yalnızca güvenilir veri ile kullanmak için. Bu özniteliği ile işaretlenmiş mevcut türleri durumu güvenliği göz ile tasarlanmış değil.  
  
-   Güvenmeyin <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> özelliği `DataMemberAttribute` durum güvenlik açısından oldukça veri güvence altına almak için öznitelik. Verileri her zaman olabilir `null`, `zero`, veya `invalid`.  
  
-   Hiçbir zaman ilk önce doğrulamadan güvenilmeyen veri kaynağından bir nesne grafiğinin seri durumdan güven. Tek tek her nesne bir bütün olmayabilir tutarlı bir duruma, ancak nesne grafiğinin olabilir. Ayrıca, Nesne grafiği koruma modu devre dışı bırakılırsa, seri durumdan çıkarılmış grafik aynı nesne birden çok başvuran sahip olabilir veya döngüsel başvuru. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
### <a name="using-the-netdatacontractserializer-securely"></a>NetDataContractSerializer güvenli bir şekilde kullanma  
 <xref:System.Runtime.Serialization.NetDataContractSerializer> Sıkı bağlantı türlerini kullanan bir seri hale getirme altyapısıdır. Bu benzer <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> ve <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>. Diğer bir deyişle, okuyarak örneği oluşturmak için tür belirler [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] gelen veri derleme ve tür adı. Bir parçası olmasına rağmen [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], bu serileştirme motoruna takma sağlanan bir yolu yoktur; özel kod yazılabilir. `NetDataContractSerializer` Öncelikle geçişini kolaylaştırmak için sağlanan [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] remoting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]ilgili bölümünde [seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
 Herhangi bir tür yüklenebilir, ileti gösteriyor olabilir çünkü <xref:System.Runtime.Serialization.NetDataContractSerializer> mekanizması doğası gereği güvenli değil ve yalnızca güvenilen verilerle kullanılmalıdır. Yüklemek yalnızca güvenli türler sağlayan bir güvenli, türü sınırlama türü bağlayıcı yazarak Güvenli yapmak mümkündür (kullanarak <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> özelliği).  
  
 İle güvenilir veri bile kullanıldığında, gelen veri yeterince türü yüklemek için özellikle de belirtebilir <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> özelliği ayarlanmış <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple>. Uygulamanın dizine veya genel derleme önbelleği erişimi olan herkes, yüklemek için gereken bir yerine kötü amaçlı bir türü yerine kullanabilirsiniz. Her zaman güvenlik uygulamanızın dizinine ve Genel Derleme Önbelleği doğru izinleri ayarlayarak emin olun.  
  
 Kısmen güvenilen kod erişime izin verirseniz genel olarak, `NetDataContractSerializer` örneği veya aksi halde yedek Seçici denetim (<xref:System.Runtime.Serialization.ISurrogateSelector>) veya seri hale getirme Bağlayıcısı (<xref:System.Runtime.Serialization.SerializationBinder>), kodu denetimi için büyük bir bölümünü üzerinden deneyen Serileştirme/seri durumdan çıkarma işlemi. Örneğin, rastgele türler ekleme, bilginin açığa çıkmasına neden, sonuçta elde edilen Nesne grafiği veya serileştirilmiş verilerle değiştirmesine veya edebilir sonuç serileştirilmiş akış taşması.  
  
 İle ilgili başka bir güvenlik sorunu `NetDataContractSerializer` hizmeti, kötü amaçlı kod yürütme tehdit reddi. Kullanırken `NetDataContractSerializer`her zaman ayarlayın <xref:System.Runtime.Serialization.NetDataContractSerializer.MaxItemsInObjectGraph%2A> kota güvenli bir değer. Yalnızca bu kota tarafından büyüklüğü sınırlı nesnelerinin bir dizisi ayırır küçük bir kötü amaçlı iletisini oluşturmak kolaydır.  
  
### <a name="xmlserializer-specific-threats"></a>XmlSerializer özgü tehditleri  
 <xref:System.Xml.Serialization.XmlSerializer> Güvenlik modeli benzer olarak <xref:System.Runtime.Serialization.DataContractSerializer>. Birkaç tehditler, ancak özgü <xref:System.Xml.Serialization.XmlSerializer>.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Oluşturur *serileştirme derlemelerini* gerçekte serileştirir ve seri durumdan çıkarır; kodu içeren çalışma zamanında bir geçici dosyalar dizininde bu derlemeler oluşturulur. Başka bir işlem veya kullanıcı bu dizin için erişim haklarını varsa, bunlar rasgele koduyla serileştirme/seri durumdan çıkarma kod üzerine yazabilir. <xref:System.Xml.Serialization.XmlSerializer> Serileştirme/seri durumdan çıkarma kod yerine kendi güvenlik bağlamı kullanarak bu kodu çalıştırır. İzinler, bunun olmaması için geçici dosyalar dizini üzerinde doğru şekilde ayarlandığından emin olun.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Da içinde kullandığı önceden oluşturulmuş serileştirme derlemelerini çalışma zamanında oluşturmak yerine bir moda sahiptir. Bu mod tetiklenir her <xref:System.Xml.Serialization.XmlSerializer> uygun serileştirme derlemesini bulabilirsiniz. <xref:System.Xml.Serialization.XmlSerializer> Olsun veya olmasın seri hale getirme derlemesi imzalı serileştirilen türleri içeren bütünleştirilmiş kodun imzalamak için kullanılan aynı anahtar ile denetler. Bu kötü amaçlı derlemelerden serileştirme derlemelerini gösterebilecek koruma sağlar. Seri hale getirilebilir türler içeren derlemenin değilse, ancak, imzalı <xref:System.Xml.Serialization.XmlSerializer> doğru ada sahip bir derleme kullanır ve bu denetimi gerçekleştiremezsiniz. Kötü amaçlı kod çalıştıran bu mümkün kılar. Seri hale getirilebilir türler içeren derlemeler her zaman imzala veya sıkı bir şekilde uygulamanızın dizinine ve kötü amaçlı derlemeleri giriş önlemek için Genel Derleme Önbelleği erişimi denetleme.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Bir hizmet reddi saldırısına tabi olabilir. <xref:System.Xml.Serialization.XmlSerializer> Sahip olmayan bir `MaxItemsInObjectGraph` kota (kullanılabilir olduğu <xref:System.Runtime.Serialization.DataContractSerializer>). Bu nedenle, yalnızca ileti boyutuyla sınırlı nesnelerin rasgele bir tutar çıkarır.  
  
### <a name="partial-trust-threats"></a>Kısmi güven tehditleri  
 Kısmi güven ile çalışan kod ilgili tehditleri ilgili aşağıdaki sorunları unutmayın. Bu tehditler, diğer saldırı senaryoları (belirli bir dizeyi ve ardından seri oluşturan Örneğin, kısmen güvenilen kod) ile birlikte kötü amaçlı kısmen güvenilen kod yanı sıra, kötü amaçlı kısmen güvenilen kod içerir.  
  
-   Hiçbir zaman herhangi bir seri hale getirme bileşenini kullanırken, bu tür kullanımı önce tüm izinleri, assert kapsamında tüm serileştirme senaryodur ve herhangi bir güvenilir olmayan verileri veya nesneleri ile ilgili olmayan olsa bile assert. Bu tür kullanımı güvenlik açıklarına neden olabilir.  
  
-   Kısmen güvenilen kod seri hale getirme işlemi, genişletilebilirlik noktaları (yedekleri), seri hale türleri veya başka yöntemler aracılığıyla denetime sahip olduğu durumlarda kısmen güvenilen kod büyük miktarda çıktısını almak seri hale getirici neden olabilir Hizmet Reddi (DoS) Bu akış alıcıya neden olabilir serileştirilmiş akış verilerini. DoS tehditleri hassas bir hedef yönelik veri seri hale getirme, değil kısmen güvenilen türleri serileştirmek veya aksi halde kısmen güvenilen kod denetim serileştirme olanak tanır.  
  
-   Kısmen güvenilen kod erişime izin verirseniz, <xref:System.Runtime.Serialization.DataContractSerializer> örneği veya aksi takdirde denetlemek [veri sözleşmesi yedekleri](../../../../docs/framework/wcf/extending/data-contract-surrogates.md), serileştirme/seri durumdan çıkarma işlemi üzerinde denetim önemli miktarda çalışma. Örneğin, rastgele türler ekleme, bilginin açığa çıkmasına neden, sonuçta elde edilen Nesne grafiği veya serileştirilmiş verilerle değiştirmesine veya edebilir sonuç serileştirilmiş akış taşması. Eşdeğer bir <xref:System.Runtime.Serialization.NetDataContractSerializer> tehdit "Kullanarak NetDataContractSerializer güvenli bir şekilde" bölümünde açıklanmıştır.  
  
-   Varsa <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik türü için geçerli olduğu (veya türü olarak işaretlenmiş `[Serializable]` ancak `ISerializable`), seri durumdan çıkarıcının genel olmayan ya da taleplerin tarafından korunan tüm oluşturucular olsa bile, bu tür bir türünün bir örneği oluşturabilirsiniz.  
  
-   Hiçbir zaman seri durumdan çıkarma sonucunu seri durumdan çıkarılacak veriler güvenilir ve tüm bilinen türler güvendiğiniz türleri olan sürece güven. Bilinen türlerini uygulama yapılandırma dosyasından yüklenen değildir, (ancak bilgisayar yapılandırma dosyasından yüklenir) unutmayın kısmi güvende çalıştırırken.  
  
-   Geçirirseniz bir `DataContractSerializer` bir yedek örneğiyle eklenen kısmen güvenilen kod için kod, bu yedek üzerinde değiştirilebilir tüm ayarları değiştirebilirsiniz.  
  
-   Seri durumdan çıkarılmış nesne için XML okuyucusu (ya da verileri okuduğunuzu) gelen kısmen güvenilen koddan elde edilen seri durumdan çıkarılmış nesne güvenilmeyen verisi olarak kabul eder.  
  
-   Olgu, <xref:System.Runtime.Serialization.ExtensionDataObject> türünde hiçbir ortak üyeler içerdiği verilerin güvenli olduğunu gelmez. Bazı verilerin bulunduğu, kısmen güvenilen kod, nesne sonra elle bir nesneye bir ayrıcalıklı veri kaynağından seri durumdan Örneğin, kısmen güvenilen kod verileri okuyabilir `ExtensionDataObject` nesnesi seri hale getirilirken tarafından. Ayar göz önünde bulundurun <xref:System.Runtime.Serialization.DataContractSerializer.IgnoreExtensionDataObject%2A> için `true` ne zaman ayrıcalıklı veri kaynağından daha sonraki bir nesnede seri durumdan izin ver geçirilen kısmen güvenilen kod.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer>ve <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> özel, korumalı, iç ve Genel üyeler serileştirmek tam güvende destekler. Ancak, kısmi güvende yalnızca Genel üyeler seri hale getirilebilir. A `SecurityException` genel olmayan üyesi seri hale getirmek bir uygulama denemesi olursa oluşturulur.  
  
     İç izin vermek veya kısmi güvende serileştirilmesi için korumalı iç üyeleri `System.Runtime.CompilerServices.InternalsVisibleTo` derleme özniteliği. Bu öznitelik iç üyeleri başka bir derleme halinde görünür olduğunu bildirmek bir derleme sağlar. Bu durumda, serileştirilmiş kendi iç üyelere sahip istediği bir derlemeyi iç üyeleri için System.Runtime.Serialization.dll görünür olduğunu bildirir.  
  
     Bu yaklaşımın avantajı, yükseltilmiş kod oluşturma yolu gerektirmez ' dir.  
  
     Aynı anda iki ana dezavantajları vardır.  
  
     İlk dezavantajı, katılımı özelliğidir `InternalsVisibleTo` derleme çapında bir özniteliktir. Diğer bir deyişle, yalnızca belirli bir sınıfı serileştirilmiş kendi iç üyelere sahip olabilir belirtemezsiniz. Elbette, yine belirli iç üyesi basitçe değil ekleyerek seri değil seçebilirsiniz bir `DataMember` özniteliği bu üye için. Benzer şekilde, bir geliştirici üye özel veya hafif görünürlük sorunları ile korunan yerine iç yapmak de seçebilirsiniz.  
  
     İkinci dezavantajı, bunu hala özel veya korumalı üyeleri desteklemediğine ' dir.  
  
     Kullanımını göstermek için `InternalsVisibleTo` özniteliği kısmi güvende, aşağıdaki programı göz önünde bulundurun:  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#1)]  
  
     Yukarıdaki örnekte `PermissionsHelper.InternetZone` karşılık gelen `PermissionSet` kısmi güven. Şimdi, olmadan `InternalsVisibleToAttribute`, uygulama atma başarısız olur bir `SecurityException` belirten ortak olmayan üyeler kısmi güvende seri hale getirilemez.  
  
     Ancak, aşağıdaki satırı kaynak dosyasını eklerseniz program başarıyla çalışır.  
  
     [!code-csharp[CDF_WCF_SecurityConsiderationsForData#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/cdf_wcf_securityconsiderationsfordata/cs/program.cs#2)]  
  
## <a name="other-state-management-concerns"></a>Diğer durum yönetimi konuları  
 Nesne durumu yönetimi ile ilgili bazı sorunları tümleştirilmediği şunlardır:  
  
-   İleti ulaştığında ile akış aktarma akışı tabanlı programlama modeli kullanarak, ileti işlenmesini oluşur. İletiyi gönderen, daha fazla içerik bekleniyorsa, kodunuzu öngörülemeyen durumda bırakarak akış ortasında gönderme işlemini iptal. Genel olarak, tam olan akışta güvenmeyin ve herhangi bir iş akışı geri durduruldu durumunda, alınamaz akışı tabanlı bir işlemde gerçekleştirmeyin. Bu durum burada bir ileti olabilir hatalı biçimlendirilmiş akış gövde sonra durum için de geçerlidir (örneğin, SOAP Zarfı için bir bitiş etiketi eksik olabilir veya ikinci bir ileti gövdesi olabilir).  
  
-   Kullanarak `IExtensibleDataObject` özelliği yayınlaması hassas verileri neden olabilir. Güvenilmeyen bir kaynaktan veri veri Sözleşmelerle içine kabul ettiğiniz, `IExtensibleObjectData` ve daha sonra onu güvenli bir kanal nerede imzalı iletiler üzerinde yeniden yayma, büyük olasılıkla bildiğiniz bir şey hakkında veriler için doğrulanmasından. Ayrıca, gönderdiğiniz genel durumu veri bilinen ve bilinmeyen parçalarını dikkate varsa geçersiz olabilir. Her iki seçmeli olarak uzantısını verileri özelliğini ayarlayarak bu durumdan kaçınmak `null` veya seçmeli olarak devre dışı bırakarak `IExtensibleObjectData` özelliği.  
  
## <a name="schema-import"></a>Şema alma  
 Normalde, türleri oluşturmak için şemayı içe aktarma işlemi yalnızca tasarım zamanında, örneğin, kullanarak olur [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) istemci sınıfı oluşturmak için bir Web hizmeti üzerinde. Ancak, daha gelişmiş senaryolarda, çalışma zamanında şema işleyebilir. Bunun yapılması, hizmet reddi riskleri ortaya çıkarabilirsiniz olduğunu unutmayın. Bazı şeması içeri aktarılacak uzun sürebilir. Hiçbir zaman kullanmayın <xref:System.Xml.Serialization.XmlSerializer> şema alma bileşen şemaları büyük olasılıkla güvenilmeyen bir kaynaktan gelip senaryolarda.  
  
## <a name="threats-specific-to-aspnet-ajax-integration"></a>Tehditler belirli ASP.NET AJAX tümleştirme  
 Ne zaman kullanıcı arabirimini uygulayan <xref:System.ServiceModel.Description.WebScriptEnablingBehavior> veya <xref:System.ServiceModel.Description.WebHttpBehavior>, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML ve JSON iletileri kabul edebilir bir uç noktasını kullanıma sunar. Ancak, hem XML okuyucusu ve JSON okuyucu tarafından kullanılan okuyucu kotaları, yalnızca bir kümesi yok. Bazı kota ayarları bir okuyucu için uygun ancak diğer çok büyük olabilir.  
  
 Uygularken `WebScriptEnablingBehavior`, kullanıcı bir JavaScript proxy'si uç noktada kullanıma sunmak için olanağına sahiptir. Aşağıdaki güvenlik konularını ele alınmalıdır:  
  
-   (İşlemi adları, parametre adları ve benzeri) hizmeti hakkında bilgi JavaScript proxy'si incelenerek elde edilebilir.  
  
-   JavaScript uç nokta kullanılırken, hassas ve özel bilgileri istemci Web tarayıcısının önbelleğine korunur.  
  
## <a name="a-note-on-components"></a>Not bileşenleri  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]bir esnek ve özelleştirilebilir sistemidir. Bu konuda içeriğini çoğunu odak en sık karşılaşılan [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kullanım senaryoları. Ancak, bu bileşenleri oluşturmak mümkündür [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] birçok farklı yolla sağlar. Her bileşen kullanarak güvenlik etkilerini anlamak önemlidir. Özellikle:  
  
-   XML okuyucular kullandığınızda gerekir okuyucular kullanın <xref:System.Xml.XmlDictionaryReader> sınıfı, aksine başka bir okuyucu sağlar. Güvenli okuyucular kullanılarak oluşturulan <xref:System.Xml.XmlDictionaryReader.CreateTextReader%2A>, <xref:System.Xml.XmlDictionaryReader.CreateBinaryReader%2A>, veya <xref:System.Xml.XmlDictionaryReader.CreateMtomReader%2A> yöntemleri. Kullanmayın <xref:System.Xml.XmlReader.Create%2A> yöntemi. Okuyucular her zaman güvenli kotaları yapılandırın. Seri hale getirme altyapıları [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] yalnızca güvenli XML okuyuculardan ile kullanıldığında güvenlidir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
-   Kullanırken <xref:System.Runtime.Serialization.DataContractSerializer> potansiyel olarak güvenilmeyen veri serisi için her zaman ayarlayın <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A> özelliği.  
  
-   Bir ileti oluştururken ayarlama `maxSizeOfHeaders` parametresi varsa `MaxReceivedMessageSize` yeterli koruma sağlamaz.  
  
-   Bir kodlayıcı oluştururken, her zaman ilgili kotalar gibi yapılandırmadan `MaxSessionSize` ve `MaxBufferSize`.  
  
-   Bir XPath İleti Filtresi kullanırken ayarlayın <xref:System.ServiceModel.Dispatcher.XPathMessageFilter.NodeQuota%2A> filtre ziyaret XML düğümlerini miktarını sınırlamak için. Birçok düğümünü ziyaret etmenize gerek kalmadan işlem için uzun zaman alabilir XPath ifadeler kullanmayın.  
  
-   Genel olarak, bir kota kabul eden herhangi bir bileşeni kullanırken, kendi güvenlik etkilerini anlama ve güvenli bir değere ayarlayın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.XmlDictionaryReader>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Veri Anlaşması Bilinen Türler](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)
