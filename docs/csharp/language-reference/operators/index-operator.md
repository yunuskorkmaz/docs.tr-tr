---
title: '[] İşleci - C# başvurusu'
ms.custom: seodec18
ms.date: 01/10/2019
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: c464dab1ebf62d33b74c83b8d5c3c563fef4e77c
ms.sourcegitcommit: 75567a3cb437009db55949c6092f4e77ed1a9da4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54307129"
---
# <a name="-operator-c-reference"></a>[] İşleci (C# Başvurusu)

Köşeli ayraçlar `[]`, genellikle dizi, dizin oluşturucu veya işaretçiyi öğe erişimi için kullanılır.

İşaretçi öğe erişimi hakkında daha fazla bilgi için bkz: [nasıl yapılır: işaretçiyle bir dizi öğesine erişme](../../programming-guide/unsafe-code-pointers/how-to-access-an-array-element-with-a-pointer.md).

Köşeli ayraçlar belirtmek için de [öznitelikleri](../../programming-guide/concepts/attributes/index.md):

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="array-access"></a>Dizi erişimi

Aşağıdaki örnekte, dizi öğelerinin nasıl erişileceğini gösteren:

[!code-csharp-interactive[array access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Arrays)]

Bir dizi dizini karşılık gelen boyutuna bir dizinin sınırları dışında ise bir <xref:System.IndexOutOfRangeException> oluşturulur.

Yukarıdaki örnekte gösterildiği gibi de köşeli ayraç örnekleme dizi örnekleri bir dizi türü bildirimi de kullanabilirsiniz.

Diziler hakkında daha fazla bilgi için bkz. [diziler](../../programming-guide/arrays/index.md).

## <a name="indexer-access"></a>Dizinleyici erişimi

Aşağıdaki örnek, .NET kullanır <xref:System.Collections.Generic.Dictionary%602> dizinleyici erişimi göstermek için türü:

[!code-csharp-interactive[indexer access](~/samples/snippets/csharp/language-reference/operators/IndexOperatorExamples.cs#Indexers)]

Dizin oluşturucular dizi dizini oluşturma olarak benzer şekilde, kullanıcı tanımlı bir tür dizin örneğini olanak tanır. Dizin oluşturucu bağımsız değişken tamsayı olması gerekir, dizi dizinleri, herhangi bir türde olması bildirilir.

Dizin oluşturucular hakkında daha fazla bilgi için bkz: [dizin oluşturucular](../../programming-guide/indexers/index.md).

## <a name="operator-overloadability"></a>İşleç overloadability

Öğe erişimi `[]` bir aşırı yüklenebilir işleç olarak kabul edilmez. Kullanım [dizin oluşturucular](../../programming-guide/indexers/index.md) için kullanıcı tanımlı türler ile dizin oluşturmayı destekler.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [öğe erişimi](~/_csharplang/spec/expressions.md#element-access) ve [işaretçi öğe erişimi](~/_csharplang/spec/unsafe-code.md#pointer-element-access) bölümlerini [ C# dil belirtimi](../language-specification/index.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# İşleçleri](index.md)
- [Diziler](../../programming-guide/arrays/index.md)
- [Dizin Oluşturucular](../../programming-guide/indexers/index.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Öznitelikler](../../programming-guide/concepts/attributes/index.md)
