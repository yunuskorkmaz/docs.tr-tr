---
title: 'Nasıl yapılır: Erişim XML alt öğelerine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 874c7490e451d64bf50e25934ea43a9b928ddab9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980561"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Nasıl yapılır: Erişim XML alt öğelerine (Visual Basic)
Bu örnek belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir. Özellikle, kullandığı <xref:System.Xml.Linq.XElement.Value%2A> özelliğini koleksiyondaki ilk öğenin değerini alma `name` alt eksen özelliğini döndürür. `name` Child axis özelliği adlı tüm alt öğe alır `phone` içinde `contact` nesne. Bu örnekte ayrıca `phone` adlı tüm alt öğelere erişmek için alt axis özelliği `phone` içerdiği `contact` nesne.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System.Xml.Linq> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML Alt Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
