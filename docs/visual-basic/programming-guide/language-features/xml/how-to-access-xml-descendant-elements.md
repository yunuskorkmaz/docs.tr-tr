---
title: 'Nasıl yapılır: Erişim XML bağımlı öğelerine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: f1248109dfcc853f701ea2ab61edc67d768e9663
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666182"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Nasıl yapılır: Erişim XML bağımlı öğelerine (Visual Basic)
Bu örnek, bir descendant axis özelliği bir XML öğesi altında yer alır ve belirtilen ada sahip olan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir. Özellikle, kullandığı `Value` özelliğini koleksiyondaki ilk öğenin değerini alma `name` descendant axis özelliği döndürür. `name` Descendant axis özelliği adlı tüm öğeleri alır `name` içerdiği `contacts` nesne. Bu örnekte ayrıca `phone` adlı tüm alt öğeleri erişmeye descendant axis özelliği `phone` içerdiği `contacts` nesne.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System.Xml.Linq> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML Descendant Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
