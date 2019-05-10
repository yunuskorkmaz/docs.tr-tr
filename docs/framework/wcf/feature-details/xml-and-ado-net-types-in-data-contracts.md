---
title: Veri Sözleşmelerinde XML ve ADO.NET Türleri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
ms.openlocfilehash: 0d052c0f178c2dc6e2eb5a740faa42239fb91068
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64637225"
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Veri Sözleşmelerinde XML ve ADO.NET Türleri
Windows Communication Foundation (WCF) veri sözleşme modeli XML doğrudan temsil eden belirli türlerini destekler. Bu türleri XML olarak serileştirilme şeklini, seri hale getirici herhangi başka bir işlemeye olmadan bu tür XML içeriği yazar. Desteklenen türler <xref:System.Xml.XmlElement>, dizilerin <xref:System.Xml.XmlNode> (ama `XmlNode` kendisini yazın), türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Data.DataSet> Ve <xref:System.Data.DataTable> türü belirtilmiş datasets yanı sıra türü veritabanı programlamada kullanılan yaygın olarak. Bu türleri uygulayan `IXmlSerializable` modeli sözleşme arabirimi ve verileri bu nedenle serileştirilebilir şunlardır. Bu tür için bazı özel durumlar, bu konunun sonunda listelenmiştir.  
  
## <a name="xml-types"></a>XML türleri  
  
### <a name="xml-element"></a>XML öğesi  
 `XmlElement` Türü seri kullanarak XML içeriği. Örneğin, aşağıdaki tür kullanılıyor.  
  
 [!code-csharp[DataContractAttribute#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#4)]
 [!code-vb[DataContractAttribute#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#4)]  
  
 Bu XML şu şekilde sıralanır:  
  
```xml  
<MyDataContract xmlns="http://schemas.contoso.com">  
    <myDataMember>  
        <myElement xmlns="" myAttribute="myValue">  
            myContents  
        </myElement>  
    </myDataMember>  
</MyDataContract>  
```  
  
 Dikkat bir sarmalayıcı veri üyesi öğe `<myDataMember>` hala mevcut olduğundan. Bu öğe veri sözleşme modelindeki kaldırmanın bir yolu yoktur. Bu model işlemek seri hale getiricileri genişletme ( <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer>) özel öznitelikler bu sarmalayıcı öğesine yayabilir. Bu öznitelikler standart XML Şeması örneği "nil" özniteliği ekleyin (izin vererek `XmlElement` olmasını `null`) ve "type" özniteliği (izin vererek `XmlElement` polymorphically kullanılmak üzere). Ayrıca, aşağıdaki XML öznitelikleri WCF'ye özeldir: "İd", "Başvuru", "Type" ve "Derleme". Bu öznitelikler kullanarak desteklemek için yayınlaması gerektiğini `XmlElement` etkin nesne grafiği koruma modu veya ile <xref:System.Runtime.Serialization.NetDataContractSerializer>. (Nesne grafiği koruma modu hakkında daha fazla bilgi için bkz. [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Diziler veya koleksiyonları `XmlElement` izin verildiğini ve tüm diğer dizi veya koleksiyon işlenir. Diğer bir deyişle, var. tüm koleksiyon için bir sarmalayıcı öğe ve ayrı sarmalayıcı öğe (benzer şekilde `<myDataMember>` önceki örnekte) her `XmlElement` dizi.  
  
 Seri durumundan çıkarma üzerinde bir `XmlElement` gelen XML seri durumdan çıkarıcının tarafından oluşturulur. Geçerli bir üst <xref:System.Xml.XmlDocument> seri durumdan çıkarıcı tarafından sağlanır.  
  
 XML parçası olan için seri durumdan çıkarılmış olduğundan emin olun bir `XmlElement` kullanan ve üst öğelerinden herhangi bir önek tanımı üzerinde kullanmayan tüm ön eklerin tanımlar. Bu sorun yalnızca kullanıldığında `DataContractSerializer` XML farklı bir erişim (olmayan`DataContractSerializer`) kaynak.  
  
 İle kullanıldığında `DataContractSerializer`, `XmlElement` polymorphically, ancak yalnızca bir veri türünün üyesi için atanabilir <xref:System.Object>. Bunu uygulayan olsa bile <xref:System.Collections.IEnumerable>e `XmlElement` koleksiyon türü olarak kullanılamaz ve atanamaz bir <xref:System.Collections.IEnumerable> veri üyesi. Tüm polimorfik atamalarını gibi ile `DataContractSerializer` veri anlaşması adına yayar elde edilen XML – bu durumda, "XmlElement" durumda "http://schemas.datacontract.org/2004/07/System.Xml" ad alanı.  
  
 İle `NetDataContractSerializer`, geçerli herhangi bir çok biçimli atamasının `XmlElement` (için `Object` veya `IEnumerable`) desteklenir.  
  
 Seri hale getiricileri genişletme birini türetilmiş türleri ile kullanılacak çalışmayın `XmlElement`, polymorphically ya da olmasın atanan olmadığını.  
  
### <a name="array-of-xmlnode"></a>XmlNode dizisi  
 Dizileri kullanma <xref:System.Xml.XmlNode> kullanmaya çok benzer `XmlElement`. Dizileri kullanma `XmlNode` kullanmaktan daha fazla esneklik `XmlElement`. Kaydırma öğesi veri üyesi içinde birden çok öğe yazabilirsiniz. Kaydırma öğesi, XML açıklamaları gibi veri üyesi içinde öğeleri dışındaki içeriği de ekleyebilir. Son olarak, öznitelikleri sarmalama içine koyabilirsiniz veri üyesi öğesi. Tüm bu dizisi doldurarak gerçekleştirilebilir `XmlNode` belirli türetilmiş sınıfları `XmlNode` gibi <xref:System.Xml.XmlAttribute>, `XmlElement` veya <xref:System.Xml.XmlComment>. Örneğin, aşağıdaki tür kullanılıyor.  
  
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
  
 Unutmayın veri üyesi sarmalayıcı öğe `<myDataMember>` bir öznitelik, bir açıklama ve iki öğe içeriyor. Dört bunlar `XmlNode` seri örnekleri.  
  
 Bir dizi `XmlNode` geçersiz XML sonuçları seri hale getirilemiyor. Örneğin, bir dizi iki `XmlNode` örnekleri ilki bulunduğu bir `XmlElement` ve ikinci bir <xref:System.Xml.XmlAttribute> bu dizisi (özniteliğine eklemek için bir yer yoktur) geçerli XML örneklerine karşılık gelmediğinden geçersiz.  
  
 Bir dizi seri durumdan çıkarma üzerinde `XmlNode`, düğüm oluşturulur ve gelen XML alınan bilgilerle doldurulur. Geçerli bir üst <xref:System.Xml.XmlDocument> seri durumdan çıkarıcı tarafından sağlanır. Tüm düğümleri seri, sarmalayıcı veri üyesi öğe üzerinde herhangi bir özniteliği dahil olmak üzere ancak öznitelikleri dışlayarak WCF seri hale getiricileri genişletme (örneğin, çok biçimli atama göstermek için kullanılan öznitelikleri) tarafından var. yerleştirilir. Diziler seri durumundan çıkarma için XML parçası tüm ad alanı öneklerini tanımlama hakkında uyarı geçerlidir `XmlNode` yalnızca seri durumdan çıkarmak için yaptığı gibi `XmlElement`.  
  
 Seri hale getiricileri genişletme açık nesne grafiği korumasını kullanırken nesne eşitliği düzeyini yalnızca korunur `XmlNode` diziler, bireysel `XmlNode` örnekleri.  
  
 Bir dizi serileştirmek çalışmayın `XmlNode` bir veya daha fazla düğüm ayarlandığı `null`. Tüm dizi üyesinin için izin verilen `null`, ancak herhangi bir kişi için `XmlNode` dizisinde bulunan. Tüm dizi üyesi null ise sarmalayıcı veri üyesi öğe null olduğunu belirten özel bir öznitelik içeriyor. Seri durumundan çıkarma işleminde tüm dizi üyesini ayrıca null olur.  
  
 Yalnızca normal dizilerin `XmlNode` özel seri hale getirici tarafından kabul edilir. Veri üyeleri içeren diğer koleksiyon türleri bildirilen `XmlNode`, ya da veri üyeleri, türetilen türlerin dizileri olarak bildirilen `XmlNode`, özel olarak değerlendirilir. Ayrıca serileştirmeye yönelik diğer ölçütlerinden karşıladıkları sürece bu nedenle, seri hale getirilebilir değiller normalde.  
  
 Diziler veya dizileri koleksiyonları `XmlNode` izin verilir. Tüm koleksiyon için bir sarmalayıcı öğe ve ayrı sarmalayıcı öğe (benzer şekilde `<myDataMember>` önceki örnekte) her dizi için `XmlNode` dış dizi veya koleksiyon.  
  
 Bir veri üyesi türünün doldurma <xref:System.Array> , `Object` veya `Array` , `IEnumerable` ile `XmlNode` örnekleri veri üye kabul neden olmaz bir `Array` , `XmlNode` örnekleri. Her dizi üyesini ayrı olarak seri hale getirilir.  
  
 İle kullanıldığında `DataContractSerializer`, dizilerin `XmlNode` polymorphically, ancak yalnızca bir veri türünün üyesi için atanan `Object`. Bunu uygulayan olsa bile `IEnumerable`, bir dizi `XmlNode` koleksiyon türü olarak kullanılamaz ve atanmış bir `IEnumerable` veri üyesi. Tüm polimorfik atamalarını gibi ile `DataContractSerializer` veri anlaşması adına yayar elde edilen XML – bu durumda, "ArrayOfXmlNode" durumda "http://schemas.datacontract.org/2004/07/System.Xml" ad alanı. İle kullanıldığında `NetDataContractSerializer`, herhangi bir geçerli atamasının bir `XmlNode` dizi desteklenir.  
  
### <a name="schema-considerations"></a>Şema konuları  
 Şema eşleme XML türleri hakkında daha fazla ayrıntı için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu bölümde, önemli noktaları özetini sağlar.  
  
 Bir veri üyesi türünün `XmlElement` aşağıdaki anonim tür kullanılarak tanımlanmış bir öğesine eşlendi.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Veri üye türü dizi `XmlNode` aşağıdaki anonim tür kullanılarak tanımlanmış bir öğesine eşlendi.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>IXmlSerializable arabirimi uygulayan türleri  
 Türleri uygulayan `IXmlSerializable` arabirimi tarafından tam olarak desteklenmektedir `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Özniteliği her zaman uygulanması, şema denetlemek için bu tür.  
  
 Uygulayan türler üç çeşitleri vardır `IXmlSerializable`: bir öğeyi ve eski temsil eden rastgele içerik türlerini temsil eden türleri <xref:System.Data.DataSet> türleri.  
  
- İçerik türlerini kullanan bir şema sağlayıcı yöntemi tarafından belirtilen `XmlSchemaProviderAttribute` özniteliği. Yöntem döndürmez `null`ve <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> öznitelik özelliği varsayılan değerinde sol `false`. Bu en yaygın kullanımı, `IXmlSerializable` türleri.  
  
- Öğe türleri kullanılır, bir `IXmlSerializable` denetlemenize kendi kök öğe adı gerekir. Bir tür bir öğe türü olarak işaretlemek için ayarlayın ya da <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> özelliği <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliğini `true` veya şema sağlayıcısı yöntemden null döndürür. Bir şema sağlayıcısı yöntemine sahip olan öğe türleri için isteğe bağlı – yöntemi adı yerine null belirtebilir `XmlSchemaProviderAttribute`. Ancak, varsa `IsAny` olduğu `true` ve şema sağlayıcı yöntemi belirtildi, yöntem boş döndürmelidir.  
  
- Eski <xref:System.Data.DataSet> türleridir `IXmlSerializable` ile işaretli olmayan türleri `XmlSchemaProviderAttribute` özniteliği. Bunun yerine, şirketler güvenmektedir <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> şeması oluşturma için yöntemi. Bu düzen için kullanılan `DataSet` türü ve kendi türü belirtilmiş veri kümesi türetilen bir sınıfta bir .NET Framework'ün önceki sürümlerinde, ancak artık kullanımdan kalkmıştır ve yalnızca eski nedenlerle desteklenir. Değil Bu modeli temel kullanır ve her zaman geçerli `XmlSchemaProviderAttribute` için `IXmlSerializable` türleri.  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable içerik türleri  
 Uygulayan bir tür veri üyesi serileştirilirken `IXmlSerializable` ve bir içerik türü olarak tanımlanmış daha önce seri hale getirici veri üyesi ve geçiş denetimi için sarmalayıcı öğe Yazar <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama sarmalayıcı öğe özniteliklerini ekleme dahil olmak üzere herhangi bir XML yazabilirsiniz. Sonra `WriteXml` olan Bitti, seri hale getirici öğe kapatır.  
  
 Uygulayan bir tür veri üyesi işlenirken `IXmlSerializable` ve bir içerik türü tanımlanmış daha önce geçişi ve veri üyesi için sarmalayıcı öğe XML okuyucuyu denetlemek için seri durumdan çıkarıcının konumları <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> yöntemi. Yöntemi, başlangıç ve bitiş etiketleri dahil olmak üzere tüm öğeyi okumalısınız. Emin olun, `ReadXml` kod burada öğesi boş durumu işler. Ayrıca, `ReadXml` uygulama belirli bir şekilde adın geçmesi sarmalayıcı öğe üzerinde değil kullanan. Ad tarafından seçmiş seri hale getirici farklılık gösterebilir.  
  
 Atamak için izin `IXmlSerializable` içerik türleri polymorphically, örneğin, veri türü üyeleri <xref:System.Object>. Ayrıca türü örneklerinin null olmasına izin verilir. Son olarak, kullanmak mümkün mü `IXmlSerializable` türleri içeren ve etkin nesne grafiği korunması <xref:System.Runtime.Serialization.NetDataContractSerializer>. Bu özelliklerin tümünü belirli öznitelikleri sarmalayıcı öğe eklemek WCF serileştirici gerektirir ("nil" ve bir WCF özgü ad alanı içinde XML Şeması örneği ad alanı ve "Id", "Başvuru", "Type" ve "Derleme" "type").  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml uygularken yok saymak için öznitelikler  
 Denetime geçirmeden önce `ReadXml` kodu, seri durumdan çıkarıcı XML öğesi inceler, bu özel XML öznitelikleri algılar ve bunlar üzerinde çalışır. Örneğin, "nil" ise `true`, bir null değer seri durumdan ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, farklı bir tür olduğu gibi öğenin içeriğini seri. Polymorphically atanan türün uygulamasını `ReadXml` çağrılır. Herhangi bir durumda, bir `ReadXml` uygulama tarafından seri durumdan çıkarıcının işlenen çünkü bu özel öznitelikleri yoksay.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable içerik türleri için şema konuları  
 Şema dışarı aktarılırken bir `IXmlSerializable` içerik türü, şema sağlayıcısı yöntemi çağrılır. Bir <xref:System.Xml.Schema.XmlSchemaSet> şema sağlayıcısı yöntemine geçirilir. Yöntem herhangi bir geçerli şema şema kümesine ekleyebilirsiniz. Şema kümesi, şema verme ne zaman oluştuğu anda zaten biliniyor şema içeriyor. Şema sağlayıcı yöntemi şema kümesi için bir öğe eklemeniz gerektiğinde, belirlemelisiniz bir <xref:System.Xml.Schema.XmlSchema> uygun ad alanı ile kümede zaten mevcut. Aşması durumunda şema sağlayıcı yöntemi yeni öğenin varolan eklemelisiniz `XmlSchema`. Aksi takdirde, yeni bir oluşturmalısınız `XmlSchema` örneği. Bu önemlidir, dizilerin `IXmlSerializable` türleri kullanılmaktadır. Örneğin, bir `IXmlSerializable` "A", "B", ad alanına yazarken verilen türü onu içeren şema sağlayıcısı yöntemi, önceden şema çağrılır zamanına göre "ArrayOfA" türü tutacak "B" için şema mümkündür.  
  
 Türlere ekleme yanı sıra <xref:System.Xml.Schema.XmlSchemaSet>, içerik türleri için şema sağlayıcı yöntemi null olmayan bir değer döndürmesi gerekir. Geri dönebilirsiniz bir <xref:System.Xml.XmlQualifiedName> için kullanılacak şema türü adını belirten verilen `IXmlSerializable` türü. Bu tam ad aynı zamanda verileri olarak hizmet sözleşme adı ve türü için ad alanı. Hemen şema sağlayıcısı yöntem döndürüldüğünde ayarlayın şemada var olmayan bir tür dönmek için izin verilir. Ancak, bu zaman tüm türleri verilir ilgili beklenir ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi çağrıldığında tüm ilgili türleri için <xref:System.Runtime.Serialization.XsdDataContractExporter> ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliği erişilen), şema kümesinde türü yok. Erişim `Schemas` özelliği önce tüm ilgili `Export` çağrıları yapılan neden olabilir bir <xref:System.Xml.Schema.XmlSchemaException>. Dışarı aktarma işlemine ilişkin daha fazla bilgi için bkz. [sınıflardan Şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Şema sağlayıcı yöntemi ayrıca döndürebilir <xref:System.Xml.Schema.XmlSchemaType> kullanılacak. Türü olabilir veya anonim olmayabilir. Anonim ise şeması `IXmlSerializable` türü her zaman anonim bir tür dışarı `IXmlSerializable` türü, bir veri üyesi kullanılır. `IXmlSerializable` Türü bir veri anlaşması adına ve ad alanı yine de sahiptir. (Bu bölümünde anlatıldığı gibi belirlenir [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md) dışında <xref:System.Runtime.Serialization.DataContractAttribute> öznitelik adı özelleştirmek için kullanılamaz.) Anonim değilse içinde türlerden biri olmalıdır `XmlSchemaSet`. Bu durumda, döndürmekle eşdeğerdir `XmlQualifiedName` türü.  
  
 Ayrıca, genel bir öğe bildirimi türü için dışarı aktarılır. Türü yoksa <xref:System.Xml.Serialization.XmlRootAttribute> öğe uygulanmış özniteliği varsa aynı ada ve bir veri anlaşması ad alanına ve onun "nillable" özelliği true olarak ayarlandığında. Bunun tek istisnası Şema ad alanı ("http://www.w3.org/2001/XMLSchema") – türün veri anlaşması bu ad alanında ise, şema ad alanına yeni öğeler eklemek için Yasak olduğundan karşılık gelen genel öğe boş ad alanı içinde olur. Türündeyse `XmlRootAttribute` , genel bir öğe bildirimi özniteliğinin şunları kullanarak aktarılır: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> ve <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> özellikleri. Varsayılan değerlerle `XmlRootAttribute` veri anlaşması adına, bir boş ad alanı ve "nillable" doğru uygulanmış olan.  
  
 Aynı genel öğesi bildirim kuralları, eski veri kümesi türleri için geçerlidir. Unutmayın `XmlRootAttribute` ya da eklenen özel kod aracılığıyla eklenen genel öğesi bildirimleri geçersiz kılınamaz `XmlSchemaSet` şema sağlayıcı yöntemi kullanarak aracılığıyla veya `GetSchema` eski veri kümesi türleri için.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri  
 `IXmlSerializable` öğe türleri ya da sahip `IsAny` özelliğini `true` veya dönüş şema sağlayıcısı yöntemi `null`.  
  
 Serileştirme ve seri kaldırma öğe türü seri hale getirme ve bir içerik türü seri durumdan çıkarmak için çok benzer. Ancak, bazı önemli farklar vardır:  
  
- `WriteXml` Uygulama (kuşkusuz birden çok alt öğe içerebilir) tam olarak bir öğenin yazma beklenir. Bu öznitelikler birden çok kardeş öğeler veya karma içerik bu tek öğede dışında yazılmıyor. Öğe boş olabilir.  
  
- `ReadXml` Uygulama sarmalayıcı öğe değil okumalıdır. Bir öğe okumak için beklenen, `WriteXml` üretir.  
  
- Bir öğe türü düzenli olarak (örneğin, bir veri üyesi olarak bir veri anlaşması) serileştirilirken bir sarmalayıcı öğe çağırmadan önce seri hale getirici çıkarır `WriteXml`, içerik türleri gibi. Ancak, bir öğe türü en üst düzeyde serileştirilirken seri hale getirici normalde hiç öğe çevresinde bir sarmalayıcı öğe çıktı vermez, `WriteXml` kök adı veya ad alanı seri hale getirici oluştururken açıkça belirtilen sürece Yazar içinde `DataContractSerializer` veya `NetDataContractSerializer` oluşturucular. Daha fazla bilgi için [serileştirme ve seri durumundan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
- En üst düzeydeki bir öğe türü kök adı ve ad alanı oluşturma zamanında belirtmeden serileştirilirken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> aslında hiçbir şey yapmaz ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> çağrıları `WriteXml`. Bu modda serileştirilmekte olan nesne null olamaz ve polymorphically atanamaz. Ayrıca, Nesne grafiği koruma etkinleştirilemiyor ve `NetDataContractSerializer` kullanılamaz.  
  
- Kök ad ve ad alanı oluşturma zamanında belirtmeden en üst düzeydeki bir öğe türü seri durumdan çıkarılırken zaman <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> döndürür `true` varsa herhangi bir öğenin başlangıç bulabilirsiniz. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> ile `verifyObjectName` parametresini `true` aynı şekilde davranır `IsStartObject` gerçekten nesnesi okuma önce. `ReadObject` Daha sonra denetime geçirir `ReadXml` yöntemi.  
  
 Verilen öğe türleri için şema aynı olan `XmlElement` türü bir önceki bölümde açıklandığı gibi şema sağlayıcı yöntemi herhangi bir ek şema ekleyebilirsiniz dışında <xref:System.Xml.Schema.XmlSchemaSet> içerik türleri gibi. Kullanarak `XmlRootAttribute` öğe türleri ile özniteliği izin verilmez ve genel öğesi bildirimleri hiçbir zaman bu tür için gösterilir.  
  
### <a name="differences-from-the-xmlserializer"></a>XmlSerializer arasındaki farklar  
 `IXmlSerializable` Arabirimi ve `XmlSchemaProviderAttribute` ve `XmlRootAttribute` öznitelikleri ayrıca tarafından anlaşılan <xref:System.Xml.Serialization.XmlSerializer> . Ancak, bu veri sözleşme modeli nasıl ele alındığı bazı farklar vardır. Önemli farklar aşağıda özetlenmiştir:  
  
- Şema sağlayıcı yöntemi içinde kullanılabilir olması için genel `XmlSerializer`, ancak ortak veri sözleşme modelinde kullanılabilir olması gerekmez.  
  
- Şema sağlayıcı yöntemi aldığında çağrılan `IsAny` veri sözleşme modelinde geçerlidir ancak `XmlSerializer`.  
  
- Zaman `XmlRootAttribute` özniteliği için içerik veya eski bir veri kümesi türleri yoksa `XmlSerializer` boş ad alanı bir genel öğesi bildiriminde dışarı aktarır. Veri sözleşmesi modelinde kullanılan ad normalde daha önce açıklandığı gibi veri anlaşması ad alanıdır.  
  
 Her iki serileştirme teknoloji ile kullanılan türler oluştururken bu farklılıklara dikkat edin.  
  
### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable Şemayı içeri aktarma  
 Oluşturulan şema içeri aktarılırken `IXmlSerializable` türleri, birkaç olasılık vardır:  
  
- Oluşturulan şema açıklandığı gibi geçerli bir veri sözleşmesi şema olabilir [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu durumda, şema zamanki içeri aktarılabilir ve normal bir veri anlaşması türleri oluşturulur.  
  
- Oluşturulan şema geçerli veri sözleşmesi şema olmayabilir. Örneğin, şema sağlayıcısı yönteminizi veri sözleşme modelinde Desteklenmeyen XML öznitelikleri içeren şema oluşturabilir. Bu durumda, şema olarak içeri aktarabilirsiniz `IXmlSerializable` türleri. Bu içeri aktarma modu varsayılan olarak açık değildir ancak kolayca – örneğin ile etkinleştirilebilir `/importXmlTypes` için komut satırı anahtarı [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu ayrıntılı olarak açıklanan [sınıfları oluşturmak için şema alma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Tür örnekleriniz için doğrudan XML ile iş unutmayın. Farklı bir kullanmayı da düşünebilirsiniz geniş bir şema – destekleyen serileştirme teknolojiyi kullanarak konusuna bakın `XmlSerializer`.  
  
- Mevcut yeniden kullanmak isteyebileceğiniz `IXmlSerializable` yenilerini oluşturmak yerine proxy türleri. Bu durumda, içeri aktarma şema oluşturma türleri konusuna açıklanan başvurulan türleri özellik yeniden türünü belirtmek için kullanılabilir. Bunu kullanarak karşılık gelen `/reference` yeniden kullanmak için türler içeren derlemeyi belirtir svcutil.exe üzerinde geçin.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Rastgele bir XML veri anlaşmalarında temsil eden  
 `XmlElement`, Dizi `XmlNode` ve `IXmlSerializable` türleri rastgele bir XML veri anlaşması modeline eklemesine izin. `DataContractSerializer` Ve `NetDataContractSerializer` bu XML kullanımda, işlemde engellemeden açın XML yazıcısı içerik geçirin. Ancak, XML yazarların yazmadan XML üzerinde belirli kısıtlamaları zorunlu kılabilir. Özellikle önemli bazı örnekler şunlardır:  
  
- XML yazıcılar genellikle bir XML belgesi bildirimi izin verme (örneğin, \<? xml version ='1.0 '? >) başka bir belgede yazma ortasında. Tam bir XML belgesi almak ve olarak serileştirmek bir `Array` , `XmlNode` veri üyesi. Bunu yapmak için belge bildirimi ya da atmak zorunda veya bunu temsil etmek için kendi kodlama düzeni kullanın.  
  
- WCF ile sağlanan XML yazarların tüm XML işleme yönergeleri Reddet (\<? … ? >) ve belge tanımları yazın (\<! … ">), çünkü SOAP iletilerini izin verilmiyor. Kendi kodlama mekanizması, bu kısıtlamayı çözmek almak için yeniden kullanabilirsiniz. Bu sonuç XML dosyanızı eklemeniz gerekir, bunları destekleyen XML yazarların kullanan özel bir kodlayıcı yazabilirsiniz.  
  
- Uygularken `WriteXml`, çağırmaktan kaçınmanız <xref:System.Xml.XmlWriter.WriteRaw%2A> yöntemi XML yazıcısı. WCF kullanan çeşitli XML kodlamaları (ikili dahil), çok zor veya imkansız kullanılacak `WriteRaw` sağlayacak şekilde sonucu herhangi bir kodlama içinde kullanılabilir.  
  
- Uygularken `WriteXml`, kullanmaktan kaçının <xref:System.Xml.XmlWriter.WriteEntityRef%2A> ve <xref:System.Xml.XmlWriter.WriteNmToken%2A> WCF ile sağlanan XML yazarların desteklenmeyen yöntemleri.  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Veri kümesi, türü belirtilmiş DataSet ve DataTable kullanma  
 Bu türü kullanarak, veri sözleşme modeli tam olarak desteklenir. Bu tür kullanırken aşağıdaki noktaları göz önünde bulundurun:  
  
- Bu tür için şema (özellikle <xref:System.Data.DataSet> ve kendi türü belirtilmiş türetilmiş sınıflar) bazı WCF olmayan platformlarıyla çalışabilen olmayabilir veya aşağıdaki platformlarla kullanıldığında kötü kullanılabilirlik neden olabilir. Ayrıca, kullanarak `DataSet` türü, performans etkileri olabilir. Son olarak, bunu, sizin için sürüm uygulamanızı gelecekte zorlaştırır. Açıkça tanımlanmış veri anlaşması türleri yerine kullanmayı `DataSet` sözleşmelerinizi türleri.  
  
- İçeri aktarılırken `DataSet` veya `DataTable` şema, bu tür başvurmak önemli. Svcutil.exe komut satırı aracı ile bu System.Data.dll derleme adına geçirerek gerçekleştirilebilir `/reference` geçin. Türü belirtilmiş veri kümesi şema içe aktarılıyorsa, türü belirtilmiş DataSet'in bir türe başvurmalıdır. Türü belirtilmiş DataSet'in derlemeye konumunu svcutil.exe ile geçirin `/reference` geçin. Başvuru türleri hakkında daha fazla bilgi için bkz. [sınıfları oluşturmak için şema alma](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Veri sözleşmesi modelinde türü belirtilmiş DataSets için destek sınırlıdır. Türü belirtilmiş DataSets serisi seri hale getirilebilir ve kendi şemasını dışarı aktarabilirsiniz. Ancak, yalnızca var olanları kullanabilirsiniz olarak veri sözleşmesi şema içeri aktarma yeni oluşturamıyor şemada, veri kümesi türleri yazılan. Var olan bir türü belirtilmiş DataSet kullanarak gösterebilir `/r` Svcutil.exe üzerinde geçin. Bir Svcutil.exe olmadan kullanmayı denerseniz `/r` yazılan veri kümesi kullanan bir hizmet üzerinde değiştirmek, alternatif bir serileştirici (XmlSerializer) otomatik olarak seçilir. DataContractSerializer kullanmanız gerekir ve veri kümeleri, şema oluşturmak gerekir, aşağıdaki yordamı kullanabilirsiniz: türü belirtilmiş veri kümesi türleri üretmek (ile XSD.exe'nin aracını kullanarak `/d` hizmette geçiş), derleme türleri ve gelin bunları kullanarak `/r` Svcutil.exe üzerinde geçin.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Xml.Serialization.IXmlSerializable>
- [Veri Anlaşmalarını Kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Veri Anlaşması Seri Hale Getirici Tarafından Desteklenen Türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
