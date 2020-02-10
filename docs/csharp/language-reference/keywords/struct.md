---
title: struct- C# Reference
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 77d5c83dd4c81b96bc62ace6e609db8bc411dc41
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093168"
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

Yapılar ayrıca [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitler](../../programming-guide/classes-and-structs/constants.md), [alanlar](../../programming-guide/classes-and-structs/fields.md), [Yöntemler](../../programming-guide/classes-and-structs/methods.md), [Özellikler](../../programming-guide/classes-and-structs/properties.md), [Dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçler](../operators/index.md), [Olaylar](../../programming-guide/events/index.md)ve [iç içe türler](../../programming-guide/classes-and-structs/nested-types.md)içerebilir, ancak bu tür Üyeler gerekli olsa da, bu türden bir sınıf oluşturmanız gerekir.

Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).

Yapılar bir arabirim uygulayabilir, ancak başka bir struct 'tan devralınabilir. Bu nedenle, yapı üyeleri `protected`olarak bildirilemez.

Daha fazla bilgi için bkz. [yapılar](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Örnekler

Örnekler ve daha fazla bilgi için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Örnekler için bkz. [yapıları kullanma](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Değer türleri](../builtin-types/value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Sınıflar ve yapılar](../../programming-guide/classes-and-structs/index.md)
