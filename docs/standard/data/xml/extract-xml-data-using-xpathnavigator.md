---
title: XPathNavigator Kullanarak XML Verilerini Ayıklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
ms.openlocfilehash: 627da3c8c45d007e677c4f92f4d5cd602d34ae84
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710862"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>XPathNavigator Kullanarak XML Verilerini Ayıklama
Microsoft .NET çerçevesindeki bir XML belgesini temsil etmenin birkaç farklı yolu vardır. Bu, bir <xref:System.String>kullanmayı veya <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>veya <xref:System.Xml.XPath.XPathDocument> sınıflarını kullanmayı içerir. Bir XML belgesinin bu farklı temsilleri arasında geçmeyi kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> sınıfı, XML 'yi bir <xref:System.String>, <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XmlWriter> nesnesi olarak ayıklamaya yönelik çeşitli yöntemler ve özellikler sağlar.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Bir XPathNavigator 'yi dizeye Dönüştür  
 <xref:System.Xml.XPath.XPathNavigator> sınıfının <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> özelliği, tüm XML belgesi veya yalnızca tek bir düğümün ve onun alt düğümlerinin işaretlemesini almak için kullanılır.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> özelliği, bir düğümün yalnızca alt düğümlerinin işaretlemesini alır.  
  
 Aşağıdaki kod örneği, bir <xref:System.Xml.XPath.XPathNavigator> nesnesinde bulunan bir XML belgesinin tamamını, tek bir düğüm ve onun alt düğümlerinin yanı sıra bir <xref:System.String>olarak nasıl kaydedileceğini gösterir.  
  
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
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> yöntemi bir XML belgesinin tüm içeriğini veya tek bir düğümü ve onun alt düğümlerini bir <xref:System.Xml.XmlReader> nesnesine akışa almak için kullanılır.  
  
 <xref:System.Xml.XmlReader> nesnesi geçerli düğüm ve onun alt düğümleri ile oluşturulduğunda, <xref:System.Xml.XmlReader> nesnesinin <xref:System.Xml.XmlReader.ReadState%2A> özelliği <xref:System.Xml.ReadState.Initial>olarak ayarlanır. <xref:System.Xml.XmlReader> nesnesinin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında <xref:System.Xml.XmlReader> <xref:System.Xml.XPath.XPathNavigator>geçerli düğümüne taşınır. Yeni <xref:System.Xml.XmlReader> nesnesi, XML ağacının sonuna ulaşılana kadar okumaya devam eder. Bu noktada <xref:System.Xml.XmlReader.Read%2A> yöntemi `false` döndürür ve <xref:System.Xml.XmlReader> nesnesinin <xref:System.Xml.XmlReader.ReadState%2A> özelliği <xref:System.Xml.ReadState.EndOfFile>olarak ayarlanır.  
  
 <xref:System.Xml.XPath.XPathNavigator> nesnenin konumu, <xref:System.Xml.XmlReader> nesnesinin oluşturulması veya taşınması tarafından değiştirilmez. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> yöntemi yalnızca bir öğe veya kök düğüm üzerinde konumlandırıldığında geçerlidir.  
  
 Aşağıdaki örnek, tüm XML <xref:System.Xml.XPath.XPathDocument> belgesini içeren bir <xref:System.Xml.XmlReader> nesnesinin ve tek bir düğüm ve onun alt düğümlerinin nasıl alınacağını gösterir.  
  
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
  
 Örnek, `books.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>XPathNavigator 'yi XmlWriter 'a dönüştürme  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> yöntemi bir XML belgesinin tüm içeriğini veya tek bir düğümü ve onun alt düğümlerini bir <xref:System.Xml.XmlWriter> nesnesine akışa almak için kullanılır.  
  
 <xref:System.Xml.XPath.XPathNavigator> nesnenin konumu, <xref:System.Xml.XmlWriter> nesnesinin oluşturulmasıyla değiştirilmez.  
  
 Aşağıdaki örnek, tüm XML <xref:System.Xml.XPath.XPathDocument> belgesini içeren bir <xref:System.Xml.XmlWriter> nesnesinin ve tek bir düğüm ve onun alt düğümlerinin nasıl alınacağını gösterir.  
  
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
  
 Örnek, bu konunun önceki kısımlarında bulunan `books.xml` dosyasını giriş olarak alır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
