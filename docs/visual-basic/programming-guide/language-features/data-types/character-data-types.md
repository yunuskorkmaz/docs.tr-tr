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
ms.openlocfilehash: 33dd4c62776ae8c5ec0ce0a6d0858a7ed0d047fb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401998"
---
# <a name="character-data-types-visual-basic"></a>Karakter Veri Türleri (Visual Basic)
Visual Basic, yazdırılabilir ve görüntülenebilen karakterlerle uğraşmak için *karakter veri türleri* sağlar. Her ikisi de Unicode karakterlerle ilgilenir, `Char` ancak `String` sonsuz sayıda karakter içeren tek bir karakter tutar.  
  
 Visual Basic veri türlerinin yan yana karşılaştırmasını görüntüleyen bir tablo için bkz. [veri türleri](../../../language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Karakter türü  
 `Char`Veri türü, tek bir iki baytlık (16 bit) Unicode karakterdir. Bir değişken her zaman tam olarak bir karakter depoluyorsa, olarak bildirin `Char` . Örnek:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Bir veya değişkenindeki olası her bir değer, `Char` `String` Unicode karakter kümesindeki bir *kod noktasıdır*veya karakter kodudur. Unicode karakterler temel ASCII karakter kümesini, diğer diğer alfabe harflerini, vurguları, para birimi sembollerini, kesirleri, vurguları ve matematik ve teknik sembolleri içerir.  
  
> [!NOTE]
> Unicode karakter kümesi, D800-DFFF (55296 ile 55551 ondalık) ile birlikte, tek bir kod noktasını temsil etmek için 2 16-bit değerleri gerektiren *yedek çiftleri*için bu kod noktalarını ayırır. Bir `Char` değişken bir vekil çifti tutamaz ve `String` Bu tür bir çift tutmak için iki konum kullanır.  
  
 Daha fazla bilgi için bkz. [char veri türü](../../../language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Dize türü  
 `String`Veri türü sıfır veya daha fazla iki baytlık (16 bit) Unicode karakterden oluşan bir dizidir. Bir değişken belirsiz sayıda karakter içeriyorsa, olarak bildirin `String` . Örnek:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Daha fazla bilgi için bkz. [dize veri türü](../../../language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Veri Türleri](elementary-data-types.md)
- [Bileşik Veri Türleri](composite-data-types.md)
- [Visual Basic genel türler](generic-types.md)
- [Değer Türleri ve Başvuru Türleri](value-types-and-reference-types.md)
- [Visual Basic'de Tür Dönüştürmeleri](type-conversions.md)
- [Veri Türü Sorunlarını Giderme](troubleshooting-data-types.md)
- [Tür Karakterleri](type-characters.md)
