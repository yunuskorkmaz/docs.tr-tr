---
title: void - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: af79d39282ea38811777ea1f23054120afc39d2c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632947"
---
# <a name="void-c-reference"></a>void (C# Başvurusu)

Bir yöntem için dönüş türü olarak kullanıldığında `void` yöntemi bir değer döndürmediğini belirtir.

`void` bir yöntemin parametre listesinde izin verilmez. Hiçbir parametre almayan ve hiçbir değer döndürmeyen bir yöntem şu şekilde bildirilir:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void` Ayrıca güvenli olmayan bir bağlamda, bir işaretçi türü bilinmiyor bildirmek için kullanılır. Daha fazla bilgi için [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void` .NET Framework için bir diğer addır <xref:System.Void?displayProperty=nameWithType> türü.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Başvuru Türleri](reference-types.md)
- [Değer Türleri](value-types.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
