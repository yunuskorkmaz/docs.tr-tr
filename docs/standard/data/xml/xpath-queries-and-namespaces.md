---
title: XPath Sorguları ve Ad Alanları
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
ms.openlocfilehash: d3314a7ff4cf957dac4cd8ad0416aad434b19af2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84283201"
---
# <a name="xpath-queries-and-namespaces"></a>XPath Sorguları ve Ad Alanları
XPath sorguları bir XML belgesindeki ad alanlarını algılar ve öğe ve öznitelik adlarını nitelemek için ad alanı öneklerini kullanabilir. Bir ad alanı önekiyle niteleyen öğe ve öznitelik adları, bir XPath sorgusunun döndürdüğü düğümleri yalnızca belirli bir ad alanına ait olan düğümlere sınırlandırır.  
  
 Örneğin, önek `books` ad alanıyla eşleniyorsa `http://www.contoso.com/books` , aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca `book` ad alanındaki öğeleri seçer `http://www.contoso.com/books` .  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Bir XPath sorgusunda ad alanlarını kullanmak için, sınıfı gibi arabiriminden türetilmiş bir nesne, <xref:System.Xml.IXmlNamespaceResolver> <xref:System.Xml.XmlNamespaceManager> ad alanı URI 'Si ve XPath sorgusuna dahil edilecek ön ek ile oluşturulur.  
  
 <xref:System.Xml.XmlNamespaceManager>Nesnesi, aşağıdaki yolların her birinde sorgusunda kullanılabilir.  
  
- <xref:System.Xml.XmlNamespaceManager>Nesnesi, <xref:System.Xml.XPath.XPathExpression> nesnesinin yöntemi kullanılarak varolan bir nesneyle ilişkilendirilir <xref:System.Xml.XPath.XPathExpression.SetContext%2A> <xref:System.Xml.XPath.XPathExpression> . Ayrıca, <xref:System.Xml.XPath.XPathExpression> <xref:System.Xml.XPath.XPathExpression.Compile%2A> XPath ifadesini ve bir nesneyi parametreler olarak temsil eden bir dize alan <xref:System.Xml.XmlNamespaceManager> ve yeni bir nesne döndüren static yöntemi kullanarak yeni bir nesne derleyebilirsiniz <xref:System.Xml.XPath.XPathExpression> .  
  
- <xref:System.Xml.XmlNamespaceManager>Nesnenin kendisi, <xref:System.Xml.XPath.XPathNavigator> XPath ifadesini temsil eden bir dize ile birlikte kabul eden bir sınıf yöntemine parametre olarak geçirilir.  
  
 Aşağıda, <xref:System.Xml.XPath.XPathNavigator> <xref:System.Xml.IXmlNamespaceResolver> arabiriminden bir parametre olarak türetilmiş bir nesneyi kabul eden sınıfının yöntemleri verilmiştir.  
  
- <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
- <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Varsayılan ad alanı  
 Aşağıdaki XML belgesinde, ad alanını bildirmek için boş ön eki olan varsayılan ad alanı kullanılır `http://www.contoso.com/books` .  
  
```xml  
<books xmlns="http://www.contoso.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath, boş öneki `null` ad alanı olarak değerlendirir. Diğer bir deyişle, XPath sorgularında yalnızca ad alanlarına eşlenmiş önekler kullanılabilir. Bu, varsayılan ad alanı olsa bile bir XML belgesinde bir ad alanı üzerinde sorgu yapmak istiyorsanız, bunun için bir ön ek tanımlamanız gerekir.  
  
 Örneğin, yukarıdaki XML belgesi için bir ön ek tanımlamadan, XPath sorgusu `/books/book` herhangi bir sonuç döndürmez.  
  
 Bir önek, bir ad alanında olmayan bazı düğümlerle ve bazıları varsayılan bir ad alanında yer alan bir düğüm sorgulanırken belirsizlik oluşmasını engellemek için bağlanmalıdır.  
  
 Aşağıdaki kod, varsayılan ad alanı için bir ön ek tanımlar ve `book` ad alanındaki tüm öğeleri seçer `http://www.contoso.com/books` .  
  
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
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](node-types-recognized-with-xpath-queries.md)
- [Derlenmiş XPath İfadeleri](compiled-xpath-expressions.md)
