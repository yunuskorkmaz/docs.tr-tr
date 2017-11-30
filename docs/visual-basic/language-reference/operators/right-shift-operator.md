---
title: "&gt;&gt;İşleci (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.>>
helpviewer_keywords:
- operator>>
- '>> operator [Visual Basic]'
- bit shift operators [Visual Basic]
- operator >>
- right shift operators [Visual Basic]
ms.assetid: 054dc6a6-47d9-47ef-82da-cfa2b59fbf8f
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4eb0ed817c95905a679de5026bf6494eb72df078
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;İşleci (Visual Basic)
Bir bit desenine aritmetik sağa kaydırma uygular.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
result = pattern >> amount  
```  
  
## <a name="parts"></a>Bölümler  
 `result`  
 Gerekli. Tam Sayı sayısal değer. Bit desenini kaydırma sonucu. Veri türü aynıdır `pattern`.  
  
 `pattern`  
 Gerekli. Tam Sayı sayısal ifade. Değişebilir bit deseni. Veri türü tamsayı türü olmalıdır (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, veya `ULong`).  
  
 `amount`  
 Gerekli. Sayısal ifade. Bit desenini kaydırılacak bit sayısı. Veri türü olmalıdır `Integer` veya için genişletmek `Integer`.  
  
## <a name="remarks"></a>Açıklamalar  
 Aritmetik kaydırmalar sonucu ucunu gölgeye BITS diğer sonunda yeniden girmesini olmayan başka bir deyişle, döngüsel, değil. Aritmetik sağa kaydırma, en sağdaki bit konumu gölgeye BITS atılır ve soldaki (oturum) bit solda vacated bit konumları içine yayılır. Bu olması durumunda gelir `pattern` negatif bir değere sahip vacated konumlar birine ayarlanır; Aksi takdirde sıfıra ayarlanır.  
  
 Unutmayın veri türleri `Byte`, `UShort`, `UInteger`, ve `ULong` ; böylece yaymak için hiçbir oturum bit imzalanmamışsa. Varsa `pattern` değil herhangi türü İmzasız, vacated konumlar her zaman sıfır olarak ayarlanır.  
  
 Sonuç tutabileceğinden daha fazla BITS kaydırma önlemek için Visual Basic değerini maskeleri `amount` veri türü için karşılık gelen boyut maskesiyle `pattern`. İkili ve bu değerleri shift tutarı için kullanılır. Boyutu maskeleri aşağıdaki gibidir:  
  
|Veri türü`pattern`|Boyutu maskesi (ondalık)|Boyutu maskesi (onaltılık)|  
|----------------------------|---------------------------|-------------------------------|  
|`SByte`, `Byte`|7|& H00000007|  
|`Short`, `UShort`|15|& H0000000F|  
|`Integer`, `UInteger`|31|& H0000001F|  
|`Long`, `ULong`|63|& H0000003F|  
  
 Varsa `amount` sıfır, değeri olan `result` değerine aynıdır `pattern`. Varsa `amount` olan negatif olduğundan imzasız bir değer olarak dikkate ve uygun boyutta maskesi ile maskelenir.  
  
 Aritmetik kaydırmalar hiçbir zaman taşma özel durumları oluşturur.  
  
## <a name="overloading"></a>Aşırı Yükleme  
 `>>` İşleci olabilir *aşırı*, işleneni, sınıf veya yapı türüne sahip olduğunda bir sınıf veya yapı davranışını tanımlayabilirsiniz, anlamına gelir. Bu tür bir sınıf veya yapı üzerinde kodunuzu bu işleç kullanıyorsa, yeniden tanımlanan davranışını anladığınızdan emin olun. Daha fazla bilgi için bkz: [işleç yordamları](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek kullanır `>>` aritmetik sağa kaydırmalar tam sayı değerleri üzerinde gerçekleştirilecek işleci. Sonucu her zaman aynı veri, gölgeye ifade türüne sahip.  
  
 [!code-vb[VbVbalrOperators#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_1.vb)]  
  
 Önceki örnekte sonuçlarını aşağıdaki gibidir:  
  
-   `result1`2560 (0000 1010 0000 0000) değil.  
  
-   `result2`160 (0000 0000 1010 0000) olur.  
  
-   `result3`2 (0000 0000 0000 0010)'dir.  
  
-   `result4`640 (0000 0010 1000 0000)'dır.  
  
-   `result5`0 (ötelenen 15 basamağa sağa)'dır.  
  
 Shift tutarını `result4` 18 hesaplanır ve hangi eşittir 2 15.  
  
 Aşağıdaki örnek aritmetik kaydırmalar üzerinde negatif bir değer gösterir.  
  
 [!code-vb[VbVbalrOperators#55](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-operator_2.vb)]  
  
 Önceki örnekte sonuçlarını aşağıdaki gibidir:  
  
-   `negresult1`-512 (1111 1110 0000 0000) olur.  
  
-   `negresult2`(oturum bit yayılır) -1 ' dir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Bit kaydırma işleçleri](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Atama İşleçleri](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [>> = işleci](../../../visual-basic/language-reference/operators/right-shift-assignment-operator.md)  
 [Visual Basic'de İşleç önceliği](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [İşlevselliğe göre listelenmiş işleçler](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Visual Basic'de aritmetik işleçler](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
