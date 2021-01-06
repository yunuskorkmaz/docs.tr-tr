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
ms.openlocfilehash: 90c1d2a1d9efcdf57f914f4318bf7a743d3f37ec
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938474"
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

Aşağıdaki örnekte, iki sınıf bildirilmiştir `PointTest` ve `Program` . Ortak üyelerine `x` ve ' `y` a `PointTest` doğrudan üzerinden erişilir `Program` .

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
- [özelleştirme](private.md)
- [protected](protected.md)
- [internal](internal.md)
