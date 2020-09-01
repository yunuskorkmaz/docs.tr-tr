---
description: volatile-C# başvurusu
title: volatile-C# başvurusu
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: bb89e99e8e28ff1e263817f498619dbfae700a50
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141705"
---
# <a name="volatile-c-reference"></a>volatile (C# Başvurusu)

`volatile`Anahtar sözcüğü, bir alanın aynı anda yürütülen birden çok iş parçacığı tarafından değiştirildiğini belirtir. Derleyici, çalışma zamanı sistemi ve hatta donanım, performans nedeniyle bellek konumlarına okuma ve yazma işlemlerini yeniden düzenleyebilir. Belirtilen alanlar `volatile` bu iyileştirmelere tabi değildir. Değiştirici eklendiğinde, `volatile` tüm iş parçacıklarının diğer bir iş parçacığı tarafından gerçekleştirilen geçici yazmaları gerçekleştirdikleri sırayla gözlemleyecek olmasını sağlar. Yürütmenin tüm iş parçacıklarından görüldüğü şekilde, tek bir toplam geçici yazma sıralaması garantisi yoktur.

`volatile`Anahtar sözcüğü bu türlerin alanlarına uygulanabilir:

- Başvuru türleri.
- İşaretçi türleri (güvenli olmayan bir bağlamda). İşaretçinin kendisi geçici olsa da, işaret ettiği nesnenin bu şekilde olduğunu unutmayın. Diğer bir deyişle, "geçici işaretçi işaretçisi" bildiremezsiniz.
- ,,, `sbyte` `byte` `short` `ushort` , `int` , `uint` , `char` , `float` Ve `bool` gibi basit türler.
- `enum`Aşağıdaki temel türlerden birine sahip bir tür: `byte` ,,, `sbyte` `short` `ushort` , `int` , veya `uint` .
- Başvuru türleri olarak bilinen genel tür parametreleri.
- <xref:System.IntPtr> ve <xref:System.UIntPtr>.

Ve dahil diğer türler `double` , `long` `volatile` Bu türlerin alanlarına okuma ve yazma işlemleri atomik olarak garanti edilmediği için işaretlenemiyor. Bu tür alanlara çok iş parçacıklı erişimi korumak için, <xref:System.Threading.Interlocked> sınıf üyelerini kullanın veya ifadesini kullanarak erişimi koruyun [`lock`](lock-statement.md) .

`volatile`Anahtar sözcüğü yalnızca bir veya alanlarına uygulanabilir `class` `struct` . Yerel değişkenler bildirilemez `volatile` .

## <a name="example"></a>Örnek

Aşağıdaki örnek, olarak bir ortak alan değişkeninin nasıl bildirilemeyeceğini gösterir `volatile` .

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

Aşağıdaki örnek, birincil iş parçacığından paralel olarak işleme gerçekleştirmek için bir yardımcı veya çalışan iş parçacığının nasıl oluşturulup kullanılabileceğini gösterir. Çoklu iş parçacığı hakkında daha fazla bilgi için bkz. [yönetilen Iş parçacığı](../../../standard/threading/index.md).

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

`volatile`Yerine gelen bildirimine eklenen değiştiriciyle `_shouldStop` , her zaman aynı sonuçları elde edersiniz (Yukarıdaki kodda gösterilen alıntıya benzer). Ancak, üye üzerinde bu değiştirici olmadan `_shouldStop` davranış tahmin edilemez. `DoWork`Yöntemi, üye erişimini iyileştirebilmenizi sağlayabilir ve bu da eski verilerin okunmasına yol açar. Çok iş parçacıklı programlama doğası nedeniyle, eski okuma sayısı tahmin edilemez. Programın farklı çalıştırmaları biraz farklı sonuçlar üretecektir.

## <a name="c-language-specification"></a>C# dili belirtimi

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Ayrıca bkz.

- [C# dil belirtimi: volatile anahtar sözcüğü](../../../../_csharplang/spec/classes.md#volatile-fields)
- [C# başvurusu](../index.md)
- [C# Programlama Kılavuzu](../../programming-guide/index.md)
- [C# anahtar sözcükleri](index.md)
- [Değiştiriciler](index.md)
- [Lock deyimleri](lock-statement.md)
- <xref:System.Threading.Interlocked>
