---
title: Örtük olarak yazılan diziler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 36ca18adc392643107b43a947656846f3b94a2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597350"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)

Dizi başlatıcısında belirtilen öğelerden dizi örneği türünün Çıkarsanan türü örtük olarak belirlenmiş bir dizi oluşturabilirsiniz. Örtük olarak yazılmış herhangi bir değişken için kurallar, örtülü olarak belirlenmiş diziler için de geçerlidir. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).

Örtük olarak yazılmış diziler genellikle anonim türler ve nesne ve koleksiyon başlatıcıları ile birlikte sorgu ifadelerinde kullanılır.

Aşağıdaki örneklerde, örtülü olarak yazılmış bir dizinin nasıl oluşturulacağı gösterilmektedir:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

Önceki örnekte, örtük olarak yazılmış diziler ile, başlatma ifadesinin sol tarafında bir köşeli ayraç kullanılmaması fark edilir. Ayrıca, basit dizilerin tıpkı tek boyutlu diziler gibi `new []` kullanılarak başlatılmış olduğunu unutmayın.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Nesne başlatıcılarında örtük olarak yazılmış diziler

Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi türün nesne başlatıcısında örtük olarak yazılmalıdır. Aşağıdaki örnekte, `contacts` her biri adlı `PhoneNumbers`bir dizi içeren, örtülü olarak yazılmış bir anonim türler dizisidir. `var` Anahtar sözcüğünün nesne başlatıcıları içinde kullanılmadığını unutmayın.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../classes-and-structs/implicitly-typed-local-variables.md)
- [Diziler](./index.md)
- [Anonim Tipler](../classes-and-structs/anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [LINQ sorgu Ifadeleri](../linq-query-expressions/index.md)
