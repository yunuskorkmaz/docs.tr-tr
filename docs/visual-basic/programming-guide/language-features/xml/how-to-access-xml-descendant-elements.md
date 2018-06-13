---
title: 'Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: 6d41844b540631df96740ce56818c125cf85e928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648492"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a>Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)
Bu örnek descendant axis özelliği, belirtilen ada sahip ve bir XML öğesi altında bulunan tüm XML öğeleri erişmek için nasıl kullanılacağını gösterir. Özellikle, kullanan `Value` özelliğine koleksiyonda ilk öğenin değerini almak `name` descendant axis özelliği döndürür. `name` Descendant axis özelliği alır adlı tüm öğeleri `name` içerdiği `contacts` nesnesi. Bu örnek ayrıca kullanır `phone` adlı tüm bağımlı öğelerini erişmek için descendant axis özelliği `phone` içerdiği `contacts` nesnesi.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System.Xml.Linq> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>  
 [XML Descendant Axis Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [XML Value Özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
