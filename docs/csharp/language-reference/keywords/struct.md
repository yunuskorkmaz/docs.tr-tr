---
title: Yapı - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 2d0cba75e067e4d75ca5b544a664d7dede153c73
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660625"
---
# <a name="struct-c-reference"></a>struct (C# Başvurusu)

A `struct` türü, genelde küçük bir dikdörtgen koordinatlarını veya bir öğe bir stok özelliklerini gibi ilişkili değişken grupları kapsüllemek için kullanılan bir değer türüdür. Aşağıdaki örnek, bir basit yapı bildirimi gösterilmektedir:

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a>Açıklamalar

Yapılar içerebilir [oluşturucular](../../programming-guide/classes-and-structs/constructors.md), [sabitleri](../../programming-guide/classes-and-structs/constants.md), [alanları](../../programming-guide/classes-and-structs/fields.md), [yöntemleri](../../programming-guide/classes-and-structs/methods.md), [özellikleri](../../programming-guide/classes-and-structs/properties.md), [dizin oluşturucular](../../programming-guide/indexers/index.md), [işleçleri](../../programming-guide/statements-expressions-operators/operators.md), [olayları](../../programming-guide/events/index.md), ve [türlerin](../../programming-guide/classes-and-structs/nested-types.md), ancak birçok üye gerekliyse, türünüz bunun yerine bir sınıf yapma dikkate almanız gerekir.

Örnekler için bkz [yapılar kullanarak](../../programming-guide/classes-and-structs/using-structs.md).

Yapı birimleri arabirim uygulayabilir, ancak bunlar başka bir yapı devralamaz. Bu nedenle, Yapı üyeleri olarak bildirilemez `protected`.

Daha fazla bilgi için [yapılar](../../programming-guide/classes-and-structs/structs.md).

## <a name="examples"></a>Örnekler

Örnekler ve daha fazla bilgi için bkz. [yapılar kullanarak](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="c-language-specification"></a>C# dili belirtimi

Örnekler için bkz [yapılar kullanarak](../../programming-guide/classes-and-structs/using-structs.md).

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Varsayılan Değerler Tablosu](default-values-table.md)
- [Yerleşik Türler Tablosu](built-in-types-table.md)
- [Türler](types.md)
- [Değer Türleri](value-types.md)
- [class](class.md)
- [interface](interface.md)
- [Sınıflar ve Yapılar](../../programming-guide/classes-and-structs/index.md)