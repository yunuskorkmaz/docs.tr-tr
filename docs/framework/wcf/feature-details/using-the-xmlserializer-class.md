---
title: XmlSerializer Sınıfını Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 2ef2d0eefb571f64040fabd16fd65fdfde7a626d
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600211"
---
# <a name="using-the-xmlserializer-class"></a>XmlSerializer Sınıfını Kullanma

Windows Communication Foundation (WCF), uygulamanızdaki verileri, serileştirme adlı bir işlem olan istemciler ve hizmetler arasında aktarılan XML 'ye dönüştürmek için iki farklı serileştirme teknolojisini kullanabilir.

## <a name="datacontractserializer-as-the-default"></a>Varsayılan olarak DataContractSerializer

Varsayılan olarak WCF, <xref:System.Runtime.Serialization.DataContractSerializer> veri türlerini seri hale getirmek için sınıfını kullanır. Bu serileştirici aşağıdaki türleri destekler:

- İlkel türler (örneğin, tamsayılar, dizeler ve bayt dizileri), ve gibi bazı özel türler <xref:System.Xml.XmlElement> ve <xref:System.DateTime> temel öğeler olarak kabul edilir.

- Veri anlaşması türleri (özniteliğiyle işaretlenmiş türler <xref:System.Runtime.Serialization.DataContractAttribute> ).

- <xref:System.SerializableAttribute>Arabirimini uygulayan türler dahil olmak üzere, özniteliğiyle işaretlenmiş türler <xref:System.Runtime.Serialization.ISerializable> .

- Arabirimi uygulayan türler <xref:System.Xml.Serialization.IXmlSerializable> .

- Birçok genel koleksiyon türü içeren birçok ortak koleksiyon türü.

Birçok .NET Framework türü, son iki kategoriye girer ve bu nedenle seri hale getirilebilir. Serileştirilebilir türlerin dizileri de seri hale getirilebilir. Tüm liste için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](specifying-data-transfer-in-service-contracts.md).

<xref:System.Runtime.Serialization.DataContractSerializer>Veri sözleşme türleriyle birlikte kullanılan, yenı WCF Hizmetleri yazmak için önerilen yoldur. Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](using-data-contracts.md).

## <a name="when-to-use-the-xmlserializer-class"></a>XmlSerializer sınıfının ne zaman kullanılacağı

WCF Ayrıca sınıfını da destekler <xref:System.Xml.Serialization.XmlSerializer> . <xref:System.Xml.Serialization.XmlSerializer>Sınıf WCF için benzersiz değil. Bu, ASP.NET Web hizmetlerinin kullandığı serileştirme altyapısının aynısıdır. <xref:System.Xml.Serialization.XmlSerializer>Sınıfı, sınıftan çok daha dar bir tür kümesini destekler <xref:System.Runtime.Serialization.DataContractSerializer> , ancak sonuçta elde edilen XML üzerinde çok daha fazla denetime izin verır ve XML şeması tanım DILI (xsd) standardının çok daha fazlasını destekler. Ayrıca, seri hale getirilebilir türlerde hiçbir bildirime dayalı öznitelik gerektirmez. Daha fazla bilgi için .NET Framework belgelerindeki XML serileştirme konusuna bakın. <xref:System.Xml.Serialization.XmlSerializer>Sınıf, veri anlaşması türlerini desteklemiyor.

Visual Studio 'da bir üçüncü taraf hizmeti için istemci kodu oluşturmak üzere Svcutil. exe ' yi veya **hizmet başvurusu Ekle** özelliğini kullanırken veya bir üçüncü taraf şemasına erişmek için, uygun bir seri hale getirici sizin için otomatik olarak seçilir. Şema ile uyumlu değilse, <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> seçilidir.

## <a name="manually-switching-to-the-xmlserializer"></a>XmlSerializer 'a el ile geçiş

Her zaman, el ile geçiş yapmanız gerekebilir <xref:System.Xml.Serialization.XmlSerializer> . Bu durum örneğin, aşağıdaki durumlarda oluşur:

- Bir uygulamayı ASP.NET Web hizmetlerinden WCF 'ye geçirirken, <xref:System.Xml.Serialization.XmlSerializer> Yeni veri anlaşması türleri oluşturmak yerine mevcut, uyumlu türleri yeniden kullanmak isteyebilirsiniz.

- İletilerde görüntülenen XML üzerinde kesin denetim önemli olduğunda, ancak bir Web Hizmetleri Açıklama Dili (WSDL) belgesi yoksa, örneğin, DataContractSerializer ile uyumlu olan belirli standartlaştırılmış, yayımlanmış bir şemaya uyum sağlamak için gereken türlere sahip bir hizmet oluştururken.

- Eski SOAP kodlama standardını izleyen hizmetler oluştururken.

Bu ve diğer durumlarda, <xref:System.Xml.Serialization.XmlSerializer> `XmlSerializerFormatAttribute` aşağıdaki kodda gösterildiği gibi, özniteliğini hizmetinize uygulayarak sınıfa el ile geçiş yapabilirsiniz.

[!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
[!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]

## <a name="security-considerations"></a>Güvenlikle İlgili Dikkat Edilmesi Gerekenler

> [!NOTE]
> Serileştirme altyapılarını değiştirirken dikkatli olmanız önemlidir. Aynı tür, kullanılmakta olan seri hale getiriciye göre farklı şekilde XML 'e serileştirilir. Yanlışlıkla yanlış seri hale getirici kullanıyorsanız, bu bilgilerin açığa çıkarmamasını istemediğiniz türden bilgileri kapatıyorsunuz olabilirsiniz.

Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı yalnızca <xref:System.Runtime.Serialization.DataMemberAttribute> veri anlaşması türlerini serileştirilirken özniteliği ile işaretlenmiş üyeleri seri hale getirir. <xref:System.Xml.Serialization.XmlSerializer>Sınıfı herhangi bir genel üyeyi seri hale getirir. Aşağıdaki kodda bulunan türe bakın.

[!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
[!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]

Tür, sınıfın seçildiği bir hizmet sözleşmesinde yanlışlıkla kullanılırsa, <xref:System.Xml.Serialization.XmlSerializer> `creditCardNumber` üye serileştirilir, büyük olasılıkla hedeflenmemiştir.

<xref:System.Runtime.Serialization.DataContractSerializer>Sınıf varsayılan olsa da, <xref:System.ServiceModel.DataContractFormatAttribute> özelliği hizmet sözleşmesi türüne uygulayarak hizmeti için açıkça seçebilirsiniz (bunu yapmanız hiçbir şekilde yapmanız gerekmese de).

Hizmet için kullanılan serileştirici, sözleşmenin ayrılmaz bir parçasıdır ve farklı bir bağlama seçilerek veya diğer yapılandırma ayarları değiştirilerek değiştirilemez.

Sınıfına yönelik diğer önemli güvenlik konuları geçerlidir <xref:System.Xml.Serialization.XmlSerializer> . İlk olarak, sınıfını kullanan tüm WCF uygulamalarının <xref:System.Xml.Serialization.XmlSerializer> , açıklanmasından korunmuş bir anahtarla imzalanmış olması önemle tavsiye edilir. Bu öneri her ikisi de için el ile yapılan bir geçiş gerçekleştirildiğinde <xref:System.Xml.Serialization.XmlSerializer> ve bir otomatik anahtar gerçekleştirildiğinde (Svcutil. exe, hizmet başvurusu Ekle veya benzer bir araçla) geçerlidir. Bunun nedeni, <xref:System.Xml.Serialization.XmlSerializer> serileştirme altyapısının uygulamayla aynı anahtarla İmzalandıkları sürece *önceden oluşturulmuş serileştirme derlemelerinin* yüklenmesini desteklemesinden kaynaklanır. İmzasız bir uygulama, uygulama klasörüne veya genel derleme önbelleğine yerleştirilmiş önceden oluşturulmuş serileştirme derlemesinin beklenen adıyla eşleşen kötü amaçlı bir derleme olasılığa karşı tamamen korumasız olur. Tabii ki, bu eylemi denemek için bir saldırganın öncelikle bu iki konumdan birine yazma erişimi edinilmesi gerekir.

Her kullanışınızda <xref:System.Xml.Serialization.XmlSerializer> , sistem geçici klasörüne yazma erişimiyle ilgili olan başka bir tehdit vardır. <xref:System.Xml.Serialization.XmlSerializer>Serileştirme altyapısı, bu klasörde geçici *serileştirme derlemeleri* oluşturur ve kullanır. Geçici klasöre yazma erişimi olan herhangi bir işlemin, bu serileştirme derlemelerinin kötü amaçlı kodla üzerine yazamayacağını bilmelisiniz.

## <a name="rules-for-xmlserializer-support"></a>XmlSerializer desteği için kurallar

<xref:System.Xml.Serialization.XmlSerializer>Anlaşma işlemi parametrelerine veya dönüş değerlerine doğrudan uyumlu öznitelikleri uygulayamazsınız. Ancak, aşağıdaki kodda gösterildiği gibi, yazılı iletilere (ileti sözleşmesi gövde parçaları) uygulanabilirler.

[!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
[!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]

Yazılı ileti üyelerine uygulandığında, bu öznitelikler yazılan ileti özniteliklerinde çakışan özellikleri geçersiz kılar. Örneğin, aşağıdaki kodda `ElementName` geçersiz kılmalar `Name` .

[!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
[!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]

<xref:System.ServiceModel.MessageHeaderArrayAttribute>Özelliği kullanılırken özniteliği desteklenmez <xref:System.Xml.Serialization.XmlSerializer> .

> [!NOTE]
> Bu durumda, WCF 'den <xref:System.Xml.Serialization.XmlSerializer> önce yayınlanan aşağıdaki özel durumu oluşturur: "şemanın en üst düzeyinde bildirildiği bir öğe `maxOccurs` > 1 olamaz. ' More ' için veya `XmlArray` `XmlArrayItem` yerine ya `XmlElementAttribute` da Sarmalanan parametre stilini kullanarak ' More ' için bir sarmalayıcı öğesi sağlayın. "
>
> Böyle bir özel durum alırsanız, bu durumun uygulanıp uygulanmadığını araştırın.

WCF, <xref:System.Xml.Serialization.SoapIncludeAttribute> <xref:System.Xml.Serialization.XmlIncludeAttribute> İleti sözleşmeleri ve işlem sözleşmeleri içindeki ve özniteliklerini desteklemez; <xref:System.Runtime.Serialization.KnownTypeAttribute> bunun yerine özniteliğini kullanın.

## <a name="types-that-implement-the-ixmlserializable-interface"></a>IXmlSerializable arabirimini uygulayan türler

Arabirimini uygulayan türler `IXmlSerializable` tarafından tamamen desteklenir `DataContractSerializer` . <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>Bu türlerin şemasını denetlemek için özniteliği her zaman bu türlere uygulanmalıdır.

> [!WARNING]
> Polimorfik türler serileştirilmiş olmanız durumunda <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> doğru türün serileştirildiğinden emin olmak için türünü türüne uygulamanız gerekir.

Şunları uygulayan tür üç değişken vardır `IXmlSerializable` : rastgele içeriği temsil eden türler, tek bir öğeyi temsil eden türler ve eski <xref:System.Data.DataSet> türler.

- İçerik türleri özniteliği tarafından belirtilen bir şema sağlayıcısı yöntemini kullanır `XmlSchemaProviderAttribute` . Yöntemi döndürmez `null` ve <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> özniteliğinde özelliği varsayılan değerinde bırakılır `false` . Bu, türlerin en yaygın kullanımdır `IXmlSerializable` .

- Öğe türleri, bir `IXmlSerializable` türün kendi kök öğe adını denetlemesini gerektiğinde kullanılır. Bir türü öğe türü olarak işaretlemek için, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> öznitelik üzerinde özelliğini, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> `true` şema sağlayıcısı yönteminden veya geri dönüş olarak ayarlayın `null` . Bir şema sağlayıcısı yönteminin olması, öğe türleri için isteğe bağlıdır `null` ; içinde Yöntem adı yerine belirtebilirsiniz `XmlSchemaProviderAttribute` . Ancak, `IsAny` `true` ve bir şema sağlayıcısı yöntemi belirtilmişse, Yöntemi döndürmelidir `null` .

- Eski <xref:System.Data.DataSet> türler `IXmlSerializable` , özniteliğiyle işaretlenmemiş türlerdir `XmlSchemaProviderAttribute` . Bunun yerine, <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> şema oluşturma yöntemine bağlıdır. Bu model, türü için kullanılır `DataSet` ve türü belirtilmiş veri kümesi .NET Framework önceki sürümlerinde bir sınıf türetiliyor, ancak artık kullanılmıyor ve yalnızca eski nedenlerden dolayı destekleniyor. Bu modele güvenmeyin ve her zaman `XmlSchemaProviderAttribute` `IXmlSerializable` türlerinizi uygulayın.

### <a name="ixmlserializable-content-types"></a>IXmlSerializable Içerik türleri

, Uygulayan `IXmlSerializable` ve daha önce tanımlanan bir içerik türü olan bir veri üyesini serileştirilirken, serileştirici veri üyesine yönelik sarmalayıcı öğesini yazar ve denetimi <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemine geçirir. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>Uygulama, sarmalayıcı öğesine öznitelik eklemeyi içeren herhangi BIR XML yazabilir. İşlem tamamlandıktan sonra `WriteXml` seri hale getirici öğeyi kapatır.

Uygulayan `IXmlSerializable` ve daha önce tanımlanan bir içerik türü olan bir veri üyesinin serisi kaldırılırken, seri hale getirici veri üyesine yönelik sarmalayıcı ÖĞESINDE XML okuyucuyu konumlandırır ve denetimi <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> yöntemine geçirir. Yöntemi, başlangıç ve bitiş etiketleri dahil olmak üzere tüm öğeyi okumalı olmalıdır. `ReadXml`Kodunuzun, öğenin boş olduğu durumu işlediğinizden emin olun. Ayrıca, `ReadXml` uygulamanız belirli bir şekilde adlandırılan sarmalayıcı öğesine dayanmamalıdır. Seri hale getirici tarafından seçilen ad değişiklik gösterebilir.

`IXmlSerializable`Örneğin, türündeki veri üyelerine polymorphically içerik türleri atama izni verilir <xref:System.Object> . Tür örneklerinin null olması de buna izin verilir. Son olarak, `IXmlSerializable` türleri nesne Graph koruması etkin ve ile birlikte kullanmak mümkündür <xref:System.Runtime.Serialization.NetDataContractSerializer> . Tüm bu özellikler, WCF serileştiricinin belirli öznitelikleri sarmalayıcı öğesine ("Nil" ve "tür" i XML şema örneği ad alanında ve "ID", "ref", "Type" ve "Assembly" adlı WCF 'ye özgü bir ad alanında) iliştirmesini gerektirir.

#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml 'i uygularken yoksayılacak öznitelikler

`ReadXml`Kodu kodunuza geçirmeden önce seri hale GETIRICI XML öğesini inceler, bu özel XML özniteliklerini algılar ve üzerinde davranır. Örneğin, "Nil" ise, `true` null değeri seri durumdan çıkarılmış olur ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, öğesinin içeriği farklı türde gibi seri durumdan çıkarılacak. Polymorphically tarafından atanan türün uygulamasının uygulamasına `ReadXml` denir. Herhangi bir durumda, bir `ReadXml` uygulama, seri hale getirici tarafından işlendiği için bu özel öznitelikleri yoksaymalıdır.

### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable Içerik türleri için şema konuları

Şema ve `IXmlSerializable` içerik türü dışarı aktarılırken, şema sağlayıcısı yöntemi çağırılır. <xref:System.Xml.Schema.XmlSchemaSet>Şema sağlayıcısı yöntemine geçirilir. Yöntemi, şema kümesine geçerli bir şema ekleyebilir. Şema kümesi, şema dışa aktarma gerçekleştiği sırada zaten bilinen şemayı içerir. Şema sağlayıcısı yönteminin şema kümesine bir öğe eklemesi gerektiğinde, <xref:System.Xml.Schema.XmlSchema> uygun ad alanı ile birlikte bir öğesinin küme içinde olup olmadığını belirlemesi gerekir. Varsa, şema sağlayıcısı yönteminin yeni öğeyi mevcut öğesine eklemesi gerekir `XmlSchema` . Aksi halde, yeni bir örnek oluşturması gerekir `XmlSchema` . Bu, tür dizileri kullanılıyorsa önemlidir `IXmlSerializable` . Örneğin, " `IXmlSerializable` b" ad alanında "A" türü olarak verilen bir tür varsa, şema sağlayıcısı yönteminin adı, şema kümesi "b" için "ArrayOfA" türünü tutmak için şemayı zaten içeriyor olabilir.

Türüne tür eklemenin yanı sıra <xref:System.Xml.Schema.XmlSchemaSet> , içerik türleri için şema sağlayıcısı yöntemi null olmayan bir değer döndürmelidir. <xref:System.Xml.XmlQualifiedName>Verilen tür için kullanılacak şema türünün adını belirten bir döndürebilir `IXmlSerializable` . Bu tam ad ayrıca tür için veri anlaşması adı ve ad alanı olarak da kullanılır. Şema sağlayıcısı yöntemi döndürüldüğünde, şema kümesinde varolmayan bir tür döndürebilir. Ancak, tüm ilişkili türlerin verildiği zaman tarafından ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi ' de tüm ilgili türler için çağrılır <xref:System.Runtime.Serialization.XsdDataContractExporter> ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliğine erişilir), tür şema kümesinde bulunur. `Schemas`Tüm ilgili çağrılar yapılmadan önce özelliğe erişilmesi `Export` bir ile sonuçlanabilir <xref:System.Xml.Schema.XmlSchemaException> . Dışarı aktarma işlemi hakkında daha fazla bilgi için bkz. [sınıflardan şemaları dışarı aktarma](exporting-schemas-from-classes.md).

Şema sağlayıcısı yöntemi kullanmak için ' i de döndürebilir <xref:System.Xml.Schema.XmlSchemaType> . Tür anonim olmayabilir veya olmayabilir. Anonim ise, tür şeması `IXmlSerializable` `IXmlSerializable` bir veri üyesi olarak her kullanıldığında anonim bir tür olarak verilir. `IXmlSerializable`Türün hala bir veri anlaşması adı ve ad alanı vardır. (Bu, ad özelleştirmek için özniteliğin kullanılamaz olması dışında, [veri anlaşması adlarında](data-contract-names.md) açıklandığı şekilde belirlenir <xref:System.Runtime.Serialization.DataContractAttribute> .) Anonim değilse, içindeki türlerden biri olmalıdır `XmlSchemaSet` . Bu durum, türünün döndürülmesi ile eşdeğerdir `XmlQualifiedName` .

Ayrıca, genel bir öğe bildirimi tür için verilir. Türün <xref:System.Xml.Serialization.XmlRootAttribute> kendisine uygulanan özniteliği yoksa, öğesi veri sözleşmesiyle aynı ada ve ad alanına sahiptir ve "boş bırakılabilir" özelliği olur `true` . Bunun tek istisnası şema ad alanıdır ( `http://www.w3.org/2001/XMLSchema` ): türün veri sözleşmesi bu ad alanında yer alıyorsa, ilgili genel öğe, şema ad alanına yeni öğeler eklemek yasak olduğundan boş ad alanıdır. Türe `XmlRootAttribute` uygulanmış özniteliği varsa, genel öğe bildirimi aşağıdaki: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A> <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> ve özellikleri kullanılarak verilir <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> . `XmlRootAttribute`Uygulanan varsayılanlar, veri sözleşmesinin adı, boş bir ad alanı ve "boş bırakılabilir" olur `true` .

Aynı genel öğe bildirimi kuralları eski veri kümesi türleri için de geçerlidir. `XmlRootAttribute`Özel kod aracılığıyla eklenen genel öğe bildirimlerinin geçersiz kılınmadığını, `XmlSchemaSet` şema sağlayıcısı yöntemi kullanılarak veya `GetSchema` eski veri kümesi türleri için aracılığıyla geçersiz kılabileceğini unutmayın.

### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri

`IXmlSerializable`öğe türlerinde, `IsAny` özelliği olarak ayarlanmış ya da `true` şema sağlayıcısı yöntemi döndürüyor `null` .

Öğe türünü serileştirmek ve serisini kaldırma, içerik türünü serileştirmek ve seri durumdan çıkarmak için çok benzerdir. Ancak bazı önemli farklılıklar vardır:

- `WriteXml`Uygulamanın tam olarak bir öğe yazması bekleniyordu (kuşkusuz birden çok alt öğe içerebilir). Bu tek öğe, birden çok eşdüzey öğe veya karışık içerik dışında öznitelikleri yazmamalıdır. Öğe boş olabilir.

- `ReadXml`Uygulama sarmalayıcı öğesini okumalı olmalıdır. Üreten bir öğeyi okuması beklenmektedir `WriteXml` .

- Öğe türü düzenli olarak serileştirilirken (örneğin, bir veri sözleşmesindeki veri üyesi olarak), seri hale getirici, `WriteXml` içerik türlerinde olduğu gibi çağrılmadan önce bir sarmalayıcı öğesi verir. Ancak, en üst düzeyde bir öğe türü serileştirilirken, seri hale getirici, `WriteXml` `DataContractSerializer` veya oluşturucularda serileştirici oluşturulurken bir kök ad ve ad alanı açıkça belirtilmediği takdirde, normalde bir sarmalayıcı öğesi yazar `NetDataContractSerializer` . Daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).

- Yapılandırma zamanında kök adı ve ad alanını belirtmeden en üst düzeyde bir öğe türü serileştirilirken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> temelde hiçbir şey ve çağrı yapmaksızın <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> `WriteXml` . Bu modda, serileştirilmekte olan nesne olamaz `null` ve polymorphically atanamaz. Ayrıca, nesne grafiği koruması etkinleştirilemez ve kullanılamaz `NetDataContractSerializer` .

- Yapılandırma sırasında kök adı ve ad alanını belirtmeden en üst düzeyde bir öğe türü seri durumdan çıkarılırken, <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> `true` herhangi bir öğenin başlangıcını bulabiliyorsanız ' ı döndürür. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>parametresi, `verifyObjectName` `true` `IsStartObject` nesne gerçekten okunmadan önce ile aynı şekilde davranır. `ReadObject`sonra denetimi yöntemine geçirir `ReadXml` .

Öğe türleri için aktarılmış şema, `XmlElement` şema sağlayıcısı yönteminin <xref:System.Xml.Schema.XmlSchemaSet> içerik türleriyle olduğu gibi ek bir şema ekleyebildiğinden, daha önceki bir bölümde açıklanan tür ile aynıdır. `XmlRootAttribute`Özniteliğin öğe türleriyle kullanılmasına izin verilmez ve genel öğe bildirimleri bu türler için hiçbir şekilde yayılmaz.

### <a name="differences-from-the-xmlserializer"></a>XmlSerializer 'ın farkları

`IXmlSerializable`Arabirimi ve `XmlSchemaProviderAttribute` ve `XmlRootAttribute` öznitelikleri de tarafından anlaşılamalıdır <xref:System.Xml.Serialization.XmlSerializer> . Bununla birlikte, bunların veri anlaşması modelinde nasıl ele alınların bazı farklılıkları vardır. Önemli farklılıklar aşağıdaki listede özetlenmiştir:

- Şema sağlayıcısı yönteminin ' de kullanılabilmesi için genel olması gerekir `XmlSerializer` , ancak veri sözleşmesi modelinde kullanılabilmesi için genel olması gerekmez.

- Şema sağlayıcısı yöntemi `IsAny` `true` , veri anlaşması modelinde olduğunda çağrılır, ancak ile değil `XmlSerializer` .

- `XmlRootAttribute`İçerik veya eski veri kümesi türleri için öznitelik mevcut olmadığında, `XmlSerializer` boş ad alanında genel bir öğe bildirimini dışarı aktarır. Veri anlaşması modelinde, kullanılan ad alanı normalde daha önce açıklandığı gibi veri sözleşmesi ad alanıdır.

Serileştirme teknolojileriyle birlikte kullanılan türler oluşturulurken bu farklılıklara dikkat edin.

### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable şeması içeri aktarılıyor

Türlerden oluşturulan bir şemayı içeri aktarırken `IXmlSerializable` birkaç olasılık vardır:

- Oluşturulan şema, [veri sözleşmesi şema başvurusunda](data-contract-schema-reference.md)açıklandığı gibi geçerli bir veri anlaşması şeması olabilir. Bu durumda, her zamanki gibi şema içeri aktarılabilir ve normal veri anlaşması türleri oluşturulur.

- Oluşturulan şema geçerli bir veri anlaşması şeması olmayabilir. Örneğin, şema sağlayıcınız yönteminiz, veri anlaşması modelinde desteklenmeyen XML özniteliklerini içeren bir şema üretebilir. Bu durumda, şemayı türler olarak içeri aktarabilirsiniz `IXmlSerializable` . Bu içeri aktarma modu varsayılan olarak açık değildir, ancak örneğin, `/importXmlTypes` [ServiceModel meta veri yardımcı programı aracına (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)komut satırı anahtarı ile birlikte kolayca etkinleştirilebilir. Bu, [sınıfları oluşturmak Için Içeri aktarma şemasında](importing-schema-to-generate-classes.md)ayrıntılı olarak açıklanmıştır. Doğrudan tür örneklerinizin XML ile birlikte çalışmanız gerektiğini unutmayın. Ayrıca, daha geniş bir şema aralığını destekleyen farklı bir serileştirme teknolojisi kullanmayı da düşünebilirsiniz; bkz. kullanma konusu `XmlSerializer` .

- Mevcut `IXmlSerializable` türlerinizi yeni bir oluşturma yerine proxy 'de yeniden kullanmak isteyebilirsiniz. Bu durumda, tür oluşturmak için şemayı Içeri aktarma konu başlığı altında açıklanan Başvurulmuş türler özelliği, yeniden kullanılacak türü belirtmek için kullanılabilir. Bu `/reference` , yeniden kullanılacak türleri içeren derlemeyi belirten Svcutil. exe ' de anahtarı kullanmaya karşılık gelir.

### <a name="xmlserializer-legacy-behavior"></a>XmlSerializer eski davranışı

.NET Framework 4,0 ve önceki sürümlerde XmlSerializer, C# kodunu bir dosyaya yazarak geçici serileştirme derlemeleri oluşturdu. Dosya daha sonra bir derlemeye derlendi.  Bu davranış, serileştiricinin başlama süresini yavaşlatarak bazı istenmeyen sonuçlara sahipti. .NET Framework 4,5 ' de, bu davranış derleyicinin kullanılmasına gerek kalmadan derlemeleri oluşturmak üzere değiştirilmiştir. Bazı geliştiriciler oluşturulan C# kodunu görmek isteyebilir. Aşağıdaki yapılandırmayla bu eski davranışı kullanmayı belirtebilirsiniz:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.xml.serialization>
    <xmlSerializer tempFilesLocation='e:\temp\XmlSerializerBug' useLegacySerializerGeneration="true" />
  </system.xml.serialization>
  <system.diagnostics>
    <switches>
      <add name="XmlSerialization.Compilation" value="1" />
    </switches>
  </system.diagnostics>
</configuration>
```

`XmlSerializer`Türetilmiş bir sınıfı genel olmayan yeni bir geçersiz kılma ile seri hale getirmek başarısız gibi uyumluluk sorunları yaşıyorsanız, `XMLSerializer` aşağıdaki yapılandırmayı kullanarak eski davranışa geri dönebilirsiniz:

```xml
<configuration>
  <appSettings>
    <add key="System:Xml:Serialization:UseLegacySerializerGeneration" value="true" />
  </appSettings>
</configuration>
```

Yukarıdaki yapılandırmaya alternatif olarak, aşağıdaki yapılandırmayı .NET Framework 4,5 veya sonraki bir sürümü çalıştıran bir makinede kullanabilirsiniz:

```xml
<configuration>
  <system.xml.serialization>
    <xmlSerializer useLegacySerializerGeneration="true"/>
  </system.xml.serialization>
</configuration>
```

> [!NOTE]
> `<xmlSerializer useLegacySerializerGeneration="true"/>`Anahtar yalnızca .NET Framework 4,5 veya üzeri bir sürümü çalıştıran bir makinede çalışır. Yukarıdaki `appSettings` yaklaşım tüm .NET Framework sürümlerinde geçerlidir.

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](specifying-data-transfer-in-service-contracts.md)
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Nasıl yapılır: XmlSerializer Kullanarak WCF İstemci Uygulamalarının Başlangıç Zamanlarını İyileştirme](startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
