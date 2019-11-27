---
title: If İşleci
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
ms.openlocfilehash: 6d25519dac31dc91f8560fd3252ba3e2622de370
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331011"
---
# <a name="if-operator-visual-basic"></a>If İşleci (Visual Basic)

İki değerden birini koşullu olarak döndürmek için kısa devre değerlendirmesi kullanır. `If` işleci, üç bağımsız değişkenle veya iki bağımsız değişkenle çağrılabilir.

## <a name="syntax"></a>Sözdizimi

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Eğer işleci üç bağımsız değişkenle çağrılırsa

`If` üç bağımsız değişken kullanılarak çağrıldığında, ilk bağımsız değişken, `Boolean`olarak yayınlanabileceğiniz bir değer olarak değerlendirilmelidir. Bu `Boolean` değeri, diğer iki bağımsız değişkenin hangisinin değerlendirileceğini ve döndürüldüğünü belirlemektir. Aşağıdaki liste yalnızca `If` işleci üç bağımsız değişken kullanılarak çağrıldığında geçerlidir.

### <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`argument1`|Gerekli. `Boolean`. Değerlendirmek ve döndürmek için diğer bağımsız değişkenlerden hangisinin verileceğini belirler.|
|`argument2`|Gerekli. `Object`. `argument1` `True`değerlendirilirse, değerlendirilir ve döndürülür.|
|`argument3`|Gerekli. `Object`. `argument1` `False` değerlendirilirse veya `argument1` [hiçbir şey](../../../visual-basic/language-reference/nothing.md)olarak değerlendirilen [null yapılabilir](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)`Boolean` bir değişken ise, değerlendirilir ve döndürülür.|

Üç bağımsız değişkenle çağrılan `If` işleci, kısa devre değerlendirmesi kullanması dışında `IIf` işlevi gibi çalışır. `IIf` işlev her zaman bağımsız değişkenlerini değerlendirir, ancak üç bağımsız değişkenine sahip bir `If` işleci yalnızca iki tane değerlendirir. İlk `If` bağımsız değişkeni değerlendirilir ve sonuç bir `Boolean` değeri, `True` veya `False`olarak ayarlanır. Değer `True`, `argument2` değerlendirilir ve değeri döndürülür, ancak `argument3` değerlendirilmez. `Boolean` ifadesinin değeri `False`, `argument3` değerlendirilir ve değeri döndürülür, ancak `argument2` değerlendirilmez. Aşağıdaki örneklerde, üç bağımsız değişken kullanıldığında `If` kullanımı gösterilmektedir:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Aşağıdaki örnek, kısa devre değerlendirmesinin değerini gösterir. Örnek, `divisor` sıfır olduğu durumlar dışında değişken `divisor` değişken `number` bölmek için iki deneme gösterir. Bu durumda, 0 döndürülmeli ve bir çalışma zamanı hatası sonucunda, Bölüm gerçekleştirmek için bir deneme yapılmamalıdır. `If` ifade kısa devre değerlendirmesi kullandığından, ilk bağımsız değişkenin değerine bağlı olarak ikinci ya da üçüncü bağımsız değişkeni değerlendirir. İlk bağımsız değişken true ise, bölen sıfır değildir ve ikinci bağımsız değişkeni değerlendirmek ve bölme gerçekleştirmek güvenlidir. İlk bağımsız değişken false ise, yalnızca üçüncü bağımsız değişken değerlendirilir ve 0 döndürülür. Bu nedenle, bölen 0 olduğunda, bölme gerçekleştirmek için bir deneme yapılmaz ve hata sonucu yoktur. Ancak, `IIf` kısa devre değerlendirmesi kullanmıyorsa, ilk bağımsız değişken false olduğunda bile ikinci bağımsız değişken değerlendirilir. Bu, çalışma zamanı sıfıra bölme hatasına neden olur.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Eğer işleci iki bağımsız değişkenle çağrılırsa

`If` ilk bağımsız değişkeni atlanabilir. Bu, işlecin yalnızca iki bağımsız değişken kullanılarak çağrılmasına olanak sağlar. Aşağıdaki liste yalnızca `If` işleci iki bağımsız değişkenle çağrıldığında geçerlidir.

### <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`argument2`|Gerekli. `Object`. Başvuru veya null yapılabilir bir tür olmalıdır. `Nothing`dışında bir şeyi değerlendirirken değerlendirilir ve döndürülür.|
|`argument3`|Gerekli. `Object`. `argument2` `Nothing`değerlendirilirse, değerlendirilir ve döndürülür.|

`Boolean` bağımsız değişkeni atlandığında, ilk bağımsız değişken bir başvuru veya null yapılabilir bir tür olmalıdır. İlk bağımsız değişken `Nothing`değerlendirilirse, ikinci bağımsız değişkenin değeri döndürülür. Diğer tüm durumlarda, ilk bağımsız değişkenin değeri döndürülür. Aşağıdaki örnek, bu değerlendirmenin nasıl çalıştığını göstermektedir:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Boş Değer Atanabilen Değer Türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
