---
title: < < Işleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: d6b186ad519bcd7cf82cce12523f2d75e09317cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966894"
---
# <a name="-operator-visual-basic"></a>\<\<İşleç (Visual Basic)
Bit bir düzende aritmetik sola kaydırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = pattern << amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Integral sayısal değeri. Bit deseninin kaydırinme sonucu. Veri türü, ile `pattern`aynıdır.  
  
 `pattern`  
 Gerekli. Integral sayısal ifadesi. Kaydırılan bit deseninin. `SByte`Veri türü bir integral türü (, `UShort` `Short` `Byte`,,, `Integer` `UInteger`, ,`Long`, veya`ULong`) olmalıdır.  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü `Integer` veya olarak `Integer`ayarlanmalıdır.  
  
## <a name="remarks"></a>Açıklamalar  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.  
  
 Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, ' ın değerini `amount` , veri `pattern`türüne karşılık gelen bir boyut maskesiyle Visual Basic. Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır. Boyut maskeleri aşağıdaki gibidir:  
  
|Veri türü`pattern`|Boyut maskesi (ondalık)|Boyut maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Sıfırsa, değeri değeri ile aynıdır `pattern`. `result` `amount` `amount` Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
> [!NOTE]
> İşleç aşırı yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. `<<` Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam sayı `<<` değerlerinde aritmetik sol vardiyaları gerçekleştirmek için işlecini kullanır. Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `result1`192 ' dir (0000 0000 1100 0000).  
  
- `result2`3072 ' dir (0000 1100 0000 0000).  
  
- `result3`-32768 (1000 0000 0000 0000).  
  
- `result4`384 ' dir (0000 0001 1000 0000).  
  
- `result5`0 ' dır (sola kaydırılacağı 15 konum).  
  
 İçin `result4` kaydırma miktarı 17 ve 15 olarak hesaplanır, 1 eşittir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= İşleci](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
