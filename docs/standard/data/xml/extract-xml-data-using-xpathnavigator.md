---
title: XPathNavigator kullanarak XML verilerini ayıklama
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 095b0987-ee4b-4595-a160-da1c956ad576
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d838f3d9f4c9400fbbef0fb24f5275eff2038c49
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086784"
---
# <a name="extract-xml-data-using-xpathnavigator"></a>XPathNavigator kullanarak XML verilerini ayıklama
Microsoft .NET Framework XML belgesinde temsil etmek için birkaç farklı yolu vardır. Bu kullanarak içerir bir <xref:System.String>, kullanarak veya <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, <xref:System.Xml.XmlDocument>, veya <xref:System.Xml.XPath.XPathDocument> sınıfları. Bu bir XML belgesi farklı temsilleri arasında taşıma kolaylaştırmak için <xref:System.Xml.XPath.XPathNavigator> XML olarak ayıklanmasında sınıfı bir dizi yöntem ve özellik sağlar bir <xref:System.String>, <xref:System.Xml.XmlReader> nesne veya <xref:System.Xml.XmlWriter> nesne.  
  
## <a name="convert-an-xpathnavigator-to-a-string"></a>Bir XPathNavigator bir dizeye Dönüştür  
 <xref:System.Xml.XPath.XPathNavigator.OuterXml%2A> Özelliği <xref:System.Xml.XPath.XPathNavigator> sınıfı, tüm XML belgesi işaretleme veya biçimlendirme yalnızca tek bir düğüm ve onun alt düğümleri almak için kullanılır.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.InnerXml%2A> Özelliği yalnızca alt biçimlendirme düğümünün düğüm alır.  
  
 Aşağıdaki kod örneğinde yer alan tüm bir XML belgesi kaydetmek gösterilmiştir bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin bir <xref:System.String>, yanı sıra tek bir düğüm ve onun alt düğümleri.  
  
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
  
## <a name="convert-an-xpathnavigator-to-an-xmlreader"></a>XmlReader'a bir XPathNavigator Dönüştür  
 <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi akışını bir XML belgesi veya tek bir düğüm ve onun alt düğümleri için tüm içeriği için kullanılan bir <xref:System.Xml.XmlReader> nesne.  
  
 Zaman <xref:System.Xml.XmlReader> nesne geçerli düğüm ve onun alt düğümleri ile oluşturulan <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği <xref:System.Xml.ReadState.Initial>. Zaman <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.Read%2A> yöntemi ilk kez çağrıldığında <xref:System.Xml.XmlReader> geçerli düğüme taşınır <xref:System.Xml.XPath.XPathNavigator>. Yeni <xref:System.Xml.XmlReader> nesne XML ağacı sonuna ulaşıncaya kadar okuyun devam eder. Bu noktada, <xref:System.Xml.XmlReader.Read%2A> yöntemi döndürür `false` ve <xref:System.Xml.XmlReader> nesnenin <xref:System.Xml.XmlReader.ReadState%2A> özelliği <xref:System.Xml.ReadState.EndOfFile>.  
  
 <xref:System.Xml.XPath.XPathNavigator> Nesnenin konumu oluşturma ve hareketini tarafından değiştirilmeden <xref:System.Xml.XmlReader> nesne. <xref:System.Xml.XPath.XPathNavigator.ReadSubtree%2A> Yöntemi, yalnızca bir öğe veya kök düğümde getirildiğinde geçerli.  
  
 Aşağıdaki örnek nasıl alınacağını gösterir. bir <xref:System.Xml.XmlReader> nesnesi içeren tüm XML belge içinde bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüm ve onun alt düğümleri yanı sıra nesnesi.  
  
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
  
 Örnek alan `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
## <a name="converting-an-xpathnavigator-to-an-xmlwriter"></a>Bir XPathNavigator XmlWriter için dönüştürme  
 <xref:System.Xml.XPath.XPathNavigator.WriteSubtree%2A> Yöntemi akışını bir XML belgesi veya tek bir düğüm ve onun alt düğümleri için tüm içeriği için kullanılan bir <xref:System.Xml.XmlWriter> nesne.  
  
 <xref:System.Xml.XPath.XPathNavigator> Nesnenin konumu tarafından oluşturulmasını değişmeden <xref:System.Xml.XmlWriter> nesne.  
  
 Aşağıdaki örnek nasıl alınacağını gösterir. bir <xref:System.Xml.XmlWriter> nesnesi içeren tüm XML belge içinde bir <xref:System.Xml.XPath.XPathDocument> tek bir düğüm ve onun alt düğümleri yanı sıra nesnesi.  
  
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
  
 Örnek alan `books.xml` girdi olarak bu konudaki daha önce dosya bulundu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathNavigator Kullanarak Düğüm Kümesinde Gezinme](../../../../docs/standard/data/xml/node-set-navigation-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak Öznitelik ve Ad Alanı Düğümünde Gezinme](../../../../docs/standard/data/xml/attribute-and-namespace-node-navigation-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak Türü Kesin Olarak Belirtilmiş XML Verilerine Erişme](../../../../docs/standard/data/xml/accessing-strongly-typed-xml-data-using-xpathnavigator.md)
