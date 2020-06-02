---
title: XPathNavigator Kullanarak XML Verilerini Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: fa331757fac3f30ee86a24bbd0ee12b5f1031a4b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288673"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verilerini Kaldırma
Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> XML belgesinden düğümleri ve değerleri kaldırmak için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır `true` .  
  
 <xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> sınıfının yöntemiyle oluşturulur <xref:System.Xml.XmlDocument> . <xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler <xref:System.Xml.XPath.XPathDocument> salt okunurdur ve bir <xref:System.Xml.XPath.XPathNavigator> nesne tarafından oluşturulan nesnenin Editing yöntemlerini kullanma girişimleri <xref:System.Xml.XPath.XPathDocument> bir ile sonuçlanır <xref:System.NotSupportedException> .  
  
 Düzenlenebilir nesneler oluşturma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator> bkz. [XPathDocument ve XMLDOCUMENT kullanarak XML verilerini okuma](reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Düğümler kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> bir XML belgesinden düğümleri kaldırmak için yöntemini sağlar.  
  
### <a name="removing-a-node"></a>Düğüm kaldırma  
 Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> <xref:System.Xml.XPath.XPathNavigator> nesne şu anda bir XML belgesinden konumlandırılmış olan geçerli düğümü silmeye yönelik yöntemi sağlar.  
  
 Bir düğüm yöntemi kullanılarak silindikten sonra <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> , artık nesnenin kökünden ulaşılamaz <xref:System.Xml.XmlDocument> . Düğüm silindikten sonra, <xref:System.Xml.XPath.XPathNavigator> silinen düğümün üst düğümüne yerleştirilir.  
  
 Silme işlemi, <xref:System.Xml.XPath.XPathNavigator> silinen düğümde konumlandırılmış herhangi bir nesnenin konumunu etkilemez. Bu <xref:System.Xml.XPath.XPathNavigator> nesneler, Silinen alt ağaçta taşıyabilecekleri, ancak sınıfın normal düğüm kümesi gezinti yöntemleri kullanılarak ana düğüm ağacına taşınamayacak anlamda geçerlidir <xref:System.Xml.XPath.XPathNavigator> .  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A>Sınıfının yöntemi, <xref:System.Xml.XPath.XPathNavigator> Bu <xref:System.Xml.XPath.XPathNavigator> nesneleri ana düğüm ağacına veya ana düğüm ağacından Silinen alt ağaca geri taşımak için kullanılabilir.  
  
 Aşağıdaki örnekte, `price` `book` dosyanın ilk öğesinin öğesi `contosoBooks.xml` yöntemi kullanılarak silinir <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> . <xref:System.Xml.XPath.XPathNavigator>Öğe silindikten sonra nesnenin konumu `price` üst `book` öğedir.  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.DeleteSelf()  
  
Console.WriteLine("Position after delete: {0}", navigator.Name)  
Console.WriteLine(navigator.OuterXml)  
```  
  
```csharp  
XmlDocument document = new XmlDocument();  
document.Load("contosoBooks.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books");  
navigator.MoveToChild("book", "http://www.contoso.com/books");  
navigator.MoveToChild("price", "http://www.contoso.com/books");  
  
navigator.DeleteSelf();  
  
Console.WriteLine("Position after delete: {0}", navigator.Name);  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-an-attribute-node"></a>Öznitelik düğümünü kaldırma  
 Öznitelik düğümleri bir XML belgesinden yöntemi kullanılarak kaldırılır <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> .  
  
 Bir öznitelik düğümü silindikten sonra, artık nesnenin kök düğümünden ulaşılamaz <xref:System.Xml.XmlDocument> ve <xref:System.Xml.XPath.XPathNavigator> nesne üst öğe üzerinde konumlandırılır.  
  
#### <a name="default-attributes"></a>Varsayılan öznitelikler  
 Öznitelikleri kaldırmak için kullanılan yöntemden bağımsız olarak, XML belgesi için DTD veya XML şemasında varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırmaya ilişkin özel sınırlamalar vardır. Ait oldukları öğe da kaldırılmadığı takdirde varsayılan öznitelikler kaldırılamaz. Varsayılan öznitelikler, varsayılan öznitelikleri olan öğeler için her zaman mevcuttur ve sonuç olarak, varsayılan bir özniteliğin silinmesi, öğesine eklenen ve varsayılan değere başlatılan bir değiştirme özniteliğiyle sonuçlanır.  
  
## <a name="removing-values"></a>Değerler kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> bir XML belgesinden türsüz ve yazılan değerleri kaldırmak için ve yöntemlerini sağlar.  
  
### <a name="removing-untyped-values"></a>Türsüz değerler kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A>Yöntemi, `string` bir parametre olarak geçirilen türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler. Yöntemine boş bir dize geçirilme, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> geçerli düğümün değerini kaldırır.  
  
 Aşağıdaki örnek, `price` `book` yöntemi kullanılarak dosyasındaki ilk öğenin öğesinin değerini kaldırır `contosoBooks.xml` <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> .  
  
```vb  
Dim document As XmlDocument = New XmlDocument()  
document.Load("contosoBooks.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
navigator.MoveToChild("bookstore", "http://www.contoso.com/books")  
navigator.MoveToChild("book", "http://www.contoso.com/books")  
navigator.MoveToChild("price", "http://www.contoso.com/books")  
  
navigator.SetValue("")  
  
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
  
navigator.SetValue("");  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
 Örnek, `contosoBooks.xml` dosyayı bir giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#2](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/contosoBooks.xml#2)]  
  
### <a name="removing-typed-values"></a>Yazılan değerler kaldırılıyor  
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, yöntemi tarafından yerleştirilen yeni değer, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer, düğüm türüne göre geçerli değilse (örneğin, `-1` türü olan bir öğe üzerinde değerini ayarlamak `xs:positiveInteger` ), bir özel durumla sonuçlanır. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A>Yöntemi `null` parametre olarak da geçirilemez. Sonuç olarak, yazılan bir düğümün değerinin kaldırılması, düğümün şema türüyle uyumlu olmalıdır.  
  
 Aşağıdaki örnek, `price` `book` `contosoBooks.xml` değerini değerine ayarlayarak, dosyasındaki ilk öğenin öğesinin değerini kaldırır <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> `0` . Düğümün değeri kaldırılmaz, ancak kitabýn fiyatı, veri türüne göre kaldırılmıştır `xs:decimal` .  
  
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
  
navigator.SetTypedValue(0)  
  
navigator.MoveToRoot()  
Console.WriteLine(navigator.OuterXml)  
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
  
navigator.SetTypedValue(0);  
  
navigator.MoveToRoot();  
Console.WriteLine(navigator.OuterXml);  
```  
  
## <a name="namespace-nodes"></a>Ad alanı düğümleri  
 Ad alanı düğümleri bir <xref:System.Xml.XmlDocument> nesneden silinemez. Yöntemi kullanarak ad alanı düğümlerini silme girişimleri <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> bir özel durumla sonuçlanır.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özellikleri, <xref:System.Xml.XPath.XPathNavigator> bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir.  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, <xref:System.Xml.XPath.XPathNavigator> belirtilen XML 'nin ayrıştırılmış içeriğiyle bir nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir `string` . Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir nesnenin şu anda bulunduğu alt DÜĞÜMLERIN XML işaretlemesini ve <xref:System.Xml.XPath.XPathNavigator> geçerli düğümün kendisini değiştirir.  
  
 Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> ÖZELLIKLERI bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılabilir. Düğümleri değiştirmek için ve özelliklerini kullanma hakkında daha fazla bilgi için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> bkz. [XPathNavigator kullanarak XML verilerini değiştirme](modify-xml-data-using-xpathnavigator.md) konusu.  
  
## <a name="saving-an-xml-document"></a>XML belgesi kaydetme  
 <xref:System.Xml.XmlDocument>Bu konuda açıklanan yöntemlerin sonucu olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, sınıfının yöntemleri kullanılarak gerçekleştirilir <xref:System.Xml.XmlDocument> . Bir nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için <xref:System.Xml.XmlDocument> bkz. [belgeyi kaydetme ve yazma](saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Ekleme](insert-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](modify-xml-data-using-xpathnavigator.md)
