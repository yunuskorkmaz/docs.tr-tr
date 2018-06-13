---
title: XPath XPathNavigator kullanarak ifadeler değerlendir
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dce97fd74b17154925d18bf18a9a8defd2e508e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569125"
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
 [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
 [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
