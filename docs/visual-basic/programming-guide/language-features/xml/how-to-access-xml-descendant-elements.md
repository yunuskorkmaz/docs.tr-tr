---
title: "Nasıl yapılır: XML Bağımlı Öğelerine Erişme (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7b3b6c8ac96bd18a379804b83f3ab3e48a5b0c89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [XML Descendant Axis özelliği](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)  
 [XML değeri özelliği](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [Visual Basic'de XML'e erişme](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
