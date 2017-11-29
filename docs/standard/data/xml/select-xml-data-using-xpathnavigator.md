---
title: "XML verileri XPathNavigator kullanarak seçin"
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
ms.assetid: c268c49e-32b9-4171-b782-dcb7b065fa73
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f63f23b1a07fbe77e77598cd05dcd25ee8ec158
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="select-xml-data-using-xpathnavigator"></a>XML verileri XPathNavigator kullanarak seçin
<xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümler kümesi seçmek için kullanılan yöntemler kümesi sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne. Seçildiğinde, seçilen düğümler küme üzerinde yineleyebilirsiniz.  
  
## <a name="xpathnavigator-selection-methods"></a>XPathNavigator seçimi yöntemleri  
 <xref:System.Xml.XPath.XPathNavigator> Sınıfı düğümler kümesi seçmek için kullanılan yöntemler kümesi sağlar bir <xref:System.Xml.XPath.XPathDocument> veya <xref:System.Xml.XmlDocument> bir XPath ifadesi kullanarak nesne. <xref:System.Xml.XPath.XPathNavigator> Sınıfı ayrıca bir XPath ifadesi kullanarak daha hızlı üst, alt ve alt düğümlerini seçmek için en iyi duruma getirilmiş yöntemler kümesi sağlar. Seçili düğüm kümesi döndürülür bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya bir <xref:System.Xml.XPath.XPathNavigator> tek Seçili düğümün söz konusu olduğunda nesne.  
  
### <a name="selecting-nodes-using-xpath-expressions"></a>XPath ifadeler kullanarak düğümleri seçme  
 Bir XPath ifadesi kullanarak düğümleri kümesi seçmek için aşağıdaki seçimi yöntemlerden birini kullanın.  
  
-   <xref:System.Xml.XPath.XPathNavigator.Select%2A>  
  
-   <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A>  
  
 Çağrıldığında, bu yöntemleri serbestçe kullanarak gezinme düğümleri kümesi döndürür. bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi veya bir <xref:System.Xml.XPath.XPathNavigator> tek Seçili düğümün söz konusu olduğunda nesne.  
  
 Gezinme bir <xref:System.Xml.XPath.XPathNodeIterator> nesne konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> oluşturmak için kullanılan nesne. <xref:System.Xml.XPath.XPathNavigator> Döndürülen nesne <xref:System.Xml.XPath.XPathNavigator.SelectSingleNode%2A> yöntemleri tek döndürülen düğümde yerleştirilir ve ayrıca konumunu etkilemez <xref:System.Xml.XPath.XPathNavigator> oluşturmak için kullanılan nesne.  
  
 Aşağıdaki örnek oluşturulmasını gösterir bir <xref:System.Xml.XPath.XPathNavigator> nesnesinin bir <xref:System.Xml.XPath.XPathDocument> nesnesi, kullanımını <xref:System.Xml.XPath.XPathNavigator.Select%2A> düğümler seçmek için yöntemi <xref:System.Xml.XPath.XPathDocument> nesne ve kullanımını <xref:System.Xml.XPath.XPathNodeIterator> seçili düğümler yineleme için nesne.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
Dim nodes As XPathNodeIterator = navigator.Select("/bookstore/book")  
  
While nodes.MoveNext()  
    Console.WriteLine(nodes.Current.Name)  
End While  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
XPathNodeIterator nodes = navigator.Select("/bookstore/book");  
  
while(nodes.MoveNext())  
{  
    Console.WriteLine(nodes.Current.Name);  
}  
```  
  
 Örnek alır `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="optimized-selection-methods"></a>En iyi duruma getirilmiş seçimi yöntemleri  
 <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemlerinin <xref:System.Xml.XPath.XPathNavigator> sınıfı alt, alt ve üst düğümleri almak için yaygın olarak kullanılan XPath ifadeleri temsil eder. Bu yöntemler için performansı en iyi duruma getirilir ve bunların karşılık gelen XPath ifadeleri hızlıdır. <xref:System.Xml.XPath.XPathNavigator.SelectChildren%2A>, <xref:System.Xml.XPath.XPathNavigator.SelectAncestors%2A>, Ve <xref:System.Xml.XPath.XPathNavigator.SelectDescendants%2A> yöntemleri seçer üst, alt ve alt düğümler dayalı bir <xref:System.Xml.XPath.XPathNodeType> değeri veya yerel ad ve ad alanı seçmek için düğümlerin URI. Seçilen üst, alt ve alt düğümler döndürülür bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPath XPathNavigator kullanarak ifadeler değerlendir](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [Eşleşen düğümleri XPathNavigator kullanma](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath sorguları tanınan düğüm türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath sorguları ve ad alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Derlenmiş XPath ifadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
