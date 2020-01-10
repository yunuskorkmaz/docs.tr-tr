---
title: void C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- void_CSharpKeyword
- void
helpviewer_keywords:
- void keyword [C#]
ms.assetid: 0d2d8a95-fe20-4fbd-bf5d-c1e54bce71d4
ms.openlocfilehash: 465aaeadca603f14432478a7e5496a9ef4589ebe
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712864"
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

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Başvuru Türleri](reference-types.md)
- [Değer Türleri](value-types.md)
- [Yöntemler](../../programming-guide/classes-and-structs/methods.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
