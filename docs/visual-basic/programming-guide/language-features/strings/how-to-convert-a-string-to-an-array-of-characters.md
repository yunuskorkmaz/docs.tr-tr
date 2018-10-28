---
title: "Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme"
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: cc12b70cddcb93a72b4421a8ddd93542ef84f55b
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041160"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme
Bazen, dize ve bu karakterleri ne zaman bir dizeyi ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır. Bu örnek, bir dizedeki dizenin çağırarak karakter nasıl alabileceğiniz gösterir <xref:System.String.ToCharArray%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dizeye bölme gösterir. bir `Char` dizi ve bir dizeye bölme bir `String` , Unicode karakterler dizisi. İki veya daha fazla Unicode metin karakterleri oluşturulabildikleri Bu ayrım sebebi `Char` karakter (bir yedek çifti ya da bir birleştirme gibi karakter dizisi). Daha fazla bilgi için <xref:System.Globalization.TextElementEnumerator> ve [Unicode standart](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Örnek  
 Bir dize, Unicode metin karakterlere bölmek daha zordur, ancak bu görsel bir dize temsilini hakkında bilgi almanız gerekiyorsa şarttır. Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> dizesini oluşturan Unicode karakterler hakkında bilgi almak için yöntemi.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Nasıl Yapılır: Dizelerdeki Karakterlere Erişme](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Dizeler ve Visual Basic'te diğer veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
