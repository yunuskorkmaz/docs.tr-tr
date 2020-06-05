---
title: 'Nasıl yapılır: XML Alt Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392824"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)
Bu örnek, bir XML öğesinde belirtilen bir ada sahip tüm XML alt öğelerine erişmek için bir alt eksen özelliğinin nasıl kullanılacağını gösterir. Özellikle, <xref:System.Xml.Linq.XElement.Value%2A> koleksiyonda `name` alt eksen özelliğinin döndürdüğü ilk öğenin değerini almak için özelliğini kullanır. `name`Alt eksen özelliği, nesnesinde adlı tüm alt öğeleri alır `phone` `contact` . Bu örnek, `phone` nesnesinde bulunan adlı tüm alt öğelere erişmek için alt eksen özelliğini de kullanır `phone` `contact` .  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a>Kodu derle  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Xml.Linq>Ad alanına başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [XML Alt Axis Özelliği](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [XML Value Özelliği](../../../language-reference/xml-axis/xml-value-property.md)
- [Visual Basic'de XML'e Erişme](accessing-xml.md)
- [XML](index.md)
