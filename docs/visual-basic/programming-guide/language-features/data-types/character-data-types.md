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
ms.openlocfilehash: 5a6a8dae63f3c0b5e3038304c1c2242f9e8c9c9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647394"
---
# <a name="character-data-types-visual-basic"></a>Karakter Veri Türleri (Visual Basic)
Visual Basic sağlar *karakter veri türleri* yazdırılabilir ve görüntülenebilecek karakterlerle dağıtılacak. Her ikisi de Unicode karakterlerle ilgilidir sırada `Char` tek bir karakter tutarken `String` sonsuz sayıda karakter içeriyor.  
  
 Visual Basic veri türleri yan yana karşılaştırmasını görüntüler bir tablo için bkz: [veri türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
## <a name="char-type"></a>Char türü  
 `Char` Veri türü olan tek bir iki baytlık (16-bit) Unicode karakter. Bir değişken her zaman tam olarak bir karakter depoluyorsa olarak bildirme `Char`. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Olası her değerin bir `Char` veya `String` değişkeni, bir *kod noktası*, veya karakter kodu, Unicode karakter kümesi. Unicode karakterler temel ASCII karakter kümesi, çeşitli diğer alfabedeki harfleri, vurgular, para birimi simgeleri, kesirler, Vurgu ve matematiksel ve teknik simgeleri içerir.  
  
> [!NOTE]
>  Kod noktaları için DFFF (55296 55551 ondalık aracılığıyla) aracılığıyla D800 yedekleri Unicode karakter kümesi *vekil çiftleri*, tek bir kod noktası göstermek için iki 16 bit değerleri gerektirir. A `Char` değişkeni, bir yedek çifti tutun olamaz ve `String` böyle bir çifti tutmak için iki konum kullanır.  
  
 Daha fazla bilgi için bkz: [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Dize türü  
 `String` Veri türü olan sıfır veya daha fazla iki baytlık (16-bit) Unicode karakter dizisi. Bir değişken sonsuz sayıda karakter içeriyorsa olarak bildirme `String`. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Daha fazla bilgi için bkz: [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
