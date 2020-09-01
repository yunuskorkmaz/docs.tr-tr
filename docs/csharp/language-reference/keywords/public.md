---
description: Public anahtar sözcüğü-C# başvurusu
title: Public anahtar sözcüğü-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 26edaf7538d11d082a4b8863228213c3ebc46937
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122348"
---
# <a name="public-c-reference"></a>public (C# Başvurusu)

`public`Anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir. Genel erişim en çok izin veren erişim düzeyidir. Şu örnekte olduğu gibi genel üyelere erişim konusunda kısıtlama yoktur:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Daha fazla bilgi için bkz. [erişim değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md) ve [Erişilebilirlik düzeyleri](accessibility-levels.md) .

## <a name="example"></a>Örnek

Aşağıdaki örnekte, iki sınıf bildirilmiştir `PointTest` ve `MainClass` . Ortak üyelerine `x` ve ' `y` a `PointTest` doğrudan üzerinden erişilir `MainClass` .

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

`public`Erişim düzeyini [özel](private.md) veya [korumalı](protected.md)olarak değiştirirseniz şu hata iletisini alırsınız:

' PointTest. y ', koruma düzeyi nedeniyle erişilebilir değil.

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [C# anahtar sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
