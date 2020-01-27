---
title: Nullable değer türleri- C# başvuru
description: Null yapılabilir C# değer türleri ve bunların nasıl kullanılacağı hakkında bilgi edinin
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 42673d16ac68bbf119e57e4c357b1b2b2a0b5c51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740939"
---
# <a name="nullable-value-types-c-reference"></a>Nullable değer türleri (C# başvuru)

Null olabilen bir değer türü `T?` temel alınan [değer `T` türünün](value-types.md) tüm değerlerini ve ek bir [null](../keywords/null.md) değeri temsil eder. Örneğin, aşağıdaki üç değerden herhangi birini bir `bool?` değişkenine atayabilirsiniz: `true`, `false`veya `null`. Temel alınan değer türü `T`, null yapılabilir bir değer türü olamaz.

> [!NOTE]
> C#8,0, Nullable başvuru türleri özelliğini tanıtır. Daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md). Null yapılabilir değer türleri 2 ile C# başlayarak kullanılabilir.

Herhangi bir null yapılabilir değer türü, genel <xref:System.Nullable%601?displayProperty=nameWithType> yapısının bir örneğidir. Aşağıdaki değiştirilebilir formlardan herhangi birinde `T`, temel alınan bir tür ile null olabilen bir değer türüne başvurabilirsiniz: `Nullable<T>` veya `T?`.

Genellikle, temel alınan bir değer türünün tanımsız değerini temsil etmeniz gerektiğinde null yapılabilen bir değer türü kullanırsınız. Örneğin, bir Boolean veya `bool`, değişken yalnızca `true` ya da `false`olabilir. Ancak bazı uygulamalarda bir değişken değeri tanımsız veya eksik olabilir. Örneğin, bir veritabanı alanı `true` veya `false`içerebilir veya hiçbir değer içeremez, diğer bir deyişle, `NULL`. Bu senaryodaki `bool?` türünü kullanabilirsiniz.

## <a name="declaration-and-assignment"></a>Bildirim ve atama

Değer türü, karşılık gelen null yapılabilir değer türüne örtük olarak dönüştürülebilir olduğundan, onun temel alınan değer türü için yaptığınız gibi, null olabilen değer türünde bir değişkene bir değer atayabilirsiniz. `null` değerini de atayabilirsiniz. Örneğin:

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

Null olabilen bir değer türünün varsayılan değeri `null`temsil eder, diğer bir deyişle, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> özelliği `false`döndüren bir örneğidir.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Null yapılabilir bir değer türünün örneğinin incelenmesi

7,0 ile C# başlayarak, [`is` işlecini bir tür düzeniyle birlikte](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) kullanarak `null` için null yapılabilir değer türünün bir örneğini inceleyebilir ve temel alınan bir türün değerini alabilirsiniz:

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

Her zaman, null olabilen bir değer türü değişkeninin değerini incelemek ve almak için aşağıdaki salt okunurdur özelliklerini kullanabilirsiniz:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>, null yapılabilir bir değer türünün bir örneğinin temel alınan türü bir değere sahip olup olmadığını gösterir.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>, <xref:System.Nullable%601.HasValue%2A> `true`bir temel alınan türün değerini alır. <xref:System.Nullable%601.HasValue%2A> `false`, <xref:System.Nullable%601.Value%2A> özelliği bir <xref:System.InvalidOperationException>oluşturur.

Aşağıdaki örnek, değişkenin görüntülemeden önce bir değer içerip içermediğini test etmek için `HasValue` özelliğini kullanır:

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

Ayrıca, aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünün değişkenini `HasValue` özelliğini kullanmak yerine `null` ile karşılaştırabilirsiniz:

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Null yapılabilir bir değer türünden temel alınan bir türe dönüştürme

Null olabilen bir değer türünün değerini null yapılamayan bir değer türü değişkenine atamak istiyorsanız, `null`yerine atanacak değeri belirtmeniz gerekebilir. Bunu yapmak için [null birleşim işleci `??`](../operators/null-coalescing-operator.md) kullanın (aynı amaçla <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> yöntemini de kullanabilirsiniz):

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

`null`yerine temel alınan değer türünün [varsayılan](default-values.md) değerini kullanmak istiyorsanız <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemini kullanın.

Ayrıca, aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünü null yapılamayan bir türe açıkça çevirebilirsiniz:

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

Çalışma zamanında, null yapılabilir bir değer türünün değeri `null`, açık atama bir <xref:System.InvalidOperationException>oluşturur.

Null yapılamayan bir değer türü `T`, örtük olarak karşılık gelen null değer türü `T?`türüne dönüştürülebilir.

## <a name="lifted-operators"></a>Yükseltilmemiş işleçleri

Önceden tanımlanmış birli ve ikili işleçler veya `T` bir değer türü tarafından desteklenen aşırı yüklenmiş işleçler, karşılık gelen null yapılabilir değer türü `T?`tarafından da desteklenir. *Yükseltilmemiş işleçleri*olarak da bilinen bu işleçler, bir veya her iki işlenen de `null``null` üretir; Aksi takdirde, işleç sonucu hesaplamak için işlenenlerinin kapsanan değerlerini kullanır. Örneğin:

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> `bool?` türü için, önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işleçlerden biri `null`olsa bile bir operatör değerlendirmesinin sonucu null olmamalıdır. Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

`<`, `>`, `<=`ve `>=`[karşılaştırma işleçleri](../operators/comparison-operators.md) için, bir veya her iki işlenen de `null`, sonuç `false`olur; Aksi takdirde, kapsanan işlenen değerleri karşılaştırılır. Belirli bir karşılaştırma (örneğin, `<=`) `false`döndürdüğünden, zıt karşılaştırma (`>`) `true`döndürdüğünü varsaymayın. Aşağıdaki örnek, 10 ' un olduğunu gösterir

- `null` büyük veya eşit değil
- `null` ve küçüktür

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

Yukarıdaki örnek ayrıca, `null` her ikisi de `true`değerlendirilen iki null yapılabilir değer türü örneğinin eşitlik karşılaştırmasını gösterir.

İki değer türü arasında [Kullanıcı tanımlı bir dönüştürme](../operators/user-defined-conversion-operators.md) varsa, aynı dönüştürme karşılık gelen null atanabilir değer türleri arasında da kullanılabilir.

## <a name="boxing-and-unboxing"></a>Kutulama ve kutudan çıkarma

Null yapılabilir bir değer türü örneği, `T?` aşağıdaki gibi [kutulanır](../../programming-guide/types/boxing-and-unboxing.md) :

- <xref:System.Nullable%601.HasValue%2A> `false`döndürürse, null başvuru üretilir.
- <xref:System.Nullable%601.HasValue%2A> `true`döndürürse, temel alınan değer `T` türünün karşılık gelen değeri <xref:System.Nullable%601>örneği değil kutulanır.

Aşağıdaki örnekte gösterildiği gibi, bir değer türünün paketlenmiş değerini, karşılık gelen null değer türü `T?``T` bırakabilirsiniz:

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Null yapılabilir değer türünü belirleme

Aşağıdaki örnek, bir <xref:System.Type?displayProperty=nameWithType> örneğinin oluşturulmuş bir null yapılabilir değer türünü (yani, belirtilen tür parametresine sahip <xref:System.Nullable%601?displayProperty=nameWithType> türü) temsil edip etmediğini gösterir `T`:

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

Örnekte gösterildiği gibi, bir <xref:System.Type?displayProperty=nameWithType> örneği oluşturmak için [typeof](../operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız.

Bir örneğin, null yapılabilir bir değer türünde olup olmadığını anlamak istiyorsanız, yukarıdaki kodla test edilecek bir <xref:System.Type> örneğini almak için <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini kullanmayın. Null olabilen değer türünün bir örneğinde <xref:System.Object.GetType%2A?displayProperty=nameWithType> yöntemini çağırdığınızda, örnek <xref:System.Object>olarak [paketlenmelidir](#boxing-and-unboxing) . Null olabilen bir değer türünün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğerdir <xref:System.Object.GetType%2A>, null olabilen bir değer türünün temel türünü temsil eden bir <xref:System.Type> örneği döndürür:

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

Ayrıca, bir örneğin null yapılabilir değer türünde olup olmadığını anlamak için [,](../operators/type-testing-and-cast.md#is-operator) işleç kullanmayın. Aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türü örneği ve temel alınan tür örneğini `is` işleçle ayırt edemezsiniz:

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

Bir örneğin null yapılabilir bir değer türünde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Bu bölümde açıklanan yöntemler, [null yapılabilir başvuru türleri](../../nullable-references.md)durumunda geçerli değildir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Null yapılabilir türler](~/_csharplang/spec/types.md#nullable-types)
- [Yükseltilmemiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators)
- [Örtük null yapılabilir dönüşümler](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Açık boş değer atanabilir dönüşümler](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Yükseltilmemiş dönüştürme işleçleri](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [' Yükseltilmemiş ' tam olarak ne anlama geliyor?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Boş değer atanabilir başvuru türleri](../../nullable-references.md)
