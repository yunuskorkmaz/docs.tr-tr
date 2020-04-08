---
title: Nullable değer türleri - C# referans
description: C# nullable değer türleri ve bunları nasıl kullanacağı hakkında bilgi edinin
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: c13ef6a091ec6aebd4608c5ed8d2c03b067c7312
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888078"
---
# <a name="nullable-value-types-c-reference"></a>Nullable değer türleri (C# başvurusu)

*Nullable değer türü,* `T?` temel [değer türünün](value-types.md) `T` tüm değerlerini ve ek bir [null](../keywords/null.md) değerini temsil eder. Örneğin, aşağıdaki üç değerden herhangi birini bir `bool?` değişkene atayabilirsiniz: `true`, `false`veya `null`. Temel değer `T` türü, nullable değer türü kendisi olamaz.

> [!NOTE]
> C# 8.0 nullable başvuru türleri özelliğini tanıtür. Daha fazla bilgi için [Nullable başvuru türlerine](nullable-reference-types.md)bakın. Nullable değer türleri C # 2 ile başlayan kullanılabilir.

Herhangi bir nullable değer türü <xref:System.Nullable%601?displayProperty=nameWithType> genel yapının bir örneğidir. Aşağıdaki değiştirilebilir formlardan herhangi birinde altta `T` yatan bir türe sahip nullable değer türüne başvurabilirsiniz: `Nullable<T>` veya `T?`.

Temel değer türünün tanımlanmamış değerini temsil etmeniz gerektiğinde genellikle nullable değer türü kullanırsınız. Örneğin, bir Boolean `bool`veya , değişken `true` sadece `false`ya da olabilir . Ancak, bazı uygulamalarda değişken değer tanımsız veya eksik olabilir. Örneğin, bir veritabanı alanı `true` `false`içerebilir veya , ya da hiç değer `NULL`içerebilir, yani. Bu senaryoda `bool?` türü kullanabilirsiniz.

## <a name="declaration-and-assignment"></a>Beyan ve atama

Değer türü dolaylı olarak karşılık gelen nullable değer türüne dönüştürülebilir olduğundan, bir değeri temel değer türü için yaptığınız gibi, nullable değer türündeki bir değişkene atayabilirsiniz. `null` Değeri de atayabilirsiniz. Örneğin:

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

Nullable değer türünün varsayılan `null`değeri temsil eder , yani, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> bu `false`özelliği döndürür bir örnektir.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Nullable değer türübir örneğin incelenmesi

C# 7.0 ile başlayarak, hem için nullable değer türü bir örnek incelemek `null` ve altta yatan bir tür bir değer almak için [ `is` bir tür desen ile işleci](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) kullanabilirsiniz:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Nullable değer türü değişkeninin değerini incelemek ve almak için her zaman aşağıdaki salt okunur özelliklerini kullanabilirsiniz:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>nullable değer türü bir örnek altta yatan türü bir değere sahip olup olmadığını gösterir.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>ise, <xref:System.Nullable%601.HasValue%2A> `true`temel bir türün değerini alır. Ise, <xref:System.Nullable%601.HasValue%2A> <xref:System.Nullable%601.Value%2A> özellik atar . <xref:System.InvalidOperationException> `false`

Aşağıdaki örnek, `HasValue` değişkenin görüntülemeden önce bir değer bulunup bulunmayacağını sınamak için özelliği kullanır:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Aşağıdaki örnekte görüldüğü gibi, `null` `HasValue` özelliği kullanmak yerine nullable değer türüdeğişkenini de karşılaştırabilirsiniz:

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Geçersiz bir değer türünden temel bir türe dönüştürme

Nullable değer türü bir değer türünü nullable olmayan bir değer türü değişkenine atamak istiyorsanız, `null`''nin yerine atanacak değeri belirtmeniz gerekebilir Bunu yapmak için [null-coalescing işleci `??` ](../operators/null-coalescing-operator.md) kullanın <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> (aynı amaç için de yöntemi kullanabilirsiniz):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Yerine temel değer türünün [varsayılan](default-values.md) değerini kullanmak `null`istiyorsanız, <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemi kullanın.

Ayrıca, aşağıdaki örnekte görüldüğü gibi, nullable değer türünü nullable olmayan bir türe açıkça atabilirsiniz:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

Çalışma zamanında, nullable değer türünün değeri `null`ise, açık döküm <xref:System.InvalidOperationException>bir .

Nullable değer türü `T` dolaylı olarak karşılık gelen nullable değer `T?`türüne dönüştürülebilir.

## <a name="lifted-operators"></a>Kaldırılan operatörler

Önceden tanımlanmış unary ve ikili [işleçler](../operators/index.md) veya bir değer `T` türü tarafından desteklenen herhangi bir aşırı `T?`yüklü işleçleri de ilgili nullable değer türü tarafından desteklenir. Bu operatörler, aynı zamanda *kaldırılan operatörler*olarak bilinen, `null`bir veya her iki operands ise üretmek; `null` aksi takdirde, işleç sonucu hesaplamak için operands içerdiği değerleri kullanır. Örneğin:

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> `bool?` Türü için, önceden `&` tanımlanmış `|` ve işleçler bu bölümde açıklanan kurallara uymaz: operands biri olsa bile bir `null`operatör değerlendirme sonucu geçersiz olabilir. Daha fazla bilgi için [Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçleri](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

Karşılaştırma [işleçleri](../operators/comparison-operators.md) `<` `<=`için `>=`, `>`, , ve , `null`eğer bir `false`veya her iki operands , sonuç; aksi takdirde, operands içerdiği değerleri karşılaştırılır. Belirli bir karşılaştırma `<=`(örneğin, ) döndürür `false`çünkü,`>`ters `true`karşılaştırma ( ) döndürür varsaymayın . Aşağıdaki örnek, 10'un

- ne büyük ya da eşit`null`
- ne de daha az`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Eşitlik [işleci](../operators/equality-operators.md#equality-operator-) `==`için, her iki operands `null` `true`ise , sonuç , eğer sadece `null`bir operands , sonuç; `false` aksi takdirde, operands içerdiği değerleri karşılaştırılır.

Eşitsizlik [işleci](../operators/equality-operators.md#inequality-operator-) `!=`için , her iki `null`operands `false`ise , sonuç , eğer sadece `null`bir operands , sonuç; `true` aksi takdirde, operands içerdiği değerleri karşılaştırılır.

İki değer türü arasında [kullanıcı tanımlı](../operators/user-defined-conversion-operators.md) bir dönüştürme varsa, aynı dönüştürme karşılık gelen nullable değer türleri arasında da kullanılabilir.

## <a name="boxing-and-unboxing"></a>Boks ve unboxing

Nullable değer türü `T?` örneği aşağıdaki gibi [kutulanır:](../../programming-guide/types/boxing-and-unboxing.md)

- İade <xref:System.Nullable%601.HasValue%2A> `false`edilirse, null başvuru üretilir.
- İade <xref:System.Nullable%601.HasValue%2A> `true`edilirse, alttaki değer türünün `T` karşılık gelen değeri <xref:System.Nullable%601>kutulanır, '' örneğini değil.

Aşağıdaki örnekte görüldüğü gibi, ilgili `T` nullable değer türüne `T?`bir değer türünün kutulanmış değerini açabilirsiniz:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Nullable değer türünü tanımlama

Aşağıdaki örnek, bir <xref:System.Type?displayProperty=nameWithType> örneğin oluşturulmuş bir nullable değer türünü, yani <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen tür parametresi `T`olan türü temsil edip etmediğini nasıl belirleyeceklerini gösterir:

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Örnekte görüldüğü gibi, [typeof](../operators/type-testing-and-cast.md#typeof-operator) bir <xref:System.Type?displayProperty=nameWithType> örnek oluşturmak için işleç türünü kullanırsınız.

Bir örneğin boş değer türüne sahip olup olmadığını belirlemek istiyorsanız, <xref:System.Object.GetType%2A?displayProperty=nameWithType> bir <xref:System.Type> örneğin önceki kodla sınanmasını sağlamak için yöntemi kullanmayın. Metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> nullable değer türü örneğinde çağırdığınızda, [boxed](#boxing-and-unboxing) örnek <xref:System.Object>. Nullable değer türünün null olmayan bir örneğinin kutulaması, temel türün <xref:System.Object.GetType%2A> bir <xref:System.Type> değerinin kutulatılabilir bir değeri ne eşdeğer olduğundan, temel değer türünü temsil eden bir örneği döndürür:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

Ayrıca, bir örneğin nullable değer türüolup olmadığını belirlemek için [is](../operators/type-testing-and-cast.md#is-operator) işleci kullanmayın. Aşağıdaki örnekte de görüldüğü gibi, nullable değer türü örneğinin türlerini `is` ve onun temel türü örneğini işleçle ayırt edemezsiniz:

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Bir örneğin nullable değer türüne ait olup olmadığını belirlemek için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Bu bölümde açıklanan yöntemler [geçersiz başvuru türleri](nullable-reference-types.md)durumunda geçerli değildir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Nullable türleri](~/_csharplang/spec/types.md#nullable-types)
- [Kaldırılan operatörler](~/_csharplang/spec/expressions.md#lifted-operators)
- [Örtülü nullable dönüşümler](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Açık geçersiz dönüşümler](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Kaldırılan dönüşüm operatörleri](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- ['Kaldırdı' tam olarak ne anlama geliyor?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Boş değer atanabilir başvuru türleri](nullable-reference-types.md)
