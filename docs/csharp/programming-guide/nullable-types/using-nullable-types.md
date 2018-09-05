---
title: Boş değer atanabilir türler (C# programlama Kılavuzu) kullanma
description: C# boş değer atanabilir türler ile çalışma hakkında bilgi edinin
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 8ef875aee8c40f60472df52c19d1c1f2c73e95e8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515443"
---
# <a name="using-nullable-types-c-programming-guide"></a>Boş değer atanabilir türler (C# programlama Kılavuzu) kullanma

Boş değer atanabilir türler, temel alınan bir değer türünün tüm değerleri temsil eden türler `T`ve ek [null](../../language-reference/keywords/null.md) değeri. Daha fazla bilgi için [boş değer atanabilir türler](index.md) konu.

Aşağıdaki biçimlerden birinde boş değer atanabilir bir tür bakabilirsiniz: `Nullable<T>` veya `T?`. İki yöntemden birini birbirinin yerine kullanılabilir.  
  
## <a name="declaration-and-assignment"></a>Bildirimi ve atama

Bir değer türü için karşılık gelen null olabilen türü örtük olarak dönüştürülebilir gibi kendi temel değer türü için yaptığınız gibi boş değer atanabilir bir tür için bir değer atayın. Ayrıca atayabilirsiniz `null` değeri.  Örneğin:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Boş değer atanabilir tür değeri incelemesi

Boş değer atanabilir bir tür için null örneğini inceleyin ve bir temel türü değerini almak için aşağıdaki salt okunur özelliklerini kullanın:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> boş değer atanabilir bir tür örneği, esas türünün bir değer olup olmadığını gösterir.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> bir temel türü değeri varsa alır <xref:System.Nullable%601.HasValue%2A> olduğu `true`. Varsa <xref:System.Nullable%601.HasValue%2A> olduğu `false`, <xref:System.Nullable%601.Value%2A> özelliği oluşturur bir <xref:System.InvalidOperationException>.
  
Aşağıdaki örnekte kod `HasValue` özelliği görüntülemeden önce değişken bir değer içerip içermediğini test etmek için:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Bir boş değer atanabilir tür değişken ile de karşılaştırabilirsiniz `null` kullanmak yerine `HasValue` özelliği, aşağıdaki örnekte gösterildiği gibi:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Kullanabileceğiniz C# 7.0 ile başlayarak, [desen eşleştirme](../../pattern-matching.md) hem incelemek ve boş değer atanabilir bir tür değerini almak için:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Bir temel türü boş değer atanabilir bir tür dönüştürme

İçin alamayan bir tür boş değer atanabilir tür değer atamak ihtiyacınız varsa [null birleşim işleci `??` ](../../language-reference/operators/null-coalescing-operator.md) boş değer atanabilir tür değer null ise atanacak değeri belirtmek için (Ayrıca <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> yapmak için yöntemi ):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Kullanım <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> temel değer türünün varsayılan değeri null yapılabilir bir tür değeri null olduğunda kullanılacak değer gerekiyorsa yöntemi.
  
Boş değer atanabilir bir tür için alamayan bir tür açıkça çevirebilirsiniz. Örneğin:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

Çalışma zamanında null yapılabilir bir tür değeri null ise açık tür dönüştürme oluşturur bir <xref:System.InvalidOperationException>.

NULL olmayan bir değer türü için karşılık gelen null olabilen türü örtük olarak dönüştürülür.
  
## <a name="operators"></a>İşleçler

Ayrıca önceden tanımlanmış birli ve ikili işleçler ve değer türleri için mevcut kullanıcı tanımlı işleçler boş değer atanabilir türleri tarafından kullanılıyor olabilir. Bir veya iki işlenenin null ise null değeri bu işleçlerden üretmek; Aksi takdirde, işlecin sonucu hesaplamak için kapsanan değerleri kullanır. Örneğin:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
İlişkisel işleçleri (`<`, `>`, `<=`, `>=`), bir veya iki işlenenin null ise sonucudur `false`. Çünkü varsaymayın belirli bir karşılaştırmanın (örneğin, `<=`) döndürür `false`, karşılaştırma ters (`>`) döndürür `true`. Aşağıdaki örnek, 10 olduğunu gösterir.

- ne büyüktür veya eşittir null,
- ya da null değerinden küçük.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Yukarıdaki örnek, ayrıca her ikisi de null iki boş değer atanabilir türler bir eşitlik karşılaştırması olarak değerlendirilen gösterir `true`.

## <a name="boxing-and-unboxing"></a>Kutulama ve kutudan çıkarma

Boş değer atanabilir değer türü [Kutulu](../types/boxing-and-unboxing.md) aşağıdaki kurallar tarafından:

- Varsa <xref:System.Nullable%601.HasValue%2A> döndürür `false`, null başvuru oluşturulur.  
- Varsa <xref:System.Nullable%601.HasValue%2A> döndürür `true`, temel alınan değer türünde bir değer `T` Kutulu olmasıdır örneği değil <xref:System.Nullable%601>.

Aşağıdaki örnekte gösterildiği gibi kutulanmış değer türüne karşılık gelen boş değer atanabilir tür unbox:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a>Bool? türü

`bool?` Null olabilen türü üç farklı değer içerebilir: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) ve [null](../../language-reference/keywords/null.md). `bool?` SQL'de kullanılan Boole değişken türü gibi türüdür. Tarafından üretilen sonuçlar emin olmak için `&` ve `|` işleçleridir üç değerli Boole türü ile tutarlı SQL'de aşağıdaki önceden tanımlı operatörler sağlanır:

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
Bu işleçler semantiği aşağıdaki tabloda tanımlanır:  
  
|x|y|x & y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Bu iki işleç içinde açıklanan kurallar izlemeyin Not [işleçleri](#operators) bölüm: biri null olsa bile null olmayan bir işleç değerlendirme sonucu olabilir.
  
## <a name="see-also"></a>Ayrıca Bkz.

- [Boş değer atanabilir türler](index.md)  
- [C# Programlama Kılavuzu](../../programming-guide/index.md)  
- [Tam olarak 'yükseltilmiş' ne demektir?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  
