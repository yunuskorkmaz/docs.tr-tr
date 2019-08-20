---
title: Null yapılabilir türler kullanma C# -Programlama Kılavuzu
ms.custom: seodec18
description: C# Null yapılabilir türlerle nasıl çalışacağınızı öğrenin
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588827"
---
# <a name="using-nullable-types-c-programming-guide"></a>Nullable türler kullanma (C# Programlama Kılavuzu)

Null yapılabilir türler, temel alınan bir değer türünün `T`tüm değerlerini temsil eden türlerdir ve ek bir [null](../../language-reference/keywords/null.md) değer. Daha fazla bilgi için, [Nullable türler](index.md) konusuna bakın.

Aşağıdaki biçimlerden birinde null yapılabilen bir türe başvurabilirsiniz: `Nullable<T>` veya. `T?` Bu iki form birbirinin yerine kullanılabilir.  
  
## <a name="declaration-and-assignment"></a>Bildirim ve atama

Bir değer türü örtük olarak karşılık gelen null yapılabilir türe dönüştürülebileceğinden, kendisine ait değer türü için yaptığınız gibi, null olabilen bir türe bir değer atarsınız. Ayrıca `null` değeri atayabilirsiniz.  Örneğin:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Null yapılabilir bir tür değeri incelemesi

Null yapılabilir bir türün bir örneğini null için incelemek ve temel alınan bir türün değerini almak için aşağıdaki ReadOnly özelliklerini kullanın:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>null yapılabilir bir türün bir örneğinin temel alınan türü bir değere sahip olup olmadığını gösterir.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType><xref:System.Nullable%601.HasValue%2A> ise ,`true`temel alınan bir türün değerini alır. <xref:System.Nullable%601.HasValue%2A> İse ,`false`özelliği bir<xref:System.InvalidOperationException>oluşturur. <xref:System.Nullable%601.Value%2A>
  
Aşağıdaki örnekteki kod, değişkenin görüntülemeden önce bir `HasValue` değer içerip içermediğini test etmek için özelliğini kullanır:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Ayrıca, aşağıdaki örnekte gösterildiği gibi, `null` `HasValue` özelliği kullanmak yerine null olabilen bir tür değişkenini karşılaştırabilirsiniz:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

7,0 ile C# başlayarak, null yapılabilir bir türdeki değeri incelemek ve almak için [model eşleştirmeyi](../../pattern-matching.md) kullanabilirsiniz:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Null yapılabilir bir türden temel alınan bir türe dönüştürme

Null olabilen bir türe null atanabilir bir tür değeri atamanız gerekiyorsa, null yapılabilir bir tür değeri null ise atanacak değeri belirtmek için [null birleşim işlecini `??` ](../../language-reference/operators/null-coalescing-operator.md) kullanın (bunu yapmak için <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> de kullanabilirsiniz):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Null yapılabilir bir tür değeri null olduğunda kullanılacak değer, temel alınan değer türünün varsayılan değeri olmalıdır yönteminikullanın.<xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>
  
Null yapılabilir bir türü açıkça null atanamaz bir türe çevirebilirsiniz. Örneğin:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

Çalışma zamanında, null yapılabilir bir türün değeri null ise, açık atama bir <xref:System.InvalidOperationException>atar.

Null yapılamayan bir değer türü örtük olarak karşılık gelen null yapılabilir türe dönüştürülür.
  
## <a name="operators"></a>İşleçler

Önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut olan herhangi bir Kullanıcı tanımlı işleç, null yapılabilir türler tarafından da kullanılabilir. Bu işleçler bir veya her iki işlenen de null ise null değeri üretir; Aksi halde, işleç sonucu hesaplamak için kapsanan değerleri kullanır. Örneğin:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Türü için, önceden tanımlanmış `&` ve `|` işleçleri bu bölümde açıklanan kurallara uymalıdır: işleçlerden biri null olsa bile bir operatör değerlendirmesinin sonucu null olmamalıdır. `bool?` Daha fazla bilgi için, [Boole mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md) makalesinin [Nullable Boolean mantıksal işleçler](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) bölümüne bakın.
  
İlişkisel`<`işleçler ( `false`, `>`, `<=`, `>=`) için, bir veya her iki işlenen de null ise sonuç olur. Belirli bir karşılaştırma `<=`(örneğin,) döndürdüğünden `false`, zıt karşılaştırma (`>`) işlevinin döndürdüğü `true`varsayılmayın. Aşağıdaki örnek, 10 ' un olduğunu gösterir

- null değerinden büyük veya buna eşit değil,
- null veya daha küçüktür.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Yukarıdaki örnek ayrıca, null olarak `true`değerlendirilen iki null yapılabilir türün eşitlik karşılaştırmasını gösterir.

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [yükseltilmemiş işleçleri](~/_csharplang/spec/expressions.md#lifted-operators) bölümüne bakın.

## <a name="boxing-and-unboxing"></a>Kutulama ve kutudan çıkarma

Null yapılabilir bir değer türü [](../types/boxing-and-unboxing.md) , aşağıdaki kurallara göre kutulanır:

- <xref:System.Nullable%601.HasValue%2A> Dönerse`false`, null başvuru üretilir.  
- Döndürülürse, temel alınan değer türünün `T` bir değeri kutulanır, örneği <xref:System.Nullable%601>değildir. `true` <xref:System.Nullable%601.HasValue%2A>

Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türünü karşılık gelen null yapılabilir türe bırakabilirsiniz:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Ayrıca bkz.

- [Null yapılabilir türler](index.md)
- [C# Programlama Kılavuzu](../index.md)
- [' Yükseltilmemiş ' tam olarak ne anlama geliyor?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
