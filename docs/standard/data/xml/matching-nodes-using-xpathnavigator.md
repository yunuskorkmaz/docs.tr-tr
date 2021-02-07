---
description: 'Daha fazla bilgi edinin: XPathNavigator kullanarak eşleşen düğümler'
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: d142490829473d0891c5b2f18b1c3ec9e7ace426
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99732013"
---
# <a name="matching-nodes-using-xpathnavigator"></a>XPathNavigator Kullanarak Düğümleri Eşleştirme

<xref:System.Xml.XPath.XPathNavigator>Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini belirleme yöntemini sağlar. <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, giriş olarak bir XPath ifadesi alır ve <xref:System.Boolean> geçerli düğümün verilen XPath ifadesiyle veya belirtilen derlenmiş nesneyle eşleşip eşleşmediğini gösteren bir döndürür <xref:System.Xml.XPath.XPathExpression> .  
  
## <a name="matching-nodes"></a>Eşleşen düğümler  

 <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, `true` geçerli düğüm belirtilen XPath ifadesiyle eşleşiyorsa döndürür. Örneğin, aşağıdaki kod örneğinde, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> `true` geçerli düğüm öğesi ise `b` ve öğesinin bir özniteliği varsa yöntemi döndürülür `b` `c` .  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A>Yöntemi, öğesinin durumunu değiştirmez <xref:System.Xml.XPath.XPathNavigator> .  
  
```vb  
Dim document as XPathDocument = New XPathDocument("input.xml")  
Dim navigator as XPathNavigator = document.CreateNavigator()  
  
navigator.Matches("b[@c]")  
```  
  
```csharp  
XPathDocument document = new XPathDocument("input.xml");  
XPathNavigator navigator = document.CreateNavigator();  
  
navigator.Matches("b[@c]");  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.XmlDocument>
- <xref:System.Xml.XPath.XPathDocument>
- <xref:System.Xml.XPath.XPathNavigator>
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](node-types-recognized-with-xpath-queries.md)
- [XPath Sorguları ve Ad Alanları](xpath-queries-and-namespaces.md)
- [Derlenmiş XPath İfadeleri](compiled-xpath-expressions.md)
