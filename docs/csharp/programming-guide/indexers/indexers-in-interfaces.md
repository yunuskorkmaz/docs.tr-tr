---
title: Arabirimlerde Dizin oluşturucular-C# Programlama Kılavuzu
description: Dizin oluşturucular C# içindeki bir arabirimde bildirilemez. Arabirim dizin oluşturucular erişimcilerinin sınıf dizin oluşturucularının Erişimcilerden farklı olduğunu öğrenin.
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: ec77843bdf3181a543bd6c02cfb034b21ded1ae7
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303107"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a>Arabirimlerdeki Dizin Oluşturucular (C# Programlama Kılavuzu)

Dizin oluşturucular bir [arabirimde](../../language-reference/keywords/interface.md)bildirilemez. Arabirim dizin oluşturucularının erişimcileri, [sınıf](../../language-reference/keywords/class.md) dizin oluşturucularının erişimcilerine aşağıdaki yollarla göre farklılık gösterir:

- Arabirim erişimcileri değiştiriciler kullanmaz.
- Arabirim erişimcisinin genellikle gövdesi yoktur.

Erişimcinin amacı, dizin oluşturucunun okuma-yazma, salt okunurdur veya salt yazılır olduğunu belirtsağlamaktır. Bir arabirimde tanımlanmış bir Dizin Oluşturucu için uygulama sağlayabilirsiniz, ancak bu nadir bir durumdur. Dizin oluşturucular genellikle veri alanlarına erişmek için bir API tanımlar ve veri alanları bir arabirimde tanımlanamaz.

Arabirim dizin oluşturucu erişimcisine bir örnek aşağıda verilmiştir:

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

Bir dizin oluşturucunun imzası aynı arabirimde belirtilen diğer tüm dizin oluşturucularının imzalarından farklı olmalıdır.

## <a name="example"></a>Örnek

Aşağıdaki örnek, arabirim dizin oluşturucularının nasıl uygulanacağını gösterir.

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

Yukarıdaki örnekte, arabirim üyesinin tam adını kullanarak açık arabirim üye uygulamasını kullanabilirsiniz. Örneğin:

```csharp
string IIndexInterface.this[int index]
{
}
```

Ancak, tam adı yalnızca, sınıf aynı Dizin Oluşturucu imzasına sahip birden fazla arabirim uygularken karışıklığı önlemek için gereklidir. Örneğin, bir `Employee` Sınıf iki arabirim uygusa ve `ICitizen` `IEmployee` her iki arabirimde de aynı Dizin Oluşturucu imzası varsa, açık arabirim üye uygulaması gereklidir. Diğer bir deyişle, aşağıdaki Dizin Oluşturucu bildirimi:

```csharp
string IEmployee.this[int index]
{
}
```

arabirim üzerinde dizin oluşturucuyu uygular `IEmployee` , aşağıdaki bildirim:

```csharp
string ICitizen.this[int index]
{
}
```

arabirimindeki Dizin oluşturucuyu uygular `ICitizen` .

## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Dizin Oluşturucular](./index.md)
- [Özellikler](../classes-and-structs/properties.md)
- [Arabirimler](../interfaces/index.md)
