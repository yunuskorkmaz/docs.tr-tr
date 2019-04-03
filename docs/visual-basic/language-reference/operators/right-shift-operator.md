---
title: '>> İşleci (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
ms.openlocfilehash: 8803dc2e25edde756958a243d429dd30c5c78bcf
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816973"
---
# <a name="-operator-visual-basic"></a>>> İşleci (Visual Basic)
Bir bit desenine aritmetik sağa kaydırma uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tamsayı sayısal değer. Bit deseninin kaydırma sonucu. Veri türü, aynı olduğu `pattern`.  
  
 `pattern`  
 Gerekli. Tamsayı sayısal ifade. Kaydırılmasına bit deseni. Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü olmalıdır `Integer` veya genişletmek için `Integer`.  
  
## <a name="remarks"></a>Açıklamalar  
 Sonucu ucunu kaydırılacak bitlerin diğer sonunda yeniden girmesini yok anlamına gelir özelliği aritmetik kaydırmalar döngüsel, değildir. Aritmetik sağa kaydırma, en sağdaki bit ötesindeki kaydırılacak bitlerin atılır ve soldaki (imzala) bit içine solda işleci boşaltılmış bit konumlarına yayılır. Olması durumunda başka bir deyişle `pattern` negatif bir değere sahip boşaltılmış konumları birine ayarlanır; Aksi halde sıfır olarak ayarlanır.  
  
 Unutmayın veri türlerini `Byte`, `UShort`, `UInteger`, ve `ULong` yaymak için hiç imza biti olduğundan imzalanmamışsa. Varsa `pattern` değil herhangi bir türü imzalanmamış, boşaltılmış konumları her zaman sıfır olarak ayarlayın.  
  
 Sonuç tutabileceğinden daha fazla bit kaydırma önlemek için Visual Basic değerini maskeleri `amount` veri türü için karşılık gelen bir boyut maskesiyle `pattern`. İkili ve bu değerleri değiştirme miktarı için kullanılır. Boyutu maskeleri aşağıdaki gibidir:  
  
|Veri türü `pattern`|Boyutu maskesi (ondalık)|Boyutu maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&AMP; H00000007|  
|`Short`, `UShort`|15|&AMP; H0000000F|  
|`Integer`, `UInteger`|31|&AMP; H0000001F|  
|`Long`, `ULong`|63|&AMP; H0000003F|  
  
 Varsa `amount` değeri sıfır olan `result` değeri olarak aynı `pattern`. Varsa `amount` olan negatif, işaretsiz bir değer olarak yapılan ve uygun boyutta maske ile maskelenir.  
  
 Aritmetik kaydırmalar hiçbir zaman taşması özel durumları oluşturur.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `>>` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Kodunuz bu tür bir sınıf veya yapı üzerinde bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte `>>` tam sayı değerleri üzerinde aritmetik sağa kaydırmalar gerçekleştirmek için işleci. Sonucu her zaman aynı veri türüne, kaydırılacak ifade sahiptir.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Yukarıdaki örnekte sonuçları aşağıdaki gibidir:  
  
-   `result1` 2560 (0000 1010 0000 0000) olan.  
  
-   `result2` 160 (0000 0000 1010 0000) olur.  
  
-   `result3` 2 (0000 0000 0000 0010)'dir.  
  
-   `result4` 640 (0000 0010 1000 0000)'dır.  
  
-   `result5` (sağ ötelenen 15 basamak) 0'dır.  
  
 Değiştirme miktarı için `result4` 18 hesaplanır ve hangi eşittir 2 15.  
  
 Aşağıdaki örnek, negatif bir değer üzerinde aritmetik kaydırmalar gösterir.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Yukarıdaki örnekte sonuçları aşağıdaki gibidir:  
  
-   `negresult1` -512 (1111 1110 0000 0000) olur.  
  
-   `negresult2` -1 (imza biti yayılır) olur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= İşleci](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
