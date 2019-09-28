---
title: Nullable değer türleri- C# Programlama Kılavuzu
ms.custom: seodec18
description: Null yapılabilir C# değer türleri ve bunların nasıl kullanılacağı hakkında bilgi edinin
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396225"
---
# <a name="nullable-value-types-c-programming-guide"></a>Nullable değer türleri (C# Programlama Kılavuzu)

Null yapılabilir değer türleri <xref:System.Nullable%601?displayProperty=nameWithType> yapısının örnekleridir. Null yapılabilir değer türleri, `T` temel türünün tüm değerlerini ve ek [null](../../language-reference/keywords/null.md) değeri temsil edebilir. @No__t-0 temel türü, null olamayan bir [değer türü](../../language-reference/keywords/value-types.md)olabilir. `T` bir başvuru türü olamaz.

> [!NOTE]
> C#8,0, Nullable başvuru türleri özelliğini tanıtır. Daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md). Null yapılabilir değer türleri 2 ' den C# başlayarak kullanılabilir.

Örneğin, `null` ya da <xref:System.Int32.MinValue?displayProperty=nameWithType> ' den <xref:System.Int32.MaxValue?displayProperty=nameWithType> ' ye `Nullable<int>` ve [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md)veya `null` ' a `Nullable<bool>` ' ye kadar herhangi bir tamsayı değeri atayabilirsiniz.

Temel alınan bir türün tanımsız değerini temsil etmeniz gerektiğinde null yapılabilir bir değer türü kullanın. Boole değişkeni yalnızca iki değere sahip olabilir: `true` ve `false`. "Tanımsız" değeri yok. Birçok programlama uygulamasında, çoğu bilinen veritabanı etkileşimi, bir değişken değeri tanımsız veya eksik olabilir. Örneğin, veritabanındaki bir alan doğru veya yanlış değerlerini içerebilir veya hiçbir değer içermez. Bu durumda `Nullable<bool>` türü kullanırsınız.

Null yapılabilir değer türleri aşağıdaki özelliklere sahiptir:

- Null yapılabilir değer türleri, `null` değeri atanabilen değer türü değişkenleri temsil eder.

- @No__t-0 `Nullable<T>` için toplu sözdizimidir. İki form birbirinin yerine kullanılır.

- Bir değer atanabilir değer türüne, temel alınan bir değer türü için yaptığınız gibi bir değer atayın: `int? x = 10;` veya `double? d = 4.108;`. @No__t-0 değerini de atayabilirsiniz: `int? x = null;`.

- Null için test etmek ve değeri almak için aşağıdaki örnekte gösterildiği gibi, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> ve <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> ReadOnly özelliklerini kullanın: `if (x.HasValue) y = x.Value;`

  - @No__t-0 özelliği, değişken bir değer içeriyorsa-1 ' i veya @no__t 3 ' se `false` ' ye @no__t döndürür.

  - @No__t-0 özelliği, <xref:System.Nullable%601.HasValue%2A> `true` döndürürse bir değer döndürür. Aksi takdirde, bir <xref:System.InvalidOperationException> oluşturulur.

- Aşağıdaki örnekte gösterildiği gibi, `==` ve `!=` işleçlerini null olabilen bir değer türü ile de kullanabilirsiniz: `if (x != null) y = x.Value;`. @No__t-0 ve `b` her ikisi de null ise, `a == b` `true` olarak değerlendirilir.

- 7,0 ' C# den başlayarak, null yapılabilir bir türdeki değeri incelemek ve almak için [model eşleştirmeyi](../../pattern-matching.md#the-is-type-pattern-expression) kullanabilirsiniz: `if (x is int valueOfX) y = valueOfX;`.

- @No__t-0 ' ın varsayılan değeri, <xref:System.Nullable%601.HasValue%2A> özelliği `false` ' i döndüren bir örneğidir.

- Atanan değeri döndürmek için <xref:System.Nullable%601.GetValueOrDefault> yöntemini veya null yapılabilir tür değeri `null` ise temel alınan değer türünün [varsayılan](../../language-reference/keywords/default-values-table.md) değerini kullanın.

- Atanan değeri döndürmek için <xref:System.Nullable%601.GetValueOrDefault(%600)> yöntemini veya null yapılabilir türdeki değer `null` ise belirtilen varsayılan değeri kullanın.

- Null olabilen bir tür değerine göre temel alınan değer türünün değişkenine bir değer atamak için, `??` [null birleşim işlecini](../../language-reference/operators/null-coalescing-operator.md)kullanın: `int? x = null; int y = x ?? -1;`. Örnekte, `x` `null` olduğundan `y` ' nin sonuç değeri `-1` ' dir.

- İki değer türü arasında Kullanıcı tanımlı bir dönüştürme tanımlanmışsa, aynı dönüştürme karşılık gelen null yapılabilir türler ile de kullanılabilir.

- İç içe null yapılabilir değer türlerine izin verilmez. Şu satır derlenmiyor: `Nullable<Nullable<int>> n;`

Daha fazla bilgi için bkz. [null yapılabilir değer türleri kullanma](using-nullable-types.md) ve [nasıl yapılır: null yapılabilir değer türü belirleme](how-to-identify-a-nullable-type.md) konuları.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [?? İşleç](../../language-reference/operators/null-coalescing-operator.md)
- [Nullable değer türleri (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
