---
title: XPathNavigator Kullanarak XML Verilerini Ayıklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: e639931204a416c3cde87044730364a4f387799a
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287772"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verilerini Ayıklama
Microsoft .NET çerçevesindeki bir XML belgesini temsil etmenin birkaç farklı yolu vardır. Bu,, veya kullanarak, veya <xref:System.String> sınıflarını içerir <xref:System.Xml.XmlReader> <xref:System.Xml.XmlWriter> <xref:System.Xml.XmlDocument> <xref:System.Xml.XPath.XPathDocument> . XML belgesinin bu farklı temsilleri arasında geçmeyi kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> sınıfı, XML <xref:System.String> 'i bir, <xref:System.Xml.XmlReader> nesne veya nesne olarak ayıklamaya yönelik çeşitli yöntemler ve özellikler sağlar <xref:System.Xml.XmlWriter> .  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Bir XPathNavigator 'yi dizeye Dönüştür  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A>Sınıfının özelliği, <xref:System.Xml.XPath.XPathNavigator> tüm XML belgesi veya yalnızca tek bir düğüm ve onun alt düğümleri için biçimlendirme almak için kullanılır.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A>Özelliği, bir düğümün yalnızca alt düğümlerinin işaretlemesini alır.  
  
 Aşağıdaki kod örneği, bir nesnesinde bulunan bir XML belgesinin tamamını <xref:System.Xml.XPath.XPathNavigator> <xref:System.String> , tek bir düğüm ve onun alt düğümleri olarak nasıl kaydedileceğini gösterir.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("input.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Save the entire input.xml document to a string.  
Dim xml As String = navigator.OuterXml  
  
' Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element)  
Dim root As String = navigator.OuterXml  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Save the entire input.xml document to a string.  
string xml = navigator.OuterXml;  
  
// Now save the Root element and its child nodes to a string.  
navigator.MoveToChild(XPathNodeType.Element);  
string root = navigator.OuterXml;  
```  
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Bir XPathNavigator 'yi XmlReader 'ye dönüştürme  
 Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> XML belgesinin tüm içeriğini veya tek bir düğümü ve onun alt düğümlerini bir nesnesine akışa almak için kullanılır <xref:System.Xml.XmlReader> .  
  
 <xref:System.Xml.XmlReader>Nesne geçerli düğüm ve onun alt düğümleri ile oluşturulduğunda <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği olarak ayarlanır <xref:System.Xml.ReadState.Initial> . <xref:System.Xml.XmlReader>Nesnenin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında,, <xref:System.Xml.XmlReader> öğesinin geçerli düğümüne taşınır <xref:System.Xml.XPath.XPathNavigator> . Yeni <xref:System.Xml.XmlReader> nesne, xml ağacının sonuna ulaşılana kadar okumaya devam eder. Bu noktada, <xref:System.Xml.XmlReader.Read%2A> yöntemi döner `false` ve <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği olarak ayarlanır <xref:System.Xml.ReadState.EndOfFile> .  
  
 Nesnenin <xref:System.Xml.XPath.XPathNavigator> konumu nesnenin oluşturulması veya taşınması tarafından değiştirilmez <xref:System.Xml.XmlReader> . <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A>Yöntemi yalnızca bir öğe veya kök düğüm üzerinde konumlandırıldığında geçerlidir.  
  
 Aşağıdaki örnek, <xref:System.Xml.XmlReader> bir nesnenin tüm XML belgesini <xref:System.Xml.XPath.XPathDocument> ve tek bir düğüm ve onun alt düğümlerini içeren bir nesnenin nasıl alınacağını gösterir.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlReader.  
Dim xml As XmlReader = navigator.ReadSubtree()  
  
While xml.Read()  
    Console.WriteLine(xml.ReadInnerXml())  
End While  
  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlReader = navigator.ReadSubtree()  
  
While book.Read()  
    Console.WriteLine(book.ReadInnerXml())  
End While  
  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlReader.  
XmlReader xml = navigator.ReadSubtree();  
  
while (xml.Read())  
{  
    Console.WriteLine(xml.ReadInnerXml());  
}  
  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlReader.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlReader book = navigator.ReadSubtree();  
  
while (book.Read())  
{  
    Console.WriteLine(book.ReadInnerXml());  
}  
  
book.Close();  
```  
  
 Örnek, `books.xml` dosyayı giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>XPathNavigator 'yi XmlWriter 'a dönüştürme  
 Yöntemi, bir <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> XML belgesinin tüm içeriğini veya tek bir düğümü ve onun alt düğümlerini bir nesnesine akışa almak için kullanılır <xref:System.Xml.XmlWriter> .  
  
 <xref:System.Xml.XPath.XPathNavigator>Nesnenin konumu nesnenin oluşturulmasıyla değiştirilmez <xref:System.Xml.XmlWriter> .  
  
 Aşağıdaki örnek, <xref:System.Xml.XmlWriter> bir nesnenin tüm XML belgesini <xref:System.Xml.XPath.XPathDocument> ve tek bir düğüm ve onun alt düğümlerini içeren bir nesnenin nasıl alınacağını gösterir.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
' Stream the entire XML document to the XmlWriter.  
Dim xml As XmlWriter = XmlWriter.Create("newbooks.xml")  
navigator.WriteSubtree(xml)  
xml.Close()  
  
' Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "")  
navigator.MoveToChild("book", "")  
  
Dim book As XmlWriter = XmlWriter.Create("book.xml")  
navigator.WriteSubtree(book)  
book.Close()  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
// Stream the entire XML document to the XmlWriter.  
XmlWriter xml = XmlWriter.Create("newbooks.xml");  
navigator.WriteSubtree(xml);  
xml.Close();  
  
// Stream the book element and its child nodes to the XmlWriter.  
navigator.MoveToChild("bookstore", "");  
navigator.MoveToChild("book", "");  
  
XmlWriter book = XmlWriter.Create("book.xml");  
navigator.WriteSubtree(book);  
book.Close();  
```  
  
 Örnek, `books.xml` Bu konunun önceki kısımlarında bulunan dosyayı giriş olarak alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](accessing-strongly-typed-xml-data-using-xpathnavigator.md)
