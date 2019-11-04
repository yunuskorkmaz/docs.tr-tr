---
title: ortak anahtar sözcük C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422553"
---
# <a name="public-c-reference"></a>public (C# Başvurusu)

`public` anahtar sözcüğü, türler ve tür üyeleri için bir erişim değiştiricisidir. Genel erişim en çok izin veren erişim düzeyidir. Şu örnekte olduğu gibi genel üyelere erişim konusunda kısıtlama yoktur:

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

Daha fazla bilgi için bkz. [erişim değiştiriciler](../../programming-guide/classes-and-structs/access-modifiers.md) ve [Erişilebilirlik düzeyleri](accessibility-levels.md) .

## <a name="example"></a>Örnek

Aşağıdaki örnekte, `PointTest` ve `MainClass`iki sınıf bildirilmiştir. `PointTest` `x` ve `y` ortak üyelere doğrudan `MainClass`erişilir.

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

`public` erişim düzeyini [özel](private.md) veya [korumalı](protected.md)olarak değiştirirseniz, şu hata iletisini alırsınız:

' PointTest. y ', koruma düzeyi nedeniyle erişilebilir değil.

## <a name="c-language-specification"></a>C# dili belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Erişilebilirlik bildirimi](~/_csharplang/spec/basic-concepts.md#declared-accessibility) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [Erişim Değiştiricileri](../../programming-guide/classes-and-structs/access-modifiers.md)
- [C# Anahtar Sözcükleri](index.md)
- [Erişim Değiştiricileri](access-modifiers.md)
- [Erişilebilirlik Düzeyleri](accessibility-levels.md)
- [Değiştiriciler](index.md)
- [private](private.md)
- [protected](protected.md)
- [internal](internal.md)
