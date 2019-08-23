---
title: Karakter Veri Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], character
- String data type [Visual Basic], character data types
- character data types [Visual Basic]
- Char data type [Visual Basic], character data types
- data types [Visual Basic], choosing
ms.assetid: 902479ef-1679-47fc-9911-0c1c5008226c
ms.openlocfilehash: d29e8771d61c04cf35aa71b5ba7fbba0d308c730
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965685"
---
# <a name="character-data-types-visual-basic"></a>Karakter Veri Türleri (Visual Basic)
Visual Basic, yazdırılabilir ve görüntülenebilen karakterlerle uğraşmak için *karakter veri türleri* sağlar. Her ikisi de Unicode karakterlerle ilgilenir, `Char` ancak `String` sonsuz sayıda karakter içeren tek bir karakter tutar.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını görüntüleyen bir tablo için bkz. [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Karakter türü  
 `Char` Veri türü, tek bir iki baytlık (16 bit) Unicode karakterdir. Bir değişken her zaman tam olarak bir karakter depoluyorsa, olarak `Char`bildirin. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Bir `Char` veya`String` değişkenindeki olası her bir değer, Unicode karakter kümesindeki bir *kod noktasıdır*veya karakter kodudur. Unicode karakterler temel ASCII karakter kümesini, diğer diğer alfabe harflerini, vurguları, para birimi sembollerini, kesirleri, vurguları ve matematik ve teknik sembolleri içerir.  
  
> [!NOTE]
> Unicode karakter kümesi, D800-DFFF (55296 ile 55551 ondalık) ile birlikte, tek bir kod noktasını temsil etmek için 2 16-bit değerleri gerektiren *yedek çiftleri*için bu kod noktalarını ayırır. Bir değişken bir vekil çifti tutamaz `String` ve bu tür bir çift tutmak için iki konum kullanır. `Char`  
  
 Daha fazla bilgi için bkz. [char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Dize türü  
 `String` Veri türü sıfır veya daha fazla iki baytlık (16 bit) Unicode karakterden oluşan bir dizidir. Bir değişken belirsiz sayıda karakter içeriyorsa, olarak `String`bildirin. Örneğin:  
  
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
