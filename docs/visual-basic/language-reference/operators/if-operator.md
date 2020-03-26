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
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249493"
---
# <a name="if-operator-visual-basic"></a>If İşleci (Visual Basic)

İki değerden birini koşullu olarak döndürmek için kısa devre değerlendirmesini kullanır. İşleç `If` üç bağımsız değişkenle veya iki bağımsız değişkenle çağrılabilir.

## <a name="syntax"></a>Sözdizimi

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Operatör üç bağımsız değişkenle aradıysa

Üç `If` bağımsız değişken kullanılarak çağrıldığında, ilk bağımsız değişkenin bir `Boolean`. Bu `Boolean` değer, diğer iki bağımsız değişkenden hangisinin değerlendirilip döndürüleceğini belirler. Aşağıdaki liste yalnızca `If` işleç üç bağımsız değişken kullanılarak çağrıldığında geçerlidir.

### <a name="parts"></a>Bölümler

|Sözleşme Dönemi|Tanım|
|---|---|
|`argument1`|Gereklidir. `Boolean`. Diğer bağımsız değişkenlerden hangisini değerlendirip döndüreceklerini belirler.|
|`argument2`|Gereklidir. `Object`. Değerlendirilir ve değerlendirilirse `argument1` `True`döndürülür.|
|`argument3`|Gereklidir. `Object`. Değerlendirme deolsa `argument1` `False` veya Hiçbir [şey](../../../visual-basic/language-reference/nothing.md)için değerlendiren [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` değişken ise `argument1` değerlendirilir ve döndürülür.|

Üç `If` bağımsız değişkenle çağrılan bir `IIf` işleç, kısa devre değerlendirmesi kullanması dışında bir işlev gibi çalışır. Bir `IIf` işlev her zaman üç bağımsız değişkenini değerlendirirken, üç bağımsız değişkeni olan bir `If` işleç yalnızca ikisini değerlendirir. İlk `If` bağımsız değişken değerlendirilir ve sonuç bir `Boolean` değer `True` `False`olarak atılır veya . Değer `True`ise, `argument2` değerlendirilir ve değeri döndürülür, `argument3` ancak değerlendirilmez. `Boolean` İfadenin değeri ise `False`değerlendirilir `argument3` ve değeri döndürülür, ancak `argument2` değerlendirilmez. Aşağıdaki örnekler, üç `If` bağımsız değişkenin ne zaman kullanıldığını göstermektedir:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Aşağıdaki örnek, kısa devre değerlendirmenin değerini göstermektedir. Örnek, sıfır olduğu zaman `number` `divisor` dışında `divisor` değişkeni değişkene bölmeye yönelik iki girişimi gösterir. Bu durumda, bir 0 döndürülmelidir ve çalışma zamanı hatası neden olacağından bölümü gerçekleştirmek için hiçbir girişimde bulunulmamalıdır. İfade `If` kısa devre değerlendirme kullandığından, ilk bağımsız değişkenin değerine bağlı olarak ikinci veya üçüncü bağımsız değişkeni değerlendirir. İlk bağımsız değişken doğruysa, bölen sıfır değildir ve ikinci bağımsız değişkeni değerlendirmek ve bölmeyi gerçekleştirmek güvenlidir. İlk bağımsız değişken yanlışsa, yalnızca üçüncü bağımsız değişken değerlendirilir ve 0 döndürülür. Bu nedenle, bölen 0 olduğunda, bölme gerçekleştirmek için hiçbir girişimde bulunulur ve hata sonuçları yoktur. Ancak, `IIf` kısa devre değerlendirme kullanmadığı için, ikinci bağımsız değişken ilk bağımsız değişken yanlış olsa bile değerlendirilir. Bu, çalışma zamanı sıfıra bölme hatasına neden olur.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>İşleç iki bağımsız değişkenle çağrılsa

İlk bağımsız `If` değişken atlanabilir. Bu, işlecinin yalnızca iki bağımsız değişken kullanarak çağrılmasını sağlar. Aşağıdaki liste yalnızca `If` işleç iki bağımsız değişkenle çağrıldığında geçerlidir.

### <a name="parts"></a>Bölümler

|Sözleşme Dönemi|Tanım|
|---|---|
|`argument2`|Gereklidir. `Object`. Bir başvuru veya nullable değer türü olmalıdır. Başka bir şey için değerlendirilir ve `Nothing`döndürülür.|
|`argument3`|Gereklidir. `Object`. Değerlendirilir ve değerlendirilirse `argument2` `Nothing`döndürülür.|

`Boolean` Bağımsız değişken atlandığında, ilk bağımsız değişken bir başvuru veya nullable değer türü olmalıdır. İlk bağımsız değişken , `Nothing`ikinci bağımsız değişkenin değeri döndürülür dise. Diğer tüm durumlarda, ilk bağımsız değişkenin değeri döndürülür. Aşağıdaki örnek, bu değerlendirmenin nasıl çalıştığını göstermektedir:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Boş Değer Atanabilen Değer Türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Hiçbir şey](../nothing.md)
