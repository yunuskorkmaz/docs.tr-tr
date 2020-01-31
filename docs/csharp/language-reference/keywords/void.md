---
title: void C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 0624b547ee2586334ac35d366ae3c8dfd14963ee
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742765"
---
# <a name="void-c-reference"></a>void (C# Başvurusu)

Bir yöntem için dönüş türü olarak kullanıldığında, `void` metodun bir değer döndürmediğini belirtir.

metodun parametre listesinde `void` izin verilmez. Hiçbir parametre alan ve değer döndüren bir yöntem aşağıdaki şekilde bildirilmiştir:

```csharp
public void SampleMethod()
{
    // Body of the method.
}
```

`void`, bilinmeyen bir tür için bir işaretçi bildirmek üzere güvenli olmayan bir bağlamda de kullanılır. Daha fazla bilgi için bkz. [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md).

`void`, .NET Framework <xref:System.Void?displayProperty=nameWithType> türü için bir diğer addır.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#başvurunun](../index.md)
- [C# anahtar sözcükleri](index.md)
- [Başvuru türleri](reference-types.md)
- [Değer türleri](../builtin-types/value-types.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)
- [Güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
