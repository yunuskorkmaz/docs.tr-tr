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
ms.openlocfilehash: 1300ab60e825e7910825be2c65dcab90135ba988
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701124"
---
# <a name="-operator-visual-basic"></a>\< @ no__t-1 Işleci (Visual Basic)
Bit bir düzende aritmetik sola kaydırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Integral sayısal değeri. Bit deseninin kaydırinme sonucu. Veri türü `pattern` ' dır.  
  
 `pattern`  
 Gerekli. Integral sayısal ifadesi. Kaydırılan bit deseninin. Veri türü bir tam sayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü `Integer` olmalı veya `Integer` ' e genişlemelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.  
  
 Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, `amount` değerini `pattern` veri türüne karşılık gelen bir boyut maskesiyle Visual Basic. Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır. Boyut maskeleri aşağıdaki gibidir:  
  
|@No__t veri türü-0|Boyut maskesi (ondalık)|Boyut maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 @No__t-0 sıfırsa, `result` değeri `pattern` değeri ile aynıdır. @No__t-0 negatifse, imzasız bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
> [!NOTE]
> @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tamsayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için `<<` işlecini kullanır. Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `result1`, 192 (0000 0000 1100 0000).  
  
- `result2`, 3072 (0000 1100 0000 0000).  
  
- `result3`,-32768 (1000 0000 0000 0000).  
  
- `result4`, 384 (0000 0001 1000 0000).  
  
- `result5`, 0 ' dır (soldaki 15 konum).  
  
 @No__t-0 için SHIFT miktarı 17 ve 15 olarak hesaplanır; bu değer 1 ' dir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<<= İşleci](../../../visual-basic/language-reference/operators/left-shift-assignment-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
