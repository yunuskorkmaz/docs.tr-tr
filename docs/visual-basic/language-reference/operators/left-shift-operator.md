---
title: '&lt;&lt;İşleci (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 56cfb227f7e5c68de802c1f2cfb842a770f65ae0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;İşleci (Visual Basic)
Bir bit desenine aritmetik sola kaydırma uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tam Sayı sayısal değer. Bit desenini kaydırma sonucu. Veri türü aynıdır `pattern`.  
  
 `pattern`  
 Gerekli. Tam Sayı sayısal ifade. Değişebilir bit deseni. Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit desenini kaydırılacak bit sayısı. Veri türü olmalıdır `Integer` veya için genişletmek `Integer`.  
  
## <a name="remarks"></a>Açıklamalar  
 Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil. Aritmetik sola kaydırma, sonuç veri türü aralık dışında gölgeye BITS atılır ve sağ taraftaki vacated bit konumları sıfıra ayarlanır.  
  
 Shift sonucu tutabileceğinden daha fazla BITS tarafından önlemek için Visual Basic değerini maskeleri `amount` veri türüne karşılık gelen boyut maskesiyle `pattern`. İkili ve bu değerleri shift tutarı için kullanılır. Boyutu maskeleri aşağıdaki gibidir:  
  
|Veri türü`pattern`|Boyutu maskesi (ondalık)|Boyutu maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Varsa `amount` sıfır, değeri olan `result` değerine aynıdır `pattern`. Varsa `amount` olan negatif olduğundan imzasız bir değer olarak dikkate ve uygun boyutta maskesi ile maskelenir.  
  
 Aritmetik kaydırmalar hiçbir zaman taşma özel durumları oluşturur.  
  
> [!NOTE]
>  `<<` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `<<` tam sayı değerleri üzerinde kaydırmalar sol aritmetik gerçekleştirmek için işleci. Sonucu her zaman aynı veri, gölgeye ifade türüne sahip.  
  
 [!code-vb[VbVbalrOperators#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-operator_1.vb)]  
  
 Önceki örneği sonuçları aşağıdaki gibidir:  
  
-   `result1`192 (0000 0000 1100 0000) olur.  
  
-   `result2`3072 (0000 1100 0000 0000) değil.  
  
-   `result3`-32768 (1000 0000 0000 0000) olur.  
  
-   `result4`384 (0000 0001 1000 0000) olur.  
  
-   `result5`0 (sol ötelenen 15 basamak)'dır.  
  
 Shift tutarını `result4` 17 hesaplanır ve hangi eşittir 1 15.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bit kaydırma işleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [<< = işleci](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
