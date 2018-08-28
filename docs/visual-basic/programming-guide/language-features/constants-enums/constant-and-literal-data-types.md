---
title: Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declaring constants [Visual Basic], literal data types
- data types [Visual Basic], declaring
- constants [Visual Basic], declaring
- explicit declarations
- literals [Visual Basic], coercing data type
- declarations [Visual Basic], data types
ms.assetid: 057206d2-3a5b-40b9-b3af-57446f9b52fa
ms.openlocfilehash: 1d030f8058cd497212c20bca8f064f2bedc99fce
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2018
ms.locfileid: "42999933"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)
Bir sabit değer kendisi yerine bir değişkenin değerini veya 3 sayı veya dize "Hello" gibi bir ifadenin sonucu olarak ifade bir değerdir. Bir değişmez değerin yerini alır ve bu değer bir değişken değerini değiştirebilir, programın boyunca saklar anlamlı bir ad bir sabittir.  
  
 Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olduğu `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olduğu `On`, tüm sabit bir türle açıkça bildirmelidir. Aşağıdaki örnekte, veri türü `MyByte` açıkça veri türü olarak bildirilmiş `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Zaman `Option Infer` olduğu `On` veya `Option Strict` olduğu `Off`, bir veri türüyle belirtmeden bir sabit bildirebilirsiniz bir `As` yan tümcesi. Derleyici sabiti ifadesinin türünden türünü belirler. Varsayılan olarak sayısal tamsayı sabit değeri saçıldığı `Integer` veri türü. Kayan noktalı sayılar için varsayılan veri türü `Double`ve anahtar sözcükler `True` ve `False` belirtin bir `Boolean` sabit.  
  
## <a name="literals-and-type-coercion"></a>Değişmez değerler ve tür zorlama  
 Bazı durumlarda, belirli bir tür için bir sabit değer zorlamak isteyebilirsiniz; Örneğin, özellikle büyük tamsayı değişmez değer türünde bir değişkene atarken `Decimal`. Aşağıdaki örnek, bir hata oluşturur:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Değişmez değerin gösterimi hata sonuçları. `Decimal` Veri türü tutabilir değeri bu büyük ancak değişmez değer olarak örtük olarak temsil edilen bir `Long`, hangi olamaz.  
  
 İki yolla belirli veri türü için bir sabit değer coerce: bir tür kendisine karakterinin ya da karakterini içinde yerleştirme. Türü bir karakteri veya karakterleri kapsayan gerekir hemen önünde ve/veya boşluk olmaması veya herhangi bir türde karakter değişmez değeri izleyin.  
  
 Önceki örnekte iş yapmak için ekleyebilir `D` karakter olarak temsil edilen neden değişmez değer türü bir `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 Aşağıdaki örnek, türü, kapsayan karakter doğru kullanımını gösterir:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Aşağıdaki tabloda gösterilen kapsayan karakterleri ve karakter türü Visual Basic'te kullanılabilir.  
  
|Veri türü|Kapsayan karakter|Eklenen türü karakteri|  
|---|---|---|  
|`Boolean`|(hiçbiri)|(hiçbiri)|  
|`Byte`|(hiçbiri)|(hiçbiri)|  
|`Char`|"|C|  
|`Date`|#|(hiçbiri)|  
|`Decimal`|(hiçbiri)|D veya @|  
|`Double`|(hiçbiri)|R veya #|  
|`Integer`|(hiçbiri)|%|  
|`Long`|(hiçbiri)|M veya &|  
|`Short`|(hiçbiri)|S|  
|`Single`|(hiçbiri)|F veya!|  
|`String`|"|(hiçbiri)|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kullanıcı Tanımlı Sabitler](../../../../visual-basic/programming-guide/language-features/constants-enums/user-defined-constants.md)  
 [Nasıl yapılır: Bir Sabit Bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-a-constant.md)  
 [Sabitlere Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [Option Strict Deyimi](../../../../visual-basic/language-reference/statements/option-strict-statement.md)  
 [Option Explicit Deyimi](../../../../visual-basic/language-reference/statements/option-explicit-statement.md)  
 [Sabit Listelerine Genel Bakış](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [Nasıl yapılır: bir numaralandırma bildirme](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [Sabit Listeleri ve Ad Niteliği](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/index.md)  
 [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
