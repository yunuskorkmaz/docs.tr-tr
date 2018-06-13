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
ms.openlocfilehash: 8d110ec17bcdb03f339d779b2950ba56d77957cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649854"
---
# <a name="constant-and-literal-data-types-visual-basic"></a>Sabit ve Değişmez Değerli Veri Türleri (Visual Basic)
Bir sabit değer olarak kendisi yerine bir değişkenin değeri veya 3 sayı veya dize "Hello" gibi bir ifadenin sonucu olarak ifade bir değerdir. Bir sabit bir hazır değer yerini alır ve bu aynı değer değerini değiştirebilir, bir değişken aksine program boyunca korur anlamlı bir addır.  
  
 Zaman [Option Infer](../../../../visual-basic/language-reference/statements/option-infer-statement.md) olan `Off` ve [Option Strict](../../../../visual-basic/language-reference/statements/option-strict-statement.md) olan `On`, tüm sabit veri türüne sahip açıkça bildirilmelidir. Aşağıdaki örnekte, veri türü `MyByte` açıkça veri türü olarak bildirilmiş `Byte`:  
  
 [!code-vb[VbVbalrConstants#1](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_1.vb)]  
  
 Zaman `Option Infer` olan `On` veya `Option Strict` olan `Off`, bir veri türüyle belirtmeden bir sabit bildirebilir bir `As` yan tümcesi. Derleyici ifade türünden sabiti türünü belirler. Varsayılan olarak sabit bir sayısal tamsayı cast `Integer` veri türü. Kayan nokta sayıları için varsayılan veri türü `Double`ve anahtar sözcükler `True` ve `False` belirtin bir `Boolean` sabit.  
  
## <a name="literals-and-type-coercion"></a>Değişmez değerler ve tür zorlama  
 Bazı durumlarda, belirli veri türü için bir hazır değer zorlamak isteyebilirsiniz; Örneğin, özellikle büyük tam sayı değişmez değer türü bir değişkene atarken `Decimal`. Aşağıdaki örnek, bir hata üretir:  
  
```  
Dim myDecimal as Decimal  
myDecimal = 100000000000000000000   ' This causes a compiler error.  
```  
  
 Sabit gösteriminden hata oluşur. `Decimal` Veri türü tutun değeri bu büyük ancak sabit örtük olarak temsil edilen bir `Long`, hangi olamaz.  
  
 İki yolla belirli veri türü için bir hazır değer coerce: ona bir tür karakteri ekleyerek veya karakterini içinde yerleştirebilirsiniz. Tür karakteri veya karakterini gerekir hemen önünde ve/veya boşluk olmaması veya herhangi bir türde karakter olmayan sabit izleyin.  
  
 Önceki örnekte iş yapmak için ekleyebilirsiniz `D` türü karakteri olarak gösterilemeyecek kadar neden değişmez değeri için bir `Decimal`:  
  
 [!code-vb[VbVbalrConstants#2](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_2.vb)]  
  
 Aşağıdaki örnek, türü ve kapsayan karakterleri doğru kullanımını gösterir:  
  
 [!code-vb[VbVbalrConstants#3](../../../../visual-basic/programming-guide/language-features/constants-enums/codesnippet/VisualBasic/constant-and-literal-data-types_3.vb)]  
  
 Aşağıdaki tabloda gösterildiği kapsayan karakterler ve Visual Basic'te kullanılabilir karakterleri yazın.  
  
|Veri türü|Kapsayan karakter|Eklenen türü karakteri|  
|---|---|---|  
|`Boolean`|(hiçbiri)|(hiçbiri)|  
|`Byte`|(hiçbiri)|(hiçbiri)|  
|`Char`|"|C|  
|`Date`|#|(hiçbiri)|  
|`Decimal`|(hiçbiri)|D @|  
|`Double`|(hiçbiri)|R veya #|  
|`Integer`|(hiçbiri)|Veya %|  
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
 [Veri Türleri](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Sabitler ve Sabit Listeleri](../../../../visual-basic/language-reference/constants-and-enumerations.md)
