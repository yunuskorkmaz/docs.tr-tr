---
title: XPathNavigator Kullanarak XPath İfadelerini Değerlendirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2913ccf3-f932-4363-8028-9e2d22ce6093
ms.openlocfilehash: b6e18fe02a828ae307ac7ade15650d3303f2600c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287811"
---
# <a name="evaluate-xpath-expressions-using-xpathnavigator"></a>XPathNavigator Kullanarak XPath İfadelerini Değerlendirme
<xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> bir XPath ifadesini değerlendirmek için yöntemini sağlar. <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi bir XPath ifadesi alır, değerlendirir ve XPath ifadesinin sonucuna göre Boole, sayı, dize veya düğüm KÜMESININ W3C XPath türünü döndürür.  
  
## <a name="the-evaluate-method"></a>Değerlendir yöntemi  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi bir XPath ifadesi alır, bunu değerlendirir ve Boole ( <xref:System.Boolean> ), sayı ( <xref:System.Double> ), dize () <xref:System.String> veya düğüm kümesi ( <xref:System.Xml.XPath.XPathNodeIterator> ) ile yazılmış bir sonuç döndürür. Örneğin, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yöntemi matematiksel bir yöntemde kullanılabilir. Aşağıdaki örnek kod, dosyadaki tüm kitapların toplam fiyatını hesaplar `books.xml` .  
  
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
  
 Örnek, `books.xml` dosyayı giriş olarak alır.  
  
 [!code-xml[XPathXMLExamples#1](../../../../samples/snippets/xml/VS_Snippets_Data/XPathXMLExamples/XML/books.xml#1)]  
  
### <a name="position-and-last-functions"></a>konum ve son Işlevler  
 <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A>Yöntemi aşırı yüklendi. Yöntemlerden biri bir <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> <xref:System.Xml.XPath.XPathNodeIterator> nesneyi parametre olarak alır. Bu belirli <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> Yöntem, <xref:System.Xml.XPath.XPathNavigator.Evaluate%2A> yalnızca bir nesneyi parametre olarak alan ve bir <xref:System.Xml.XPath.XPathExpression> düğüm kümesi bağımsız değişkeninin üzerinde değerlendirmeyi gerçekleştirmek için geçerli bağlamı belirtmesini olanaklı hale getirecağından, bu yöntem ile aynıdır. Bu bağlam, XPath `position()` ve `last()` işlevler için geçerli bağlam düğümü göreli oldukları için gereklidir. Bir konum adımında koşul olarak kullanılmadığı sürece `position()` ve `last()` işlevleri, aksi takdirde değerlendirilmek üzere bir düğüm kümesine başvuru gerektirir, `position` ve `last` işlevleri döndürülür `0` .  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak Düğümleri Eşleştirme](matching-nodes-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](node-types-recognized-with-xpath-queries.md)
- [XPath Sorguları ve Ad Alanları](xpath-queries-and-namespaces.md)
- [Derlenmiş XPath İfadeleri](compiled-xpath-expressions.md)
