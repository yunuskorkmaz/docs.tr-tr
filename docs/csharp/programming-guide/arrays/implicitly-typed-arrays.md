---
title: Örtük olarak yazılan diziler C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: ac47ec6e69b7910f474378eebd91d58c171a802e
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73419557"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Türü Örtük Olarak Belirlenmiş Diziler (C# Programlama Kılavuzu)

Dizi başlatıcısında belirtilen öğelerden dizi örneği türünün Çıkarsanan türü örtük olarak belirlenmiş bir dizi oluşturabilirsiniz. Örtük olarak yazılmış herhangi bir değişken için kurallar, örtülü olarak belirlenmiş diziler için de geçerlidir. Daha fazla bilgi için bkz. [örtülü olarak yazılan yerel değişkenler](../classes-and-structs/implicitly-typed-local-variables.md).

Örtük olarak yazılmış diziler genellikle anonim türler ve nesne ve koleksiyon başlatıcıları ile birlikte sorgu ifadelerinde kullanılır.

Aşağıdaki örneklerde, örtülü olarak yazılmış bir dizinin nasıl oluşturulacağı gösterilmektedir:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

Önceki örnekte, örtük olarak yazılmış diziler ile, başlatma ifadesinin sol tarafında bir köşeli ayraç kullanılmaması fark edilir. Ayrıca, tek boyutlu diziler gibi `new []` kullanılarak pürüzlü Diziler başlatılmış olduğunu unutmayın.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Nesne başlatıcılarında örtük olarak yazılmış diziler

Bir dizi içeren anonim bir tür oluşturduğunuzda, dizi türün nesne başlatıcısında örtük olarak yazılmalıdır. Aşağıdaki örnekte `contacts`, her biri `PhoneNumbers`adlı bir dizi içeren anonim türlerin örtük olarak yazılmış bir dizisidir. `var` anahtar sözcüğünün nesne başlatıcıları içinde kullanılmadığını unutmayın.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Örtülü Olarak Yazılan Yerel Değişkenler](../classes-and-structs/implicitly-typed-local-variables.md)
- [Diziler](./index.md)
- [Anonim Tipler](../classes-and-structs/anonymous-types.md)
- [Nesne ve Koleksiyon Başlatıcıları](../classes-and-structs/object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [C# üzerinde LINQ](../../linq/index.md)
