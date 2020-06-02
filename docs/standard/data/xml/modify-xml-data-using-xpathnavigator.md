---
title: XPathNavigator Kullanarak XML Verilerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 3b64bc8666274798ebaefc87ef3883fcec1ef6b1
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288842"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verilerini Değiştirme
Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> XML belgesindeki düğümleri ve değerleri değiştirmek için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true` .  
  
 <xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> sınıfının yöntemiyle oluşturulur <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> salt okunurdur ve <xref:System.Xml.XPath.XPathNavigator> bir nesne tarafından oluşturulan nesnenin Editing yöntemlerini kullanma girişimleri <xref:System.Xml.XPath.XPathDocument> bir ile sonuçlanır <xref:System.NotSupportedException> .  
  
 Düzenlenebilir nesneler oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Düğümleri değiştirme  
 Bir düğümün değerini değiştirmenin basit bir tekniği, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> sınıfının ve yöntemlerini kullanmaktır <xref:System.Xml.XPath.XPathNavigator> .  
  
 Aşağıdaki tabloda, bu yöntemlerin farklı düğüm türlerinde etkileri listelenmektedir.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Değiştirilen veriler|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Desteklenmiyor.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Öğenin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Özniteliğin değeri.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Metin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Hedef hariç içerik.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Yorumun içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Desteklenmiyor.|  
  
> [!NOTE]
> Düğüm <xref:System.Xml.XPath.XPathNodeType.Namespace> veya düğüm düzenlenme <xref:System.Xml.XPath.XPathNodeType.Root> desteklenmiyor.  
  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı ayrıca düğüm eklemek ve kaldırmak için kullanılan bir yöntemler kümesi sağlar. XML belgesinden düğüm ekleme ve kaldırma hakkında daha fazla bilgi için bkz. [XML verilerini XPathNavigator kullanarak ekleme](insert-xml-data-using-xpathnavigator.md) ve XPathNavigator 'YI [kullanarak XML verilerini kaldırma](remove-xml-data-using-xpathnavigator.md) .  
  
### <a name="modifying-untyped-values"></a>Türsüz değerleri değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Yöntemi, `string` bir parametre olarak geçirilen türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.  
  
 Aşağıdaki örnekte, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi dosyadaki tüm öğeleri güncelleştirmek için kullanılır `price` `contosoBooks.xml` .  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Yazılan değerleri değiştirme  
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, yöntemi tarafından yerleştirilen yeni değer, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer, düğüm türüne göre geçerli değilse (örneğin, `-1` türü olan bir öğe üzerinde değerini ayarlamak `xs:positiveInteger` ), bir özel durumla sonuçlanır.  
  
 Aşağıdaki örnek, `price` dosyasındaki ilk öğe öğesinin değerini `book` `contosoBooks.xml` bir değere değiştirmeye çalışır <xref:System.DateTime> . Öğesinin XML şeması türü `price` dosyalarda olarak tanımlandığından `xs:decimal` `contosoBooks.xsd` , bu durum bir özel durumla sonuçlanır.  
  
```vb  
Dim settings As XmlReaderSettings = New XmlReaderSettings()  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd")  
settings.ValidationType = ValidationType.Schema  
  
Dim reader As XmlReader = XmlReader.Create("contosoBooks.xml", settings)  
  
Dim document As XmlDocument = New XmlDocument()  
document.Load(reader)  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetTypedValue(DateTime.Now)  
```  
  
```csharp  
XmlReaderSettings settings = new XmlReaderSettings();  
settings.Schemas.Add("http://www.contoso.com/books", "contosoBooks.xsd");  
settings.ValidationType = ValidationType.Schema;  
  
XmlReader reader = XmlReader.Create("contosoBooks.xml", settings);  
  
XmlDocument document = new XmlDocument();  
document.Load(reader);  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.SetTypedValue(DateTime.Now);  
```  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek de `contosoBooks.xsd` bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Türü kesin belirlenmiş XML verilerinin düzenlenmesinin etkileri  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, türü kesin BELIRLENMIŞ XML 'yi açıklamak için temel olarak W3C XML şemasını kullanır. Bir W3C XML şema belgesine karşı doğrulamaya dayalı tür bilgileriyle öğe ve özniteliklere açıklama eklenebilir. Diğer öğeleri veya öznitelikleri içerebilen öğelere karmaşık türler denir, ancak yalnızca metinsel içeriğe sahip olanlar basit türler olarak adlandırılır.  
  
> [!NOTE]
> Özniteliklerde yalnızca basit türler olabilir.  
  
 Bir öğe veya öznitelik, tür tanımına özgü tüm kurallara uygunsa şema geçerli olarak kabul edilebilir. Basit türe sahip bir öğe, `xs:int` şema geçerli olması için-2147483648 ile 2147483647 arasında bir sayısal değer içermelidir. Karmaşık türler için, öğenin şema geçerliliği, alt öğelerinin ve özniteliklerinin şema geçerliliği üzerine bağımlıdır. Bu nedenle, bir öğe karmaşık tür tanımına karşı geçerliyse, tüm alt öğeleri ve öznitelikleri tür tanımlarına göre geçerli olur. Benzer şekilde, alt öğelerinden biri veya bir öğenin öznitelikleri tür tanımına göre geçersizdir veya bilinmeyen bir geçerlilik içeriyorsa, öğe geçersiz ya da bilinmeyen bir geçerlilik olur.  
  
 Bir öğenin geçerliliği alt öğelerinin ve özniteliklerinin geçerlilik süresine bağlı olduğu için, daha önceden geçerliyse, öğenin geçerliliğini değiştirmeye neden olan değişiklikler. Özellikle, alt öğeleri veya bir öğenin öznitelikleri eklenirse, güncelleştirilirse veya silinirse, öğenin geçerliliği bilinmiyor olur. Bu, <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> öğesinin <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliği olarak ayarlanan özelliği tarafından temsil edilir <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown> . Ayrıca, bu efekt, öğenin üst öğesi (ve onun üst öğesi, vb.) geçerliliği da bilinmediği için, bu efekt, XML belgesi genelinde özyinelemeli olarak yukarı doğru bir şekilde basamaklanır.  
  
 Şema doğrulaması ve sınıfı hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathNavigator kullanarak şema doğrulaması](schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Öznitelikleri değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türsüz ve yazılan öznitelik düğümlerini ve "düğümleri değiştirme" bölümünde listelenen diğer düğüm türlerini değiştirmek için kullanılabilir.  
  
 Aşağıdaki örnek, `genre` dosyasındaki ilk öğenin özniteliğinin değerini değiştirir `book` `books.xml` .  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", String.Empty)  
navigator.MoveToChild("book", String.Empty)  
navigator.MoveToAttribute("genre", String.Empty)  
  
navigator.SetValue("non-fiction")  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", String.Empty);  
navigator.MoveToChild("book", String.Empty);  
navigator.MoveToAttribute("genre", String.Empty);  
  
navigator.SetValue("non-fiction");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Ve yöntemleri hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> , "türsüz değerleri değiştirme" ve "yazılı değerleri değiştirme" bölümlerine bakın.  
  
## <a name="innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özellikleri, <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, <xref:System.Xml.XPath.XPathNavigator> belirtilen XML 'nin ayrıştırılmış içeriğiyle bir nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir `string` . Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir nesnenin şu anda bulunduğu alt DÜĞÜMLERIN XML işaretlemesini ve <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün kendisini değiştirir.  
  
 Aşağıdaki örnek, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> öğesinin değerini değiştirmek `price` ve `discount` dosyadaki ilk öğeye yeni bir öznitelik eklemek için özelliğini kullanır `book` `contosoBooks.xml` .  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml");  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>"  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.OuterXml = "<price discount=\"0\">10.99</price>";  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Ad alanı düğümlerini değiştirme  
 Belge Nesne Modeli (DOM) içinde, ad alanı bildirimleri eklenebilir, güncelleştirilemeyebilir ve silinebilecek normal öznitelikler gibi değerlendirilir. <xref:System.Xml.XPath.XPathNavigator>Bir ad alanı düğümünün değerini değiştirme, aşağıdaki örnekte gösterildiği gibi ad alanı düğümünün kapsamındaki öğelerin ve özniteliklerin kimliğini değiştirebildiğinden, sınıf ad alanı düğümleri üzerinde bu tür işlemlere izin vermez.  
  
```xml  
<root xmlns="http://www.contoso.com">  
    <child />  
</root>  
```  
  
 Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, her bir öğenin ad alanı URI 'sinin değeri değiştiği için bu, belgedeki her öğeyi etkili bir şekilde yeniden adlandırır.  
  
```xml  
<root xmlns="urn:contoso.com">  
    <child />  
</root>  
```  
  
 İçinde eklendiği kapsamda ad alanı bildirimleriyle çakışmayan ad alanı düğümlerine ekleme, sınıfı tarafından izin veriliyor <xref:System.Xml.XPath.XPathNavigator> . Bu durumda, ad alanı bildirimleri XML belgesindeki daha düşük kapsamlar olarak bildirilmez ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırmayla sonuçlanmaz.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent>  
        <a:child />  
    </parent>  
</root>  
```  
  
 Yukarıdaki XML örneği aşağıdaki şekilde değiştirilirse, ad alanı bildirimleri diğer ad alanı bildiriminin kapsamındaki XML belgesi üzerine doğru şekilde yayılır.  
  
```xml  
<root xmlns:a="http://www.contoso.com">  
    <parent a:parent-id="1234" xmlns:a="http://www.contoso.com/parent-id">  
        <a:child xmlns:a="http://www.contoso.com/" />  
    </parent>  
</root>  
```  
  
 Yukarıdaki XML örneğinde, özniteliği `a:parent-id` `parent` `http://www.contoso.com/parent-id` ad alanındaki öğesine eklenir. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A>Yöntemi, öğesinde konumlandırılmış özniteliği eklemek için kullanılır `parent` . `http://www.contoso.com`Ad alanı bildirimi, <xref:System.Xml.XPath.XPathNavigator> XML belgesinin geri kalanının tutarlılığını korumak için sınıfı tarafından otomatik olarak eklenir.  
  
## <a name="modifying-entity-reference-nodes"></a>Varlık başvurusu düğümlerini değiştirme  
 Bir nesnedeki varlık başvuru düğümleri <xref:System.Xml.XmlDocument> salt okunurdur ve ya da sınıfları kullanılarak düzenlenemez <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XmlNode> . Bir varlık başvuru düğümünü değiştirme girişimleri bir ile sonuçlanır <xref:System.InvalidOperationException> .  
  
## <a name="modifying-xsinil-nodes"></a>Xsi: Nil düğümlerini değiştirme  
 W3C XML şeması önerisi, boş bırakılamakta olan bir öğe kavramını tanıtır. Bir öğe boş bırakıldığında, öğede içerik olmaması ve hala geçerli olması mümkündür. Boş bırakılmakta olan bir öğe kavramı, nesne kavramıyla benzerdir `null` . Temel fark, bir `null` nesneye hiçbir şekilde erişilememektedir, `xsi:nil` ancak bir öğesi erişilebilir ancak içeriğe (alt öğe veya metin) sahip olmayan nitelikler gibi özelliklere sahip olabilir. Bir `xsi:nil` XML belgesindeki öğesi üzerinde değeri olan özniteliğin varlığı, `true` bir öğenin içeriğe sahip olmadığını göstermek için kullanılır.  
  
 Bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, değeri olan bir özniteliğe sahip geçerli bir öğeye içerik eklemek için kullanılırsa `xsi:nil` `true` , `xsi:nil` özniteliğinin değeri olarak ayarlanır `false` .  
  
> [!NOTE]
> `xsi:nil`Özniteliği olarak ayarlanmış bir öğenin içeriği `false` silinirse, özniteliğinin değeri olarak değiştirilmez `true` .  
  
## <a name="saving-an-xml-document"></a>XML belgesi kaydetme  
 <xref:System.Xml.XmlDocument>Bu konu başlığı altında açıklanan Düzenle yöntemlerinin sonucu olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, sınıfının yöntemleri kullanılarak gerçekleştirilir <xref:System.Xml.XmlDocument> . Bir nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için <xref:System.Xml.XmlDocument> bkz. [belgeyi kaydetme ve yazma](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Ekleme](insert-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](remove-xml-data-using-xpathnavigator.md)
