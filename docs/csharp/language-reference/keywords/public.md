---
title: ortak anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 19906d7fd0f7d41ef9e4cdaf951c77825e0bbead
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713176"
---
# <a name="public-c-reference"></a>public (C# Başvurusu)

`public` Anahtar kelime, türler ve tür üyeleri için bir erişim değiştiricidir. Genel erişim en izin verilen erişim düzeyidir. Bu örnekte olduğu gibi, herkese açık üyelere erişimkonusunda herhangi bir kısıtlama yoktur:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Daha fazla bilgi için [Erişim Değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md) ve [Erişilebilirlik Düzeyleri'ne](accessibility-levels.md) bakın.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, iki sınıf `PointTest` bildirilir `MainClass`ve . Kamu üyeleri `x` `y` ve `PointTest` doğrudan `MainClass`erişilir.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

`public` Erişim düzeyini [özel](private.md) veya [korumalı](protected.md)olarak değiştirirseniz, hata iletisi alırsınız:

'PointTest.y' koruma düzeyi nedeniyle erişilemez.

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Bildirilen Erişilebilirlik'e](~/_csharplang/spec/basic-concepts.md#declared-accessibility) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [C# Anahtar Kelimeler](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [Özel](private.md)
- [protected](protected.md)
- [Iç](internal.md)
