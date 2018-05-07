---
title: fixed Deyimi (C# Başvurusu)
ms.date: 04/20/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: e1664f508cb861ffa73b800eeb0da3a1f1cdc432
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)

`fixed` Deyimi taşınabilir bir değişken yerini değiştirme atık toplayıcı engeller. `fixed` Deyimi izin yalnızca bir [güvensiz](unsafe.md) bağlamı. `Fixed` oluşturmak için de kullanılabilir [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Deyimi ayarlar bir işaretçi bir yönetilen değişken ve "PIN" için değişken deyimin yürütülmesi sırasında. İşaretçileri taşınabilir yönetilen değişkenlere yalnızca yararlı bir `fixed` bağlamı. Olmadan bir `fixed` bağlamı, atık toplama taşımanızı değişkenleri beklenmedik şekilde. C# Derleyici yalnızca bir işaretçi yönetilen bir değişkene atayın olanak sağlayan bir `fixed` deyimi.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Bir dizi, bir dize, bir sabit boyutlu arabellek veya değişkenin adresini kullanarak bir işaretçi başlatabilirsiniz. Aşağıdaki örnekte değişken adresleri, dizileri ve dizeleri kullanımını göstermektedir. Sabit boyutlu arabellekler hakkında daha fazla bilgi için bkz: [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

Aynı türde olmaları durumunda bir deyimde birden çok işaretçileri başlatılabilir:

```csharp
fixed (byte* ps = srcarray, pd = dstarray) {...}
```

Farklı türlerdeki işaretçileri başlatmak için yalnızca içe `fixed` aşağıdaki örnekte gösterildiği gibi deyimleri.

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#3)]

Deyim kodda yürütüldükten sonra tüm sabitlenmiş sabitlenmemiş ve atık toplama değişkenlerdir. Bu nedenle, bu değişkenleri dışında işaret etmiyor `fixed` deyimi. Bildirilen değişkenlerin `fixed` deyimi bu kolaylaştıran bu deyim için kapsamlı:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
   ...
}
// ps and pd are no longer in scope here.
```

İşaretçileri başlatılmış `fixed` deyimleri olan salt okunur değişkenler. İşaretçi değeri değiştirmek istiyorsanız, ikinci bir işaretçi değişkeni bildirme ve değiştiren gerekir. Bildirilen değişken `fixed` deyimi değiştirilemez:

```csharp
fixed (byte* ps = srcarray, pd = dstarray)
{
    byte* pSourceCopy = ps;
    pSourceCopy++; // point to the next element.
    ps++; // invalid: cannot modify ps, as it is declared in the fixed statement.
}
```


Güvenli modda, burada atık toplama tabi değildir ve bu nedenle sabitlenmelidir gerekmez yığında bellek ayrılabilir. Daha fazla bilgi için bkz: [stackalloc](stackalloc.md).

[!code-csharp[Initializing multiple pointers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#4)]

## <a name="c-language-specification"></a>C# Dil Belirtimi

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca Bkz.

 [C# başvurusu](../index.md)  
 [C# Programlama Kılavuzu](../../programming-guide/index.md)  
 [C# Anahtar Sözcükleri](index.md)  
 [unsafe](unsafe.md)  
 [Sabit Boyutlu Arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
