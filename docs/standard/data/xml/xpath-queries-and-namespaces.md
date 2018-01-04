---
title: "XPath sorguları ve ad alanları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: ef6402be-2f8e-4be2-8d3e-a80891cdef8b
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: eeed1594582765e5079aa1e3d82f95737a79d1f0
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="xpath-queries-and-namespaces"></a>XPath sorguları ve ad alanları
XPath sorguları bir XML belgesi, ad alanlarının farkında olduğundan ve ad alanı öneklerini öğe ve öznitelik adları nitelemek için kullanabilirsiniz. Bir ad alanı öneki ile öğe ve öznitelik adları niteleme belirli bir ad alanına ait düğümlere bir XPath sorgusu tarafından döndürülen düğümleri sınırlar.  
  
 Örneğin, önek `books` eşleyen ad alanına `http://www.contoso.com/books`, ardından aşağıdaki XPath sorgusu `/books:books/books:book` yalnızca seçer `book` ad alanındaki öğeler `http://www.contoso.com/books`.  
  
## <a name="the-xmlnamespacemanager"></a>XmlNamespaceManager  
 Ad alanları bir XPath sorgusu kullanmak için bir nesne türetilmiş <xref:System.Xml.IXmlNamespaceResolver> gibi arabirim <xref:System.Xml.XmlNamespaceManager> sınıfı XPath sorgusu eklenecek öneki ve ad alanı URI'si ile yapılandırılmıştır.  
  
 <xref:System.Xml.XmlNamespaceManager> Nesnesi, her aşağıdaki yollardan biriyle sorgusunda kullanılabilir.  
  
-   <xref:System.Xml.XmlNamespaceManager> Nesnesidir varolan ile ilişkili <xref:System.Xml.XPath.XPathExpression> kullanarak nesne <xref:System.Xml.XPath.XPathExpression.SetContext%2A> yöntemi <xref:System.Xml.XPath.XPathExpression> nesnesi. Ayrıca yeni bir derleme <xref:System.Xml.XPath.XPathExpression> statik kullanarak nesne <xref:System.Xml.XPath.XPathExpression.Compile%2A> XPath ifadesi temsil eden bir dize alan yöntemi ve bir <xref:System.Xml.XmlNamespaceManager> nesne parametreleri ve yeni bir döndürür olarak <xref:System.Xml.XPath.XPathExpression> nesnesi.  
  
-   <xref:System.Xml.XmlNamespaceManager> Nesnenin kendisine geçirilen parametre olarak kabul bir <xref:System.Xml.XPath.XPathNavigator> sınıf XPath ifadesi temsil eden bir dize birlikte yöntemi.  
  
 Yöntemleri şunlardır <xref:System.Xml.XPath.XPathNavigator> nesneyi kabul sınıfı türetilen <xref:System.Xml.IXmlNamespaceResolver> bir parametre olarak arabirimi.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
### <a name="the-default-namespace"></a>Varsayılan Namespace  
 Aşağıdaki XML belgesinde bildirmek için varsayılan ad alanı boş bir önek ile kullanılan `http://www.contoso.com/books` ad alanı.  
  
```xml  
<books xmlns="http://www.example.com/books">  
    <book>  
        <title>Title</title>  
        <author>Author Name</author>  
        <price>5.50</price>  
    </book>  
</books>  
```  
  
 XPath boş önek davranır `null` ad alanı. Diğer bir deyişle, ad alanlarına eşlenen önekleri XPath sorguları kullanılabilir. Bu, varsayılan ad alanını olsa bile da, bir ad alanı bir XML belgesi karşı sorgulamak istiyorsanız, bunun için bir önek tanımlamak yapmanız gerektiği anlamına gelir.  
  
 Örneğin, yukarıdaki XPath XML belgesi için bir önek tanımlamadan sorgu `/books/book` herhangi bir sonuç döndürür değil.  
  
 Bir ad değil, bazı düğümler ve bazı durumlarda bir varsayılan ad alanı belgelerle sorgulanırken Karışıklığı önlemek için bir önek bağlı olması gerekir.  
  
 Aşağıdaki kod, varsayılan ad alanı için bir önek tanımlar ve tüm seçer `book` öğelerinden `http://www.contoso.com/books` ad alanı.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
