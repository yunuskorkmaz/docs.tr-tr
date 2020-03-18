---
title: Örtülü Daktino Dizileri - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705723"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)

Dizi örneği türünün dizi initializer'inde belirtilen öğelerden çıkarıldığı örtülü olarak yazılmış bir dizi oluşturabilirsiniz. Herhangi bir örtülü olarak yazılan değişkeniçin kurallar, örtülü olarak yazılan diziler için de geçerlidir. Daha fazla bilgi için [bkz.](../classes-and-structs/implicitly-typed-local-variables.md)

Dolaylı olarak yazılan diziler genellikle sorgu ifadelerinde anonim türler ve nesne ve koleksiyon başlatmalayıcılarıyla birlikte kullanılır.

Aşağıdaki örnekler, örtülü olarak yazılan bir dizinin nasıl oluşturulabildiğini gösterir:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

Önceki örnekte, örtülü olarak yazılan dizilerde, başlatma deyiminin sol tarafında kare ayraç kullanılmadığını unutmayın. Pürüzlü dizilerin tek boyutlu diziler gibi kullanılarak `new []` baş harflere batmış olduğunu da unutmayın.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Nesne Başharflerinde Örtülü Olarak Yazılan Diziler

Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi örtülü olarak tür nesnesi baş harflerine yazılmalıdır. Aşağıdaki örnekte, `contacts` her biri .. `PhoneNumbers` Anahtar kelimenin `var` nesne baş harflerini içinde kullanılmadığını unutmayın.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../classes-and-structs/implicitly-typed-local-variables.md)
- [Diziler](./index.md)
- [Anonim Türler](../classes-and-structs/anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
