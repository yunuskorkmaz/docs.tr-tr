---
title: "Nasıl yapılır: Visual Basic'de Dizelerdeki karakterlere erişim"
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: f2831333008844c959c3625698fce6c485450683
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967561"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Nasıl yapılır: Visual Basic'de Dizelerdeki karakterlere erişim
Bu örnek nasıl kullanılacağını gösterir <xref:System.String.Chars%2A> belirtilen konumda bir dizedeki karakter erişmek için özelliği.  
  
## <a name="example"></a>Örnek  
 Bazen, dize ve bu karakterleri, dize içindeki konumunu karakterler hakkında veriler kullanışlıdır. Bir dizenin karakter dizisi olarak düşünebilirsiniz (`Char` örnekleri); belirli bir karakterin bu karakter dizinini başvurarak alabilirsiniz <xref:System.String.Chars%2A> özelliği.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index` Parametresinin <xref:System.String.Chars%2A> özelliği sıfır tabanlı.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.String.Chars%2A> Özelliği belirtilen konumdaki karakteri döndürür. Ancak, bazı Unicode karakterler birden fazla karakter gösterilebilir. Unicode karakter ile çalışma konusunda daha fazla bilgi için bkz. [nasıl yapılır: Bir dizeyi karakter dizilerine dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> Özelliği oluşturur bir <xref:System.IndexOutOfRangeException> özel durum, `index` parametresi değerinden büyük veya eşit bir dizenin uzunluğunu veya onu küçükse sıfırdan  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.String.Chars%2A>
- [Nasıl yapılır: Bir dizeyi karakter dizilerine dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Dizeler ve Visual Basic'te diğer veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
