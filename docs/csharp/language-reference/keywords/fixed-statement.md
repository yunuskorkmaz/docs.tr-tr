---
title: Fixed deyimidir- C# Reference
ms.custom: seodec18
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: d3c87f0e71095bbcc7c5a1d64b026e92838a6306
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433747"
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)

`fixed` İfade, çöp toplayıcısının taşınabilir bir değişkenin yerini değiştirmesini engeller. Deyime yalnızca güvenli olmayan bir bağlamda izin verilir. [](unsafe.md) `fixed` [Sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)oluşturmak için `fixed` anahtar sözcüğünü de kullanabilirsiniz.

`fixed` İfade, yönetilen bir değişkene bir işaretçi ayarlar ve deyimin yürütülmesi sırasında bu değişkene "PIN" koyar. Taşınabilir olarak yönetilen değişkenlere yönelik işaretçiler yalnızca bir `fixed` bağlamda yararlıdır. `fixed` Bağlam olmadan çöp toplama, değişkenleri tahmin edilmemiş şekilde yeniden konumlandırmaya yönelik olabilir. C# Derleyici yalnızca bir `fixed` ifadede yönetilen değişkene bir işaretçi atamanızı sağlar.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Bir diziyi, dizeyi, sabit boyutlu arabelleği veya bir değişkenin adresini kullanarak bir işaretçiyi başlatabilirsiniz. Aşağıdaki örnek, değişken adreslerinin, dizilerin ve dizelerin kullanımını göstermektedir:

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

7,3 ile C# başlayarak, `fixed` ifade diziler, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenlerin ötesinde ek türler üzerinde çalışır. Adlı `GetPinnableReference` bir yöntemi uygulayan herhangi bir tür sabitlenebilir. , `GetPinnableReference` [Yönetilmeyen türde](../builtin-types/unmanaged-types.md)bir `ref` değişken döndürmelidir. .NET Core 2,0 <xref:System.Span%601?displayProperty=nameWithType> ' <xref:System.ReadOnlySpan%601?displayProperty=nameWithType> de sunulan .net türleri bu düzenin kullanımını ve sabitlenebilir. Bu, aşağıdaki örnekte gösterilmiştir:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Bu modele katılması gereken türler oluşturuyorsanız, bu düzenin uygulanması örneği için bkz <xref:System.Span%601.GetPinnableReference?displayProperty=nameWithType> .

Aynı türde olan birden çok işaretçi tek bir bildirimde başlatılabilir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Farklı türlerin işaretçilerini başlatmak için aşağıdaki örnekte gösterildiği gibi `fixed` deyimlerini iç içe geçirebilirsiniz.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Deyimdeki kod yürütüldükten sonra, sabitlenmiş değişkenler sabitlenir ve çöp toplamaya tabidir. Bu nedenle, bu değişkenleri `fixed` deyimin dışında işaret etmez. `fixed` Bildiriminde belirtilen değişkenler, bu ifadeye göre kapsamlandırılır ve daha kolay hale getirir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

`fixed` Deyimlerde başlatılan işaretçiler salt okunur değişkenlerdir. İşaretçi değerini değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirmeniz ve bunu değiştirmeniz gerekir. `fixed` İfadede belirtilen değişken değiştirilemez:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```

Yığın üzerinde bellek ayırabilirsiniz, burada çöp toplamaya tabi değildir ve bu nedenle sabitlenmiş olması gerekmez. Bunu yapmak için [ `stackalloc` işlecini](../operators/stackalloc.md)kullanın.

## <a name="c-language-specification"></a>C# dili belirtimi

Daha fazla bilgi için, [ C# dil belirtiminin](~/_csharplang/spec/introduction.md) [fixed deyimin](~/_csharplang/spec/unsafe-code.md#the-fixed-statement) bölümüne bakın.

## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [unsafe](unsafe.md)
- [İşaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Sabit Boyutlu Arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
