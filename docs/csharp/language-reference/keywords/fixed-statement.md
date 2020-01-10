---
title: Fixed deyimidir- C# Reference
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e527e8a54a739391d18b180532372b5b70f34d37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713516"
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)

`fixed` deyimleri, çöp toplayıcısının taşınabilir bir değişkenin yerini değiştirmesini engeller. Deyime yalnızca güvenli olmayan bir bağlamda izin verilir. [emniyetsiz](unsafe.md) `fixed` [Sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)oluşturmak için `fixed` anahtar sözcüğünü de kullanabilirsiniz.

`fixed` deyimiyle yönetilen bir değişkene yönelik bir işaretçi ve deyimin yürütülmesi sırasında bu değişkenin "PIN" değeri ayarlanır. Taşınabilir yönetilen değişkenlere yönelik işaretçiler yalnızca `fixed` bağlamında faydalıdır. `fixed` bağlamı olmadan çöp toplama, değişkenleri tahmin edilmemiş şekilde yeniden konumlandırmaya yönelik olabilir. C# Derleyici yalnızca bir `fixed` deyimindeki yönetilen değişkene bir işaretçi atamanızı sağlar.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Bir diziyi, dizeyi, sabit boyutlu arabelleği veya bir değişkenin adresini kullanarak bir işaretçiyi başlatabilirsiniz. Aşağıdaki örnek, değişken adreslerinin, dizilerin ve dizelerin kullanımını göstermektedir:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

7,3 ile C# başlayarak, `fixed` deyimleri diziler, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenlerin ötesinde ek türler üzerinde çalışır. `GetPinnableReference` adlı bir yöntemi uygulayan herhangi bir tür sabitlenebilir. , `GetPinnableReference` [Yönetilmeyen türde](../builtin-types/unmanaged-types.md)bir `ref` değişken döndürmelidir. .NET Core 2,0 ' de tanıtılan <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> .NET türleri bu düzenin kullanımını ve sabitlenebilir. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Bu modele katılması gereken türler oluşturuyorsanız, <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> için bir örnek için bkz.

Aynı türde olan birden çok işaretçi tek bir bildirimde başlatılabilir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Farklı türlerin işaretçilerini başlatmak için, aşağıdaki örnekte gösterildiği gibi `fixed` deyimlerini iç içe geçirebilirsiniz.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Deyimdeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenir ve çöp toplamaya tabidir. Bu nedenle, `fixed` deyimin dışında bu değişkenlere işaret vermeyin. `fixed` bildiriminde belirtilen değişkenler bu ifadeye kapsamlıdır ve bu daha kolay hale getirir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

`fixed` deyimlerde başlatılan işaretçiler salt okunur değişkenlerdir. İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir. `fixed` ifadesinde belirtilen değişken değiştirilemez:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Yığın üzerinde bellek ayırabilirsiniz, burada çöp toplamaya tabi değildir ve bu nedenle sabitlenmiş olması gerekmez. Bunu yapmak için [`stackalloc` işlecini](../operators/stackalloc.md)kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [fixed deyimin](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [unsafe](unsafe.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Sabit Boyutlu Arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
