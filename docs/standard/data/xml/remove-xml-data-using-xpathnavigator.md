---
title: XPathNavigator Kullanarak XML Verilerini Kaldırma
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 9f436bca-1b96-494b-a6d2-e102c7551752
ms.openlocfilehash: 062a98a9cc10e6be00f165cf617de2d92d65acbf
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710368"
---
# <a name="remove-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verilerini Kaldırma
Sınıfı <xref:System.Xml.XPath.XPathNavigator> , bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılan bir yöntemler kümesi sağlar. Bu yöntemleri kullanabilmeniz için <xref:System.Xml.XPath.XPathNavigator> nesnesi düzenlenebilir olmalıdır, yani <xref:System.Xml.XPath.XPathNavigator.CanEdit%2A> özelliği olmalıdır. `true`  
  
 <xref:System.Xml.XPath.XPathNavigator>bir XML belgesini düzenleyebilen nesneler, <xref:System.Xml.XmlDocument.CreateNavigator%2A> <xref:System.Xml.XmlDocument> sınıfının yöntemiyle oluşturulur. <xref:System.Xml.XPath.XPathNavigator>sınıfı tarafından oluşturulan nesneler salt okunurdur ve bir <xref:System.Xml.XPath.XPathDocument> nesne tarafından oluşturulan <xref:System.NotSupportedException> <xref:System.Xml.XPath.XPathNavigator> nesnenin Editing yöntemlerini kullanma girişimleri bir ile sonuçlanır. <xref:System.Xml.XPath.XPathDocument>  
  
 Düzenlenebilir <xref:System.Xml.XPath.XPathNavigator> nesneler oluşturma hakkında daha fazla bilgi için bkz. [XPathDocument ve XmlDocument kullanarak XML verilerini okuma](../../../../docs/standard/data/xml/reading-xml-data-using-xpathdocument-and-xmldocument.md).  
  
## <a name="removing-nodes"></a>Düğümler kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı, bir XML <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> belgesinden düğümleri kaldırmak için yöntemini sağlar.  
  
### <a name="removing-a-node"></a>Düğüm kaldırma  
 Sınıfı, bir <xref:System.Xml.XPath.XPathNavigator> nesne <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> Şu anda bir XML belgesinden konumlandırılmış olan geçerli düğümü silmeye yönelik yöntemi sağlar. <xref:System.Xml.XPath.XPathNavigator>  
  
 Bir düğüm <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi kullanılarak silindikten sonra, artık <xref:System.Xml.XmlDocument> nesnenin kökünden ulaşılamaz. Düğüm silindikten <xref:System.Xml.XPath.XPathNavigator> sonra, silinen düğümün üst düğümüne yerleştirilir.  
  
 Silme işlemi, silinen düğümde konumlandırılmış herhangi bir <xref:System.Xml.XPath.XPathNavigator> nesnenin konumunu etkilemez. Bu <xref:System.Xml.XPath.XPathNavigator> nesneler, Silinen alt ağaçta taşıyabilecekleri, ancak <xref:System.Xml.XPath.XPathNavigator> sınıfın normal düğüm kümesi gezinti yöntemleri kullanılarak ana düğüm ağacına taşınamayacak anlamda geçerlidir.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator> Sınıfının <xref:System.Xml.XPath.XPathNavigator.MoveTo%2A> yöntemi, bu <xref:System.Xml.XPath.XPathNavigator> nesneleri ana düğüm ağacına veya ana düğüm ağacından Silinen alt ağaca geri taşımak için kullanılabilir.  
  
 Aşağıdaki `price` örnekte, `book` `contosoBooks.xml` dosyanın ilk öğesinin öğesi <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi kullanılarak silinir. Öğe silindikten sonra <xref:System.Xml.XPath.XPathNavigator> nesnenin konumu üst `book` öğedir. `price`  
  
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
 Öznitelik düğümleri bir XML belgesinden <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> yöntemi kullanılarak kaldırılır.  
  
 Bir öznitelik düğümü silindikten sonra, artık <xref:System.Xml.XmlDocument> nesnenin kök düğümünden ulaşılamaz ve <xref:System.Xml.XPath.XPathNavigator> nesne üst öğe üzerinde konumlandırılır.  
  
#### <a name="default-attributes"></a>Varsayılan öznitelikler  
 Öznitelikleri kaldırmak için kullanılan yöntemden bağımsız olarak, XML belgesi için DTD veya XML şemasında varsayılan öznitelikler olarak tanımlanan öznitelikleri kaldırmaya ilişkin özel sınırlamalar vardır. Ait oldukları öğe da kaldırılmadığı takdirde varsayılan öznitelikler kaldırılamaz. Varsayılan öznitelikler, varsayılan öznitelikleri olan öğeler için her zaman mevcuttur ve sonuç olarak, varsayılan bir özniteliğin silinmesi, öğesine eklenen ve varsayılan değere başlatılan bir değiştirme özniteliğiyle sonuçlanır.  
  
## <a name="removing-values"></a>Değerler kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı, <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> bir XML belgesinden <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> türsüz ve yazılan değerleri kaldırmak için ve yöntemlerini sağlar.  
  
### <a name="removing-untyped-values"></a>Türsüz değerler kaldırılıyor  
 <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemi, bir parametre olarak geçirilen `string` türsüz değeri <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda konumlandırılmış olan düğümün değeri olarak ekler. <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> Yöntemine boş bir dize geçirilme, geçerli düğümün değerini kaldırır.  
  
 Aşağıdaki `price` örnek, `book` `contosoBooks.xml` <xref:System.Xml.XPath.XPathNavigator.SetValue%2A> yöntemi kullanılarak dosyasındaki ilk öğenin öğesinin değerini kaldırır.  
  
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
 Bir düğümün türü bir W3C XML şeması basit türü olduğunda, <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> yöntemi tarafından yerleştirilen yeni değer, değer ayarlanmadan önce basit türdeki modellerle denetlenir. Yeni değer, düğüm türüne göre geçerli değilse (örneğin, türü olan bir öğe `-1` üzerinde değerini ayarlamak `xs:positiveInteger`), bir özel durumla sonuçlanır. <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> Yöntemi parametre olarak da geçirilemez `null` . Sonuç olarak, yazılan bir düğümün değerinin kaldırılması, düğümün şema türüyle uyumlu olmalıdır.  
  
 Aşağıdaki örnek, değerini değerine ayarlayarak `price` , `book` `contosoBooks.xml` <xref:System.Xml.XPath.XPathNavigator.SetTypedValue%2A> dosyasındaki ilk öğenin öğesinin değerini kaldırır. `0` Düğümün değeri kaldırılmaz, ancak kitabýn fiyatı, veri türüne göre kaldırılmıştır `xs:decimal`.  
  
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
 Ad alanı düğümleri bir <xref:System.Xml.XmlDocument> nesneden silinemez. <xref:System.Xml.XPath.XPathNavigator.DeleteSelf%2A> Yöntemi kullanarak ad alanı düğümlerini silme girişimleri bir özel durumla sonuçlanır.  
  
## <a name="the-innerxml-and-outerxml-properties"></a>InnerXml ve OuterXml özellikleri  
 Sınıfının ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> bir <xref:System.Xml.XPath.XPathNavigator> NESNENIN Şu anda konumlandırılmış olduğu düğümlerin XML işaretlemesini değiştirir. <xref:System.Xml.XPath.XPathNavigator>  
  
 <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği, belirtilen XML `string`'nin ayrıştırılmış içeriğiyle bir <xref:System.Xml.XPath.XPathNavigator> nesne şu anda konumlandırılmış olan alt düğümlerin XML işaretlemesini değiştirir. Benzer şekilde, <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği de bir <xref:System.Xml.XPath.XPathNavigator> nesnenin şu anda bulunduğu alt düğümlerin XML işaretlemesini ve geçerli düğümün kendisini değiştirir.  
  
 Bu konuda açıklanan yöntemlere ek olarak, <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özellikleri bir XML belgesinden düğümleri ve değerleri kaldırmak için kullanılabilir. Düğümleri değiştirmek için <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> ve <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliklerini kullanma hakkında daha fazla bilgi için bkz. [XPathNavigator kullanarak XML verilerini değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md) konusu.  
  
## <a name="saving-an-xml-document"></a>XML belgesi kaydetme  
 Bu konuda açıklanan yöntemlerin sonucu <xref:System.Xml.XmlDocument> olarak bir nesne üzerinde yapılan değişikliklerin kaydedilmesi, <xref:System.Xml.XmlDocument> sınıfının yöntemleri kullanılarak gerçekleştirilir. Bir <xref:System.Xml.XmlDocument> nesne üzerinde yapılan değişiklikleri kaydetme hakkında daha fazla bilgi için bkz. [belgeyi kaydetme ve yazma](../../../../docs/standard/data/xml/saving-and-writing-a-document.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Ekleme](../../../../docs/standard/data/xml/insert-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XML Verilerini Değiştirme](../../../../docs/standard/data/xml/modify-xml-data-using-xpathnavigator.md)
