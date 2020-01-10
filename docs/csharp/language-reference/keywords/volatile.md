---
title: Geçici C# başvuru
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712851"
---
# <a name="volatile-c-reference"></a>volatile (C# Başvurusu)

`volatile` anahtar sözcüğü, bir alanın aynı anda yürütülen birden çok iş parçacığı tarafından değiştirildiğini belirtir. Derleyici, çalışma zamanı sistemi ve hatta donanım, performans nedeniyle bellek konumlarına okuma ve yazma işlemlerini yeniden düzenleyebilir. `volatile` olarak belirtilen alanlar bu iyileştirmelere tabi değildir. `volatile` değiştiricisini eklemek, tüm iş parçacıklarının gerçekleştirilen diğer bir iş parçacığı tarafından gerçekleştirilen geçici yazmaları gözlemleyecek olmasını sağlar. Yürütmenin tüm iş parçacıklarından görüldüğü şekilde, tek bir toplam geçici yazma sıralaması garantisi yoktur.

`volatile` anahtar sözcüğü bu türlerin alanlarına uygulanabilir:

- Başvuru türleri.
- İşaretçi türleri (güvenli olmayan bir bağlamda). İşaretçinin kendisi geçici olsa da, işaret ettiği nesnenin bu şekilde olduğunu unutmayın. Diğer bir deyişle, "geçici işaretçi işaretçisi" bildiremezsiniz.
- `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`ve `bool`gibi basit türler.
- Aşağıdaki temel türlerden birine sahip `enum` türü: `byte`, `sbyte`, `short`, `ushort`, `int`veya `uint`.
- Başvuru türleri olarak bilinen genel tür parametreleri.
- <xref:System.IntPtr> ve <xref:System.UIntPtr>.

`double` ve `long`dahil diğer türler `volatile` olarak işaretlenemez, çünkü bu türlerin alanlarına okuma ve yazma işlemleri atomik olarak garanti edilemez. Bu tür alanlara çok iş parçacıklı erişimi korumak için, <xref:System.Threading.Interlocked> sınıf üyelerini kullanın veya [`lock`](lock-statement.md) ifadesini kullanarak erişimi koruyun.

`volatile` anahtar sözcüğü yalnızca bir `class` veya `struct`alanlara uygulanabilir. Yerel değişkenler `volatile`olarak bildirilemez.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `volatile`olarak bir ortak alan değişkeninin nasıl bildirilemeyeceğini gösterir.

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

Aşağıdaki örnek, birincil iş parçacığından paralel olarak işleme gerçekleştirmek için bir yardımcı veya çalışan iş parçacığının nasıl oluşturulup kullanılabileceğini gösterir. Çoklu iş parçacığı hakkında daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

`_shouldStop` bildirimine eklenen `volatile` değiştiricisi ile, her zaman aynı sonuçları elde edersiniz (Yukarıdaki kodda gösterilen alıntıya benzer). Ancak, `_shouldStop` üyesinde Bu değiştirici olmadan davranış tahmin edilemez. `DoWork` yöntemi üye erişimini iyileştirebilmenizi sağlayabilir ve bu da eski verilerin okunmasına yol açar. Çok iş parçacıklı programlama doğası nedeniyle, eski okuma sayısı tahmin edilemez. Programın farklı çalıştırmaları biraz farklı sonuçlar üretecektir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C#dil belirtimi: volatile anahtar sözcüğü](../../../../_csharplang/spec/classes.md#volatile-fields)
- [C#Başvurunun](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# Anahtar Sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [Lock deyimleri](lock-statement.md)
- <xref:System.Threading.Interlocked>
