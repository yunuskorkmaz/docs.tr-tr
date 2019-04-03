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
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834641"
---
# <a name="if-operator-visual-basic"></a>If İşleci (Visual Basic)
Kullanır, koşullu olarak iki değerden birini döndürmek için değerlendirmesi. `If` İşleci iki bağımsız değişkeni veya üç bağımsız değişken ile çağrılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>İşleç üç bağımsız değişken ile çağrılırsa  
 Zaman `If` çağrılır üç bağımsız değişken kullanarak, ilk bağımsız değişkeni olarak dönüştürülebilen bir değere hesaplanmalıdır bir `Boolean`. Olduğunu `Boolean` , diğer iki bağımsız değişken değerlendirilir ve döndürülen değer belirler. Aşağıdaki listede yalnızca geçerli `If` işleci, üç bağımsız değişkenler kullanarak çağrılır.  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`argument1`|Gerekli. `Boolean`. Değerlendirilip döndürülecek diğer bağımsız değişkenlerin belirler.|  
|`argument2`|Gerekli. `Object`. Değerlendirilen ve döndürülen if `argument1` değerlendiren `True`.|  
|`argument3`|Gerekli. `Object`. Değerlendirilen ve döndürülen if `argument1` değerlendiren `False` veya `argument1` olduğu bir [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değerlendiren değişkeni [hiçbir şey](../../../visual-basic/language-reference/nothing.md).|  
  
 Bir `If` üç bağımsız değişkenlerle çağrıldı işleci çalışır gibi bir `IIf` işlevi da kullanması hariç, değerlendirme kısa devre oluşturur. Bir `IIf` işlevi ise üç bağımsız değişkenlerinden biri her zaman değerlendirilir bir `If` üç bağımsız değişkenlere sahip bir işleç iki yalnızca değerlendirir. İlk `If` bağımsız değişken değerlendirilir ve sonuç olarak cast bir `Boolean` değeri `True` veya `False`. Değer ise `True`, `argument2` olan değerlendirilir ve değer döndürülür, ancak `argument3` değerlendirilmez. Varsa değerini `Boolean` ifade `False`, `argument3` olan değerlendirilir ve değer döndürülür, ancak `argument2` değerlendirilmez. Aşağıdaki örnekler, kullanımını gösterir `If` üç bağımsız değişken kullanıldığında:  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 Değerini aşağıdaki örnekte kısa devre değerlendirmesi. Örnek değişkeni ayırmak için iki deneme gösterir `number` değişkenin `divisor` olmadığı dışında `divisor` sıfırdır. Bu durumda 0 döndürdü ve çalışma zamanı hatası neden olacağından bölme işlemi gerçekleştirmek için hiç girişimde. Çünkü `If` ifade kullanır, değerlendirme kısa devre oluşturur, ikinci veya ilk bağımsız değişkenin değerine bağlı olarak, üçüncü bağımsız değişkeni değerlendirir. İlk bağımsız değişken true ise, bölen sıfır değil ve ikinci bağımsız değişkeni değerlendirir ve bölme işlemi gerçekleştirmek güvenlidir. İlk bağımsız değişken false ise, yalnızca üçüncü bağımsız değişken değerlendirilir ve 0 değeri döndürülür. Bölen 0 olduğunda, bu nedenle, hiçbir hata sonuçları ve bölme işlemi gerçekleştirmek için girişimde bulunulmaz. Ancak, çünkü `IIf` kullanmaz kısa devre değerlendirmesi, ilk bağımsız değişken false olduğunda bile ikinci bağımsız değişken değerlendirilir. Bu, bir çalışma zamanı sıfırla bölme hatasına neden olur.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>İşleci iki bağımsız değişkeni ile çağrılırsa  
 İlk bağımsız değişkeni `If` atlanabilir. Bu, yalnızca iki bağımsız değişkeni kullanılarak çağrılacak işleci sağlar. Aşağıdaki listede yalnızca geçerli `If` işleci iki bağımsız değişkenlerle çağrılır.  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`argument2`|Gerekli. `Object`. Bir başvuru veya boş değer atanabilir tür olmalıdır. Değerlendirilir ve dışında hiçbir şeye sonucunu verdiğinde döndürülen `Nothing`.|  
|`argument3`|Gerekli. `Object`. Değerlendirilen ve döndürülen if `argument2` değerlendiren `Nothing`.|  
  
 Zaman `Boolean` bağımsız değişken atlanırsa, ilk bağımsız değişken başvuru veya boş değer atanabilir tür olmalıdır. İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişkenin değeri döndürülür. Diğer durumlarda, ilk bağımsız değişkenin değeri döndürülür. Aşağıdaki örnekte, bu değerlendirme nasıl çalıştığı gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)
