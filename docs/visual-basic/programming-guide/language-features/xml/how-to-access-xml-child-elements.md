---
title: "Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d3a708b787ad38f08d4673d4003db839f6cf6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a>Nasıl yapılır: XML Alt Öğelerine Erişme (Visual Basic)
Bu örnek belirtilen ada sahip bir XML öğesi tüm XML alt öğelerine erişmek için axis özelliği bir alt kullanmayı gösterir. Özellikle, kullanan <xref:System.Xml.Linq.XElement.Value%2A> özelliğine koleksiyonda ilk öğenin değerini almak `name` alt axis özelliği döndürür. `name` Child axis özelliği alır adlı tüm alt öğeleri `phone` içinde `contact` nesnesi. Bu örnek ayrıca kullanır `phone` adlı tüm alt öğeleri erişmek için alt axis özelliği `phone` içerdiği `contact` nesnesi.  
  
## <a name="example"></a>Örnek  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Bu örnek gerektirir:  
  
-   Bir başvuru <xref:System.Xml.Linq> ad alanı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [XML alt Axis özelliği](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [XML değeri özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
