---
title: XPathNavigator kullanarak XPath ifadelerini değerlendirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2712c1de4a5f4a06ba041fdc0c5df2487eebdd2
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44129607"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>XPathNavigator kullanarak XPath ifadelerini değerlendirme
<xref:System.Xml.XPath.XPathNavigator> Sağlar sınıfını <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesini değerlendirme için yöntemi. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesini alır, bu değerlendirir ve W3C XPath türü Boolean, sayı, dize döndürür veya düğüm kümesi temel XPath ifadesinin sonucu üzerinde.  
  
## <a name="the-evaluate-method"></a>Yöntemi  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi bir XPath ifadesini alır, bu değerlendirir ve belirlenmiş bir Boolean sonucunu döndürür (<xref:System.Boolean>), sayı (<xref:System.Double>), dize (<xref:System.String>), veya düğüm kümesi (<xref:System.Xml.XPath.XPathNodeIterator>). Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel bir yöntemde kullanılabilir. Aşağıdaki kod örneği tüm kitaplar toplam fiyatı hesaplar `books.xml` dosya.  
  
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
  
 Örnek alan `books.xml` dosya giriş olarak.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>konum ve son işlevlerin  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntemi aşırı yüklüdür. Aşağıdakilerden birini <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemleri alır bir <xref:System.Xml.XPath.XPathNodeIterator> bir parametre olarak nesne. Bu özellikle <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi ile aynıdır <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yönteminin yalnızca alan bir <xref:System.Xml.XPath.XPathExpression> değerlendirme gerçekleştirmek için geçerli bağlam belirtmek için bağımsız değişkeni bir düğüm kümesi sağlayan dışında bir parametre olarak nesne. Bu bağlam için XPath gereklidir `position()` ve `last()` göre geçerli bağlam düğümünün oldukları gibi çalışır. Bir koşul konumu adımda olarak kullanılmadığı sürece `position()` ve `last()` işlevleri, aksi takdirde, değerlendirilebilmesi için ayarlanmış bir düğümü için bir başvuru gerektirir `position` ve `last` işlev dönüş `0`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>  
- <xref:System.Xml.XPath.XPathDocument>  
- <xref:System.Xml.XPath.XPathNavigator>  
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
- [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](../../../../docs/standard/data/xml/matching-nodes-using-xpathnavigator.md)  
- [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
- [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
- [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
