---
title: uçucu - C# Referans
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712851"
---
# <a name="volatile-c-reference"></a>volatile (C# Başvurusu)

Anahtar `volatile` kelime, bir alanın aynı anda yürütülen birden çok iş parçacığı tarafından değiştirilebileceğinizi belirtir. Derleyici, çalışma zamanı sistemi ve hatta donanım, performans nedenleriyle okumaları ve yazmaları bellek konumlarına yeniden düzenleyebilir. Beyan edilen `volatile` alanlar bu optimizasyonlara tabi değildir. Değiştiricinin eklenmesi, tüm iş parçacıklarının, `volatile` gerçekleştirildikleri sırada başka bir iş parçacığı tarafından gerçekleştirilen geçici yazıları gözlemlemesini sağlar. Yürütmenin tüm iş parçacıklarından görüldüğü gibi, geçici yazmaların tek bir toplam siparişinin garantisi yoktur.

`volatile` Anahtar kelime bu tür alanlara uygulanabilir:

- Başvuru türleri.
- İşaretçi türleri (güvenli olmayan bir bağlamda). İşaretçinin kendisi geçici olsa da, işaret ettiği nesnenin geçici olamayacağını unutmayın. Başka bir deyişle, "uçucu işaretçi" olarak bildiremezsiniz.
- `sbyte` `byte`,, `short` `ushort`, `int`, `uint`, `char`, `float`, `bool`, ve .
- Aşağıdaki `enum` temel türlerden birine sahip `byte` `sbyte`bir `short` `ushort`tür: , , , `int`, veya `uint`.
- Başvuru türleri olduğu bilinen genel tür parametreleri.
- <xref:System.IntPtr> ve <xref:System.UIntPtr>.

Bu tür `double` `long` `volatile` alanlara okunup yazdığı ndan, atomik olduğu garanti edilemez. Bu tür alanlara çok iş parçacığı erişimini <xref:System.Threading.Interlocked> korumak için sınıf üyelerini [`lock`](lock-statement.md) kullanın veya deyimi kullanarak erişimi koruyun.

Anahtar `volatile` kelime yalnızca a `class` veya `struct`. alanlarına uygulanabilir Yerel değişkenler bildirilemez. `volatile`

## <a name="example"></a>Örnek

Aşağıdaki örnek, ortak alan değişkenini `volatile`nasıl .

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

Aşağıdaki örnek, yardımcı veya alt iş parçacığının birincil iş parçacığınınkine paralel olarak nasıl oluşturulabileceğini ve işleme gerçekleştirmek için nasıl kullanılabileceğini gösterir. Çok iş parçacığı hakkında daha fazla bilgi için [Yönetilen İş Parçacığı'na](../../../standard/threading/index.md)bakın.

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

`volatile` Değiştirici yerinde bildirimine `_shouldStop` eklendikten sonra, her zaman aynı sonuçları alırsınız (önceki kodda gösterilen alıntıya benzer). Ancak, `_shouldStop` üye üzerinde bu değiştirici olmadan, davranış öngörülemez. Yöntem, `DoWork` üye erişimini optimize ederek eski verilerin okunmasıyla sonuçlanabilir. Çok iş parçacığı programlama doğası nedeniyle, bayat okuma sayısı öngörülemez. Programın farklı çalışır biraz farklı sonuçlar üretecektir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# dil belirtimi: geçici anahtar kelime](../../../../_csharplang/spec/classes.md#volatile-fields)
- [C# Referans](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Kelimeler](index.md)
- [Değiştiriciler](index.md)
- [kilit deyimi](lock-statement.md)
- <xref:System.Threading.Interlocked>
