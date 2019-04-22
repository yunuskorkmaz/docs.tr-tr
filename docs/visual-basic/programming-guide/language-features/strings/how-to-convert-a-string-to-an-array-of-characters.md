---
title: "Nasıl yapılır: Visual Basic'te karakter için bir dizeye dönüştürün"
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: 921d7ad62545d3a29870aee6c6b354fdadeb0500
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823317"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te karakter için bir dizeye dönüştürün
Bazen, dize ve bu karakterleri ne zaman bir dizeyi ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır. Bu örnek, bir dizedeki dizenin çağırarak karakter nasıl alabileceğiniz gösterir <xref:System.String.ToCharArray%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dizeye bölme gösterir. bir `Char` dizi ve bir dizeye bölme bir `String` , Unicode karakterler dizisi. İki veya daha fazla Unicode metin karakterleri oluşturulabildikleri Bu ayrım sebebi `Char` karakter (bir yedek çifti ya da bir birleştirme gibi karakter dizisi). Daha fazla bilgi için <xref:System.Globalization.TextElementEnumerator> ve [Unicode standart](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Örnek  
 Bir dize, Unicode metin karakterlere bölmek daha zordur, ancak bu görsel bir dize temsilini hakkında bilgi almanız gerekiyorsa şarttır. Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> dizesini oluşturan Unicode karakterler hakkında bilgi almak için yöntemi.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Nasıl yapılır: Karakterleri dizelere erişim](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Dizeler ve Visual Basic'te diğer veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
