---
title: Nullable değer türleri-C# başvurusu
description: C# Nullable değer türleri ve bunların nasıl kullanılacağı hakkında bilgi edinin
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 8c3a8b997fbb8154f79dff04018cf3ea76f85d7a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537359"
---
# <a name="nullable-value-types-c-reference"></a>Nullable değer türleri (C# Başvurusu)

*Null yapılabilir bir değer türü* , `T?` temel alınan [değer türünün](value-types.md) tüm değerlerini `T` ve ek bir [null](../keywords/null.md) değeri temsil eder. Örneğin, aşağıdaki üç değerden herhangi birini bir `bool?` değişkene atayabilirsiniz: `true` , `false` veya `null` . Temel alınan değer türü `T` null yapılabilir bir değer türü olamaz.

> [!NOTE]
> C# 8,0, Nullable başvuru türleri özelliğini tanıtır. Daha fazla bilgi için bkz. [Nullable başvuru türleri](nullable-reference-types.md). Nullable değer türleri C# 2 ' den başlayarak kullanılabilir.

Herhangi bir null yapılabilir değer türü, genel yapının bir örneğidir <xref:System.Nullable%601?displayProperty=nameWithType> . Aşağıdaki her türlü değiştirilebilir formdan bir temel alınan tür ile null yapılabilir bir değer türüne başvurabilirsiniz `T` : `Nullable<T>` veya `T?` .

Genellikle, temel alınan bir değer türünün tanımsız değerini temsil etmeniz gerektiğinde null yapılabilen bir değer türü kullanırsınız. Örneğin, bir Boolean veya `bool` değişken yalnızca ya da olabilir `true` `false` . Ancak bazı uygulamalarda bir değişken değeri tanımsız veya eksik olabilir. Örneğin, bir veritabanı alanı `true` veya içerebilir `false` veya hiçbir değer içeremez, yani, `NULL` . `bool?`Bu senaryodaki türü kullanabilirsiniz.

## <a name="declaration-and-assignment"></a>Bildirim ve atama

Değer türü, karşılık gelen null yapılabilir değer türüne örtük olarak dönüştürülebilir olduğundan, onun temel alınan değer türü için yaptığınız gibi, null olabilen değer türünde bir değişkene bir değer atayabilirsiniz. Ayrıca değeri de atayabilirsiniz `null` . Örnek:

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

Null olabilen bir değer türünün varsayılan değeri temsil eder `null` , diğer bir deyişle, <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> özelliği işlevinin döndürdüğü bir örneğidir `false` .

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Null yapılabilir bir değer türünün örneğinin incelenmesi

C# 7,0 ' den başlayarak [ `is` işleci bir tür düzeniyle birlikte](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) kullanarak, için null olabilen değer türünün bir örneğini inceleyebilir `null` ve temel alınan bir türün değerini alabilirsiniz:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Her zaman, null olabilen bir değer türü değişkeninin değerini incelemek ve almak için aşağıdaki salt okunurdur özelliklerini kullanabilirsiniz:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> null yapılabilir bir değer türünün bir örneğinin temel alınan türünün bir değeri olup olmadığını gösterir.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> ise, temel alınan bir türün değerini alır <xref:System.Nullable%601.HasValue%2A> `true` . <xref:System.Nullable%601.HasValue%2A>İse `false` , <xref:System.Nullable%601.Value%2A> özelliği bir oluşturur <xref:System.InvalidOperationException> .

Aşağıdaki örnek, `HasValue` değişkenin görüntülemeden önce bir değer içerip içermediğini test etmek için özelliğini kullanır:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Ayrıca `null` `HasValue` , aşağıdaki örnekte gösterildiği gibi, null atanabilir bir değer türünün değişkenini özelliğini kullanmak yerine ile karşılaştırabilirsiniz.

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Null yapılabilir bir değer türünden temel alınan bir türe dönüştürme

Null olabilen bir değer türünün değerini null yapılamayan bir değer türü değişkenine atamak istiyorsanız, yerine atanacak değeri belirtmeniz gerekebilir `null` . Bunu yapmak için [null birleşim işlecini `??` ](../operators/null-coalescing-operator.md) kullanın ( <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> aynı amaçla yöntemini de kullanabilirsiniz):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Yerine temel alınan değer türünün [varsayılan](default-values.md) değerini kullanmak istiyorsanız `null` <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemini kullanın.

Ayrıca, aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türünü null yapılamayan bir türe açıkça çevirebilirsiniz:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

Çalışma zamanında, null yapılabilir bir değer türünün değeri ise `null` , açık atama bir oluşturur <xref:System.InvalidOperationException> .

Null yapılamayan bir değer türü, `T` karşılık gelen null yapılabilir değer türüne örtük olarak dönüştürülebilir `T?` .

## <a name="lifted-operators"></a>Yükseltilmemiş işleçleri

Önceden tanımlanmış birli ve ikili [işleçler](../operators/index.md) ya da bir değer türü tarafından desteklenen aşırı yüklenmiş işleçler, `T` karşılık gelen Nullable değer türü tarafından da desteklenir `T?` . *Yükseltilmemiş işleçleri*olarak da bilinen bu işleçler, `null` bir veya her iki işlenen ise üretir `null` ; Aksi takdirde işleç, sonucu hesaplamak için işlenenlerinin kapsanan değerlerini kullanır. Örnek:

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Türü için `bool?` , önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işleçlerden biri olsa bile bir operatör değerlendirmesinin sonucu null olmamalıdır `null` . Daha fazla bilgi için, [Boole mantıksal işleçler](../operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.

[Karşılaştırma işleçleri](../operators/comparison-operators.md) ,, `<` `>` `<=` ve `>=` bir veya her iki işlenen ise `null` sonuç olur `false` ; Aksi takdirde, kapsanan işlenen değerleri karşılaştırılır. Belirli bir karşılaştırma (örneğin, `<=` ) döndürdüğünden `false` , zıt karşılaştırma ( `>` ) işlevinin döndürdüğü varsayılmayın `true` . Aşağıdaki örnek, 10 ' un olduğunu gösterir

- Ne büyük ne de eşittir `null`
- ya da küçüktür `null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

[Eşitlik işleci](../operators/equality-operators.md#equality-operator-) için, her iki işlenen de, sonuç ise, sonuç olur `==` `null` `true` `null` `false` ; Aksi takdirde, kapsanan işlenen değerleri karşılaştırılır.

[Eşitsizlik işleci](../operators/equality-operators.md#inequality-operator-) için, `!=` her iki işlenen de ise `null` sonuç olur `false` `null` ; Aksi takdirde, işlenen, `true` işlenen değerleri karşılaştırılır.

İki değer türü arasında [Kullanıcı tanımlı bir dönüştürme](../operators/user-defined-conversion-operators.md) varsa, aynı dönüştürme karşılık gelen null atanabilir değer türleri arasında da kullanılabilir.

## <a name="boxing-and-unboxing"></a>Kutulama ve kutudan çıkarma

Null yapılabilir değer türünün bir örneği `T?` aşağıdaki gibi [kutulanır](../../programming-guide/types/boxing-and-unboxing.md) :

- <xref:System.Nullable%601.HasValue%2A>Dönerse `false` , null başvuru üretilir.
- Döndürülürse <xref:System.Nullable%601.HasValue%2A> `true` , temel alınan değer türünün karşılık gelen değeri `T` kutulanır, örneği değildir <xref:System.Nullable%601> .

`T` `T?` Aşağıdaki örnekte gösterildiği gibi, bir değer türünün paketlenmiş değerini karşılık gelen null yapılabilir değer türüne bırakabilirsiniz:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Null yapılabilir değer türünü belirleme

Aşağıdaki örnek, bir <xref:System.Type?displayProperty=nameWithType> Örneğin oluşturulmuş bir null yapılabilir değer türünü, diğer bir deyişle <xref:System.Nullable%601?displayProperty=nameWithType> belirtilen tür parametresine sahip türü temsil edip etmediğini nasıl belirleyeceğini gösterir `T` :

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Örnekte gösterildiği gibi, bir örnek oluşturmak için [typeof](../operators/type-testing-and-cast.md#typeof-operator) işlecini kullanırsınız <xref:System.Type?displayProperty=nameWithType> .

Bir örneğin, null olabilen bir değer türünde olup olmadığını anlamak istiyorsanız, <xref:System.Object.GetType%2A?displayProperty=nameWithType> <xref:System.Type> önceki kodla test edilecek bir örnek almak için yöntemini kullanmayın. <xref:System.Object.GetType%2A?displayProperty=nameWithType>Yöntemini null yapılabilir bir değer türünün bir örneğinde çağırdığınızda, örnek olarak öğesine ayarlanır [boxed](#boxing-and-unboxing) <xref:System.Object> . Null olabilen bir değer türünün null olmayan bir örneğinin kutulenmesi, temel alınan türün bir değer kutulamasında eşdeğerdir, <xref:System.Object.GetType%2A> <xref:System.Type> null olabilen bir değer türünün temel türünü temsil eden bir örnek döndürür:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

Ayrıca, bir örneğin null yapılabilir değer türünde olup olmadığını anlamak için [,](../operators/type-testing-and-cast.md#is-operator) işleç kullanmayın. Aşağıdaki örnekte gösterildiği gibi, null olabilen bir değer türü örneği ve temel alınan tür örneğini işleçle ayırt edemezsiniz `is` :

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Bir örneğin null yapılabilir bir değer türünde olup olmadığını anlamak için aşağıdaki örnekte sunulan kodu kullanabilirsiniz:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Bu bölümde açıklanan yöntemler, [null yapılabilir başvuru türleri](nullable-reference-types.md)durumunda geçerli değildir.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md)aşağıdaki bölümlerine bakın:

- [Null atanabilir türler](~/_csharplang/spec/types.md#nullable-types)
- [Yükseltilmemiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators)
- [Örtük null yapılabilir dönüşümler](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Açık boş değer atanabilir dönüşümler](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Yükseltilmemiş dönüştürme işleçleri](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [' Yükseltilmemiş ' tam olarak ne anlama geliyor?](/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Boş değer atanabilir başvuru türleri](nullable-reference-types.md)
