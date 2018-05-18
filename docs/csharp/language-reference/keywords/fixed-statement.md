---
title: fixed Deyimi (C# Başvurusu)
ms.date: 05/10/2018
f1_keywords:
- fixed_CSharpKeyword
- fixed
helpviewer_keywords:
- fixed keyword [C#]
ms.openlocfilehash: decf906efeebf1723b4c5d6f0c75ba57affe9a98
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2018
---
# <a name="fixed-statement-c-reference"></a>fixed Deyimi (C# Başvurusu)

`fixed` Deyimi taşınabilir bir değişken yerini değiştirme atık toplayıcı engeller. `fixed` Deyimi izin yalnızca bir [güvensiz](unsafe.md) bağlamı. `Fixed` oluşturmak için de kullanılabilir [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

`fixed` Deyimi ayarlar bir işaretçi bir yönetilen değişken ve "PIN" için değişken deyimin yürütülmesi sırasında. İşaretçileri taşınabilir yönetilen değişkenlere yalnızca yararlı bir `fixed` bağlamı. Olmadan bir `fixed` bağlamı, atık toplama taşımanızı değişkenleri beklenmedik şekilde. C# Derleyici yalnızca bir işaretçi yönetilen bir değişkene atayın olanak sağlayan bir `fixed` deyimi.

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#1)]

Bir dizi, bir dize, bir sabit boyutlu arabellek veya değişkenin adresini kullanarak bir işaretçi başlatabilirsiniz. Aşağıdaki örnekte değişken adresleri, dizileri ve dizeleri kullanımını göstermektedir. Sabit boyutlu arabellekler hakkında daha fazla bilgi için bkz: [sabit boyutlu arabellekler](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md).

[!code-csharp[Initializing fixed size buffers](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#2)]

C# ile 7.3, başlangıç `fixed` deyimi çalışır dizileri, dizeler, sabit boyutlu arabellekler veya yönetilmeyen değişkenleri ötesinde ek türlerinde. Adlı bir yöntem uygulayan herhangi bir türü `DangerousGetPinnableReference` sabitlenmiş. `DangerousGetPinnableReference` Döndürmelidir bir `ref` değişken olarak bir yönetilmeyen tür. Üzerinde konusuna [işaretçi türleri](../../programming-guide/unsafe-code-pointers/pointer-types.md) daha fazla bilgi için. .NET türleri <xref:System.Span%601?displayProperty=nameWithType> ve <xref:System.ReadonlySpan%601?displayProperty=nameWithType> .NET Core 2.0 olun sunulan sabitlenmiş ve bu desenini kullanın. Bu aşağıdaki örnekte gösterilmiştir:

[!code-csharp[Accessing fixed memory](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#FixedSpan)]

Bu desen alması gereken türlerini oluşturduysanız bkz <xref:System.Span%601.DangerousGetPinnableReference?displayProperty=nameWithType> düzeni uygulama örneği için.

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
