---
title: '>> Operatör'
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
ms.openlocfilehash: 00f43bc9bae6d550ed175906777ac273fc8e9a23
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873344"
---
# <a name="-operator-visual-basic"></a>>> Işleci (Visual Basic)

Bit bir düzende aritmetik sağa kaydırma gerçekleştirir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Bölümler  

 `result`  
 Gereklidir. Integral sayısal değeri. Bit deseninin kaydırinme sonucu. Veri türü, ile aynıdır `pattern` .  
  
 `pattern`  
 Gereklidir. Integral sayısal ifadesi. Kaydırılan bit deseninin. Veri türü bir integral türü ( `SByte` , `Byte` ,,,, `Short` `UShort` `Integer` `UInteger` , `Long` , veya `ULong` ) olmalıdır.  
  
 `amount`  
 Gereklidir. Sayısal ifade. Bit deseninin kaydırılacak bit sayısı. Veri türü `Integer` veya olarak ayarlanmalıdır `Integer` .  
  
## <a name="remarks"></a>Açıklamalar  

 Aritmetik vardiyalar dairesel değildir, bu da sonucun bir sonunun dışına sürüklenen bitlerin diğer uçta yeniden tanıtılmadığını gösterir. Aritmetik sağa kaydırma ' de, en sağdaki bit konumlarından daha fazla kaydırılan bitler atılır ve en soldaki (oturum açma) biti, sol taraftaki bit konumlarına yayılır. Yani `pattern` negatif bir değer varsa, karıştırılmış konumlar bir olarak ayarlanır; Aksi takdirde sıfır olarak ayarlanır.  
  
 ,, Ve veri türlerinin `Byte` `UShort` imzasız olduğunu `UInteger` ve bu `ULong` nedenle, yaymaya yönelik bir işaret biti olmadığını unutmayın. `pattern`Herhangi bir işaretsiz türde ise, karıştırılmış konumlar her zaman sıfır olarak ayarlanır.  
  
 Sonucun tutabileceğinden daha fazla bite göre kaydırmasını engellemek için, ' ın ' ın `amount` veri türüne karşılık gelen bir boyut maskesiyle değerini Visual Basic `pattern` . Bu değerlerin ikili dosyası ve kaydırma miktarı için kullanılır. Boyut maskeleri aşağıdaki gibidir:  
  
|Veri türü `pattern`|Boyut maskesi (ondalık)|Boyut maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|&H00000007|  
|`Short`, `UShort`|15|&H0000000F|  
|`Integer`, `UInteger`|31|&H0000001F|  
|`Long`, `ULong`|63|&H0000003F|  
  
 `amount`Sıfırsa, değeri `result` değeri ile aynıdır `pattern` . `amount`Negatifse, işaretsiz bir değer olarak alınır ve uygun boyut maskesiyle maskelenir.  
  
 Aritmetik vardiyalar hiçbir şekilde taşma özel durumu oluşturmaz.  
  
## <a name="overloading"></a>Aşırı Yükleme  

 `>>`İşleç *aşırı*yüklenebilir, yani bir işlenen bu sınıf veya yapının türüne sahip olduğunda bir sınıf veya yapının davranışını yeniden tanımlayabileceği anlamına gelir. Kodunuz böyle bir sınıf veya yapıda bu işleci kullanıyorsa, yeniden tanımlanmış davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz. [operatör yordamları](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, `>>` tam sayı değerlerinde aritmetik sağa kaymalar gerçekleştirmek için işlecini kullanır. Sonuç, kaydırılan deyimden her zaman aynı veri türüne sahiptir.  
  
 [!code-vb[VbVbalrOperators#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#14)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `result1` 2560 ' dir (0000 1010 0000 0000).  
  
- `result2` 160 ' dir (0000 0000 1010 0000).  
  
- `result3` 2 ' dir (0000 0000 0000 0010).  
  
- `result4` 640 ' dir (0000 0010 1000 0000).  
  
- `result5` 0 ' dır (sağa kaydırılan 15 konum).  
  
 İçin kaydırma miktarı `result4` 18 ve 15 olarak hesaplanır, bu da 2 ' ye eşittir.  
  
 Aşağıdaki örnek, negatif bir değer üzerinde aritmetik vardiyaları gösterir.  
  
 [!code-vb[VbVbalrOperators#55](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#55)]  
  
 Önceki örneğin sonuçları aşağıdaki gibidir:  
  
- `negresult1` -512 (1111 1110 0000 0000).  
  
- `negresult2` -1 ' dir (işaret biti yayılır).  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Bit Kaydırma İşleçleri](bit-shift-operators.md)
- [Atama Işleçleri](assignment-operators.md)
- [>>= Işleci](right-shift-assignment-operator.md)
- [Visual Basic'de İşleç Önceliği](operator-precedence.md)
- [İşlevselliğe Göre Listelenmiş İşleçler](operators-listed-by-functionality.md)
- [Visual Basic'de Aritmetik İşleçler](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
