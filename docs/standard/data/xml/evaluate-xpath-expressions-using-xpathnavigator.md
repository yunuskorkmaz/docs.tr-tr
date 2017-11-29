---
title: "XPath XPathNavigator kullanarak ifadeler değerlendir"
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
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d513f48155a582a5158cccdd682f5b8485caefd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>XPath XPathNavigator kullanarak ifadeler değerlendir
<xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesi değerlendirmek için bir yöntem. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesi alır, bu hesaplar ve mantıksal değer, sayı, dize W3C XPath türünü döndürür veya düğüm kümesi XPath ifadesi sonucuna bağlı.  
  
## <a name="the-evaluate-method"></a>Yöntemini değerlendirin  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesi alır, bu değerlendirir ve Boolean yazılan sonucunu döndürür (<xref:System.Boolean>), sayı (<xref:System.Double>), dize (<xref:System.String>), veya düğüm kümesi (<xref:System.Xml.XPath.XPathNodeIterator>). Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel yönteminde kullanılan. Aşağıdaki kod örneği tüm books toplam fiyatını hesaplar `books.xml` dosya.  
  
```vb  
Dim document As XPathDocument = New XPathDocument("books.xml")  
Dim navigator As XPathNavigator = document.CreateNavigator()  
  
Dim query As XPathExpression = navigator.Compile("sum(//price/text())")  
Dim total As Double = CType(navigator.Evaluate(query), Double)  
Console.WriteLine(total)  
```  
  
```csharp  
XPathDocument document = new XPathDocument("books.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
XPathExpression query = navigator.Compile("sum(//price/text())");  
Double total = (Double)navigator.Evaluate(query);  
Console.WriteLine(total);  
```  
  
 Örnek alır `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>konum ve son işlevleri  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi aşırı yüklü. Aşağıdakilerden birini <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemleri alır bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesini parametre olarak. Bu belirli <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi ile aynıdır <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yönteminin yalnızca alan bir <xref:System.Xml.XPath.XPathExpression> bir düğüm kümesi değerlendirme yapmak için geçerli bağlamı belirtmek için bağımsız değişken sağlar ancak bu nesne bir parametre olarak. Bu bağlam için XPath gereklidir `position()` ve `last()` göre geçerli bağlam düğümünün oldukları gibi çalışır. Konum adımda, bir koşul olarak kullanılmadığı sürece `position()` ve `last()` işlevleri düğüm Aksi halde, değerlendirilebilmesi için kümesi başvurusu gerektiren `position` ve `last` işlevleri return `0`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XML verileri XPathNavigator kullanarak seçin](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [Eşleşen düğümleri XPathNavigator kullanma](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath sorguları tanınan düğüm türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath sorguları ve ad alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Derlenmiş XPath ifadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
