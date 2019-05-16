---
title: güven olmayan anahtar sözcük - C# başvurusu
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 8b220e0d6b7e6ab5a7b6d964d1910eaafb63d2d9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633929"
---
# <a name="unsafe-c-reference"></a>unsafe (C# Başvurusu)

`unsafe` Anahtar sözcüğü, işaretçileri içeren tüm işlemler için gerekli olan güvensiz bir bağlamı gösterir. Daha fazla bilgi için [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).

Kullanabileceğiniz `unsafe` bildirimi bir tür veya üye değiştiricisi. Türe veya üyeye tüm metinsel kapsamını, bu nedenle güvenli olmayan bir bağlam kabul edilir. Örneğin, aşağıdaki ile bildirilen bir yöntemi olan `unsafe` değiştiricisi:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

İşaretçiler, parametre listesinde kullanılabilmesi için güvenli olmayan bir bağlam kapsamını parametre listesinden, yöntemin sonuna kadar genişletir:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Güvenli olmayan bir blok, bu blok içinde bir güvenli olmayan kod kullanımını etkinleştirmek için de kullanabilirsiniz. Örneğin:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Güvenli olmayan kod olarak derlemek için belirtmelisiniz [/ unsafe](../compiler-options/unsafe-compiler-option.md) derleyici seçeneği. Güvenli olmayan kod ortak dil çalışma zamanı tarafından doğrulanabilir değil.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) içinde [ C# dil belirtimi](../language-specification/index.md). Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [fixed Deyimi](fixed-statement.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
- [Sabit Boyutlu Arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
