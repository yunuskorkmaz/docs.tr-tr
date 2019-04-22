---
title: << İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 75c16c27dc919ba365cbe3c28c61a1e46496b0ae
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58824292"
---
# <a name="-operator-visual-basic"></a>\<\< İşleci (Visual Basic)
Bir bit desenine aritmetik sola kaydırma uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tamsayı sayısal değer. Bit deseninin kaydırma sonucu. Veri türü, aynı olduğu `pattern`.  
  
 `pattern`  
 Gerekli. Tamsayı sayısal ifade. Kaydırılmasına bit deseni. Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü olmalıdır `Integer` veya genişletmek için `Integer`.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir. Aritmetik sola kaydırma, sonuç veri türü aralığının dışında kaydırılacak bitlerin atılır ve sağ tarafta işleci boşaltılmış bit konumları sıfır olarak ayarlanır.  
  
 Bir sonuç tutabileceğinden daha fazla bit kaydırma önlemek için Visual Basic değerini maskeleri `amount` veri türüne karşılık gelen bir boyut maskesiyle `pattern`. İkili ve bu değerleri değiştirme miktarı için kullanılır. Boyutu maskeleri aşağıdaki gibidir:  
  
|Veri türü `pattern`|Boyutu maskesi (ondalık)|Boyutu maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|15|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 Varsa `amount` değeri sıfır olan `result` değeri olarak aynı `pattern`. Varsa `amount` olan negatif, işaretsiz bir değer olarak yapılan ve uygun boyutta maske ile maskelenir.  
  
 Aritmetik kaydırmalar hiçbir zaman taşması özel durumları oluşturur.  
  
> [!NOTE]
>  `<<` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `<<` kaydırmalar sol tam sayı değerleri üzerinde aritmetik işlemleri için işleci. Sonucu her zaman aynı veri türüne, kaydırılacak ifade sahiptir.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Önceki örneği sonuçları aşağıdaki gibidir:  
  
-   `result1` 192 (0000 0000 1100 0000) olur.  
  
-   `result2` 3072 (0000 1100 0000 0000) olan.  
  
-   `result3` -32768 (1000 0000 0000 0000) olur.  
  
-   `result4` 384 (0000 0001 1000 0000) olur.  
  
-   `result5` (sol ötelenen 15 basamak) 0'dır.  
  
 Değiştirme miktarı için `result4` 17 ' hesaplanır ve hangi eşittir 1 15.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= İşleci](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
