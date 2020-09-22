---
title: << İşleci
ms.date: 07/20/2015
f1_keywords:
- vb.<<
helpviewer_keywords:
- bit shift operators [Visual Basic]
- << operator [Visual Basic]
- operator <<, Visual Basic left shift operator
ms.assetid: fdb93d25-81ba-417f-b808-41207bfb8440
ms.openlocfilehash: 77bf26d4e6bb068f9130deed5eb1ecbaee62afce
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90866791"
---
# <a name="-operator-visual-basic"></a>\<\< İşleç (Visual Basic)

Bit bir düzende aritmetik sola kaydırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = pattern << amount  
```  
  
## <a name="parts"></a>Bölümler  

 `result`  
 Gereklidir. Integral sayısal değeri. Bit deseninin kaydırinme sonucu. Veri türü, ile aynıdır `pattern` .  
  
 `pattern`  
 Gereklidir. Integral sayısal ifadesi. Kaydırılan bit deseninin. Veri türü bir integral türü ( `SByte` , `Byte` ,,,, `Short` `UShort` `Integer` `UInteger` , `Long` , veya `ULong` ) olmalıdır.  
  
 `amount`  
 Gereklidir. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü `Integer` veya olarak ayarlanmalıdır `Integer` .  
  
## <a name="remarks"></a>Açıklamalar  

 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sola kaydırma içinde, sonuç veri türü aralığının ötesinde kaydırılan bitler atılır ve sağdaki bit konumları sıfır olarak ayarlanır.  
  
 Vardiyanın, sonucun tutabileceğinden daha fazla bit olmasını engellemek için, ' ın değerini, `amount` veri türüne karşılık gelen bir boyut maskesiyle Visual Basic `pattern` . Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır. Boyut maskeleri aşağıdaki gibidir:  
  
|Veri türü `pattern`|Boyut maskesi (ondalık)|Boyut maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 `amount`Sıfırsa, değeri `result` değeri ile aynıdır `pattern` . `amount`Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
> [!NOTE]
> `<<`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `<<` tam sayı değerlerinde aritmetik sol vardiyaları gerçekleştirmek için işlecini kullanır. Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.  
  
 [!code-vb[VbVbalrOperators#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#12)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `result1` 192 ' dir (0000 0000 1100 0000).  
  
- `result2` 3072 ' dir (0000 1100 0000 0000).  
  
- `result3` -32768 (1000 0000 0000 0000).  
  
- `result4` 384 ' dir (0000 0001 1000 0000).  
  
- `result5` 0 ' dır (sola kaydırılacağı 15 konum).  
  
 İçin kaydırma miktarı `result4` 17 ve 15 olarak hesaplanır, 1 eşittir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](bit-shift-operators.md)
- [Atama Işleçleri](assignment-operators.md)
- [<<= Işleci](left-shift-assignment-operator.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
