---
title: XPathNavigator kullanarak XML veri ayıklamak
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3191528e1add5a12019c2ad3a2cd87aa73fe1df7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572014"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>XPathNavigator kullanarak XML veri ayıklamak
Microsoft .NET Framework XML belgesinde temsil etmek için birkaç farklı yolu vardır. Bu kullanmayı da içeren bir <xref:System.String>, veya kullanarak <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, veya <xref:System.Xml.XPath.XPathDocument> sınıfları. Bu bir XML belgesi farklı sunumu arasında taşıma kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> sınıfı XML olarak ayıklanması için bir dizi yöntem ve özellikleri sağlar bir <xref:System.String>, <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XmlWriter> nesnesi.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Bir XPathNavigator bir dizeye dönüştürme  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı, tüm XML belgenin biçimlendirme veya işaretleme yalnızca tek bir düğüme ve alt düğümleri almak için kullanılır.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği yalnızca alt biçimlendirme düğümün öğelerinin alır.  
  
 Aşağıdaki kod örneğinde yer alan tüm XML belgesi kaydedileceği gösterilmektedir bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin bir <xref:System.String>, tek bir düğüme ve alt düğümlerini yanı sıra.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>Bir XPathNavigator XmlReader için Dönüştür  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi bir XML belgesi veya yalnızca tek bir düğüme ve alt düğümlerini tüm içeriğini akış için kullanılan bir <xref:System.Xml.XmlReader> nesnesi.  
  
 Zaman <xref:System.Xml.XmlReader> nesne geçerli düğüme ve alt düğümlerini ile oluşturulur <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği ayarlanmış <xref:System.Xml.ReadState.Initial>. Zaman <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında <xref:System.Xml.XmlReader> geçerli düğüme taşınır <xref:System.Xml.XPath.XPathNavigator>. Yeni <xref:System.Xml.XmlReader> XML ağaç sonuna ulaşılana kadar okuma nesne devam eder. Bu noktada, <xref:System.Xml.XmlReader.Read%2A> yöntemi döndürür `false` ve <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği ayarlanmış <xref:System.Xml.ReadState.EndOfFile>.  
  
 <xref:System.Xml.XPath.XPathNavigator> Oluşturma veya hareketini nesnenin konumu değişmeden <xref:System.Xml.XmlReader> nesnesi. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi geçerli yalnızca bir öğe veya kök düğümde konumlandırıldı.  
  
 Aşağıdaki örnekte nasıl alınacağını gösteren bir <xref:System.Xml.XmlReader> tüm XML içeren bir nesne belge bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüme ve alt düğümlerini yanı sıra nesnesi.  
  
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
  
 Örnek alır `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Bir XPathNavigator bir XmlWriter dönüştürme  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Yöntemi bir XML belgesi veya yalnızca tek bir düğüme ve alt düğümlerini tüm içeriğini akış için kullanılan bir <xref:System.Xml.XmlWriter> nesnesi.  
  
 <xref:System.Xml.XPath.XPathNavigator> Nesnenin konumu tarafından oluşturulmasını değişmeden <xref:System.Xml.XmlWriter> nesnesi.  
  
 Aşağıdaki örnekte nasıl alınacağını gösteren bir <xref:System.Xml.XmlWriter> tüm XML içeren bir nesne belge bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüme ve alt düğümlerini yanı sıra nesnesi.  
  
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
  
 Örnek alır `books.xml` girdi olarak bu konunun önceki kısımlarında dosyası bulundu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
