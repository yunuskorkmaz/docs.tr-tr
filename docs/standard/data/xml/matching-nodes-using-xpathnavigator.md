---
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
ms.openlocfilehash: f0988c3a112fefc351175de02c790dc25fe6e94a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710693"
---
# <a name="matching-nodes-using-xpathnavigator"></a>XPathNavigator Kullanarak Düğümleri Eşleştirme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini belirleme yöntemini sağlar. Yöntemi <xref:System.Xml.XPath.XPathNavigator.Matches%2A> , giriş olarak bir XPath ifadesi alır ve geçerli düğümün <xref:System.Boolean> verilen XPath ifadesiyle veya belirtilen derlenmiş <xref:System.Xml.XPath.XPathExpression> nesneyle eşleşip eşleşmediğini gösteren bir döndürür.  
  
## <a name="matching-nodes"></a>Eşleşen düğümler  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi, geçerli `true` düğüm belirtilen XPath ifadesiyle eşleşiyorsa döndürür. Örneğin, aşağıdaki kod örneğinde, geçerli düğüm <xref:System.Xml.XPath.XPathNavigator.Matches%2A> öğesi `true` `b`ise ve öğesinin `b` bir özniteliği `c`varsa yöntemi döndürülür.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi, <xref:System.Xml.XPath.XPathNavigator>öğesinin durumunu değiştirmez.  
  
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
- [XPath Veri Modelini Kullanarak XML Verilerini İşleme](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
- [XPathNavigator Kullanarak XML Verileri Seçme](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)
- [XPathNavigator Kullanarak XPath İfadelerini Değerlendirme](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)
- [XPath Sorguları ile Tanınan Düğüm Türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)
- [XPath Sorguları ve Ad Alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)
- [Derlenmiş XPath İfadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
