---
title: XPathNavigator Kullanarak Düğümleri Eşleştirme
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882e92c6c8cb6e638ca299ed4c43b9da8f4bf235
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923320"
---
# <a name="matching-nodes-using-xpathnavigator"></a>XPathNavigator Kullanarak Düğümleri Eşleştirme
<xref:System.Xml.XPath.XPathNavigator> Sınıfı ,<xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesiyle eşleşip eşleşmediğini belirleme yöntemini sağlar. Yöntemi <xref:System.Xml.XPath.XPathNavigator.Matches%2A> , giriş olarak bir XPath ifadesi alır ve geçerli düğümün <xref:System.Boolean> verilen XPath ifadesiyle veya belirtilen derlenmiş <xref:System.Xml.XPath.XPathExpression> nesneyle eşleşip eşleşmediğini gösteren bir döndürür.  
  
## <a name="matching-nodes"></a>Eşleşen düğümler  
 Yöntemi, geçerli düğüm belirtilen XPath ifadesiyle eşleşiyorsa döndürür `true`. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Örneğin, aşağıdaki kod örneğinde, <xref:System.Xml.XPath.XPathNavigator.Matches%2A> geçerli düğüm öğesi `b`ise ve öğesinin `b` bir özniteliği `true` `c`varsa yöntemi döndürülür.  
  
> [!NOTE]
> <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi ,<xref:System.Xml.XPath.XPathNavigator>öğesinin durumunu değiştirmez.  
  
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
