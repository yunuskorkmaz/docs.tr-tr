---
title: If İşleci (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 244c0598c65ba691decc09c36293799571211a40
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701162"
---
# <a name="if-operator-visual-basic"></a>If İşleci (Visual Basic)
İki değerden birini koşullu olarak döndürmek için kısa devre değerlendirmesi kullanır. @No__t-0 işleci üç bağımsız değişkenle veya iki bağımsız değişkenle çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```vb  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Eğer Işleci üç bağımsız değişkenle çağrılırsa  
 @No__t-0 üç bağımsız değişken kullanılarak çağrıldığında, ilk bağımsız değişken, `Boolean` olarak yayınlanabileceğiniz bir değer olarak değerlendirilmelidir. Bu `Boolean` değeri, diğer iki bağımsız değişkenin hangisinin değerlendirileceğini ve döndürüldüğünü belirlemektir. Aşağıdaki liste yalnızca `If` işleci üç bağımsız değişken kullanılarak çağrıldığında geçerlidir.  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`argument1`|Gerekli. `Boolean`. Değerlendirmek ve döndürmek için diğer bağımsız değişkenlerden hangisinin verileceğini belirler.|  
|`argument2`|Gerekli. `Object`. @No__t-0 `True` olarak değerlendirilirse, değerlendirilir ve döndürülür.|  
|`argument3`|Gerekli. `Object`. @No__t-0 `False` ' i değerlendirilirse veya `argument1` değeri [Nothing](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilen bir [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` değişkeni ise değerlendirilir ve döndürülür.|  
  
 Üç bağımsız değişkenle çağrılan `If` işleci, kısa devre değerlendirmesi kullanması dışında `IIf` işlevi gibi çalışır. @No__t-0 işlevi her zaman bağımsız değişkenlerini değerlendirir, ancak üç bağımsız değişkenine sahip bir `If` işleci yalnızca ikisini değerlendirir. İlk `If` bağımsız değişkeni değerlendirilir ve sonuç, `Boolean` değeri `True` veya `False` olarak ayarlanır. Değer `True` ise, `argument2` değerlendirilir ve değeri döndürülür, ancak `argument3` değerlendirilmez. @No__t-0 ifadesinin değeri `False` ise, `argument3` değerlendirilir ve değeri döndürülür, ancak `argument2` değerlendirilmez. Aşağıdaki örneklerde, üç bağımsız değişken kullanıldığında `If` kullanımı gösterilmektedir:  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 Aşağıdaki örnek, kısa devre değerlendirmesinin değerini gösterir. Örnekte, `divisor` sıfır olduğunda, `divisor` değişkenine `number` değişkenini bölmek için iki deneme gösterilmektedir. Bu durumda, 0 döndürülmeli ve bir çalışma zamanı hatası sonucunda, Bölüm gerçekleştirmek için bir deneme yapılmamalıdır. @No__t-0 ifadesi kısa devre değerlendirmesi kullandığından, ilk bağımsız değişkenin değerine bağlı olarak ikinci ya da üçüncü bağımsız değişkeni değerlendirir. İlk bağımsız değişken true ise, bölen sıfır değildir ve ikinci bağımsız değişkeni değerlendirmek ve bölme gerçekleştirmek güvenlidir. İlk bağımsız değişken false ise, yalnızca üçüncü bağımsız değişken değerlendirilir ve 0 döndürülür. Bu nedenle, bölen 0 olduğunda, bölme gerçekleştirmek için bir deneme yapılmaz ve hata sonucu yoktur. Ancak, `IIf` kısa devre değerlendirmesi kullanmıyorsa, ilk bağımsız değişken false olduğunda bile ikinci bağımsız değişken değerlendirilir. Bu, çalışma zamanı sıfıra bölme hatasına neden olur.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Eğer Işleci Iki bağımsız değişkenle çağrılırsa  
 @No__t-0 ' a yönelik ilk bağımsız değişken atlanabilir. Bu, işlecin yalnızca iki bağımsız değişken kullanılarak çağrılmasına olanak sağlar. Aşağıdaki liste yalnızca `If` işleci iki bağımsız değişkenle çağrıldığında geçerlidir.  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`argument2`|Gerekli. `Object`. Başvuru veya null yapılabilir bir tür olmalıdır. @No__t-0 dışında bir şeyi değerlendirirken değerlendirilir ve döndürülür.|  
|`argument3`|Gerekli. `Object`. @No__t-0 `Nothing` olarak değerlendirilirse, değerlendirilir ve döndürülür.|  
  
 @No__t-0 bağımsız değişkeni atlandığında, ilk bağımsız değişken bir başvuru veya null yapılabilir bir tür olmalıdır. İlk bağımsız değişken `Nothing` olarak değerlendirilirse ikinci bağımsız değişkenin değeri döndürülür. Diğer tüm durumlarda, ilk bağımsız değişkenin değeri döndürülür. Aşağıdaki örnek, bu değerlendirmenin nasıl çalıştığını gösterir.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
