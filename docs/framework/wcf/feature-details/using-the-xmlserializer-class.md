---
title: XmlSerializer Sınıfını Kullanma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XmlSerializer [WCF], using
ms.assetid: c680602d-39d3-44f1-bf22-8e6654ad5069
ms.openlocfilehash: 966c3c17c3c42e20ad55681e1c17b13d3f466fa3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967814"
---
# <a name="using-the-xmlserializer-class"></a>XmlSerializer Sınıfını Kullanma
Windows Communication Foundation (WCF), uygulamanızdaki verileri, serileştirme adlı bir işlem olan istemciler ve hizmetler arasında aktarılan XML 'ye dönüştürmek için iki farklı serileştirme teknolojisini kullanabilir.  
  
## <a name="datacontractserializer-as-the-default"></a>Varsayılan olarak DataContractSerializer  
 Varsayılan olarak WCF, <xref:System.Runtime.Serialization.DataContractSerializer> veri türlerini seri hale getirmek için sınıfını kullanır. Bu serileştirici aşağıdaki türleri destekler:  
  
- İlkel türler (örneğin, tamsayılar, dizeler ve bayt dizileri), <xref:System.Xml.XmlElement> ve gibi bazı özel türler ve <xref:System.DateTime>temel öğeler olarak kabul edilir.  
  
- Veri anlaşması türleri ( <xref:System.Runtime.Serialization.DataContractAttribute> özniteliğiyle işaretlenmiş türler).  
  
- Arabirimini uygulayan türler dahil <xref:System.SerializableAttribute> olmak üzere, özniteliğiyle işaretlenmiş türler. <xref:System.Runtime.Serialization.ISerializable>  
  
- <xref:System.Xml.Serialization.IXmlSerializable> Arabirimi uygulayan türler.  
  
- Birçok genel koleksiyon türü içeren birçok ortak koleksiyon türü.  
  
 Birçok .NET Framework türü, son iki kategoriye girer ve bu nedenle seri hale getirilebilir. Serileştirilebilir türlerin dizileri de seri hale getirilebilir. Tüm liste için bkz. [hizmet sözleşmeleri içinde veri aktarımı belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>Veri sözleşme türleriyle birlikte kullanılan, yeni WCF Hizmetleri yazmak için önerilen yoldur. Daha fazla bilgi için bkz. [Veri Sözleşmelerini Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
## <a name="when-to-use-the-xmlserializer-class"></a>XmlSerializer sınıfının ne zaman kullanılacağı  
 WCF Ayrıca <xref:System.Xml.Serialization.XmlSerializer> sınıfını da destekler. <xref:System.Xml.Serialization.XmlSerializer> Sınıf WCF için benzersiz değil. Bu, ASP.NET Web hizmetlerinin kullandığı serileştirme altyapısının aynısıdır. Sınıfı, <xref:System.Runtime.Serialization.DataContractSerializer> sınıftan çok daha dar bir tür kümesini destekler, ancak sonuçta elde edilen XML üzerinde çok daha fazla denetime izin verir ve XML şeması tanım dili (xsd) standardının çok daha fazlasını destekler. <xref:System.Xml.Serialization.XmlSerializer> Ayrıca, seri hale getirilebilir türlerde hiçbir bildirime dayalı öznitelik gerektirmez. Daha fazla bilgi için .NET Framework belgelerindeki XML serileştirme konusuna bakın. Sınıf <xref:System.Xml.Serialization.XmlSerializer> , veri anlaşması türlerini desteklemiyor.  
  
 Visual Studio 'da bir üçüncü taraf hizmeti için istemci kodu oluşturmak üzere Svcutil. exe ' yi veya **hizmet başvurusu Ekle** özelliğini kullanırken veya bir üçüncü taraf şemasına erişmek için, uygun bir seri hale getirici sizin için otomatik olarak seçilir. Şema ile <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Xml.Serialization.XmlSerializer> uyumlu değilse, seçilidir.  
  
## <a name="manually-switching-to-the-xmlserializer"></a>XmlSerializer 'a el ile geçiş  
 Her zaman, el ile geçiş <xref:System.Xml.Serialization.XmlSerializer>yapmanız gerekebilir. Bu durum örneğin, aşağıdaki durumlarda oluşur:  
  
- Bir uygulamayı ASP.NET Web hizmetlerinden WCF 'ye geçirirken, yeni veri anlaşması türleri oluşturmak yerine mevcut, <xref:System.Xml.Serialization.XmlSerializer>uyumlu türleri yeniden kullanmak isteyebilirsiniz.  
  
- İletilerde görüntülenen XML üzerinde kesin denetim önemli olduğunda, ancak bir Web Hizmetleri Açıklama Dili (WSDL) belgesi yoksa, örneğin belirli bir standartlaştırılmış, yayımlanmış bir şemaya uyum sağlamak üzere olan türler içeren bir hizmet oluştururken DataContractSerializer ile uyumlu değildir.  
  
- Eski SOAP kodlama standardını izleyen hizmetler oluştururken.  
  
 Bu ve diğer durumlarda, aşağıdaki kodda gösterildiği gibi, <xref:System.Xml.Serialization.XmlSerializer> `XmlSerializerFormatAttribute` özniteliğini hizmetinize uygulayarak sınıfa el ile geçiş yapabilirsiniz.  
  
 [!code-csharp[c_XmlSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#1)]
 [!code-vb[c_XmlSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#1)]  
  
## <a name="security-considerations"></a>Güvenlik Değerlendirmeleri  
  
> [!NOTE]
> Serileştirme altyapılarını değiştirirken dikkatli olmanız önemlidir. Aynı tür, kullanılmakta olan seri hale getiriciye göre farklı şekilde XML 'e serileştirilir. Yanlışlıkla yanlış seri hale getirici kullanıyorsanız, bu bilgilerin açığa çıkarmamasını istemediğiniz türden bilgileri kapatıyorsunuz olabilirsiniz.  
  
 Örneğin, <xref:System.Runtime.Serialization.DataContractSerializer> sınıfı yalnızca veri anlaşması türlerini serileştirilirken <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliği ile işaretlenmiş üyeleri seri hale getirir. <xref:System.Xml.Serialization.XmlSerializer> Sınıfı herhangi bir genel üyeyi seri hale getirir. Aşağıdaki kodda bulunan türe bakın.  
  
 [!code-csharp[c_XmlSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#2)]
 [!code-vb[c_XmlSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#2)]  
  
 Tür, <xref:System.Xml.Serialization.XmlSerializer> sınıfın seçildiği `creditCardNumber` bir hizmet sözleşmesinde yanlışlıkla kullanılırsa, üye serileştirilir, büyük olasılıkla hedeflenmemiştir.  
  
 Sınıf varsayılan olsa da, <xref:System.ServiceModel.DataContractFormatAttribute> özelliği hizmet sözleşmesi türüne uygulayarak hizmeti için açıkça seçebilirsiniz (bunu yapmanız hiçbir şekilde yapmanız gerekmese de). <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 Hizmet için kullanılan serileştirici, sözleşmenin ayrılmaz bir parçasıdır ve farklı bir bağlama seçilerek veya diğer yapılandırma ayarları değiştirilerek değiştirilemez.  
  
 <xref:System.Xml.Serialization.XmlSerializer> Sınıfına yönelik diğer önemli güvenlik konuları geçerlidir. İlk olarak, <xref:System.Xml.Serialization.XmlSerializer> sınıfını kullanan tüm WCF uygulamalarının, açıklanmasından korunmuş bir anahtarla imzalanmış olması önemle tavsiye edilir. Bu öneri her ikisi de için <xref:System.Xml.Serialization.XmlSerializer> el ile yapılan bir geçiş gerçekleştirildiğinde ve bir otomatik anahtar gerçekleştirildiğinde (Svcutil. exe, hizmet başvurusu Ekle veya benzer bir araçla) geçerlidir. Bunun nedeni, <xref:System.Xml.Serialization.XmlSerializer> serileştirme altyapısının uygulamayla aynı anahtarla İmzalandıkları sürece *önceden oluşturulmuş serileştirme derlemelerinin* yüklenmesini desteklemesinden kaynaklanır. İmzasız bir uygulama, uygulama klasörüne veya genel derleme önbelleğine yerleştirilmiş önceden oluşturulmuş serileştirme derlemesinin beklenen adıyla eşleşen kötü amaçlı bir derleme olasılığa karşı tamamen korumasız olur. Tabii ki, bu eylemi denemek için bir saldırganın öncelikle bu iki konumdan birine yazma erişimi edinilmesi gerekir.  
  
 Her <xref:System.Xml.Serialization.XmlSerializer> kullanışınızda, sistem geçici klasörüne yazma erişimiyle ilgili olan başka bir tehdit vardır. Serileştirme <xref:System.Xml.Serialization.XmlSerializer> altyapısı, bu klasörde geçici *serileştirme derlemeleri* oluşturur ve kullanır. Geçici klasöre yazma erişimi olan herhangi bir işlemin, bu serileştirme derlemelerinin kötü amaçlı kodla üzerine yazamayacağını bilmelisiniz.  
  
## <a name="rules-for-xmlserializer-support"></a>XmlSerializer desteği için kurallar  
 Anlaşma işlemi parametrelerine veya <xref:System.Xml.Serialization.XmlSerializer>dönüş değerlerine doğrudan uyumlu öznitelikleri uygulayamazsınız. Ancak, aşağıdaki kodda gösterildiği gibi, yazılı iletilere (ileti sözleşmesi gövde parçaları) uygulanabilirler.  
  
 [!code-csharp[c_XmlSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#3)]
 [!code-vb[c_XmlSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#3)]  
  
 Yazılı ileti üyelerine uygulandığında, bu öznitelikler yazılan ileti özniteliklerinde çakışan özellikleri geçersiz kılar. Örneğin, aşağıdaki kodda `ElementName` geçersiz kılmalar. `Name`  
  
 [!code-csharp[c_XmlSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_xmlserializer/cs/source.cs#4)]
 [!code-vb[c_XmlSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_xmlserializer/vb/source.vb#4)]  
  
 Özelliği kullanılırken özniteliği desteklenmez. <xref:System.Xml.Serialization.XmlSerializer> <xref:System.ServiceModel.MessageHeaderArrayAttribute>  
  
> [!NOTE]
> Bu durumda, <xref:System.Xml.Serialization.XmlSerializer> WCF 'den önce yayınlanan aşağıdaki özel durumu oluşturur: "Şemanın en üst düzeyinde tanımlanan bir öğe `maxOccurs` > 1 olamaz. ' More ' için veya `XmlArray` `XmlArrayItem` yerine `XmlElementAttribute`ya da Sarmalanan parametre stilini kullanarak ' More ' için bir sarmalayıcı öğesi sağlayın. "  
>   
>  Böyle bir özel durum alırsanız, bu durumun uygulanıp uygulanmadığını araştırın.  
  
 WCF, <xref:System.Xml.Serialization.SoapIncludeAttribute> ileti sözleşmeleri ve <xref:System.Runtime.Serialization.KnownTypeAttribute> işlem <xref:System.Xml.Serialization.XmlIncludeAttribute> sözleşmeleri içindeki ve özniteliklerini desteklemez; bunun yerine özniteliğini kullanın.  
  
## <a name="types-that-implement-the-ixmlserializable-interface"></a>IXmlSerializable arabirimini uygulayan türler  
 `IXmlSerializable` Arabirimini uygulayan türler `DataContractSerializer`tarafından tamamen desteklenir. Bu türlerin şemasını denetlemek için özniteliğiherzamanbutürlereuygulanmalıdır.<xref:System.Xml.Serialization.XmlSchemaProviderAttribute>  
  
> [!WARNING]
>  Polimorfik türler serileştirilmiş olmanız durumunda doğru <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> türün serileştirildiğinden emin olmak için türünü türüne uygulamanız gerekir.  
  
 Şunları uygulayan `IXmlSerializable`tür üç değişken vardır: rastgele içeriği temsil eden türler, tek bir öğeyi temsil eden türler ve eski <xref:System.Data.DataSet> türler.  
  
- İçerik türleri `XmlSchemaProviderAttribute` özniteliği tarafından belirtilen bir şema sağlayıcısı yöntemini kullanır. Yöntemi döndürmez `null` <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> ve özniteliğinde özelliği varsayılan değerinde `false`bırakılır. Bu, `IXmlSerializable` türlerin en yaygın kullanımdır.  
  
- Öğe türleri, bir `IXmlSerializable` türün kendi kök öğe adını denetlemesini gerektiğinde kullanılır. Bir türü öğe türü <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> olarak işaretlemek için, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> öznitelik `true` üzerinde özelliğini, şema sağlayıcısı yönteminden veya geri dönüş `null` olarak ayarlayın. Bir şema sağlayıcısı yönteminin olması, `null` `XmlSchemaProviderAttribute`öğe türleri için isteğe bağlıdır; içinde Yöntem adı yerine belirtebilirsiniz. Ancak, ve bir şema sağlayıcısı yöntemi belirtilmişse, Yöntemi döndürmelidir `null`. `IsAny` `true`  
  
- Eski <xref:System.Data.DataSet> türler, `IXmlSerializable` özniteliğiyleişaretlenmemiştürlerdir.`XmlSchemaProviderAttribute` Bunun yerine, şema oluşturma <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> yöntemine bağlıdır. Bu model, `DataSet` türü için kullanılır ve türü belirtilmiş veri kümesi .NET Framework önceki sürümlerinde bir sınıf türetiliyor, ancak artık kullanılmıyor ve yalnızca eski nedenlerden dolayı destekleniyor. Bu modele güvenmeyin ve her zaman `XmlSchemaProviderAttribute` `IXmlSerializable` türlerinizi uygulayın.  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable Içerik türleri  
 , Uygulayan `IXmlSerializable` ve daha önce tanımlanan bir içerik türü olan bir veri üyesini serileştirilirken, serileştirici veri üyesine yönelik sarmalayıcı öğesini yazar ve denetimi <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemine geçirir. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama, sarmalayıcı öğesine öznitelik eklemeyi içeren herhangi bir XML yazabilir. İşlem `WriteXml` tamamlandıktan sonra seri hale getirici öğeyi kapatır.  
  
 Uygulayan `IXmlSerializable` ve daha önce tanımlanan bir içerik türü olan bir veri üyesinin serisi kaldırılırken, seri hale getirici veri üyesine yönelik sarmalayıcı öğesinde XML okuyucuyu konumlandırır ve denetimi <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> yöntemine geçirir. Yöntemi, başlangıç ve bitiş etiketleri dahil olmak üzere tüm öğeyi okumalı olmalıdır. `ReadXml` Kodunuzun, öğenin boş olduğu durumu işlediğinizden emin olun. Ayrıca, `ReadXml` uygulamanız belirli bir şekilde adlandırılan sarmalayıcı öğesine dayanmamalıdır. Seri hale getirici tarafından seçilen ad değişiklik gösterebilir.  
  
 Örneğin, türündeki <xref:System.Object>veri üyelerine `IXmlSerializable` polymorphically içerik türleri atama izni verilir. Tür örneklerinin null olması de buna izin verilir. Son olarak, türleri nesne Graph koruması `IXmlSerializable` etkin ve <xref:System.Runtime.Serialization.NetDataContractSerializer>ile birlikte kullanmak mümkündür. Tüm bu özellikler, WCF serileştiricinin belirli öznitelikleri sarmalayıcı öğesine ("Nil" ve "tür" i XML şema örneği ad alanında ve "ID", "ref", "Type" ve "Assembly" adlı WCF 'ye özgü bir ad alanında) iliştirmesini gerektirir.  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml 'i uygularken yoksayılacak öznitelikler  
 `ReadXml` Kodu kodunuza geçirmeden önce seri hale getirici XML öğesini inceler, bu özel XML özniteliklerini algılar ve üzerinde davranır. Örneğin, "Nil" ise `true`, null değeri seri durumdan çıkarılmış olur ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, öğesinin içeriği farklı türde gibi seri durumdan çıkarılacak. Polymorphically tarafından atanan türün uygulamasının uygulamasına `ReadXml` denir. Herhangi bir durumda, bir `ReadXml` uygulama, seri hale getirici tarafından işlendiği için bu özel öznitelikleri yoksaymalıdır.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable Içerik türleri için şema konuları  
 Şema ve `IXmlSerializable` içerik türü dışarı aktarılırken, şema sağlayıcısı yöntemi çağırılır. <xref:System.Xml.Schema.XmlSchemaSet> Şema sağlayıcısı yöntemine geçirilir. Yöntemi, şema kümesine geçerli bir şema ekleyebilir. Şema kümesi, şema dışa aktarma gerçekleştiği sırada zaten bilinen şemayı içerir. Şema sağlayıcısı yönteminin şema kümesine bir öğe eklemesi gerektiğinde, uygun ad alanı ile birlikte bir <xref:System.Xml.Schema.XmlSchema> öğesinin küme içinde olup olmadığını belirlemesi gerekir. Varsa, şema sağlayıcısı yönteminin yeni öğeyi mevcut `XmlSchema`öğesine eklemesi gerekir. Aksi halde, yeni `XmlSchema` bir örnek oluşturması gerekir. Bu, `IXmlSerializable` tür dizileri kullanılıyorsa önemlidir. Örneğin, "b" ad alanında `IXmlSerializable` "A" türü olarak verilen bir tür varsa, şema sağlayıcısı yönteminin adı, şema kümesi "b" için "ArrayOfA" türünü tutmak için şemayı zaten içeriyor olabilir.  
  
 Türüne tür <xref:System.Xml.Schema.XmlSchemaSet>eklemenin yanı sıra, içerik türleri için şema sağlayıcısı yöntemi null olmayan bir değer döndürmelidir. <xref:System.Xml.XmlQualifiedName> Verilen`IXmlSerializable` tür için kullanılacak şema türünün adını belirten bir döndürebilir. Bu tam ad ayrıca tür için veri anlaşması adı ve ad alanı olarak da kullanılır. Şema sağlayıcısı yöntemi döndürüldüğünde, şema kümesinde varolmayan bir tür döndürebilir. Ancak, tüm ilişkili türlerin verildiği zaman tarafından ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi ' <xref:System.Runtime.Serialization.XsdDataContractExporter> de tüm ilgili türler için çağrılır ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliğine erişilir), tür şema kümesinde bulunur. <xref:System.Xml.Schema.XmlSchemaException>Tüm ilgili `Export` çağrılar yapılmadan önce özelliğeerişilmesi`Schemas` bir ile sonuçlanabilir. Dışarı aktarma işlemi hakkında daha fazla bilgi için bkz. [sınıflardan şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Şema sağlayıcısı yöntemi kullanmak <xref:System.Xml.Schema.XmlSchemaType> için ' i de döndürebilir. Tür anonim olmayabilir veya olmayabilir. Anonim ise, tür şeması `IXmlSerializable` bir veri üyesi olarak her `IXmlSerializable` kullanıldığında anonim bir tür olarak verilir. `IXmlSerializable` Türün hala bir veri anlaşması adı ve ad alanı vardır. (Bu, ad özelleştirmek için özniteliğin kullanılamaz olması dışında, <xref:System.Runtime.Serialization.DataContractAttribute> [veri anlaşması adlarında](../../../../docs/framework/wcf/feature-details/data-contract-names.md) açıklandığı şekilde belirlenir.) Anonim değilse, içindeki `XmlSchemaSet`türlerden biri olmalıdır. Bu durum, `XmlQualifiedName` türünün döndürülmesi ile eşdeğerdir.  
  
 Ayrıca, genel bir öğe bildirimi tür için verilir. Türün <xref:System.Xml.Serialization.XmlRootAttribute> kendisine uygulanan özniteliği yoksa, öğesi veri sözleşmesiyle aynı ada ve ad alanına sahiptir ve "boş bırakılabilir" özelliği olur `true`. Bunun tek istisnası şema ad alanıdır (`http://www.w3.org/2001/XMLSchema`): türün veri sözleşmesi bu ad alanında yer alıyorsa, ilgili genel öğe, şema ad alanına yeni öğeler eklemek yasak olduğundan boş ad alanıdır. Türe `XmlRootAttribute` uygulanmış özniteliği varsa, genel öğe bildirimi aşağıdaki <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> : <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>ve <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> özellikleri kullanılarak verilir. `XmlRootAttribute` Uygulanan varsayılanlar, veri sözleşmesinin adı, boş bir ad alanı ve "boş bırakılabilir `true`" olur.  
  
 Aynı genel öğe bildirimi kuralları eski veri kümesi türleri için de geçerlidir. Özel kod aracılığıyla eklenen genel öğe bildirimlerinin geçersiz `XmlSchemaSet` `GetSchema` kılınmadığını, şema sağlayıcısı yöntemi kullanılarak veya eski veri kümesi türleri için aracılığıyla geçersiz kılabileceğini unutmayın. `XmlRootAttribute`  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri  
 `IXmlSerializable`öğe türlerinde, `IsAny` özelliği olarak `true` ayarlanmış ya da şema sağlayıcısı yöntemi döndürüyor `null`.  
  
 Öğe türünü serileştirmek ve serisini kaldırma, içerik türünü serileştirmek ve seri durumdan çıkarmak için çok benzerdir. Ancak bazı önemli farklılıklar vardır:  
  
- `WriteXml` Uygulamanın tam olarak bir öğe yazması bekleniyordu (kuşkusuz birden çok alt öğe içerebilir). Bu tek öğe, birden çok eşdüzey öğe veya karışık içerik dışında öznitelikleri yazmamalıdır. Öğe boş olabilir.  
  
- `ReadXml` Uygulama sarmalayıcı öğesini okumalı olmalıdır. `WriteXml` Üreten bir öğeyi okuması beklenmektedir.  
  
- Öğe türü düzenli olarak serileştirilirken (örneğin, bir veri sözleşmesindeki veri üyesi olarak), seri hale getirici, içerik türlerinde olduğu gibi çağrılmadan `WriteXml`önce bir sarmalayıcı öğesi verir. Ancak, üst düzeyde bir öğe türü serileştirilirken, seri hale getirici normalde bir sarmalayıcı öğesinde `WriteXml` yazma öğesi, bir kök adı ve ad alanı, içinde serileştirici oluşturulurken açıkça belirtilmediği takdirde `DataContractSerializer` veya`NetDataContractSerializer` oluşturucuları. Daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
- Yapılandırma zamanında <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> kök adı ve ad alanını belirtmeden en üst düzeyde bir öğe türü serileştirilirken ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> temelde hiçbir şey ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> çağrı `WriteXml`yapmaksızın. Bu modda, serileştirilmekte `null` olan nesne olamaz ve polymorphically atanamaz. Ayrıca, nesne grafiği koruması etkinleştirilemez ve `NetDataContractSerializer` kullanılamaz.  
  
- Yapılandırma sırasında kök adı ve ad alanını belirtmeden en üst düzeyde bir öğe türü seri durumdan çıkarılırken, herhangi bir <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> öğenin `true` başlangıcını bulabiliyorsanız ' ı döndürür. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>parametresi, nesne gerçekten `IsStartObject` okunmadan önce ile aynı şekilde davranır.`true` `verifyObjectName` `ReadObject`sonra denetimi `ReadXml` yöntemine geçirir.  
  
 Öğe türleri için aktarılmış şema, şema sağlayıcısı yönteminin içerik türleriyle `XmlElement` <xref:System.Xml.Schema.XmlSchemaSet> olduğu gibi ek bir şema ekleyebildiğinden, daha önceki bir bölümde açıklanan tür ile aynıdır. `XmlRootAttribute` Özniteliğin öğe türleriyle kullanılmasına izin verilmez ve genel öğe bildirimleri bu türler için hiçbir şekilde yayılmaz.  
  
### <a name="differences-from-the-xmlserializer"></a>XmlSerializer 'ın farkları  
 `IXmlSerializable` Arabirimi`XmlSchemaProviderAttribute` ve ve`XmlRootAttribute` öznitelikleri de tarafından<xref:System.Xml.Serialization.XmlSerializer> anlaşılamalıdır. Bununla birlikte, bunların veri anlaşması modelinde nasıl ele alınların bazı farklılıkları vardır. Önemli farklılıklar aşağıdaki listede özetlenmiştir:  
  
- Şema sağlayıcısı yönteminin `XmlSerializer`' de kullanılabilmesi için genel olması gerekir, ancak veri sözleşmesi modelinde kullanılabilmesi için genel olması gerekmez.  
  
- Şema sağlayıcısı yöntemi, veri anlaşması modelinde `IsAny` olduğunda `true` çağrılır, `XmlSerializer`ancak ile değil.  
  
- İçerik veya eski veri kümesi türleri `XmlSerializer` için öznitelikmevcutolmadığında,boşadalanındagenelbiröğebildiriminidışarıaktarır.`XmlRootAttribute` Veri anlaşması modelinde, kullanılan ad alanı normalde daha önce açıklandığı gibi veri sözleşmesi ad alanıdır.  
  
 Serileştirme teknolojileriyle birlikte kullanılan türler oluşturulurken bu farklılıklara dikkat edin.  
  
### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable şeması içeri aktarılıyor  
 `IXmlSerializable` Türlerden oluşturulan bir şemayı içeri aktarırken birkaç olasılık vardır:  
  
- Oluşturulan şema, [veri sözleşmesi şema başvurusunda](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)açıklandığı gibi geçerli bir veri anlaşması şeması olabilir. Bu durumda, her zamanki gibi şema içeri aktarılabilir ve normal veri anlaşması türleri oluşturulur.  
  
- Oluşturulan şema geçerli bir veri anlaşması şeması olmayabilir. Örneğin, şema sağlayıcınız yönteminiz, veri anlaşması modelinde desteklenmeyen XML özniteliklerini içeren bir şema üretebilir. Bu durumda, şemayı türler olarak `IXmlSerializable` içeri aktarabilirsiniz. Bu içeri aktarma modu varsayılan olarak açık değildir, ancak örneğin, `/importXmlTypes` [ServiceModel meta veri yardımcı programı aracına (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)komut satırı anahtarı ile birlikte kolayca etkinleştirilebilir. Bu, [sınıfları oluşturmak Için Içeri aktarma şemasında](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md)ayrıntılı olarak açıklanmıştır. Doğrudan tür örneklerinizin XML ile birlikte çalışmanız gerektiğini unutmayın. Ayrıca, `XmlSerializer`daha geniş bir şema aralığını destekleyen farklı bir serileştirme teknolojisi kullanmayı da düşünebilirsiniz; bkz. kullanma konusu.  
  
- Mevcut `IXmlSerializable` türlerinizi yeni bir oluşturma yerine proxy 'de yeniden kullanmak isteyebilirsiniz. Bu durumda, tür oluşturmak için şemayı Içeri aktarma konu başlığı altında açıklanan Başvurulmuş türler özelliği, yeniden kullanılacak türü belirtmek için kullanılabilir. Bu, yeniden kullanılacak türleri `/reference` içeren derlemeyi belirten Svcutil. exe ' de anahtarı kullanmaya karşılık gelir.  
  
### <a name="xmlserializer-legacy-behavior"></a>XmlSerializer eski davranışı  
 .NET Framework 4,0 ve önceki sürümlerde XmlSerializer, bir dosyaya kod yazarak C# geçici serileştirme derlemeleri oluşturdu. Dosya daha sonra bir derlemeye derlendi.  Bu davranış, serileştiricinin başlama süresini yavaşlatarak bazı istenmeyen sonuçlara sahipti. .NET Framework 4,5 ' de, bu davranış derleyicinin kullanılmasına gerek kalmadan derlemeleri oluşturmak üzere değiştirilmiştir. Bazı geliştiriciler oluşturulan C# kodu görmek isteyebilir. Aşağıdaki yapılandırmayla bu eski davranışı kullanmayı belirtebilirsiniz:  
  
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
  
 Türetilmiş bir sınıfı genel olmayan yeni bir geçersiz kılma ile `XmlSerializer` seri hale getirmek başarısız gibi uyumluluk sorunları yaşıyorsanız, aşağıdaki yapılandırmayı kullanarak `XMLSerializer` eski davranışa geri dönebilirsiniz:  
  
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
> `<xmlSerializer useLegacySerializerGeneration="true"/>` Anahtar yalnızca .NET Framework 4,5 veya üzeri bir sürümü çalıştıran bir makinede çalışır. Yukarıdaki `appSettings` yaklaşım tüm .NET Framework sürümlerinde geçerlidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.ServiceModel.DataContractFormatAttribute>
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.XmlSerializer>
- <xref:System.ServiceModel.MessageHeaderArrayAttribute>
- [Hizmet Anlaşmalarında Veri Aktarımını Belirtme](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Nasıl yapılır: XmlSerializer kullanarak WCF Istemci uygulamalarının başlama süresini geliştirme](../../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md)
