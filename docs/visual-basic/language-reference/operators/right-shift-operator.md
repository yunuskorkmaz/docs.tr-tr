---
title: '>> İşleç (Visual Basic)'
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
ms.openlocfilehash: 337d651e831dc2ab132056f6e9a1f2b5300bf7f8
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701322"
---
# <a name="-operator-visual-basic"></a>> > Işleci (Visual Basic)
Bit bir düzende aritmetik sağa kaydırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Integral sayısal değeri. Bit deseninin kaydırinme sonucu. Veri türü `pattern` ' dır.  
  
 `pattern`  
 Gerekli. Integral sayısal ifadesi. Kaydırılan bit deseninin. Veri türü bir tam sayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long` veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü `Integer` olmalı veya `Integer` ' e genişlemelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki (oturum açma) biti, sol taraftaki bit konumlarına yayılır. Bu, `pattern` negatif bir değere sahipse, karıştırılmış konumların tek olarak ayarlandığı anlamına gelir; Aksi takdirde, sıfır olarak ayarlanır.  
  
 @No__t-0, `UShort`, `UInteger` ve `ULong` veri türlerinin işaretsiz olduğunu ve bu nedenle yaymaya yönelik bir oturum açma işlemi olmadığını unutmayın. @No__t-0 herhangi bir işaretsiz türde ise, karıştırılmış konumlar her zaman sıfır olarak ayarlanır.  
  
 Sonucun tutabileceğinden daha fazla bite göre kaydırmasını engellemek için, Visual Basic `amount` değeri `pattern` veri türüne karşılık gelen bir boyut maskesiyle. Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır. Boyut maskeleri aşağıdaki gibidir:  
  
|@No__t veri türü-0|Boyut maskesi (ondalık)|Boyut maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 @No__t-0 sıfırsa, `result` değeri `pattern` değeri ile aynıdır. @No__t-0 negatifse, imzasız bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 @No__t-0 işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam sayı değerlerinde aritmetik sağa kaymalar gerçekleştirmek için `>>` işlecini kullanır. Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `result1`, 2560 (0000 1010 0000 0000).  
  
- `result2`, 160 (0000 0000 1010 0000).  
  
- `result3`, 2 ' dir (0000 0000 0000 0010).  
  
- `result4`, 640 (0000 0010 1000 0000).  
  
- `result5` 0 ' dır (sağa kaydırılan 15 konum).  
  
 @No__t-0 için SHIFT miktarı 18 ve 15 olarak hesaplanır, bu da 2 ' ye eşittir.  
  
 Aşağıdaki örnek, negatif bir değer üzerinde aritmetik vardiyaları gösterir.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `negresult1`,-512 (1111 1110 0000 0000).  
  
- `negresult2`,-1 ' dir (işaret biti yayılır).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= İşleci](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
