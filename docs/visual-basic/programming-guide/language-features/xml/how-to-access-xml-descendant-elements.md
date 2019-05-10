---
title: 'Nasıl yapılır: Erişim XML bağımlı öğelerine (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 008fd599e527ad4a8d483d2468a57ece1d2b4bdc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64598592"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Nasıl yapılır: Erişim XML bağımlı öğelerine (Visual Basic)
Bu örnek, bir descendant axis özelliği bir XML öğesi altında yer alır ve belirtilen ada sahip olan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir. Özellikle, kullandığı `Value` özelliğini koleksiyondaki ilk öğenin değerini alma `name` descendant axis özelliği döndürür. `name` Descendant axis özelliği adlı tüm öğeleri alır `name` içerdiği `contacts` nesne. Bu örnekte ayrıca `phone` adlı tüm alt öğeleri erişmeye descendant axis özelliği `phone` içerdiği `contacts` nesne.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
- Bir başvuru <xref:System.Xml.Linq> ad alanı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML Descendant Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
