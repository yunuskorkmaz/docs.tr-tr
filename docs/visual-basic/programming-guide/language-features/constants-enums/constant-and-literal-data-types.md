---
title: Sabit ve Değişmez Değerli Veri Türleri
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: b94259326b42104db05d9fc5bb09f686075d0759
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414537"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)
Değişmez değer, değişkenin değeri veya "Hello" dizesi gibi bir ifadenin sonucu yerine kendisini ifade eden bir değerdir. Sabit, bir sabit değerin yerini alan anlamlı bir addır ve değer değişebilir bir değişkenin aksine, bu değeri program genelinde tutar.  
  
 [Option Infer](../../../language-reference/statements/option-infer-statement.md) `Off` ve [Option Strict](../../../language-reference/statements/option-strict-statement.md) olduğunda `On` , tüm sabitleri açıkça bir veri türüyle bildirmeniz gerekir. Aşağıdaki örnekte, veri türü `MyByte` açıkça veri türü olarak bildirilmiştir `Byte` :  
  
 [!code-vb[VbVbalrConstants#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#1)]  
  
 `Option Infer`Veya olduğunda `On` `Option Strict` `Off` , yan tümcesiyle bir veri türü belirtmeden bir sabit bildirebilirsiniz `As` . Derleyici, ifadenin türünden sabit türünü belirler. Sayısal tamsayı sabit değeri varsayılan olarak `Integer` veri türüne ayarlanır. Kayan nokta numaraları için varsayılan veri türü `Double` ve anahtar sözcükler `True` ve `False` bir `Boolean` sabit belirtin.  
  
## <a name="literals-and-type-coercion"></a>Değişmez değerler ve tür zorlaması  
 Bazı durumlarda, bir sabit değeri belirli bir veri türüne zorlamak isteyebilirsiniz; Örneğin, tür değişkenine özellikle büyük bir integral sabit değer atama yaparken `Decimal` . Aşağıdaki örnek bir hata üretir:  
  
```vb  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Hata, sabit değerinin gösteriminden kaynaklanmaktadır. `Decimal`Veri türü bu büyüklükte bir değer tutabilir, ancak değişmez değer örtülü olarak bir olarak temsil edilir, ancak `Long` .  
  
 Bir sabit değeri, belirli bir veri türüne iki şekilde dönüştürebilirsiniz: buna bir tür karakteri ekleyerek veya kapsayan karakterlerin içine yerleştirerek. Bir tür karakteri veya kapsayan karakterler, hiçbir türden boşluk veya karakter olmadan hemen önce ve/veya sabit değer içermelidir.  
  
 Önceki örneğin çalışmasını sağlamak için, `D` tür karakterini değişmez değere ekleyebilirsiniz, bu, şöyle temsil edilmesine neden olur `Decimal` :  
  
 [!code-vb[VbVbalrConstants#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#2)]  
  
 Aşağıdaki örnek, tür karakterlerinin ve kapsayan karakterlerin doğru kullanımını gösterir:  
  
 [!code-vb[VbVbalrConstants#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrConstants/VB/Class1.vb#3)]  
  
 Aşağıdaki tabloda, Visual Basic ' de bulunan karakterlerin ve tür karakterlerinin gösterildiği gösterilmektedir.  
  
|Veri türü|Kapsayan karakter|Eklenen tür karakteri|  
|---|---|---|  
|`Boolean`|(yok)|(yok)|  
|`Byte`|(yok)|(yok)|  
|`Char`|"|C|  
|`Date`|#|(yok)|  
|`Decimal`|(yok)|D veya @|  
|`Double`|(yok)|R veya #|  
|`Integer`|(yok)|I veya%|  
|`Long`|(yok)|L veya &|  
|`Short`|(yok)|S|  
|`Single`|(yok)|F veya!|  
|`String`|"|(yok)|  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kullanıcı Tanımlı Sabitler](user-defined-constants.md)
- [Nasıl yapılır: Bir Sabit Bildirme](how-to-declare-a-constant.md)
- [Sabitlere Genel Bakış](constants-overview.md)
- [Option Strict Deyimi](../../../language-reference/statements/option-strict-statement.md)
- [Option Explicit Deyimi](../../../language-reference/statements/option-explicit-statement.md)
- [Sabit Listelerine Genel Bakış](enumerations-overview.md)
- [Nasıl yapılır: numaralandırma bildirme](how-to-declare-enumerations.md)
- [Sabit Listeleri ve Ad Niteliği](enumerations-and-name-qualification.md)
- [Veri türleri](../../../language-reference/data-types/index.md)
- [Sabitler ve numaralandırmalar](../../../language-reference/constants-and-enumerations.md)
