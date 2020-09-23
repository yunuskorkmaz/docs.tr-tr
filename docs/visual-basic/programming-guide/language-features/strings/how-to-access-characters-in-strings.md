---
title: 'Nasıl Yapılır: Dizelerdeki Karakterlere Erişme'
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], accessing characters
- characters [Visual Basic], accessing in strings
ms.assetid: 02c5206c-ffab-494d-b648-3b2ea358dc34
ms.openlocfilehash: 4ea37c4393a8ece5513327b22c6c0ba4b027c781
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059190"
---
# <a name="how-to-access-characters-in-strings-in-visual-basic"></a>Nasıl Yapılır: Visual Basic'de Dizelerdeki Karakterlere Erişme

Bu örnek, <xref:System.String.Chars%2A> bir dizedeki belirtilen konumdaki karaktere erişmek için özelliğinin nasıl kullanılacağını gösterir.  
  
## <a name="example"></a>Örnek  

 Bazen dizinizdeki karakterler ve dizeniz içindeki bu karakterlerin konumları hakkında veri olması yararlı olur. Bir dizeyi bir karakter dizisi ( `Char` örnekler) olarak düşünebilirsiniz; özelliği aracılığıyla söz konusu karakterin dizinine başvurarak belirli bir karakteri alabilirsiniz <xref:System.String.Chars%2A> .  
  
 [!code-vb[VbVbalrStrings#49](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#49)]  
  
 `index` <xref:System.String.Chars%2A> Özelliğin parametresi sıfır tabanlıdır.  
  
## <a name="robust-programming"></a>Güçlü Programlama  

 <xref:System.String.Chars%2A>Özelliği belirtilen konumdaki karakteri döndürür. Ancak bazı Unicode karakterler birden fazla karakterle temsil edilebilir. Unicode karakterlerle çalışma hakkında daha fazla bilgi için bkz. [nasıl yapılır: dizeyi bir karakter dizisine dönüştürme](how-to-convert-a-string-to-an-array-of-characters.md).  
  
 <xref:System.String.Chars%2A> <xref:System.IndexOutOfRangeException> `index` Parametresi, dizenin uzunluğuna eşit veya daha büyükse veya sıfırdan küçükse özellik bir özel durum oluşturur  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Chars%2A>
- [Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme](how-to-convert-a-string-to-an-array-of-characters.md)
- [Visual Basic'de Dizeler ve Diğer Veri Türleri Arasında Dönüştürme](converting-between-strings-and-other-data-types.md)
- [Dizeler](index.md)
