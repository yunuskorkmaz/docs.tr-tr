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
ms.openlocfilehash: 192309a7ca728feb300e867bf2340e669e9da16c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603970"
---
# <a name="if-operator-visual-basic"></a>If İşleci (Visual Basic)
Kullanır, koşullu iki değerden birini veren değerlendirmesi. `If` İşleci üç bağımsız değişken veya iki bağımsız değişkenlerle çağrılamaz.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>İşleç üç bağımsız değişkenlerle çağrıldıklarında  
 Zaman `If` çağrılır üç bağımsız değişken kullanarak, ilk bağımsız değişken olarak cast bir değer olarak değerlendirilmelidir bir `Boolean`. Olduğunu `Boolean` , diğer iki bağımsız değişken değerlendirilir ve döndürülen değeri belirler. Aşağıdaki listede yalnızca geçerli `If` işleci üç bağımsız değişken kullanarak çağrılır.  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`argument1`|Gerekli. `Boolean`. Hangi değerlendirmek ve dönmek için başka bir bağımsız değişken belirler.|  
|`argument2`|Gerekli. `Object`. Değerlendirilen ve döndürülen IF `argument1` değerlendiren `True`.|  
|`argument3`|Gerekli. `Object`. Değerlendirilen ve döndürülen IF `argument1` değerlendiren `False` veya `argument1` olan bir [null atanabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değerlendiren değişkeni [hiçbir şey](../../../visual-basic/language-reference/nothing.md).|  
  
 Bir `If` ile üç bağımsız değişken olarak adlandırılan işleci çalışır gibi bir `IIf` işlevini kullanır ancak bu değerlendirme kısa devre oluşturur. Bir `IIf` işlevi ancak üçünü bağımsız değişkenlerini her zaman değerlendiren bir `If` üç bağımsız değişkenlere sahiptir işleci iki yalnızca değerlendirir. İlk `If` bağımsız değişkeni değerlendirildiği ve sonuç olarak cast bir `Boolean` değeri `True` veya `False`. Değer ise `True`, `argument2` olan değerlendirilir ve değer döndürülür, ancak `argument3` değerlendirilmez. Varsa değerini `Boolean` ifade `False`, `argument3` olan değerlendirilir ve değer döndürülür, ancak `argument2` değerlendirilmez. Aşağıdaki örnekler kullanımını göstermek `If` üç bağımsız kullanıldığında:  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 Aşağıdaki örnek değeri gösterilmektedir değerlendirmesi. Örnek değişkeni bölmek için iki denemesi gösterir `number` değişkeni tarafından `divisor` olmadığı dışında `divisor` sıfırdır. Bu durumda, 0 döndürülmelidir ve bir çalışma zamanı hatası neden olacağından bölme gerçekleştirmek için bir girişimde. Çünkü `If` ifade kullanır, değerlendirme kısa devre oluşturur, ikinci veya ilk bağımsız değişkenin değeri bağlı olarak üçüncü bağımsız değişken olarak değerlendirilir. İlk bağımsız değişken true ise, bölen sıfır değil ve ikinci bağımsız değişkeni değerlendirmek ve bölme gerçekleştirmek güvenlidir. İlk bağımsız değişken false ise, yalnızca üçüncü bağımsız değişken değerlendirilir ve 0 değeri döndürülür. Bölen 0 olduğunda, bu nedenle, bölme ve hiçbir hata sonuçları gerçekleştirmek için girişimde bulunulmaz. Ancak, çünkü `IIf` kullanmayan değerlendirmesi, ikinci bağımsız değişkeni, ilk bağımsız değişkeni false olduğunda bile değerlendirilir. Bu, bir çalışma zamanı sıfırla bölme hatasına neden olur.  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>İşleç iki bağımsız değişkenlerle çağrıldıklarında  
 İlk bağımsız değişken `If` atlanabilir. Bu, yalnızca iki bağımsız değişken kullanarak çağrılacak işleci sağlar. Aşağıdaki listede yalnızca geçerli `If` işleci iki bağımsız değişkenlerle çağrılır.  
  
## <a name="parts"></a>Bölümler  
  
|Terim|Tanım|  
|---|---|  
|`argument2`|Gerekli. `Object`. Bir başvuru ya da null olabilir bir tür olmalıdır. Değerlendirilir ve başka hiçbir şeye değerlendirirken, döndürülen `Nothing`.|  
|`argument3`|Gerekli. `Object`. Değerlendirilen ve döndürülen IF `argument2` değerlendiren `Nothing`.|  
  
 Zaman `Boolean` bağımsız değişken atlanırsa, ilk bağımsız değişkeni bir başvuru veya boş değer atanabilir tür olması gerekir. İlk bağımsız değişken değerlendirilirse `Nothing`, ikinci bağımsız değişken değeri döndürülür. Diğer durumlarda, ilk bağımsız değişkenin değeri döndürülür. Aşağıdaki örnek, bu değerlendirmeyi nasıl çalıştığı gösterilmektedir.  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [Boş Değer Atanabilen Değer Türleri](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)
