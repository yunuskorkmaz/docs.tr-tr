---
title: "Veri Sözleşmelerinde XML ve ADO.NET Türleri"
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
ms.assetid: c2ce8461-3c15-4c41-8c81-1cb78f5b59a6
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c5395797dd2ebba467448b90be139d750bbcc6b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/02/2017
---
# <a name="xml-and-adonet-types-in-data-contracts"></a>Veri Sözleşmelerinde XML ve ADO.NET Türleri
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Veri sözleşmesi modeli XML doğrudan temsil eden belirli türlerini destekler. Bu tür için XML serileştirildiği zaman seri hale getirici herhangi başka bir işleme olmadan bu tür XML içeriği yazar. Desteklenen türler <xref:System.Xml.XmlElement>, dizilerin <xref:System.Xml.XmlNode> (ama `XmlNode` kendisini yazın), türleri uygulayan <xref:System.Xml.Serialization.IXmlSerializable>. <xref:System.Data.DataSet> Ve <xref:System.Data.DataTable> türü olarak yazılan veri kümeleri, veritabanı programlaması kullanılan yaygın olarak. Bu türleri uygulayan `IXmlSerializable` arabirimi ve bu nedenle veriler serileştirilebilir sözleşme modeli. Bu tür için bazı özel durumlar, bu konunun sonunda listelenmiştir.  
  
## <a name="xml-types"></a>XML türleri  
  
### <a name="xml-element"></a>XML öğesi  
 `XmlElement` Türü seri XML içeriğini kullanarak. Örneğin, aşağıdaki türü kullanıyor.  
  
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
  
 Dikkat bir sarmalayıcı veri üyesi öğesi `<myDataMember>` hala mevcut olduğu. Bu öğe veri sözleşmesi modelinde kaldırmanın yolu yoktur. Bu model işlemek serileştiricileri ( <xref:System.Runtime.Serialization.DataContractSerializer> ve <xref:System.Runtime.Serialization.NetDataContractSerializer>) özel öznitelikleri bu sarmalayıcı öğesine yayabilir. Bu öznitelikler standart XML şema örneği "nil" özniteliği içerir (izin verme `XmlElement` olmasını `null`) ve "tür" özniteliği (izin verme `XmlElement` polymorphically kullanılmak üzere). Ayrıca, aşağıdaki XML öznitelikleri özgü [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]: "Id", "Ref", "Tür" ve "Derlemesi". Bu öznitelikler kullanarak desteklemek için yayınlaması gerektiğini `XmlElement` Nesne grafiği koruma modu etkin olmayan veya <xref:System.Runtime.Serialization.NetDataContractSerializer>. ([!INCLUDE[crabout](../../../../includes/crabout-md.md)] Nesne grafiği koruma modu bkz [seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).)  
  
 Diziler veya koleksiyonları `XmlElement` izin verilir ve diğer dizi veya koleksiyon işlenir. Diğer bir deyişle, olduğundan tüm koleksiyon için bir kapsayıcı öğe ve ayrı sarmalayıcı öğesi (benzer şekilde `<myDataMember>` önceki örnekte) her `XmlElement` dizideki.  
  
 Seri durumdan çıkarma işleminde, bir `XmlElement` gelen XML'den seri durumdan çıkarıcının tarafından oluşturulur. Geçerli bir üst <xref:System.Xml.XmlDocument> kaldırıcı tarafından sağlanır.  
  
 XML parçası, için seri durumdan çıkarılmış olduğundan emin olun bir `XmlElement` kullanır ve tüm üst öğelerinden önek tanımları üzerinde kalmaz tüm ön eklerin tanımlar. Bu bir sorun yalnızca kullanıldığında `DataContractSerializer` XML farklı bir erişmek için (olmayan`DataContractSerializer`) kaynak.  
  
 İle kullanıldığında `DataContractSerializer`, `XmlElement` polymorphically, ancak yalnızca veri türünün bir üyesi için atanabilir <xref:System.Object>. Bunu uygulayan olsa bile <xref:System.Collections.IEnumerable>, bir `XmlElement` koleksiyon türü olarak kullanılamaz ve atanamaz bir <xref:System.Collections.IEnumerable> veri üyesi. Tüm çok biçimli atamaları gibi ile `DataContractSerializer` veri sözleşme adına yayar elde edilen XML'de – bu durumda, "XmlElement" "http://schemas.datacontract.org/2004/07/System.Xml" ad alanında öyledir.  
  
 İle `NetDataContractSerializer`, tüm geçerli biçimli atamasının `XmlElement` (için `Object` veya `IEnumerable`) desteklenir.  
  
 Türetilen türlerle kullanın ya da serileştiricileri denemeyin `XmlElement`, polymorphically ya da olmasın atanmış olup olmadığını.  
  
### <a name="array-of-xmlnode"></a>XmlNode dizisi  
 Dizileri kullanma <xref:System.Xml.XmlNode> kullanarak çok benzer `XmlElement`. Dizileri kullanma `XmlNode` kullanmaktan daha fazla esneklik `XmlElement`. Kaydırma öğesi veri üyesi içinde birden çok öğe yazabilirsiniz. XML açıklamaları gibi öğesi kaydırma veri üyesi içinde öğeleri dışındaki içeriği de ekleyemezsiniz. Son olarak, öznitelikler kaydırma içine koyabilirsiniz veri üyesi öğesi. Tüm bu dizisi doldurarak sağlanabilir `XmlNode` belirli türetilmiş sınıfları, `XmlNode` gibi <xref:System.Xml.XmlAttribute>, `XmlElement` veya <xref:System.Xml.XmlComment>. Örneğin, aşağıdaki türü kullanıyor.  
  
 [!code-csharp[DataContractAttribute#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/datacontractattribute/cs/overview.cs#5)]
 [!code-vb[DataContractAttribute#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/datacontractattribute/vb/overview.vb#5)]  
  
 Seri, sonuçta elde edilen XML aşağıdaki kodu benzer.  
  
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
  
 Unutmayın veri üyesi sarmalayıcı öğesi `<myDataMember>` bir öznitelik, bir açıklama ve iki öğe içeriyor. Dört bunlar `XmlNode` sıralanmış örnekleri.  
  
 Bir dizi `XmlNode` geçersiz XML sonuçlarında seri hale getirilemez. Örneğin, bir dizi iki `XmlNode` ilk olduğu örnekleri bir `XmlElement` ve ikincisi ise bir <xref:System.Xml.XmlAttribute> bu dizisi (özniteliğe eklemek için bir yer olan) herhangi geçerli bir XML örneğine karşılık gelmediğinden geçersiz.  
  
 Seri durumdan çıkarma işleminde dizisi `XmlNode`, düğüm oluşturulur ve gelen XML alınan bilgilerle doldurulur. Geçerli bir üst <xref:System.Xml.XmlDocument> kaldırıcı tarafından sağlanır. Tüm düğümleri sarmalayıcı veri üyesi öğede öznitelikleri de dahil olmak üzere serisi ancak öznitelikleri dışlayarak yerleştirilen var. tarafından [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serileştiricileri (örneğin, çok biçimli atama göstermek için kullanılan öznitelikleri). Tüm ad alanı öneklerini XML parçadaki tanımlama hakkında uyarısıyla dizileri seri durumdan çıkarma geçerlidir `XmlNode` bu seri durumdan çıkarmak için yaptığı gibi `XmlElement`.  
  
 Nesne eşitliği serileştiricileri açık nesne grafiği koruma ile kullanırken, yalnızca düzeyi üzerinde korunur `XmlNode` dizileri, bireysel `XmlNode` örnekleri.  
  
 Bir dizi serileştirmek çalışmayın `XmlNode` bir veya daha fazla düğüm ayarlandığı `null`. Tüm dizi üyesi olacak şekilde izin `null`, ancak her kullanıcı için `XmlNode` dizisi içinde yer alan. Tüm dizi üyesi null ise, sarmalayıcı veri üyesi öğesi null olduğunu gösteren özel bir öznitelik içeriyor. Seri durumundan çıkarma işleminde tüm dizi üyesi de null olur.  
  
 Yalnızca normal dizileri `XmlNode` özel seri hale getirici tarafından kabul edilir. Veri üyeleri içeren diğer koleksiyon türleri bildirilen `XmlNode`, veya veri üyeleri bildirilen türetilen türlerin dizileri gibi `XmlNode`, özel olarak kabul edilmediği. Bunlar ayrıca serileştirmek için diğer ölçütleri karşılayan sürece bu nedenle, seri hale getirilebilir olmadıkları normalde.  
  
 Diziler veya dizileri koleksiyonları `XmlNode` izin verilir. Tüm koleksiyon için bir kapsayıcı öğe ve ayrı sarmalayıcı öğesi (benzer şekilde `<myDataMember>` önceki örnekte) her dizisi için `XmlNode` dış dizi ya da koleksiyonu.  
  
 Türünün bir veri üyesi doldurma <xref:System.Array> , `Object` veya `Array` , `IEnumerable` ile `XmlNode` örnekleri ele veri üyesi olarak neden olmaz bir `Array` , `XmlNode` örnekleri. Her dizi üyesini ayrı olarak serileştirilir.  
  
 İle kullanıldığında `DataContractSerializer`, dizilerin `XmlNode` polymorphically, ancak yalnızca veri türünün bir üyesi için atanan `Object`. Bunu uygulayan olsa bile `IEnumerable`, bir dizi `XmlNode` koleksiyon türü olarak kullanılamaz ve atanması bir `IEnumerable` veri üyesi. Tüm çok biçimli atamaları gibi ile `DataContractSerializer` veri sözleşme adına yayar elde edilen XML'de – bu durumda, "ArrayOfXmlNode" "http://schemas.datacontract.org/2004/07/System.Xml" ad alanında öyledir. İle kullanıldığında `NetDataContractSerializer`, tüm geçerli atamasının bir `XmlNode` dizi desteklenir.  
  
### <a name="schema-considerations"></a>Şema konuları  
 Şema eşleme XML türleri hakkında daha fazla ayrıntı için bkz: [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu bölümde önemli noktaları özetini sağlar.  
  
 Türünün bir veri üyesi `XmlElement` aşağıdaki anonim tür kullanılarak tanımlanmış bir öğe olarak eşlenmiş.  
  
```xml  
<xsd:complexType>  
   <xsd:sequence>  
      <xsd:any minOccurs="0" processContents="lax" />  
   </xsd:sequence>  
</xsd:complexType>  
```  
  
 Veri üye türü dizisi `XmlNode` aşağıdaki anonim tür kullanılarak tanımlanmış bir öğe olarak eşlenmiş.  
  
```xml  
<xsd:complexType mixed="true">  
   <xsd:sequence>  
      <xsd:any minOccurs="0" maxOccurs="unbounded" processContents="lax" />  
   </xsd:sequence>  
   <xsd:anyAttribute/>  
</xsd:complexType>  
```  
  
## <a name="types-implementing-the-ixmlserializable-interface"></a>IXmlSerializable arabirimi uygulama türleri  
 Türleri uygulayan `IXmlSerializable` arabirimi tarafından tam olarak desteklenmektedir `DataContractSerializer`. <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> Özniteliği her zaman uygulanamaz kendi şema denetlemek için bu tür.  
  
 Uygulama türleri üç çeşitleri vardır `IXmlSerializable`: tek bir öğe ve eski temsil eden rasgele içerik, türleri temsil eden türlerin <xref:System.Data.DataSet> türleri.  
  
-   İçerik türleri tarafından belirtilen bir şema sağlayıcısı yöntemi kullanır `XmlSchemaProviderAttribute` özniteliği. Yöntem döndürmez `null`ve <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> öznitelik özelliği varsayılan değerinde sol `false`. En yaygın kullanımı budur `IXmlSerializable` türleri.  
  
-   Öğe türleri kullanılır olduğunda bir `IXmlSerializable` denetlemenize kendi kök öğe adı gerekir. Bir tür bir öğe türü olarak işaretlemek için ya da ayarlamak <xref:System.Xml.Serialization.XmlSchemaProviderAttribute.IsAny%2A> özelliği <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> özniteliğini `true` veya şema sağlayıcısı yönteminden null döndürür. Bir şema sağlayıcı yöntemi sahip öğe türleri için isteğe bağlı – yöntemi adı yerine null belirtebilir `XmlSchemaProviderAttribute`. Ancak, varsa `IsAny` olan `true` ve şema sağlayıcı yöntemi belirtilirse, yöntem null döndürmelidir.  
  
-   Eski <xref:System.Data.DataSet> türleri `IXmlSerializable` ile işaretli olmayan türleri `XmlSchemaProviderAttribute` özniteliği. Bunun yerine, güvenirler <xref:System.Xml.Serialization.IXmlSerializable.GetSchema%2A> şema oluşturma için yöntem. Bu model için kullanılan `DataSet` türü ve onun türü belirtilmiş veri kümesi türeyen bir sınıf .NET Framework'ün önceki sürümlerindeki ancak artık kullanımdan kalkmıştır ve yalnızca eski nedenlerle desteklenir. Değil Bu deseni temel kullanır ve her zaman geçerli `XmlSchemaProviderAttribute` için `IXmlSerializable` türleri.  
  
### <a name="ixmlserializable-content-types"></a>IXmlSerializable içerik türleri  
 Veri üyesi uygulayan bir tür serileştirilirken `IXmlSerializable` ve bir içerik türü olarak tanımlanmış daha önce seri hale getirici veri üyesi ve geçişi denetimi için sarmalayıcı öğesi Yazar <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> yöntemi. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Uygulama sarmalayıcı öğesine öznitelikleri ekleme de dahil olmak üzere tüm XML yazabilirsiniz. Sonra `WriteXml` olan Bitti, seri hale getirici öğesi kapatır.  
  
 Veri üyesi uygulayan bir tür çıkarılırken `IXmlSerializable` ve bir içerik türü tanımlanmış daha önce geçişi ve veri üyesi için sarmalayıcı öğede XML okuyucusu denetlemek için seri durumdan çıkarıcının Konumlar <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> yöntemi. Yöntemi başlangıç ve bitiş etiketleri de dahil olmak üzere tüm öğeyi okumalısınız. Emin olun, `ReadXml` kodu nereye öğe boş durumu işler. Ayrıca, `ReadXml` uygulama belirli bir şekilde adın geçmesi sarmalayıcı öğede değil kullanan. Adı tarafından seçilen seri hale getirici değişebilir.  
  
 Atamak için izin `IXmlSerializable` içerik türleri polymorphically, örneğin, veri türü üyeleri <xref:System.Object>. Ayrıca türü örnekleri boş olmasına izin verilir. Son olarak, kullanmak mümkün `IXmlSerializable` türleri ile etkin nesne grafiği koruma ile <xref:System.Runtime.Serialization.NetDataContractSerializer>. Bu özelliklerin tümü gerektiren [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] sarmalayıcı öğesine belirli öznitelikler eklemek için seri hale getirici ("nil" ve XML şema örneği ad ve "Id", "Ref", "Tür" ve "Derlemesindeki" "type" bir [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-belirli bir ad alanı).  
  
#### <a name="attributes-to-ignore-when-implementing-readxml"></a>ReadXml uygularken yoksaymak için öznitelikler  
 Denetime geçirmeden önce `ReadXml` kodu, seri durumdan çıkarıcının XML öğesi inceler, bu özel XML öznitelikleri algılar ve bunlar üzerinde çalışır. Örneğin, "nil" ise `true`, bir null değer serisi ve `ReadXml` çağrılmaz. Çok biçimlilik algılanırsa, öğenin içeriğini farklı bir tür boşmuş gibi serisi. Polymorphically atanan tür uyarlamasını `ReadXml` olarak adlandırılır. Herhangi bir durumda, bir `ReadXml` uygulaması tarafından seri durumdan çıkarıcının işlenir çünkü bu özel öznitelikler yoksay.  
  
### <a name="schema-considerations-for-ixmlserializable-content-types"></a>IXmlSerializable içerik türleri için şema konuları  
 Şema dışarı aktarılırken bir `IXmlSerializable` içerik türü, şema sağlayıcısı yöntemi çağrılır. Bir <xref:System.Xml.Schema.XmlSchemaSet> şema sağlayıcısı yönteme geçirilen. Yöntemin geçerli bir şema şema kümesine ekleyebilirsiniz. Şema kümesini şema verme oluştuğunda zamanında zaten biliniyor bir şema içeriyor. Şema sağlayıcı yöntemi şema kümesine bir öğe eklemelisiniz, varsa belirlemelisiniz bir <xref:System.Xml.Schema.XmlSchema> uygun ad alanı zaten kümesinde var. Destekliyorsa, şema sağlayıcı yöntemi yeni öğe varolan eklemelisiniz `XmlSchema`. Aksi takdirde, yeni bir oluşturmalısınız `XmlSchema` örneği. Bu önemlidir, dizilerin `IXmlSerializable` türleri kullanılmaktadır. Örneğin, bir `IXmlSerializable` ad "B", "A" türü olarak dışarı türü içeren şema sağlayıcısı yöntemi, önceden ayarlanmış şema çağrılır zamana göre "ArrayOfA" türü tutmak "B" için şemayı mümkün değil.  
  
 Türlere ekleme yanı sıra <xref:System.Xml.Schema.XmlSchemaSet>, içerik türleri için şema sağlayıcı yöntemi null olmayan bir değer döndürmesi gerekir. Geri dönebilirsiniz bir <xref:System.Xml.XmlQualifiedName> için kullanılacak şema türü adını belirtir verilen `IXmlSerializable` türü. Bu tam adı da verileri olarak hizmet sözleşme adı ve türü için ad alanı. Var olmayan bir tür hemen şema sağlayıcı yöntem döndüğünde kümesi şemasında dönüş izin verilir. Ancak, bunu zamanına göre tüm türleri verilir ilgili beklenen ( <xref:System.Runtime.Serialization.XsdDataContractExporter.Export%2A> yöntemi, üzerinde tüm ilgili türleri için çağrılır <xref:System.Runtime.Serialization.XsdDataContractExporter> ve <xref:System.Runtime.Serialization.XsdDataContractExporter.Schemas%2A> özelliği erişilir), şema kümesinde türü mevcut. Erişme `Schemas` tüm önce özelliği ilgili `Export` çağrıları yapılan sonuçlanabilir bir <xref:System.Xml.Schema.XmlSchemaException>. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]dışa aktarma işlemi bkz [sınıflardan Şemaları dışarı aktarma](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md).  
  
 Şema sağlayıcı yöntem de döndürebilir <xref:System.Xml.Schema.XmlSchemaType> kullanmak için. Türü olabilir veya anonim olmayabilir. Anonim, ise için şemayı `IXmlSerializable` türü her zaman anonim bir tür olarak dışarı `IXmlSerializable` türü, bir veri üyesi olarak kullanılır. `IXmlSerializable` Türü hala sahip bir veri sözleşmesi adı ve ad alanı. (Bu açıklandığı gibi belirlenir [veri sözleşmesi adları](../../../../docs/framework/wcf/feature-details/data-contract-names.md) dışında <xref:System.Runtime.Serialization.DataContractAttribute> özniteliği, adını özelleştirmek için kullanılamaz.) Anonim değilse, türlerden biri olmalıdır `XmlSchemaSet`. Bu durumda döndürmek için eşdeğer `XmlQualifiedName` türü.  
  
 Ayrıca, bir genel öğesi bildirimi türü için verilir. Tür yoksa <xref:System.Xml.Serialization.XmlRootAttribute> öğesi uygulanmış özniteliğine sahip aynı ad ve veri sözleşmesi ad alanına ve "bırakılabilir" özelliği true olarak ayarlandığında. Tür veri sözleşmesi ise tek özel durum Şema ad alanı ("http://www.w3.org/2001/XMLSchema") – bu ad alanında, karşılık gelen bir genel öğesi şemaya yeni öğeler eklemek için Yasak boş ad alanında nedeni ad alanı. Türündeyse `XmlRootAttribute` , genel bir öğe bildirimi özniteliğinin, aşağıdakileri kullanarak aktarılır: <xref:System.Xml.Serialization.XmlRootAttribute.ElementName%2A>, <xref:System.Xml.Serialization.XmlRootAttribute.Namespace%2A> ve <xref:System.Xml.Serialization.XmlRootAttribute.IsNullable%2A> özellikleri. Varsayılan değerlerle `XmlRootAttribute` uygulanan veri sözleşme adına, bir boş ad alanı ve "bırakılabilir" true ' dır.  
  
 Aynı genel öğesi bildirim kuralları eski veri kümesi türleri için geçerlidir. Unutmayın `XmlRootAttribute` ya da eklenen özel kod aracılığıyla eklenen genel öğesi bildirimleri geçersiz kılamaz `XmlSchemaSet` şema sağlayıcı yöntemi kullanarak aracılığıyla veya `GetSchema` eski veri kümesi türleri için.  
  
### <a name="ixmlserializable-element-types"></a>IXmlSerializable öğe türleri  
 `IXmlSerializable`öğe türleri ya da sahip `IsAny` özelliğini `true` veya dönüş kendi şema sağlayıcı yöntemi `null`.  
  
 Seri hale getirme ve bir öğe türü seri durumdan seri hale getirme ve bir içerik türü seri durumdan çıkarmak için çok benzer. Ancak, önemli bazı farklar vardır:  
  
-   `WriteXml` Uygulaması (elbette birden çok alt öğelerini içerebilir) tam olarak bir öğe yazma beklenir. Birden çok kardeş öğeler veya karışık içerik bu tek öğe dışında öznitelikleri yazmayı değil. Öğe boş olabilir.  
  
-   `ReadXml` Uygulama sarmalayıcı öğesi değil kimler. Bir öğeyi okumak için beklenen, `WriteXml` üretir.  
  
-   Düzenli olarak bir öğe türü (örneğin, bir veri üyesi olarak bir veri sözleşmesi) serileştirilirken bir kapsayıcı öğe çağırmadan önce seri hale getirici çıkarır `WriteXml`, içerik türleri gibi. Ancak, en üst düzeyinde bir öğe türü seri hale getirme, seri hale getirici normalde hiç öğe çevresinde bir sarmalayıcı öğesi çıktı vermez, `WriteXml` bir kök ve ad alanına seri hale getirici oluştururken açıkça belirtilen sürece Yazar içinde `DataContractSerializer` veya `NetDataContractSerializer` oluşturucular. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Seri hale getirme ve seri durumdan çıkarma](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md).  
  
-   En üst düzeydeki bir öğe türü kök adı ve ad alanı oluşturma zamanında belirtmeden serileştirilirken <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> temelde hiçbir şey yapmaz ve <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> çağrıları `WriteXml`. Bu modda, serileştirilen nesnesi null olamaz ve polymorphically atanamaz. Ayrıca, Nesne grafiği korunması olamaz etkin ve `NetDataContractSerializer` kullanılamaz.  
  
-   En üst düzeydeki bir öğe türü kök adı ve ad alanı oluşturma zamanında belirtmeden çıkarılırken <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> döndürür `true` herhangi bir öğenin başlangıç bulursanız. <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A>ile `verifyObjectName` parametre kümesine `true` aynı şekilde davranır `IsStartObject` gerçekten nesnesi okuma önce. `ReadObject`Ardından, denetimine geçirir `ReadXml` yöntemi.  
  
 Öğe türleri için verilen şema olarak aynıdır `XmlElement` türü bir önceki bölümde açıklandığı gibi şema sağlayıcı yöntemi herhangi bir ek şema ekleyebilirsiniz dışında <xref:System.Xml.Schema.XmlSchemaSet> gibi içerik türleri. Kullanarak `XmlRootAttribute` öğe türleri özniteliğiyle izin verilmez ve genel öğesi bildirimleri hiçbir zaman bu türleri için gösterilen.  
  
### <a name="differences-from-the-xmlserializer"></a>XmlSerializer arasındaki farklar  
 `IXmlSerializable` Arabirimi ve `XmlSchemaProviderAttribute` ve `XmlRootAttribute` öznitelikleri ayrıca tarafından anlaşılan <xref:System.Xml.Serialization.XmlSerializer> . Ancak, bu veri sözleşmesi modelinde nasıl işlenir bazı farklar vardır. Önemli farklılıklar aşağıda özetlenmiştir:  
  
-   Şema sağlayıcı yöntemi kullanılabilir olması için ortak `XmlSerializer`, ancak veri sözleşmesi modelinde kullanılabilmesi için ortak olması gerekmez.  
  
-   Şema sağlayıcı yöntemi aldığında çağrılan `IsAny` veri sözleşmesi modelinde doğrudur bilgisayardı `XmlSerializer`.  
  
-   Zaman `XmlRootAttribute` özniteliği içeriği veya eski veri kümesi türleri için mevcut değil `XmlSerializer` boş ad alanı bir genel öğesi bildiriminde dışa aktarır. Veri sözleşmesi modeli kullanılan ad normal olarak daha önce açıklandığı gibi veri sözleşmesi ad alanıdır.  
  
 Her iki serileştirme teknolojileriyle kullanılan türleri oluştururken bu farklılıkları unutmayın.  
  
### <a name="importing-ixmlserializable-schema"></a>IXmlSerializable şemayı içe aktarma  
 Üretilen bir şema alırken `IXmlSerializable` türleri, birkaç olasılık vardır:  
  
-   Oluşturulan şema açıklandığı gibi geçerli bir veri sözleşmesi şema olabilir [veri sözleşmesi şema başvurusu](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Bu durumda, şema her zamanki gibi alınabilir ve normal veri sözleşme türleri üretilir.  
  
-   Oluşturulan şema geçerli bir veri sözleşmesi şema olmayabilir. Örneğin, şema sağlayıcısı yönteminizi veri sözleşmesi modelde Desteklenmeyen XML öznitelikleri içerir şema oluşturabilir. Bu durumda, şema olarak içeri aktarabilirsiniz `IXmlSerializable` türleri. Bu içeri aktarma mod varsayılan olarak açık değildir ancak kolayca – örneğin ile etkinleştirilebilir `/importXmlTypes` komut satırı anahtarını [ServiceModel meta veri yardımcı Programracı (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Bu ayrıntılı olarak açıklanmıştır [oluşturmak sınıfları içeri aktarma şemaya](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md). Türü örnekleri için doğrudan XML ile çalışmalıdır unutmayın. Farklı bir kullanarak düşünebilirsiniz geniş bir şema – destekleyen serileştirme teknolojisini kullanarak konusuna bakın `XmlSerializer`.  
  
-   Var olan yeniden isteyebilirsiniz `IXmlSerializable` yenilerini oluşturmak yerine proxy türlerinde. Bu durumda, türleri oluşturmak konu alma şemaya açıklanan başvurulan tür özelliği yeniden türünü belirtmek için kullanılabilir. Bu kullanarak karşılık gelen `/reference` yeniden türleri içeren bütünleştirilmiş kodun belirten svcutil.exe üzerinde geçin.  
  
## <a name="representing-arbitrary-xml-in-data-contracts"></a>Veri sözleşmelerinde rasgele XML temsil eden  
 `XmlElement`, Dizi `XmlNode` ve `IXmlSerializable` türleri veri sözleşmesi modeline rasgele XML eklemesine izin. `DataContractSerializer` Ve `NetDataContractSerializer` bu XML kullanımda, işlemde engellemeden açın XML yazıcıyı içerik geçirin. Ancak, XML yazıcılarının yazmadan XML üzerinde belirli kısıtlamaları zorunlu. Özellikle, önemli bazı örnekler şunlardır:  
  
-   XML yazıcılar genellikle bir XML belgesi bildirimi izin verme (örneğin, \<? xml sürümü ='1.0 '? >) başka bir belge yazma gerçekleştiriyor. Tam bir XML belgesi alın ve olarak seri hale bir `Array` , `XmlNode` veri üyesi. Bunu yapmak için her iki Şerit belge bildiriminde çıkışı gerekir veya onu temsil etmek için kendi kodlama düzenini kullanın.  
  
-   Tüm ile sağlanan XML yazıcılarının [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XML işleme yönergelerini Reddet (\<? … ? >) ve belge tanımları yazın (\<! … >), çünkü SOAP iletilerine izin verilmiyor. Yeniden, bu kısıtlamaya almak için kendi kodlama mekanizması kullanabilirsiniz. Bu sonuç XML içermelidir gerekiyorsa, bunları destekleyen XML yazıcılarının kullanan özel bir kodlayıcı yazabilirsiniz.  
  
-   Uygularken `WriteXml`, arama kaçının <xref:System.Xml.XmlWriter.WriteRaw%2A> XML yazıcıyı yöntemi. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]XML kodlamaları (dahil olmak üzere ikili) çeşitli kullanır, bu çok zor veya kullanmak mümkün `WriteRaw` sonucu hiçbir kodlama kullanılabilir olacak şekilde.  
  
-   Uygularken `WriteXml`, kullanmaktan kaçının <xref:System.Xml.XmlWriter.WriteEntityRef%2A> ve <xref:System.Xml.XmlWriter.WriteNmToken%2A> ile sağlanan XML yazıcılarının desteklenmeyen yöntemleri [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="using-dataset-typed-dataset-and-datatable"></a>Veri kümesi, türü belirtilmiş veri kümesi ve DataTable kullanma  
 Bu tür kullanarak veri sözleşmesi modelinde tam olarak desteklenir. Bu tür kullanırken aşağıdaki noktaları göz önünde bulundurun:  
  
-   Bu tür için şemayı (özellikle <xref:System.Data.DataSet> ve kendi yazılan türetilmiş sınıfları) bazı ile birlikte çalışabilen olmayabilir olmayan[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] platformları, ya da bu platformları ile kullanıldığında zayıf kullanılabilirlik neden olabilir. Ayrıca, kullanarak `DataSet` türü performans etkileri olabilir. Son olarak, bu, daha zor sizin için sürüme uygulamanızı gelecekte kalmasına neden olabilir. Açıkça tanımlanmış veri sözleşme türleri yerine kullanmayı `DataSet` sözleşmelerinizi türlerinde.  
  
-   İçe aktarma sırasında `DataSet` veya `DataTable` şema, bu tür başvurmak önemli. Svcutil.exe komut satırı aracı ile bu System.Data.dll derleme adı geçirerek gerçekleştirilebilir `/reference` geçin. Türü belirtilmiş veri kümesi şema alma, yazılan veri kümesi'nin bir türe başvurmalıdır. Türü belirtilmiş veri kümesi'nin derlemeye konumunu svcutil.exe ile geçirmek `/reference` geçin. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]türlerine başvurma, bkz: [oluşturmak sınıfları içeri aktarma şemaya](../../../../docs/framework/wcf/feature-details/importing-schema-to-generate-classes.md).  
  
 Veri sözleşmesi modelindeki yazılan veri kümeleri için destek sınırlıdır. Yazılan veri kümeleri serisi seri hale getirilebilir ve kendi şema dışarı aktarabilirsiniz. Ancak, yalnızca var olanları yeniden kullanabilir olarak şema alma yeni oluşturamıyor veri sözleşmesi şema DataSet türlerinden yazılan. Kullanarak mevcut türü belirtilmiş veri kümesi için gösterebilir `/r` üzerinde Svcutil.exe geçin. Svcutil.exe olmadan kullanmayı denerseniz, `/r` türü belirtilmiş veri kümesi kullanan bir hizmet anahtarı, alternatif bir serileştirici (XmlSerializer) otomatik olarak seçilir. DataContractSerializer kullanmanız gerekir ve veri kümeleri şemadan oluşturmanız gerekir, aşağıdaki yordamı kullanabilirsiniz: türü belirtilmiş veri kümesi türleri oluştur (XSD.exe'nin aracıyla kullanarak `/d` hizmette geçiş) türleri derleyin ve ardından bunları kullanarak `/r` üzerinde Svcutil.exe geçin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Xml.Serialization.IXmlSerializable>  
 [Veri sözleşmelerini kullanma](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Veri sözleşmesi seri hale getirici tarafından desteklenen türler](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
