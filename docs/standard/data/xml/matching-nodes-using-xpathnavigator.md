---
title: "Eşleşen düğümleri XPathNavigator kullanma"
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
ms.assetid: e6848c47-ee5d-401a-89a5-50b5eed40f30
caps.latest.revision: "2"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a51c358ecb50c94ccde9f86ba80fc8f0670f82d9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="matching-nodes-using-xpathnavigator"></a>Eşleşen düğümleri XPathNavigator kullanma
<xref:System.Xml.XPath.XPathNavigator> SAX <xref:System.Xml.XPath.XPathNavigator.Matches%2A> bir düğümün bir XPath ifadesi eşleşip eşleşmediğini belirlemek için yöntem. <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi giriş olarak bir XPath ifadesi alıp döndüren bir <xref:System.Boolean> belirten geçerli düğüm verilen XPath ifadesi eşleşip eşleşmediğini veya derlenmiş verilen <xref:System.Xml.XPath.XPathExpression> nesnesi.  
  
## <a name="matching-nodes"></a>Eşleşen düğümleri  
 <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi döndürür `true` belirtilen XPath ifadesi geçerli düğüm eşleşmesi durumunda. Örneğin, aşağıdaki kod örneğinde <xref:System.Xml.XPath.XPathNavigator.Matches%2A> yöntemi döndürür `true` geçerli düğüm öğe ise `b`ve öğesini `b` bir öznitelik `c`.  
  
> [!NOTE]
>  <xref:System.Xml.XPath.XPathNavigator.Matches%2A> Yöntemi durumunu değiştirmez <xref:System.Xml.XPath.XPathNavigator>.  
  
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
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.XmlDocument>  
 <xref:System.Xml.XPath.XPathDocument>  
 <xref:System.Xml.XPath.XPathNavigator>  
 [XPath veri modelini kullanarak işlem XML verileri](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 [XML verileri XPathNavigator kullanarak seçin](../../../../docs/standard/data/xml/select-xml-data-using-xpathnavigator.md)  
 [XPath XPathNavigator kullanarak ifadeler değerlendir](../../../../docs/standard/data/xml/evaluate-xpath-expressions-using-xpathnavigator.md)  
 [XPath sorguları tanınan düğüm türleri](../../../../docs/standard/data/xml/node-types-recognized-with-xpath-queries.md)  
 [XPath sorguları ve ad alanları](../../../../docs/standard/data/xml/xpath-queries-and-namespaces.md)  
 [Derlenmiş XPath ifadeleri](../../../../docs/standard/data/xml/compiled-xpath-expressions.md)
