---
title: XPathNavigator Kullanarak XPath İfadelerini Değerlendirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: 1a17aea66be7f9d35336434408c49bae8046b7e7
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710914"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>XPathNavigator Kullanarak XPath İfadelerini Değerlendirme
<xref:System.Xml.XPath.XPathNavigator> sınıfı bir XPath ifadesini değerlendirmek için <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi sağlar. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi bir XPath ifadesi alır, bunu değerlendirir ve XPath ifadesinin sonucuna göre Boole, sayı, dize veya düğüm kümesinin W3C XPath türünü döndürür.  
  
## <a name="the-evaluate-method"></a>Değerlendir yöntemi  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi bir XPath ifadesi alır, bunu değerlendirir ve Boole (<xref:System.Boolean>), sayı (<xref:System.Double>), dize (<xref:System.String>) veya düğüm kümesinin (<xref:System.Xml.XPath.XPathNodeIterator>) yazılmış bir sonucunu döndürür. Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel bir yöntemde kullanılabilir. Aşağıdaki örnek kod, `books.xml` dosyasındaki tüm kitapların toplam fiyatını hesaplar.  
  
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
  
 Örnek, `books.xml` dosyasını girdi olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>konum ve son Işlevler  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi aşırı yüklendi. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemlerinden biri, bir <xref:System.Xml.XPath.XPathNodeIterator> nesnesini parametre olarak alır. Bu <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi, yalnızca bir <xref:System.Xml.XPath.XPathExpression> nesnesini parametre olarak alan <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi ile aynıdır, ancak bir düğüm kümesi bağımsız değişkeninin üzerinde değerlendirmeyi gerçekleştirmek için geçerli bağlamı belirtmesini sağlar. Bu bağlam, XPath `position()` ve `last()` işlevleri için, geçerli bağlam düğümüne göreli oldukları için gereklidir. Bir konum adımında bir koşul olarak kullanılmadıkça, `position()` ve `last()` işlevleri, aksi takdirde değerlendirilmek üzere bir düğüm kümesine başvuru gerektirir, `position` ve `last` işlevleri `0`döndürür.  
  
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
