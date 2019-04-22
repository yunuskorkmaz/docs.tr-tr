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
ms.openlocfilehash: 14085172a8f9f9d60af0495a36dd4ba7592213fa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840984"
---
# <a name="character-data-types-visual-basic"></a>Karakter Veri Türleri (Visual Basic)
Visual Basic sağlar *karakter veri türleri* yazdırılabilir ve görüntülenebilen karakterler ile dağıtılacak. Her ikisi de Unicode karakterleriyle işlem sırasında `Char` tek bir karakter tutarken `String` sonsuz sayıda karakter içeriyor.  
  
 Visual Basic veri türleri yan yana karşılaştırmasını gösteren bir tablo için bkz [veri türleri](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="char-type"></a>Char türü  
 `Char` Veri türü olan tek bir iki baytlık (16-bit) Unicode karakter. Bir değişken her zaman tam olarak bir karakter içermiyorsa, olarak bildirin `Char`. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#1)]
  
 Olası her değeri bir `Char` veya `String` değişken bir *kod noktası*, veya Unicode karakter kümesindeki karakter kodu. Temel ASCII karakter kümesi, çeşitli diğer alfabedeki harfleri, vurgular, para birimi sembolleri, kesirli, aksanlar ve semboller matematiksel ve teknik Unicode karakterler içerir.  
  
> [!NOTE]
>  Kod noktaları için DFFF (55296 55551 ondalık üzerinden) aracılığıyla D800 yedekleri Unicode karakter kümesi *vekil çiftleri*, iki 16-bit değerleri temsil eden tek bir kod noktası gerektirir. A `Char` değişkeni, bir yedek çifti tutun olamaz ve bir `String` böyle bir çift tutmak için iki konum kullanır.  
  
 Daha fazla bilgi için [Char veri türü](../../../../visual-basic/language-reference/data-types/char-data-type.md).  
  
## <a name="string-type"></a>Dize türü  
 `String` Veri türü olan bir dizi iki baytlık (16-bit) sıfır veya daha fazla Unicode karakteri. Bir değişken sonsuz sayıda karakter içeriyorsa olarak bildirin `String`. Örneğin:  
  
 [!code-vb[VbVbalrCharTypes#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrchartypes/vb/module1.vb#2)]
  
 Daha fazla bilgi için [dize veri türü](../../../../visual-basic/language-reference/data-types/string-data-type.md).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlangıç Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Bileşik Veri Türleri](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Visual Basic'de genel türler](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Değer Türleri ve Başvuru Türleri](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Visual Basic'de tür dönüştürmeleri](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Veri Türü Sorunlarını Giderme](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Tür Karakterleri](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)
