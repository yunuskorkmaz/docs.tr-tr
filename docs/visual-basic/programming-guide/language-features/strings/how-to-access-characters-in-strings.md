---
title: "Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme"
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 48507cade639660e6ce36697975d09fb29206c20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
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
 [Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)  
 [Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
