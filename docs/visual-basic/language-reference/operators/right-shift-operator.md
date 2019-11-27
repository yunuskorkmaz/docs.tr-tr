---
title: '>> İşleç'
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
ms.openlocfilehash: cabf8c569435cc0fc98282f5e8f5fd410e6708dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347818"
---
# <a name="-operator-visual-basic"></a>> > Işleci (Visual Basic)
Bit bir düzende aritmetik sağa kaydırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Integral sayısal değeri. Bit deseninin kaydırinme sonucu. Veri türü `pattern`ile aynıdır.  
  
 `pattern`  
 Gerekli. Integral sayısal ifadesi. Kaydırılan bit deseninin. Veri türü bir tam sayı türü (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`veya `ULong`) olmalıdır.  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü `Integer` veya `Integer`için genişlemelidir.  
  
## <a name="remarks"></a>Açıklamalar  
 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki (oturum açma) biti, sol taraftaki bit konumlarına yayılır. Bu, `pattern` negatif bir değer içeriyorsa, karıştırılmış konumların tek olarak ayarlandığı anlamına gelir; Aksi takdirde, sıfır olarak ayarlanır.  
  
 `Byte`, `UShort`, `UInteger`ve `ULong` veri türlerinin işaretsiz olduğunu ve bu nedenle yaymaya yönelik bir oturum açma işlemi olmadığını unutmayın. `pattern` herhangi bir işaretsiz türde ise, karıştırılmış konumlar her zaman sıfır olarak ayarlanır.  
  
 Sonucun tutabileceğinden daha fazla bite göre kaydırmasını engellemek için, `amount` değerini `pattern`veri türüne karşılık gelen bir boyut maskesiyle Visual Basic maskeleri. Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır. Boyut maskeleri aşağıdaki gibidir:  
  
|`pattern` veri türü|Boyut maskesi (ondalık)|Boyut maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 `amount` sıfırsa, `result` değeri `pattern`değeriyle aynıdır. `amount` negatifse, imzasız bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `>>` işleci *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, tam sayı değerlerinde aritmetik sağa kaymalar gerçekleştirmek için `>>` işlecini kullanır. Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `result1` 2560 (0000 1010 0000 0000).  
  
- `result2` 160 (0000 0000 1010 0000).  
  
- `result3` 2 ' dir (0000 0000 0000 0010).  
  
- `result4` 640 (0000 0010 1000 0000).  
  
- `result5` 0 ' dır (sağa kaydırılan 15 konum).  
  
 `result4` için kaydırma miktarı 18 ve 15 olarak hesaplanır, bu da 2 ' ye eşittir.  
  
 Aşağıdaki örnek, negatif bir değer üzerinde aritmetik vardiyaları gösterir.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `negresult1`-512 (1111 1110 0000 0000).  
  
- `negresult2`-1 ' dir (işaret biti yayılır).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [>>= İşleci](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)
- [Visual Basic operatör önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Visual Basic aritmetik Işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
