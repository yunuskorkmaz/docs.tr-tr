---
title: XPathNavigator Kullanarak XML Verilerini Değiştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 03a7c5a1-b296-4af4-b209-043c958dc0a5
ms.openlocfilehash: 906de1ded4961b7c67d48a010555d139df97cded
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710641"
---
# <a name="modify-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verilerini Değiştirme
<xref:System.Xml.XPath.XPathNavigator> sınıfı, bir XML belgesindeki düğümleri ve değerleri değiştirmek için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği `true`olmalıdır.  
  
 bir XML belgesini düzenleyebilen <xref:System.Xml.XPath.XPathNavigator> nesneleri, <xref:System.Xml.XmlDocument> sınıfının <xref:System.Xml.XmlDocument.CreateNavigator%2A> yöntemiyle oluşturulur. <xref:System.Xml.XPath.XPathDocument> sınıfı tarafından oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesneleri salt okunurdur ve bir <xref:System.Xml.XPath.XPathDocument> nesnesi tarafından oluşturulan <xref:System.Xml.XPath.XPathNavigator> nesnesinin Editing yöntemlerini kullanma girişimleri bir <xref:System.NotSupportedException>sonuçlanır.  
  
 Düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneleri oluşturma hakkında daha fazla bilgi için bkz. [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="modifying-nodes"></a>Düğümleri değiştirme  
 Bir düğümün değerini değiştirmek için basit bir teknik, <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemlerini kullanmaktır.  
  
 Aşağıdaki tabloda, bu yöntemlerin farklı düğüm türlerinde etkileri listelenmektedir.  
  
|<xref:System.Xml.XPath.XPathNodeType>|Değiştirilen veriler|  
|---------------------------------------------------------------------------------------------------------------------------------------------|------------------|  
|<xref:System.Xml.XPath.XPathNodeType.Root>|Desteklenmez.|  
|<xref:System.Xml.XPath.XPathNodeType.Element>|Öğenin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Attribute>|Özniteliğin değeri.|  
|<xref:System.Xml.XPath.XPathNodeType.Text>|Metin içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.ProcessingInstruction>|Hedef hariç içerik.|  
|<xref:System.Xml.XPath.XPathNodeType.Comment>|Yorumun içeriği.|  
|<xref:System.Xml.XPath.XPathNodeType.Namespace>|Desteklenmiyor.|  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNodeType.Namespace> düğümlerini veya <xref:System.Xml.XPath.XPathNodeType.Root> düğümünü Düzenle desteklenmiyor.  
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı, düğüm eklemek ve kaldırmak için kullanılan bir yöntemler kümesi de sağlar. XML belgesinden düğüm ekleme ve kaldırma hakkında daha fazla bilgi için bkz. [XML verilerini XPathNavigator kullanarak ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md) ve XPathNavigator 'YI [kullanarak XML verilerini kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md) .  
  
### <a name="modifying-untyped-values"></a>Türsüz değerleri değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi, bir parametre olarak geçirilen türsüz `string` değerini, <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandığını düğümün değeri olarak ekler. Değer, herhangi bir tür olmadan veya şema bilgileri kullanılabiliyorsa düğüm türüne göre yeni değerin geçerli olduğunu doğrulamadan eklenir.  
  
 Aşağıdaki örnekte, `contosoBooks.xml` dosyasındaki tüm `price` öğelerini güncelleştirmek için <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi kullanılır.  
  
 [!code-cpp[XPathNavigatorMethods#47](../../../../samples/snippets/cpp/VS_Snippets_Data/XPathNavigatorMethods/CPP/xpathnavigatormethods.cpp#47)]
 [!code-csharp[XPathNavigatorMethods#47](../../../../samples/snippets/csharp/VS_Snippets_Data/XPathNavigatorMethods/CS/xpathnavigatormethods.cs#47)]
 [!code-vb[XPathNavigatorMethods#47](../../../../samples/snippets/visualbasic/VS_Snippets_Data/XPathNavigatorMethods/VB/xpathnavigatormethods.vb#47)]  
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="modifying-typed-values"></a>Yazılan değerleri değiştirme  
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi tarafından yerleştirilen yeni değer, değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer düğüm türüne göre geçerli değilse (örneğin, türü `xs:positiveInteger`olan bir öğe üzerinde `-1` değerini ayarlamak), bir özel durumla sonuçlanır.  
  
 Aşağıdaki örnek `contosoBooks.xml` dosyasındaki ilk `book` öğesinin `price` öğesinin değerini bir <xref:System.DateTime> değerine değiştirmeyi dener. `price` öğesinin XML şeması türü `contosoBooks.xsd` dosyalarında `xs:decimal` olarak tanımlandığından, bu durum bir özel durumla sonuçlanır.  
  
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
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
 Örnek ayrıca `contosoBooks.xsd` giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#3](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xsd#3)]  
  
#### <a name="the-effects-of-editing-strongly-typed-xml-data"></a>Türü kesin belirlenmiş XML verilerinin düzenlenmesinin etkileri  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı, kesin türü belirtilmiş XML 'yi açıklamak için bir temel olarak W3C XML şemasını kullanır. Bir W3C XML şema belgesine karşı doğrulamaya dayalı tür bilgileriyle öğe ve özniteliklere açıklama eklenebilir. Diğer öğeleri veya öznitelikleri içerebilen öğelere karmaşık türler denir, ancak yalnızca metinsel içeriğe sahip olanlar basit türler olarak adlandırılır.  
  
> [!NOTE]
> Özniteliklerde yalnızca basit türler olabilir.  
  
 Bir öğe veya öznitelik, tür tanımına özgü tüm kurallara uygunsa şema geçerli olarak kabul edilebilir. `xs:int` basit tür bir öğe, şema geçerli olması için-2147483648 ile 2147483647 arasında bir sayısal değer içermelidir. Karmaşık türler için, öğenin şema geçerliliği, alt öğelerinin ve özniteliklerinin şema geçerliliği üzerine bağımlıdır. Bu nedenle, bir öğe karmaşık tür tanımına karşı geçerliyse, tüm alt öğeleri ve öznitelikleri tür tanımlarına göre geçerli olur. Benzer şekilde, alt öğelerinden biri veya bir öğenin öznitelikleri tür tanımına göre geçersizdir veya bilinmeyen bir geçerlilik içeriyorsa, öğe geçersiz ya da bilinmeyen bir geçerlilik olur.  
  
 Bir öğenin geçerliliği alt öğelerinin ve özniteliklerinin geçerlilik süresine bağlı olduğu için, daha önceden geçerliyse, öğenin geçerliliğini değiştirmeye neden olan değişiklikler. Özellikle, alt öğeleri veya bir öğenin öznitelikleri eklenirse, güncelleştirilirse veya silinirse, öğenin geçerliliği bilinmiyor olur. Bu, öğenin <xref:System.Xml.XPath.XPathNavigator.SchemaInfo%2A> özelliğinin <xref:System.Xml.Schema.XmlSchemaValidity.NotKnown>olarak ayarlandığı <xref:System.Xml.Schema.IXmlSchemaInfo.Validity%2A> özelliği tarafından temsil edilir. Ayrıca, bu efekt, öğenin üst öğesi (ve onun üst öğesi, vb.) geçerliliği da bilinmediği için, bu efekt, XML belgesi genelinde özyinelemeli olarak yukarı doğru bir şekilde basamaklanır.  
  
 Şema doğrulaması ve <xref:System.Xml.XPath.XPathNavigator> sınıfı hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak şema doğrulaması](../../../../docs/standard/data/xml/schema-validation-using-xpathnavigator.md).  
  
### <a name="modifying-attributes"></a>Öznitelikleri değiştirme  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri, türsüz ve yazılan öznitelik düğümlerini ve "düğümleri değiştirme" bölümünde listelenen diğer düğüm türlerini değiştirmek için kullanılabilir.  
  
 Aşağıdaki örnek `books.xml` dosyasındaki ilk `book` öğesinin `genre` özniteliğinin değerini değiştirir.  
  
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
  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> ve <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemleri hakkında daha fazla bilgi için, "türsüz değerleri değiştirme" ve "yazılı değerleri değiştirme" bölümlerine bakın.  
  
## <a name="innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> özelliği, alt düğümlerin XML işaretlemesini değiştirir <xref:System.Xml.XPath.XPathNavigator> bir nesne şu anda belirtilen XML `string`ayrıştırılmış içeriğiyle konumlandırılmış. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği, alt düğümlerin XML işaretlemesini de değiştirir ve o durumda geçerli düğümün kendisi de şu anda konumlandırılmış olan <xref:System.Xml.XPath.XPathNavigator> bir nesne.  
  
 Aşağıdaki örnek, `price` öğesinin değerini değiştirmek ve `contosoBooks.xml` dosyasındaki ilk `book` öğesine yeni bir `discount` özniteliği eklemek için <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliğini kullanır.  
  
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
  
 Örnek, `contosoBooks.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
## <a name="modifying-namespace-nodes"></a>Ad alanı düğümlerini değiştirme  
 Belge Nesne Modeli (DOM) içinde, ad alanı bildirimleri eklenebilir, güncelleştirilemeyebilir ve silinebilecek normal öznitelikler gibi değerlendirilir. Bir ad alanı düğümünün değerini değiştirme, aşağıdaki örnekte gösterildiği gibi ad alanı düğümünün kapsamındaki öğelerin ve özniteliklerin kimliğini değiştirebildiğinden, <xref:System.Xml.XPath.XPathNavigator> sınıfı ad alanı düğümleri üzerinde bu tür işlemlere izin vermez.  
  
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
  
 <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından eklendikleri kapsamdaki ad alanı bildirimleriyle çakışmayan ad alanı düğümlerine ekleme. Bu durumda, ad alanı bildirimleri XML belgesindeki daha düşük kapsamlar olarak bildirilmez ve aşağıdaki örnekte gösterildiği gibi yeniden adlandırmayla sonuçlanmaz.  
  
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
        <a:child xmlns:a="http://www.contoso.com/">  
    </parent>  
</root>  
```  
  
 Yukarıdaki XML örneğinde, `a:parent-id` özniteliği `http://www.contoso.com/parent-id` ad alanındaki `parent` öğesine eklenir. <xref:System.Xml.XPath.XPathNavigator.CreateAttribute%2A> yöntemi, özniteliği `parent` öğesinde konumlandırıldığında eklemek için kullanılır. `http://www.contoso.com` ad alanı bildirimi, XML belgesinin geri kalanının tutarlılığını korumak için <xref:System.Xml.XPath.XPathNavigator> sınıfı tarafından otomatik olarak eklenir.  
  
## <a name="modifying-entity-reference-nodes"></a>Varlık başvurusu düğümlerini değiştirme  
 <xref:System.Xml.XmlDocument> nesnesindeki varlık başvuru düğümleri salt okunurdur ve <xref:System.Xml.XPath.XPathNavigator> ya da <xref:System.Xml.XmlNode> sınıfları kullanılarak düzenlenemez. Bir varlık başvuru düğümünü değiştirme girişimleri bir <xref:System.InvalidOperationException>sonuçlanır.  
  
## <a name="modifying-xsinil-nodes"></a>Xsi: Nil düğümlerini değiştirme  
 W3C XML şeması önerisi, boş bırakılamakta olan bir öğe kavramını tanıtır. Bir öğe boş bırakıldığında, öğede içerik olmaması ve hala geçerli olması mümkündür. Boş bırakılmakta olan bir öğe kavramı, `null`bir nesne kavramıyla benzerdir. Temel fark, bir `null` nesnesine hiçbir şekilde erişilememektedir, ancak bir `xsi:nil` öğesi erişilebilen öznitelikler gibi özelliklere (alt öğeler veya metin) sahip olmaya devam eder. Bir XML belgesindeki bir öğe üzerinde `true` değeri olan `xsi:nil` özniteliğinin varlığı, bir öğede içerik olmadığını göstermek için kullanılır.  
  
 Bir <xref:System.Xml.XPath.XPathNavigator> nesnesi, bir `xsi:nil` özniteliği `true`değeri olan geçerli bir öğeye içerik eklemek için kullanılırsa, `xsi:nil` özniteliğinin değeri `false`olarak ayarlanır.  
  
> [!NOTE]
> Bir `xsi:nil` özniteliği `false` olarak ayarlanmış bir öğenin içeriği silinirse, özniteliğinin değeri `true`olarak değiştirilmez.  
  
## <a name="saving-an-xml-document"></a>XML belgesi kaydetme  
 Bu konu başlığı altında açıklanan Düzenle yöntemlerinin sonucu olarak bir <xref:System.Xml.XmlDocument> nesnesi üzerinde yapılan değişikliklerin kaydedilmesi, <xref:System.Xml.XmlDocument> sınıfının yöntemleri kullanılarak gerçekleştirilir. <xref:System.Xml.XmlDocument> nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bkz. [bir belge kaydetme ve yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Kaldırma](../../../../docs/standard/data/xml/remove-xml-data-using-xpathnavigator.md)
