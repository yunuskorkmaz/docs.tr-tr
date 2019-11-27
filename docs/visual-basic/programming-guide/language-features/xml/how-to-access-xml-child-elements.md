---
title: 'Nasıl yapılır: XML Alt Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: af5ea809cb0777b16230f20e133764dd5f1f86d9
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332335"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)
Bu örnek, bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir. Özellikle, `name` alt eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için <xref:System.Xml.Linq.XElement.Value%2A> özelliğini kullanır. `name` alt eksen özelliği, `contact` nesnesinde `phone` adlı tüm alt öğeleri alır. Bu örnek ayrıca `contact` nesnesinde bulunan `phone` adlı tüm alt öğelere erişmek için `phone` alt eksen özelliğini kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Xml.Linq> ad alanına bir başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML Alt Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Visual Basic XML 'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
