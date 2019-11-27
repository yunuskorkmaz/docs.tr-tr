---
title: 'Nasıl yapılır: Bir Dizeyi Karakter Dizilerine Dönüştürme'
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352455"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>Nasıl yapılır: Visual Basic'te Bir Dizeyi Karakter Dizilerine Dönüştürme
Bazen dizinizdeki karakterlerle ilgili verilerin ve dizinizdeki karakterlerin (örneğin, bir dizeyi ayrıştırırken) bulunduğu konumlarda olması yararlı olur. Bu örnekte, dizenin <xref:System.String.ToCharArray%2A> yöntemini çağırarak bir dizedeki karakterlerin dizisini nasıl alabileceğiniz gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir dizenin bir `Char` dizisine nasıl bölüneceği ve bir dizenin Unicode metin karakterlerinin `String` dizisine nasıl bölüneceği gösterir. Bu farkın nedeni, Unicode metin karakterlerinin iki veya daha fazla `Char` karakterden (bir vekil çifti veya Birleşik karakter dizisi gibi) oluşmasının nedenidir. Daha fazla bilgi için bkz. <xref:System.Globalization.TextElementEnumerator> ve [Unicode standart](https://www.unicode.org/standard/standard.html).  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>Örnek  
 Bir dizeyi Unicode metin karakterlerine bölmek daha zordur, ancak bir dizenin görsel temsili hakkında bilgi gerekirse bu gereklidir. Bu örnek, bir dizeyi oluşturan Unicode metin karakterleri hakkında bilgi almak için <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> yöntemini kullanır.  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [Nasıl Yapılır: Dizelerdeki Karakterlere Erişme](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [Visual Basic dizeler ve diğer veri türleri arasında dönüştürme](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [Dizeler](../../../../visual-basic/programming-guide/language-features/strings/index.md)
