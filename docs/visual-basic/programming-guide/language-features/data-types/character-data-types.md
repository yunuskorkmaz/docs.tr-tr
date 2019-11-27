---
title: Karakter Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: edd1d3a41dd878649aa422256b7858d7bce366e1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346388"
---
# <a name="character-data-types-visual-basic"></a>Karakter Veri Türleri (Visual Basic)
Visual Basic, yazdırılabilir ve görüntülenebilen karakterlerle uğraşmak için *karakter veri türleri* sağlar. Her ikisi de Unicode karakterlerle ilgilenirken `Char` tek bir karakter tutar, ancak `String` sonsuz sayıda karakter içerir.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını görüntüleyen bir tablo için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Karakter türü  
 `Char` veri türü, tek bir iki baytlık (16 bit) Unicode karakterdir. Bir değişken her zaman tam olarak bir karakter depoluyorsa, `Char`olarak bildirin. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Bir `Char` veya `String` değişkeninde olası her bir değer, Unicode karakter kümesindeki bir *kod noktasıdır*veya karakter kodudur. Unicode karakterler temel ASCII karakter kümesini, diğer diğer alfabe harflerini, vurguları, para birimi sembollerini, kesirleri, vurguları ve matematik ve teknik sembolleri içerir.  
  
> [!NOTE]
> Unicode karakter kümesi, D800-DFFF (55296 ile 55551 ondalık) ile birlikte, tek bir kod noktasını temsil etmek için 2 16-bit değerleri gerektiren *yedek çiftleri*için bu kod noktalarını ayırır. `Char` değişken bir vekil çifti tutamaz ve bir `String` böyle bir çiftin bulunduğu iki konum kullanır.  
  
 Daha fazla bilgi için bkz. [char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Dize türü  
 `String` veri türü, sıfır veya daha fazla iki baytlık (16 bit) Unicode karakterden oluşan bir dizidir. Bir değişken belirsiz sayıda karakter içeriyorsa, `String`olarak bildirin. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Daha fazla bilgi için bkz. [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic dönüşümler yazın](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
