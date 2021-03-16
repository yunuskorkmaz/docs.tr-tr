---
description: güvenli olmayan anahtar sözcük-C# başvurusu
title: güvenli olmayan anahtar sözcük-C# başvurusu
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 5be895621966dd10b2b1b0f53ebf0f3c688f1ef0
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480659"
---
# <a name="unsafe-c-reference"></a>unsafe (C# Başvurusu)

`unsafe`Anahtar sözcüğü, işaretçileri içeren tüm işlemler için gerekli olan güvenli olmayan bir bağlamı gösterir. Daha fazla bilgi için bkz. [güvenli olmayan kod ve işaretçiler](../../programming-guide/unsafe-code-pointers/index.md).

`unsafe`Değiştirici bir tür veya üye bildiriminde kullanabilirsiniz. Türün veya üyenin metinsel kapsamı, bu nedenle güvenli olmayan bir bağlam olarak değerlendirilir. Örneğin, değiştirici ile belirtilen bir yöntemi aşağıda verilmiştir `unsafe` :

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Güvenli olmayan bağlamın kapsamı parametre listesinden yönteminin sonuna kadar uzanır, bu nedenle işaretçiler parametre listesinde de kullanılabilir:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Güvenli olmayan bir blok, bu blok içinde güvenli olmayan bir kod kullanımını etkinleştirmek için de kullanabilirsiniz. Örnek:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Güvenli olmayan kod derlemek için [**AllowUnsafeBlocks**](../compiler-options/language.md#allowunsafeblocks) derleyici seçeneğini belirtmeniz gerekir. Güvenli olmayan kod, ortak dil çalışma zamanı tarafından doğrulanabilir değil.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [güvenli olmayan kod](~/_csharplang/spec/unsafe-code.md) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [fixed Deyimi](fixed-statement.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
- [Sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
