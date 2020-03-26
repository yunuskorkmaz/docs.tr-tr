---
title: sabit Ekstre - C# Referans
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: 53bee82bf24a847b0b21ed2375d09a6303d4fe48
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507197"
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)

İfade, `fixed` çöp toplayıcısının taşınır değişkeninyerini değiştirmesini engeller. Bildirime `fixed` yalnızca [güvenli olmayan](unsafe.md) bir bağlamda izin verilir. Sabit boyutlu `fixed` [arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)oluşturmak için anahtar kelimeyi de kullanabilirsiniz.

İfade, `fixed` yönetilen bir değişkene işaretçi ayarlar ve deyimin yürütülmesi sırasında bu değişkeni "sabitler". Hareketli yönetilen değişkenlere işaretçiler yalnızca bir `fixed` bağlamda yararlıdır. `fixed` Bağlam olmadan, çöp toplama değişkenleri öngörülemeyen bir şekilde başka bir yere taşıyabilir. C# derleyicisi yalnızca bir `fixed` deyimde yönetilen bir değişkene işaretçi atamanızı sağlar.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Bir dizi, dize, sabit boyutlu arabellek veya bir değişkenin adresini kullanarak bir işaretçiyi başlatmayapabilirsiniz. Aşağıdaki örnekte değişken adresleri, diziler ve dizeleri kullanımı gösteriş verilmiştir:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

`fixed` C# 7.3 ile başlayarak, deyim diziler, dizeleri, sabit boyut arabellekleri veya yönetilmeyen değişkenler ötesinde ek türler üzerinde çalışır. Adlandırılmış `GetPinnableReference` bir yöntem uygulayan herhangi bir tür sabitlenebilir. Yönetilmeyen `GetPinnableReference` bir `ref` [türün](../builtin-types/unmanaged-types.md)değişkenini döndürmesi gerekir. .NET Core <xref:System.Span%601?displayProperty=nameWithType> <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> 2.0'da tanıtılan ve .NET türleri bu deseni kullanır ve sabitlenebilir. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Bu desene katılması gereken türler oluşturuyorsanız, deseni uygulama örneğine bakın. <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType>

Birden çok işaretçi, hepsi aynı türdeyse, tek bir deyimde baş harflere para bürünebilir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Farklı türdeki işaretçileri başlatmak `fixed` için, aşağıdaki örnekte gösterildiği gibi deyimleri yerleştirmenin yeterlidir.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

İfadedeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenmez ve çöp toplamaya tabi tutulur. Bu nedenle, ifade dışında `fixed` bu değişkenleri işaret etmeyin. `fixed` İfadede bildirilen değişkenler bu ifadeye göre kapsama getirilir ve bu da durumu kolaylaştırır:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

İfadelerde `fixed` başlattırılan işaretçiler yalnızca okunur değişkenlerdir. İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir. `fixed` İfadede bildirilen değişken değiştirilemez:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Bellekleri yığına ayırabilirsiniz, çöp toplamaya tabi olmadığı ve bu nedenle sabitlenmesi gerekmediği durumlarda. Bunu yapmak için [ `stackalloc` ](../operators/stackalloc.md)bir ifade kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için [C# dil belirtiminin](~/_csharplang/spec/introduction.md) [sabit ifade](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Güvenli olmayan](unsafe.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Sabit Boyutlu Arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
