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
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648625"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme
Bazen dizenizi ve bu karakterleri ne zaman bir dizesini ayrıştırma, dizesindeki konumlarını karakterler hakkında veriler kullanışlıdır. Bu örnek, bir dize dizesinin çağırarak karakter nasıl erişebileceğini gösterir <xref:System.String.ToCharArray%2A> yöntemi.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dizeye bölüneceği gösterilmiştir bir `Char` dizi ve nasıl bir dizeye bölüneceği bir `String` kendi Unicode metin karakter dizisi. Bu ayrım iki veya daha fazla Unicode metin karakterlerinin birleştirilebilen nedeni `Char` karakterleri (bir yedek çifti ya da bir birleştirme gibi karakter dizisi). Daha fazla bilgi için bkz: <xref:System.Globalization.TextElementEnumerator> ve "Unicode standart" konumundaki http://www.unicode.org.  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>Örnek  
 Bir dize, Unicode metin karakterlere bölmek daha da zor olan, ancak bu görsel bir dize gösterimini hakkında bilgi istiyorsanız gereklidir. Bu örnekte <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> bir dize olun Unicode metin karakterler hakkında bilgi almak için yöntemi.  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [Nasıl Yapılır: Dizelerdeki Karakterlere Erişme](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [Dizeler ve diğer Visual Basic veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
