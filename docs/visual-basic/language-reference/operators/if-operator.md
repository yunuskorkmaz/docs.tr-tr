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
ms.openlocfilehash: 28fb2afb2c4cf78ffbbb028145de647a8dc512ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371109"
---
# <a name="if-operator-visual-basic"></a>If İşleci (Visual Basic)

İki değerden birini koşullu olarak döndürmek için kısa devre değerlendirmesi kullanır. `If`İşleci üç bağımsız değişkenle veya iki bağımsız değişkenle çağrılabilir.

## <a name="syntax"></a>Sözdizimi

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Eğer işleci üç bağımsız değişkenle çağrılırsa

`If`Üç bağımsız değişken kullanılarak çağrıldığında, ilk bağımsız değişken, bir olarak yayınlanabileceğiniz bir değer olarak değerlendirilmelidir `Boolean` . Bu `Boolean` değer, diğer iki bağımsız değişkenin hangisinin değerlendirildiği ve döndürüldüğü belirlenir. Aşağıdaki liste yalnızca `If` işleç üç bağımsız değişken kullanılarak çağrıldığında geçerlidir.

### <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`argument1`|Gereklidir. `Boolean`. Değerlendirmek ve döndürmek için diğer bağımsız değişkenlerden hangisinin verileceğini belirler.|
|`argument2`|Gereklidir. `Object`. , Olarak değerlendirilirse, değerlendirilir ve döndürülür `argument1` `True` .|
|`argument3`|Gereklidir. `Object`. Değer olarak değerlendirilen ve değeri `argument1` `False` `argument1` Nothing olarak değerlendirilen [null yapılabilir](../../programming-guide/language-features/data-types/nullable-value-types.md) bir değişken ise, değerlendirilir `Boolean` [Nothing](../nothing.md)ve döndürülür.|

`If`Üç bağımsız değişkenle çağrılan bir operatör, `IIf` kısa devre değerlendirmesi kullanması dışında bir işlev gibi çalışır. Bir `IIf` işlev her zaman bağımsız değişkenlerini değerlendirir, ancak `If` üç bağımsız değişkeni olan bir operatör bunlardan yalnızca ikisini değerlendirir. İlk `If` bağımsız değişken değerlendirilir ve sonuç değer olarak atama yapılır `Boolean` `True` `False` . Değer ise `True` , `argument2` değerlendirilir ve değeri döndürülür, ancak `argument3` değerlendirilmez. `Boolean`İfadenin değeri ise `False` , `argument3` değerlendirilir ve değeri döndürülür, ancak `argument2` değerlendirilmez. Aşağıdaki örneklerde, `If` üç bağımsız değişkenin kullanıldığı zaman kullanımı gösterilmektedir:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Aşağıdaki örnek, kısa devre değerlendirmesinin değerini gösterir. Örnek, değişken sıfır dışında değişkeni değişkene bölmek için iki deneme gösterir `number` `divisor` `divisor` . Bu durumda, 0 döndürülmeli ve bir çalışma zamanı hatası sonucunda, Bölüm gerçekleştirmek için bir deneme yapılmamalıdır. `If`İfade kısa devre değerlendirmesi kullandığından, ilk bağımsız değişkenin değerine bağlı olarak ikinci ya da üçüncü bağımsız değişkeni değerlendirir. İlk bağımsız değişken true ise, bölen sıfır değildir ve ikinci bağımsız değişkeni değerlendirmek ve bölme gerçekleştirmek güvenlidir. İlk bağımsız değişken false ise, yalnızca üçüncü bağımsız değişken değerlendirilir ve 0 döndürülür. Bu nedenle, bölen 0 olduğunda, bölme gerçekleştirmek için bir deneme yapılmaz ve hata sonucu yoktur. Ancak, `IIf` kısa devre değerlendirmesi kullanmadığı için ikinci bağımsız değişken, ilk bağımsız değişken false olduğunda bile değerlendirilir. Bu, çalışma zamanı sıfıra bölme hatasına neden olur.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Eğer işleci iki bağımsız değişkenle çağrılırsa

İçin ilk bağımsız değişken `If` atlanabilir. Bu, işlecin yalnızca iki bağımsız değişken kullanılarak çağrılmasına olanak sağlar. Aşağıdaki liste yalnızca `If` işleç iki bağımsız değişkenle çağrıldığında geçerlidir.

### <a name="parts"></a>Bölümler

|Terim|Tanım|
|---|---|
|`argument2`|Gereklidir. `Object`. Başvuru veya null yapılabilir bir değer türü olmalıdır. ' Den başka bir şeyi değerlendirirken değerlendirilir ve döndürülür `Nothing` .|
|`argument3`|Gereklidir. `Object`. , Olarak değerlendirilirse, değerlendirilir ve döndürülür `argument2` `Nothing` .|

`Boolean`Bağımsız değişken atlanırsa, ilk bağımsız değişken bir başvuru veya null yapılabilir değer türü olmalıdır. İlk bağımsız değişken olarak değerlendirilirse `Nothing` ikinci bağımsız değişkenin değeri döndürülür. Diğer tüm durumlarda, ilk bağımsız değişkenin değeri döndürülür. Aşağıdaki örnek, bu değerlendirmenin nasıl çalıştığını göstermektedir:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Null yapılabilir değer türleri](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)
