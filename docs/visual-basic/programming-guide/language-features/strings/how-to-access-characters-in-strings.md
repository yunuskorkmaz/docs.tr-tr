---
title: "Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54d604fc08dd97e0e31f9bcec148431374e8ef8f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme
Bu örnek nasıl kullanılacağı ortaya <xref:System.String.Chars%2A> belirtilen konumda bir dizedeki karakter erişmek için özellik.  
  
## <a name="example"></a>Örnek  
 Bazen dizenizi ve bu karakterleri dizenizi içinde konumlarını karakterler hakkında veriler kullanışlıdır. Bir dize bir karakter dizisi olarak düşünebilirsiniz (`Char` örnekleri); belirli bir karakterin bu karakter dizinini başvurarak alabilirsiniz <xref:System.String.Chars%2A> özelliği.  
  
 [!code-vb[VbVbalrStrings#49](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-access-characters-in-strings_1.vb)]  
  
 `index` Parametresinin <xref:System.String.Chars%2A> özelliği sıfır tabanlı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.String.Chars%2A> Özelliği, belirtilen konumdaki karakteri döndürür. Ancak, bazı Unicode karakterler birden fazla karakteri temsil edilebilir. Unicode karakter ile çalışma konusunda daha fazla bilgi için bkz: [nasıl yapılır: bir dizeyi, bir dizi karakter dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Özelliği atar bir <xref:System.IndexOutOfRangeException> özel durum, `index` parametredir dize uzunluğu eşit veya daha büyük veya bu küçükse sıfır  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.Chars%2A>  
 [Nasıl yapılır: bir dizeyi karakter dizisi için dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Dizeleri](../../../../visual-basic/programming-guide/language-features/strings/index.md)
