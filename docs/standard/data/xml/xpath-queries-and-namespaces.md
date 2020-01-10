---
title: XPath Sorguları ve Ad Alanları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: 91503ce0bffa1a9390432a51bff1ef10d80f563a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709783"
---
# <a name="xpath-queries-and-namespaces"></a>XPath Sorguları ve Ad Alanları
XPath sorguları bir XML belgesindeki ad alanlarını algılar ve öğe ve öznitelik adlarını nitelemek için ad alanı öneklerini kullanabilir. Bir ad alanı önekiyle niteleyen öğe ve öznitelik adları, bir XPath sorgusunun döndürdüğü düğümleri yalnızca belirli bir ad alanına ait olan düğümlere sınırlandırır.  
  
 Örneğin, ön ek `books` `http://www.contoso.com/books`ad alanıyla eşleniyorsa, aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca ad alanı `http://www.contoso.com/books``book` öğelerini seçer.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Bir XPath sorgusunda ad alanlarını kullanmak için, <xref:System.Xml.XmlNamespaceManager> sınıfı gibi <xref:System.Xml.IXmlNamespaceResolver> arabiriminden türetilmiş bir nesne, ad alanı URI 'SI ve XPath sorgusuna dahil edilecek ön ek ile oluşturulur.  
  
 <xref:System.Xml.XmlNamespaceManager> nesnesi, aşağıdaki yolların her birinde sorgusunda kullanılabilir.  
  
- <xref:System.Xml.XmlNamespaceManager> nesnesi, <xref:System.Xml.XPath.XPathExpression> nesnesinin <xref:System.Xml.XPath.XPathExpression.SetContext%2A> yöntemi kullanılarak mevcut bir <xref:System.Xml.XPath.XPathExpression> nesnesi ile ilişkilendirilir. Ayrıca, XPath ifadesini ve bir <xref:System.Xml.XmlNamespaceManager> nesnesini parametre olarak temsil eden bir dize alan ve yeni bir <xref:System.Xml.XPath.XPathExpression> nesnesi döndüren statik <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemini kullanarak yeni bir <xref:System.Xml.XPath.XPathExpression> nesnesi derleyebilirsiniz.  
  
- <xref:System.Xml.XmlNamespaceManager> nesnenin kendisi, XPath ifadesini temsil eden bir dize ile birlikte kabul eden bir <xref:System.Xml.XPath.XPathNavigator> sınıf yöntemine parametre olarak geçirilir.  
  
 Aşağıda, bir parametre olarak <xref:System.Xml.IXmlNamespaceResolver> arabiriminden türetilmiş bir nesneyi kabul eden <xref:System.Xml.XPath.XPathNavigator> sınıfının yöntemleri verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Varsayılan ad alanı  
 Aşağıdaki XML belgesinde, boş bir ön eki olan varsayılan ad alanı `http://www.contoso.com/books` ad alanını bildirmek için kullanılır.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath, `null` ad alanı olarak boş ön eki değerlendirir. Diğer bir deyişle, XPath sorgularında yalnızca ad alanlarına eşlenmiş önekler kullanılabilir. Bu, varsayılan ad alanı olsa bile bir XML belgesinde bir ad alanı üzerinde sorgu yapmak istiyorsanız, bunun için bir ön ek tanımlamanız gerekir.  
  
 Örneğin, yukarıdaki XML belgesi için bir ön ek tanımlamadan, XPath sorgu `/books/book` hiçbir sonuç döndürmez.  
  
 Bir önek, bir ad alanında olmayan bazı düğümlerle ve bazıları varsayılan bir ad alanında yer alan bir düğüm sorgulanırken belirsizlik oluşmasını engellemek için bağlanmalıdır.  
  
 Aşağıdaki kod, varsayılan ad alanı için bir ön ek tanımlar ve `http://www.contoso.com/books` ad alanındaki tüm `book` öğelerini seçer.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim query As XPathExpression = navigator.Compile("/books:books/books:book")  
Dim manager As XmlNamespaceManager = New XmlNamespaceManager(navigator.NameTable)  
manager.AddNamespace("books", "http://www.contoso.com/books")  
query.SetContext(manager)  
Dim nodes As XPathNodeIterator = navigator.Select(query)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathExpression query = navigator.Compile("/books:books/books:book");  
XmlNamespaceManager manager = new XmlNamespaceManager(navigator.NameTable);  
manager.AddNamespace("books", "http://www.contoso.com/books");  
query.SetContext(manager);  
XPathNodeIterator nodes = navigator.Select(query);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
