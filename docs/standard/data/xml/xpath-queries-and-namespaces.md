---
title: XPath Sorguları ve Ad Alanları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0704e78a0e7fbf3987b3bc75bb46e135f00110e9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64615347"
---
# <a name="xpath-queries-and-namespaces"></a>XPath Sorguları ve Ad Alanları
XPath sorguları, XML belgesinde ad alanlarının farkındayız ve ad alanı öneklerini öğe ve öznitelik adları nitelemek için kullanabilirsiniz. Ad alanı öneki öğe ve öznitelik adlarını niteleme yalnızca belirli bir ad alanına ait düğümleri bir XPath sorgusu tarafından döndürülen düğümleri sınırlar.  
  
 Örneğin, ön eki `books` eşleyen ad alanına `http://www.contoso.com/books`, ardından aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca seçer `book` ad alanındaki öğeler `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Bir XPath sorgusu ad alanları kullanmak için bir nesne türetilen <xref:System.Xml.IXmlNamespaceResolver> gibi arabirim <xref:System.Xml.XmlNamespaceManager> sınıfı XPath sorgusundaki eklenecek önek ve ad alanı URI ile oluşturulur.  
  
 <xref:System.Xml.XmlNamespaceManager> Sorguda aşağıdaki yollardan biriyle her nesne kullanılabilir.  
  
- <xref:System.Xml.XmlNamespaceManager> Nesnedir varolan ile ilişkili <xref:System.Xml.XPath.XPathExpression> kullanarak nesne <xref:System.Xml.XPath.XPathExpression.SetContext%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> nesne. Ayrıca yeni bir derleme <xref:System.Xml.XPath.XPathExpression> 'using static nesne <xref:System.Xml.XPath.XPathExpression.Compile%2A> yöntemi XPath ifadesi temsil eden bir dize alır ve bir <xref:System.Xml.XmlNamespaceManager> nesnesi parametrelerini ve yeni bir döndürür olarak <xref:System.Xml.XPath.XPathExpression> nesne.  
  
- <xref:System.Xml.XmlNamespaceManager> Nesnesinin kendisi bir kabul etmek için parametre olarak geçirilir <xref:System.Xml.XPath.XPathNavigator> sınıfı XPath ifadesi temsil eden bir dize ile birlikte yöntemi.  
  
 Yöntemleri şunlardır <xref:System.Xml.XPath.XPathNavigator> kabul eden bir nesne sınıfı türetilen <xref:System.Xml.IXmlNamespaceResolver> arabirimi bir parametre olarak.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Varsayılan Namespace  
 Aşağıdaki XML belgesinde varsayılan ad alanı ön eki boş bildirmek için kullanılan `http://www.contoso.com/books` ad alanı.  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath boş önek olarak değerlendirir `null` ad alanı. Diğer bir deyişle, yalnızca ad alanlarına eşlenen ön ekleri XPath sorguları içinde kullanılabilir. Bu, varsayılan ad alanı olsa da, bir ad alanı bir XML belgesi karşı sorgulamak istiyorsanız, bunun için bir ön eki tanımlamak gerektiğini anlamına gelir.  
  
 Örneğin, yukarıdaki XPath XML belgesi için bir önek tanımlamadan sorgu `/books/book` herhangi bir sonuç döndürmek değil.  
  
 Belgeler, bir ad alanındaki bazı düğümler ve bazı durumlarda bir varsayılan ad alanı sorgulanırken belirsizlik önlemek için bir önek bağlı olmalıdır.  
  
 Aşağıdaki kod bir varsayılan ad alanı öneki tanımlar ve tüm seçer `book` öğelerden `http://www.contoso.com/books` ad alanı.  
  
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
