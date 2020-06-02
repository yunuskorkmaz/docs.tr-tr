---
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: 47b0ba7e705ad602825dcca3f24c207362174a4c
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289128"
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
