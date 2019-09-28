---
title: Nullable değer türlerini kullanma- C# Programlama Kılavuzu
ms.custom: seodec18
description: C# Null yapılabilir değer türleriyle çalışmayı öğrenin
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396168"
---
# <a name="using-nullable-value-types-c-programming-guide"></a>Nullable değer türlerini kullanma (C# Programlama Kılavuzu)

Null yapılabilir değer türleri, `T` ve ek [null](../../language-reference/keywords/null.md) değeri olan temel bir değer türünün tüm değerlerini temsil eden türlerdir. Daha fazla bilgi için, [Nullable değer türleri](index.md) konusuna bakın.

> [!NOTE]
> C#8,0, Nullable başvuru türleri özelliğini tanıtır. Daha fazla bilgi için bkz. [Nullable başvuru türleri](../../nullable-references.md). Null yapılabilir değer türleri 2 ' den C# başlayarak kullanılabilir.

Aşağıdaki değiştirilebilir formlardan herhangi birinde null olabilen bir değer türüne başvurabilirsiniz: `Nullable<T>` veya `T?`. `T` bir değer türü olmalıdır.

## <a name="declaration-and-assignment"></a>Bildirim ve atama

Bir değer türü örtük olarak karşılık gelen null yapılabilir değer türüne dönüştürülebileceğinden, bir değeri, temel alınan değer türü gibi, null olabilen bir türe atarsınız. @No__t-0 değerini de atayabilirsiniz. Örneğin:

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Null yapılabilir bir tür değeri incelemesi

Null yapılabilir değer türünün bir örneğini null için incelemek ve temel alınan bir türün değerini almak için aşağıdaki ReadOnly özelliklerini kullanın:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>, null yapılabilir bir türün bir örneğinin temel alınan türü bir değere sahip olup olmadığını gösterir.

- <xref:System.Nullable%601.HasValue%2A>,  `true` ise temel alınan bir türün değerini alır. @No__t-0 `false` ise, <xref:System.Nullable%601.Value%2A> özelliği bir <xref:System.InvalidOperationException> oluşturur.

Aşağıdaki örnekteki kod, değişkenin görüntülemeden önce bir değer içerip içermediğini sınamak için `HasValue` özelliğini kullanır:

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

Ayrıca, aşağıdaki örnekte gösterildiği gibi, null atanabilir bir değer türünün bir değişkenini `HasValue` özelliğini kullanmak yerine `null` ile karşılaştırabilirsiniz:

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

7,0 ile C# başlayarak, null olabilen bir değer türünün bir değerini incelemek ve almak için [model eşleştirmeyi](../../pattern-matching.md) kullanabilirsiniz:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Null yapılabilir bir değer türünden temel alınan bir türe dönüştürme

Null olabilen bir değer türünün değerini null yapılamayan bir türe atamanız gerekiyorsa, null yapılabilir değer türünde bir değer null ise atanacak değeri belirtmek için [`??` null birleşim işlecini](../../language-reference/operators/null-coalescing-operator.md) kullanın (bunu yapmak için <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> metodunu da kullanabilirsiniz) :

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Null yapılabilir bir değer türünün değeri `null` olduğunda, temel alınan değer türünün varsayılan değeri olmalıdır <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> yöntemini kullanın.

Null olabilen bir değer türünü açık olmayan bir türe açıkça çevirebilirsiniz. Örneğin:

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

Çalışma zamanında, null yapılabilir bir değer türünün değeri `null` ise, açık atama bir <xref:System.InvalidOperationException> oluşturur.

Null yapılamayan bir değer türü örtük olarak karşılık gelen null yapılabilir türe dönüştürülür.

## <a name="operators"></a>İşleçler

Önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut herhangi bir Kullanıcı tanımlı işleç, bunlara karşılık gelen null yapılabilir türler tarafından da kullanılabilir. Bu işleçler, bir veya her iki işlenen de `null` ise `null` üretir. Aksi halde, işleç sonucu hesaplamak için kapsanan değerleri kullanır. Örneğin:

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> @No__t-0 türü için, önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işlenenlerden biri `null` olsa bile bir operatör değerlendirmesinin sonucu null olamaz. Daha fazla bilgi için, [Boole mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.
  
İlişkisel işleçler (`<`, `>`, `<=`, `>=`) için, bir veya her iki işlenen `null` ise, sonuç `false` olur. Belirli bir karşılaştırma (örneğin, `<=`) `false` döndürdüğünden, ters karşılaştırma (`>`) `true` döndürdüğünden Bu olduğunu varsaymayın. Aşağıdaki örnek, 10 ' un olduğunu gösterir

- `null` ' dan büyük veya eşit değil
- `null` ' dan küçük.

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

Yukarıdaki örnek ayrıca, null değer alabilen iki null atanabilir değer türünün eşitlik karşılaştırmasını `true` olarak değerlendirir.

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yükseltilmemiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators) bölümüne bakın.

## <a name="boxing-and-unboxing"></a>Kutulama ve kutudan çıkarma

Null yapılabilir bir değer türü, aşağıdaki kurallara göre [kutulanır](../types/boxing-and-unboxing.md) :

- @No__t-0 `false` döndürürse, null başvuru üretilir.
- @No__t-0 `true` döndürürse, <xref:System.Nullable%601> ' in örneği değil, temel alınan değer türü `T` değeri kutulanır.

Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türünü karşılık gelen null yapılabilir türe bırakabilirsiniz:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir değer türleri](index.md)
- [' Yükseltilmemiş ' tam olarak ne anlama geliyor?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
