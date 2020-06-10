---
title: Veri Sözleşmelerinde XML ve ADO.NET Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 975d4f4f37bbbd895cab4e87686f15017e90f382
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600081"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Veri Sözleşmelerinde XML ve ADO.NET Türleri
Windows Communication Foundation (WCF) veri anlaşması modeli, XML 'i doğrudan temsil eden belirli türleri destekler. Bu türler XML 'e serileştirildiğinde seri hale getirici bu türlerin XML içeriğini başka bir işlem olmadan yazar. Desteklenen türler <xref:System.Xml.XmlElement> , <xref:System.Xml.XmlNode> (türünün kendisi değil değil) dizilerinin ve `XmlNode` uygulayan türler <xref:System.Xml.Serialization.IXmlSerializable> . <xref:System.Data.DataSet>Ve <xref:System.Data.DataTable> türü ve türü belirtilmiş veri kümeleri, veritabanı programlamasında yaygın olarak kullanılır. Bu türler arabirimini uygular `IXmlSerializable` ve bu nedenle veri sözleşmesi modelinde seri hale getirilebilir. Bu türlere ilişkin bazı özel noktalar, konunun sonunda listelenmiştir.  
  
## <a name="xml-types"></a>XML türleri  
  
### <a name="xml-element"></a>XML öğesi  
 `XmlElement`Türü, XML içerikleri kullanılarak serileştirilir. Örneğin, aşağıdaki türü kullanma.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 Bu, XML 'e aşağıdaki şekilde serileştirilir:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Sarmalayıcı veri üyesi öğesinin hala mevcut olduğuna dikkat edin `<myDataMember>` . Bu öğeyi veri sözleşmesi modelinde kaldırmanın bir yolu yoktur. Bu modeli işleyen serileştiriciler ( <xref:System.Runtime.Serialization.DataContractSerializer> ve), <xref:System.Runtime.Serialization.NetDataContractSerializer> Bu sarmalayıcı öğesine özel öznitelikler yayabilir. Bu öznitelikler, standart XML şema örneği "Nil" özniteliği ( `XmlElement` to to a izin verir `null` ) ve "Type" özniteliği ( `XmlElement` polymorphically kullanılmasına izin veriliyor) içerir. Ayrıca, aşağıdaki XML öznitelikleri WCF 'ye özgüdür: "ID", "ref", "Type" ve "Assembly". Bu öznitelikler, `XmlElement` nesne grafiği koruma modu etkin veya ile kullanılarak kullanılarak desteklemek için kullanılabilir <xref:System.Runtime.Serialization.NetDataContractSerializer> . (Nesne grafiği koruma modu hakkında daha fazla bilgi için bkz. [serileştirme ve serisini kaldırma](serialization-and-deserialization.md).)  
  
 Dizilerine veya koleksiyonlara `XmlElement` izin verilir ve diğer herhangi bir dizi veya koleksiyon olarak işlenir. Diğer bir deyişle, tüm koleksiyon için bir sarmalayıcı öğe ve dizideki her biri için ayrı bir sarmalayıcı öğesi ( `<myDataMember>` Önceki örnekte olduğu gibi) vardır `XmlElement` .  
  
 Seri durumdan çıkarma sırasında, `XmlElement` gelen XML 'den seri hale getirici tarafından oluşturulur. <xref:System.Xml.XmlDocument>Seri hale getirici, geçerli bir üst öğe tarafından sağlanır.  
  
 Seri durumdan çıkarılmış XML parçasının `XmlElement` kullandığı tüm önekleri tanımladığından ve üst öğelerden herhangi bir önek tanımına dayanmadığından emin olun. Bu, yalnızca, `DataContractSerializer` farklı bir kaynaktan XML 'e erişmek için ' i kullanırken sorun olur `DataContractSerializer` .  
  
 İle kullanıldığında, `DataContractSerializer` `XmlElement` polymorphically atanabilir, ancak yalnızca türünde bir veri üyesi olabilir <xref:System.Object> . Uygulasa da <xref:System.Collections.IEnumerable> , bir `XmlElement` koleksiyon türü olarak kullanılamaz ve bir <xref:System.Collections.IEnumerable> veri üyesine atanamaz. Tüm polimorfik atamalarında olduğu gibi, `DataContractSerializer` sonuçta elde EDILEN XML 'de veri sözleşme adını yayar; bu durumda, " http://schemas.datacontract.org/2004/07/System.Xml " ad alanında "XmlElement" olur.  
  
 İle `NetDataContractSerializer` tüm geçerli Polimorfik Atama `XmlElement` ( `Object` veya `IEnumerable` ) desteklenir.  
  
 Polymorphically atanıp atanmayacağı, öğesinden türetilmiş türler ile serileştiricilerin birini kullanmayı denemeyin `XmlElement` .  
  
### <a name="array-of-xmlnode"></a>XmlNode dizisi  
 Dizilerinin kullanılması <xref:System.Xml.XmlNode> , kullanılmasına çok benzer `XmlElement` . Dizilerinin kullanılması `XmlNode` , kullanmaktan daha fazla esneklik sağlar `XmlElement` . Veri üyesi sarmalama öğesi içinde birden çok öğe yazabilirsiniz. Ayrıca, XML açıklamaları gibi veri üyesi sarmalama öğesi içindeki öğelerden başka içerik de ekleyebilirsiniz. Son olarak, öznitelikleri sarmalama verileri üye öğesine yerleştirebilirsiniz. Tüm bunlar `XmlNode` , veya gibi belirli türetilmiş sınıflarla dizisini doldurarak elde edilebilir `XmlNode` <xref:System.Xml.XmlAttribute> `XmlElement` <xref:System.Xml.XmlComment> . Örneğin, aşağıdaki türü kullanma.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Serileştirilmiş olduğunda, elde edilen XML aşağıdaki koda benzer.  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
  <myDataMember myAttribute="myValue">  
     <!--myComment-->  
     <myElement xmlns="" myAttribute="myValue">  
 myContents  
     </myElement>  
     <myElement xmlns="" myAttribute="myValue">  
       myContents  
     </myElement>  
  </myDataMember>  
</MyDataContract>  
```  
  
 Veri üyesi sarmalayıcı öğesinin `<myDataMember>` bir öznitelik, açıklama ve iki öğe içerdiğini unutmayın. Bunlar `XmlNode` seri hale getirilen dört örneklerdir.  
  
 `XmlNode`GEÇERSIZ XML ile sonuçlanan bir dizi seri hale getirilemez. Örneğin, ilk diğeri bir olan iki örneğin bir dizisi, `XmlNode` ikinci bir, `XmlElement` GEÇERLI bir <xref:System.Xml.XmlAttribute> XML örneğine karşılık gelmediğinden (özniteliği iliştirmek için bir yer yoktur).  
  
 Bir dizisinin serisini kaldırma sırasında `XmlNode` düğümler oluşturulur ve gelen XML 'deki bilgilerle doldurulur. <xref:System.Xml.XmlDocument>Seri hale getirici, geçerli bir üst öğe tarafından sağlanır. Sarmalayıcı veri üyesi öğesindeki tüm öznitelikler de dahil olmak üzere tüm düğümlerin serisi kaldırılır, ancak WCF serileştiricileri (Polimorfik atamayı göstermek için kullanılan öznitelikler gibi) bu öznitelikleri hariç tutulur. XML parçasındaki tüm ad alanı öneklerini tanımlama hakkında desteklenmediği uyarısıyla, serisini kaldırmada olduğu gibi dizilerinin serisini kaldırma için geçerlidir `XmlNode` `XmlElement` .  
  
 Nesne grafiği koruması açık olan serileştiriciler kullanılırken, nesne eşitlik yalnızca `XmlNode` ayrı örneklere değil diziler düzeyinde korunur `XmlNode` .  
  
 `XmlNode`Bir veya daha fazla düğümün ayarlandığı bir diziyi seri hale getirme girişiminde bulunuldu `null` . Dizi üyesinin tamamına `null` , dizide yer alan herhangi bir kişi için izin verilmez `XmlNode` . Tüm dizi üyesi null ise sarmalayıcı veri üyesi öğesi, null olduğunu belirten özel bir öznitelik içerir. Seri durumdan çıkarma sırasında, tüm dizi üyesi de null olur.  
  
 Yalnızca normal dizileri `XmlNode` seri hale getirici tarafından özel olarak değerlendirilir. `XmlNode`Veya ' den türetilen türlerin dizileri olarak belirtilen veri üyelerini içeren diğer koleksiyon türleri olarak belirtilen veri üyeleri `XmlNode` özel olarak değerlendirilmez. Bu nedenle, normal olarak serileştirilmek üzere diğer ölçütlerden birini karşılamadığında seri hale getirilebilir değildir.  
  
 Dizi dizilerine veya dizilerinin koleksiyonuna `XmlNode` izin verilir. Tüm koleksiyon için bir sarmalayıcı öğe ve `<myDataMember>` `XmlNode` dış dizi ya da koleksiyonda bulunan her bir dizi için ayrı bir sarmalayıcı öğe (önceki örnekte olduğu gibi) vardır.  
  
 Ya da türündeki bir veri üyesini <xref:System.Array> `Object` `Array` `IEnumerable` `XmlNode` örnek olarak doldurmak, veri üyesinin örnek olarak değerlendirilmesiyle sonuçlanır `Array` `XmlNode` . Her dizi üyesi ayrı olarak serileştirilir.  
  
 İle kullanıldığında `DataContractSerializer` , dizilerinin dizileri `XmlNode` polymorphically atanabilir, ancak yalnızca türünde bir veri üyesi olabilir `Object` . Uygulayan olsa da `IEnumerable` , bir dizisi `XmlNode` bir koleksiyon türü olarak kullanılamaz ve bir `IEnumerable` veri üyesine atanamaz. Tüm polimorfik atamalarında olduğu gibi, `DataContractSerializer` sonuçta elde EDILEN XML 'de veri sözleşme adını yayar; bu durumda, " http://schemas.datacontract.org/2004/07/System.Xml " ad alanında "ArrayOfXmlNode" olur. İle kullanıldığında `NetDataContractSerializer` , bir dizinin geçerli atama `XmlNode` desteklenir.  
  
### <a name="schema-considerations"></a>Şema konuları  
 XML türlerinin şema eşlemesi hakkında daha fazla bilgi için bkz. [veri sözleşmesi şema başvurusu](data-contract-schema-reference.md). Bu bölüm, önemli noktaların özetini sağlar.  
  
 Türündeki bir veri üyesi, `XmlElement` aşağıdaki anonim tür kullanılarak tanımlanan bir öğeyle eşlenir.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Dizi türünde bir veri üyesi, `XmlNode` aşağıdaki anonim tür kullanılarak tanımlanan bir öğeyle eşlenir.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>IXmlSerializable arabirimini uygulayan türler  
 Arabirimini uygulayan türler `IXmlSerializable` tarafından tamamen desteklenir `DataContractSerializer` . <xref:System.Xml.Serialization.XmlSchemaProviderAttribute>Bu türlerin şemasını denetlemek için özniteliği her zaman bu türlere uygulanmalıdır.  
  
 Şunları uygulayan tür üç değişken vardır `IXmlSerializable` : rastgele içeriği temsil eden türler, tek bir öğeyi temsil eden türler ve eski <xref:System.Data.DataSet> türler.  
  
- İçerik türleri özniteliği tarafından belirtilen bir şema sağlayıcısı yöntemini kullanır `XmlSchemaProviderAttribute` . Yöntemi döndürmez `null` ve <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> özniteliğinde özelliği varsayılan değerinde bırakılır `false` . Bu, türlerin en yaygın kullanımdır `IXmlSerializable` .  
  
- Öğe türleri, bir `IXmlSerializable` türün kendi kök öğe adını denetlemesini gerektiğinde kullanılır. Bir türü öğe türü olarak işaretlemek için, <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> öznitelik üzerinde özelliğini <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> olarak ayarlayın `true` veya şema sağlayıcısı yönteminden null döndürün. Bir şema sağlayıcısı yönteminin olması, öğe türleri için isteğe bağlıdır; içinde Yöntem adı yerine null belirtebilirsiniz `XmlSchemaProviderAttribute` . Ancak, `IsAny` `true` ve bir şema sağlayıcısı yöntemi belirtilmişse, yöntemi null döndürmelidir.  
  
- Eski <xref:System.Data.DataSet> türler `IXmlSerializable` , özniteliğiyle işaretlenmemiş türlerdir `XmlSchemaProviderAttribute` . Bunun yerine, <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> şema oluşturma yöntemine bağlıdır. Bu model, türü için kullanılır `DataSet` ve türü belirtilmiş veri kümesi .NET Framework önceki sürümlerinde bir sınıf türetiliyor, ancak artık kullanılmıyor ve yalnızca eski nedenlerden dolayı destekleniyor. Bu modele güvenmeyin ve her zaman `XmlSchemaProviderAttribute` `IXmlSerializable` türlerinizi uygulayın.  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable Içerik türleri  
 `IXmlSerializable`' İ uygulayan ve daha önce tanımlanan bir içerik türü olan bir veri üyesini serileştirilirken, serileştirici veri üyesine yönelik sarmalayıcı öğesini yazar ve yöntemine denetimi geçer <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> . <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>Uygulama sarmalayıcı öğesine öznitelik ekleme dahil olmak üzere herhangi BIR XML yazabilir. İşlem tamamlandıktan sonra `WriteXml` seri hale getirici öğeyi kapatır.  
  
 `IXmlSerializable`' İ uygulayan ve daha önce tanımlanan bir içerik türü olan bir veri üyesinin serisi kaldırılırken, seri hale getirici veri üyesine yönelik sarmalayıcı ÖĞESINDE XML okuyucuyu konumlandırır ve metoduna denetimi geçer <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> . Yöntemi, başlangıç ve bitiş etiketleri dahil olmak üzere tüm öğeyi okumalı olmalıdır. `ReadXml`Kodunuzun, öğenin boş olduğu durumu işlediğinizden emin olun. Ayrıca, `ReadXml` uygulamanız belirli bir şekilde adlandırılan sarmalayıcı öğesine dayanmamalıdır. Seri hale getirici tarafından seçilen ad değişiklik gösterebilir.  
  
 `IXmlSerializable`Örneğin, türündeki veri üyelerine polymorphically içerik türleri atama izni verilir <xref:System.Object> . Tür örneklerinin null olması de buna izin verilir. Son olarak, `IXmlSerializable` türleri nesne Graph koruması etkin ve ile birlikte kullanmak mümkündür <xref:System.Runtime.Serialization.NetDataContractSerializer> . Tüm bu özellikler, WCF serileştiricinin belirli öznitelikleri sarmalayıcı öğesine ("Nil" ve "tür" i XML şema örneği ad alanında ve "ID", "ref", "Type" ve "Assembly" adlı WCF 'ye özgü bir ad alanında) iliştirmesini gerektirir.  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml 'i uygularken yoksayılacak öznitelikler  
 `ReadXml`Kodu kodunuza geçirmeden önce seri hale GETIRICI XML öğesini inceler, bu özel XML özniteliklerini algılar ve üzerinde davranır. Örneğin, "Nil" ise, `true` null değeri seri durumdan çıkarılmış olur ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, öğesinin içeriği farklı türde gibi seri durumdan çıkarılacak. Polymorphically atanmış türünün uygulamasının uygulamasına `ReadXml` denir. Herhangi bir durumda, bir `ReadXml` uygulama, seri hale getirici tarafından işlendiği için bu özel öznitelikleri yoksaymalıdır.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable Içerik türleri için şema konuları  
 Şemayı bir `IXmlSerializable` içerik türü dışa aktarırken, şema sağlayıcısı yöntemi çağırılır. <xref:System.Xml.Schema.XmlSchemaSet>Şema sağlayıcısı yöntemine geçirilir. Yöntemi, şema kümesine geçerli bir şema ekleyebilir. Şema kümesi, şema dışa aktarma gerçekleştiği sırada zaten bilinen şemayı içerir. Şema sağlayıcısı yönteminin şema kümesine bir öğe eklemesi gerektiğinde, <xref:System.Xml.Schema.XmlSchema> küme içinde uygun ad alanı ile bir sahip olup olmadığını belirlemesi gerekir. Varsa, şema sağlayıcısı yönteminin yeni öğeyi mevcut öğesine eklemesi gerekir `XmlSchema` . Aksi halde, yeni bir örnek oluşturması gerekir `XmlSchema` . Bu, tür dizileri kullanılıyorsa önemlidir `IXmlSerializable` . Örneğin, " `IXmlSerializable` b" ad alanında "A" türü olarak verilen bir tür varsa, şema sağlayıcısı yönteminin adı, şema kümesi "b" için "ArrayOfA" türünü tutmak için şemayı zaten içeriyor olabilir.  
  
 Türüne tür eklemenin yanı sıra <xref:System.Xml.Schema.XmlSchemaSet> , içerik türleri için şema sağlayıcısı yöntemi null olmayan bir değer döndürmelidir. <xref:System.Xml.XmlQualifiedName>Verilen tür için kullanılacak şema türünün adını belirten bir döndürebilir `IXmlSerializable` . Bu tam ad ayrıca tür için veri anlaşması adı ve ad alanı olarak da kullanılır. Şema sağlayıcısı yöntemi döndürüldüğünde, şema kümesinde varolmayan bir tür döndürebilir. Ancak, tüm ilişkili türlerin verildiği zaman tarafından ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi ' de tüm ilgili türler için çağrılır <xref:System.Runtime.Serialization.XsdDataContractExporter> ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliğine erişilir), tür şema kümesinde bulunur. `Schemas`Tüm ilgili çağrılar yapılmadan önce özelliğe erişilmesi `Export` bir ile sonuçlanabilir <xref:System.Xml.Schema.XmlSchemaException> . Dışarı aktarma işlemi hakkında daha fazla bilgi için bkz. [sınıflardan şemaları dışarı aktarma](exporting-schemas-from-classes.md).  
  
 Şema sağlayıcısı yöntemi kullanmak için ' i de döndürebilir <xref:System.Xml.Schema.XmlSchemaType> . Tür anonim olmayabilir veya olmayabilir. Anonim ise, tür şeması `IXmlSerializable` `IXmlSerializable` bir veri üyesi olarak her kullanıldığında anonim bir tür olarak verilir. `IXmlSerializable`Türün hala bir veri anlaşması adı ve ad alanı vardır. (Bu, ad özelleştirmek için özniteliğin kullanılamaz olması dışında, [veri anlaşması adlarında](data-contract-names.md) açıklandığı şekilde belirlenir <xref:System.Runtime.Serialization.DataContractAttribute> .) Anonim değilse, içindeki türlerden biri olmalıdır `XmlSchemaSet` . Bu durum, türünün döndürülmesi ile eşdeğerdir `XmlQualifiedName` .  
  
 Ayrıca, genel bir öğe bildirimi tür için verilir. Türün <xref:System.Xml.Serialization.XmlRootAttribute> kendisine uygulanan özniteliği yoksa, öğesi veri sözleşmesiyle aynı ada ve ad alanına sahiptir ve "boş bırakılabilir" özelliği doğru olur. Bunun tek istisnası şema ad alanıdır (" http://www.w3.org/2001/XMLSchema ") – türün veri anlaşması bu ad alanında yer alıyorsa, ilgili genel öğe boş ad alanıdır, çünkü şema ad alanına yeni öğe eklenemez. Türe `XmlRootAttribute` uygulanmış özniteliği varsa, genel öğe bildirimi aşağıdaki: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A> <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> ve özellikleri kullanılarak verilir <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> . `XmlRootAttribute`Uygulanan varsayılanlar, veri sözleşmesinin adıdır, boş bir ad alanıdır ve "boş bırakılabilir" değeri true olur.  
  
 Aynı genel öğe bildirimi kuralları eski veri kümesi türleri için de geçerlidir. `XmlRootAttribute`Özel kod aracılığıyla eklenen genel öğe bildirimlerinin geçersiz kılınmadığını, `XmlSchemaSet` şema sağlayıcısı yöntemi kullanılarak veya `GetSchema` eski veri kümesi türleri için aracılığıyla geçersiz kılabileceğini unutmayın.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri  
 `IXmlSerializable`öğe türlerinde, `IsAny` özelliği olarak ayarlanmış ya da `true` şema sağlayıcısı yöntemi döndürüyor `null` .  
  
 Öğe türünü serileştirmek ve serisini kaldırma, içerik türünü serileştirmek ve seri durumdan çıkarmak için çok benzerdir. Ancak bazı önemli farklılıklar vardır:  
  
- `WriteXml`Uygulamanın tam olarak bir öğe yazması bekleniyordu (kuşkusuz birden çok alt öğe içerebilir). Bu tek öğe, birden çok eşdüzey öğe veya karışık içerik dışında öznitelikleri yazmamalıdır. Öğe boş olabilir.  
  
- `ReadXml`Uygulama sarmalayıcı öğesini okumalı olmalıdır. Üreten bir öğeyi okuması beklenmektedir `WriteXml` .  
  
- Öğe türü düzenli olarak serileştirilirken (örneğin, bir veri sözleşmesindeki veri üyesi olarak), seri hale getirici, `WriteXml` içerik türlerinde olduğu gibi çağrılmadan önce bir sarmalayıcı öğesi verir. Ancak, en üst düzeyde bir öğe türü serileştirilirken, seri hale getirici, `WriteXml` veya oluşturucuları içinde serileştirici oluşturulurken bir kök ad ve ad alanı açıkça belirtilmediği takdirde, normalde bir sarmalayıcı öğesi yazar `DataContractSerializer` `NetDataContractSerializer` . Daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](serialization-and-deserialization.md).  
  
- Yapılandırma zamanında kök adı ve ad alanını belirtmeden en üst düzeyde bir öğe türü serileştirilirken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> temelde hiçbir şey ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> çağrı yapmaz `WriteXml` . Bu modda, serileştirilmekte olan nesne null olamaz ve polymorphically atanamaz. Ayrıca, nesne grafiği koruması etkinleştirilemez ve kullanılamaz `NetDataContractSerializer` .  
  
- Yapılandırma sırasında kök adı ve ad alanını belirtmeden en üst düzeyde bir öğe türü seri durumdan çıkarılırken, <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> `true` herhangi bir öğenin başlangıcını bulabiliyorsanız ' ı döndürür. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>parametresi, `verifyObjectName` `true` `IsStartObject` nesne gerçekten okunmadan önce ile aynı şekilde davranır. `ReadObject`sonra denetimi yöntemine geçirir `ReadXml` .  
  
 Öğe türleri için aktarılmış şema, `XmlElement` şema sağlayıcısı yönteminin <xref:System.Xml.Schema.XmlSchemaSet> içerik türleriyle olduğu gibi ek bir şema ekleyebildiğinden, daha önceki bir bölümde açıklanan tür ile aynıdır. `XmlRootAttribute`Özniteliğin öğe türleriyle kullanılmasına izin verilmez ve genel öğe bildirimleri bu türler için hiçbir şekilde yayılmaz.  
  
### <a name="differences-from-the-xmlserializer"></a>XmlSerializer 'ın farkları  
 `IXmlSerializable`Arabirimi ve `XmlSchemaProviderAttribute` ve `XmlRootAttribute` öznitelikleri de tarafından anlaşılamalıdır <xref:System.Xml.Serialization.XmlSerializer> . Bununla birlikte, bunların veri anlaşması modelinde nasıl ele alınların bazı farklılıkları vardır. Önemli farklılıklar aşağıda özetlenmiştir:  
  
- Şema sağlayıcısı yönteminin ' de kullanılabilmesi için genel olması gerekir `XmlSerializer` , ancak veri sözleşmesi modelinde kullanılabilmesi için genel olması gerekmez.  
  
- Şema sağlayıcısı yöntemi `IsAny` , veri anlaşması modelinde doğru olduğunda çağrılır, ancak ile değil `XmlSerializer` .  
  
- `XmlRootAttribute`İçerik veya eski veri kümesi türleri için öznitelik mevcut olmadığında, `XmlSerializer` boş ad alanında genel bir öğe bildirimini dışarı aktarır. Veri anlaşması modelinde, kullanılan ad alanı normalde daha önce açıklandığı gibi veri sözleşmesi ad alanıdır.  
  
 Serileştirme teknolojileriyle birlikte kullanılan türler oluşturulurken bu farklılıklara dikkat edin.  
  
### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable şeması içeri aktarılıyor  
 Türlerden oluşturulan bir şemayı içeri aktarırken `IXmlSerializable` birkaç olasılık vardır:  
  
- Oluşturulan şema, [veri sözleşmesi şema başvurusunda](data-contract-schema-reference.md)açıklandığı gibi geçerli bir veri anlaşması şeması olabilir. Bu durumda, her zamanki gibi şema içeri aktarılabilir ve normal veri anlaşması türleri oluşturulur.  
  
- Oluşturulan şema geçerli bir veri anlaşması şeması olmayabilir. Örneğin, şema sağlayıcınız yönteminiz, veri anlaşması modelinde desteklenmeyen XML özniteliklerini içeren bir şema oluşturabilir. Bu durumda, şemayı türler olarak içeri aktarabilirsiniz `IXmlSerializable` . Bu içeri aktarma modu varsayılan olarak açık değildir, ancak örneğin, `/importXmlTypes` [ServiceModel meta veri yardımcı programı aracına (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)komut satırı anahtarı ile birlikte kolayca etkinleştirilebilir. Bu, [sınıfları oluşturmak Için Içeri aktarma şemasında](importing-schema-to-generate-classes.md)ayrıntılı olarak açıklanmıştır. Doğrudan tür örneklerinizin XML ile birlikte çalışmanız gerektiğini unutmayın. Ayrıca, daha geniş bir şema aralığını destekleyen farklı bir serileştirme teknolojisi kullanmayı da düşünebilirsiniz; bkz. kullanma konusu `XmlSerializer` .  
  
- Mevcut `IXmlSerializable` türlerinizi yeni bir oluşturma yerine proxy 'de yeniden kullanmak isteyebilirsiniz. Bu durumda, tür oluşturmak için şemayı Içeri aktarma konu başlığı altında açıklanan Başvurulmuş türler özelliği, yeniden kullanılacak türü belirtmek için kullanılabilir. Bu `/reference` , yeniden kullanılacak türleri içeren derlemeyi belirten Svcutil. exe ' de anahtarı kullanmaya karşılık gelir.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Veri sözleşmelerinde rastgele XML 'yi temsil etme  
 , `XmlElement` `XmlNode` Ve türleri dizisi, `IXmlSerializable` veri ANLAŞMASı modeline rastgele XML eklemenize olanak tanır. `DataContractSerializer`Ve `NetDataContractSerializer` Bu XML içeriğini, işlemde kesintiye uğramadan KULLANıMDA olan XML yazıcı 'ya iletir. Ancak, XML yazarları, yazdıkları XML üzerinde belirli kısıtlamaları uygulayabilir. Özellikle, bazı önemli örnekler aşağıda verilmiştir:  
  
- XML yazarları genellikle \<?xml version=’1.0’ ?> başka bir belge yazmanın ortasında BIR XML belge bildirimine (örneğin,) izin vermez. Tam bir XML belgesi alıp veri üyesi olarak seri hale getirilemiyor `Array` `XmlNode` . Bunu yapmak için, belge bildirimini çıkarmanız veya kendi kodlama düzeninizi kullanarak temsil etmeniz gerekir.  
  
- WCF ile sağlanan tüm XML yazarları \<? … ?> , SOAP iletilerinde izin VERILMEDIĞINDEN XML işleme talimatlarını () ve belge türü tanımlarını ( \<! … > ) reddeder. Yine, bu kısıtlamayı gidermek için kendi kodlama mekanizmanızı kullanabilirsiniz. Bunları sonuç XML 'nize dahil etmeniz gerekiyorsa, bunları destekleyen XML yazıcılarını kullanan özel bir kodlayıcı yazabilirsiniz.  
  
- Uygulamasını uygularken `WriteXml` , <xref:System.Xml.XmlWriter.WriteRaw%2A> XML yazıcı üzerinde çağırma yöntemini kullanmaktan kaçının. WCF çeşitli XML kodlamaları kullanır (ikili dahil), `WriteRaw` sonucun herhangi bir kodlamada kullanılabilir olması gibi çok zor veya imkansız olur.  
  
- `WriteXml`' Yi uygularken, <xref:System.Xml.XmlWriter.WriteEntityRef%2A> <xref:System.Xml.XmlWriter.WriteNmToken%2A> WCF ile sağlanan xml yazıcılarında desteklenmeyen ve yöntemlerini kullanmaktan kaçının.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Veri kümesi, türü belirtilmiş veri kümesi ve DataTable kullanma  
 Bu türlerin kullanılması, veri anlaşması modelinde tam olarak desteklenmektedir. Bu türleri kullanırken aşağıdaki noktaları göz önünde bulundurun:  
  
- Bu türlerin şeması (özellikle <xref:System.Data.DataSet> ve türü belirtilmiş türetilmiş sınıfları), bazı WCF olmayan platformlarda birlikte çalışabilir veya bu platformlarla birlikte kullanıldığında zayıf kullanılabilirlik oluşmasına neden olabilir. Ayrıca, türü kullanmanın `DataSet` performansı olumsuz etkileyebilir. Son olarak, uygulamanızı gelecekte uygulamanızı daha kolay hale getirebilirsiniz. Sözleşmenizde türler yerine açıkça tanımlanmış veri anlaşması türlerini kullanmayı düşünün `DataSet` .  
  
- `DataSet`Veya şeması içeri aktarırken `DataTable` , bu türlere başvurmak önemlidir. Svcutil. exe komut satırı aracı ile, System. Data. dll derleme adı anahtara geçirerek bu yapılabilir `/reference` . Türü belirtilmiş veri kümesi şeması içeri aktarıldıysanız, türü belirtilmiş veri kümesinin türüne başvurmanız gerekir. Svcutil. exe ile, yazılan veri kümesinin derlemesinin konumunu `/reference` anahtara geçirin. Başvuru türleri hakkında daha fazla bilgi için bkz. [sınıfları oluşturmak Için Içeri aktarma şeması](importing-schema-to-generate-classes.md).  
  
 Veri anlaşması modelinde yazılı veri kümeleri için destek sınırlıdır. Türü belirtilmiş veri kümeleri serileştirilmiş ve seri durumdan çıkarılmış olabilir ve kendi şemasını dışarı aktarabilir. Ancak, veri anlaşması şeması içeri aktarma işlemi yalnızca var olanları yeniden kullanabilmesi için şemadan yeni tür belirtilmiş veri kümesi türleri oluşturamıyor. `/r`Svcutil. exe ' deki anahtarı kullanarak, varolan bir türü belirtilmiş veri kümesini işaret edebilirsiniz. Türü belirtilmiş bir veri kümesi kullanan bir hizmette anahtar olmadan Svcutil. exe kullanmayı denerseniz `/r` , otomatik olarak bir alternatif serileştirici (XmlSerializer) seçilir. DataContractSerializer ' i kullanmanız ve şemadan veri kümeleri oluşturmanız gerekiyorsa, aşağıdaki yordamı kullanabilirsiniz: türü belirtilmiş veri kümesi türlerini oluşturma (xsd. exe aracını `/d` hizmette anahtarla kullanarak), türleri derleyin ve ardından `/r` Svcutil. exe ' deki anahtarı kullanarak bunları işaret edin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Veri Anlaşmalarını Kullanma](using-data-contracts.md)
- [Veri Sözleşmesi Seri Hale Getirici Tarafından Desteklenen Türler](types-supported-by-the-data-contract-serializer.md)
