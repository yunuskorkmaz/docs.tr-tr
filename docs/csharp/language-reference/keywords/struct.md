---
title: struct- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: a78488ad902b0a96a30ad197b0ece043543c3d69
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422308"
---
# <a name="struct-c-reference"></a>struct (C# Başvurusu)

`struct` türü, genellikle bir dikdörtgenin koordinatları veya Stoktaki bir öğenin özellikleri gibi ilgili değişkenlerin küçük gruplarını kapsüllemek için kullanılan bir değer türüdür. Aşağıdaki örnek, basit bir struct bildirimini göstermektedir:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Açıklamalar

Yapılar, birçok üye olsa da, [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitler](../../programming-guide/classes-and-structs/constants.md), [alanlar](../../programming-guide/classes-and-structs/fields.md), [Yöntemler](../../programming-guide/classes-and-structs/methods.md), [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçler](../operators/index.md), [Olaylar](../../programming-guide/events/index.md)ve [iç içe türler](../../programming-guide/classes-and-structs/nested-types.md)içerebilir. gerekli, bunun yerine bir sınıf yazmanız gerekir.

Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).

Yapılar bir arabirim uygulayabilir, ancak başka bir struct 'tan devralınabilir. Bu nedenle, yapı üyeleri `protected`olarak bildirilemez.

Daha fazla bilgi için bkz. [yapılar](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Örnekler

Örnekler ve daha fazla bilgi için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Varsayılan Değerler Tablosu](default-values-table.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Türler](/dotnet/csharp/language-reference/keywords)
- [Değer Türleri](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Sınıflar ve Yapılar](../../programming-guide/classes-and-structs/index.md)
