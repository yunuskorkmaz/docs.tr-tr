---
title: güvenli olmayan anahtar kelime - C# Başvuru
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712994"
---
# <a name="unsafe-c-reference"></a>unsafe (C# Başvurusu)

`unsafe` Anahtar kelime, işaretçileri içeren herhangi bir işlem için gerekli olan güvenli olmayan bir bağlamı gösterir. Daha fazla bilgi için [Güvenli Olmayan Kod ve İşaretçiler'e](../../programming-guide/unsafe-code-pointers/index.md)bakın.

`unsafe` Bir tür veya üyenin bildiriminde değiştiriciyi kullanabilirsiniz. Bu nedenle, türün veya üyenin tüm metin boyutu güvenli olmayan bir bağlam olarak kabul edilir. Örneğin, aşağıdaki `unsafe` değiştirici ile bildirilen bir yöntemdir:

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

Güvenli olmayan bağlamın kapsamı parametre listesinden yöntemin sonuna kadar uzanır, böylece işaretçiler parametre listesinde de kullanılabilir:

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

Bu blok içinde güvenli olmayan bir kod kullanımını etkinleştirmek için güvenli olmayan bir blok da kullanabilirsiniz. Örnek:

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

Güvenli olmayan kod derlemek için [`-unsafe`](../compiler-options/unsafe-compiler-option.md) derleyici seçeneğini belirtmeniz gerekir. Güvenli olmayan kod, ortak dil çalışma süresi tarafından doğrulanabilir değildir.

## <a name="example"></a>Örnek

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Güvenli Olmayan koda](~/_csharplang/spec/unsafe-code.md) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [fixed Deyimi](fixed-statement.md)
- [Güvenli Olmayan Kod ve İşaretçiler](../../programming-guide/unsafe-code-pointers/index.md)
- [Sabit Boyutlu Arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
