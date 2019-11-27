---
title: 'Nasıl Yapılır: Dizelerdeki Karakterlere Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 44a021ed3ce1d10613cf6ab7c959c62feec6046c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352457"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme
Bu örnek, bir dizedeki belirtilen konumdaki karaktere erişmek için <xref:System.String.Chars%2A> özelliğinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  
 Bazen dizinizdeki karakterler ve dizeniz içindeki bu karakterlerin konumları hakkında veri olması yararlı olur. Dizeyi bir karakter dizisi (`Char` örnekleri) olarak düşünebilirsiniz; Bu karakterin dizinine <xref:System.String.Chars%2A> özelliği aracılığıyla başvurarak belirli bir karakteri alabilirsiniz.  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 <xref:System.String.Chars%2A> özelliğinin `index` parametresi sıfır tabanlıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  
 <xref:System.String.Chars%2A> özelliği, belirtilen konumdaki karakteri döndürür. Ancak bazı Unicode karakterler birden fazla karakterle temsil edilebilir. Unicode karakterlerle çalışma hakkında daha fazla bilgi için bkz. [nasıl yapılır: dizeyi bir karakter dizisine dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> özelliği, `index` parametresi dizenin uzunluğuna eşit veya daha büyükse veya sıfırdan küçükse bir <xref:System.IndexOutOfRangeException> özel durum oluşturur  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Chars%2A>
- [Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/how-to-convert-a-string-to-an-array-of-characters.md)
- [Visual Basic dizeler ve diğer veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
