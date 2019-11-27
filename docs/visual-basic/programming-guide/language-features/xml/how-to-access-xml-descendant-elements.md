---
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 63a094c3c2b20736f0ef6589c76d53b7cc96b29a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332309"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)
Bu örnek, bir alt eksen özelliğinin, belirtilen bir ada sahip olan ve bir XML öğesi altında bulunan tüm XML öğelerine erişmek için nasıl kullanılacağını gösterir. Özellikle, `name` alt eksen özelliğinin döndürdüğü koleksiyondaki ilk öğenin değerini almak için `Value` özelliğini kullanır. `name` alt eksen özelliği, `contacts` nesnesinde bulunan `name` adlı tüm öğeleri alır. Bu örnek ayrıca `contacts` nesnesinde bulunan `phone` adlı tüm alt öğelere erişmek için `phone` alt eksen özelliğini kullanır.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleme  
 Bu örnek şunları gerektirir:  
  
- <xref:System.Xml.Linq> ad alanına bir başvuru.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [XML Descendant Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [Visual Basic XML 'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
