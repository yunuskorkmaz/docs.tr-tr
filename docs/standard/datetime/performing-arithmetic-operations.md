---
title: Tarih ve saatlerle aritmetik işlemler gerçekleştirme
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- times [.NET Framework], arithmetic operations
- dates [.NET Framework], arithmetic operations
- time zones [.NET Framework], arithmetic operations
- arithmetic operations [.NET Framework], dates and times
- dates [.NET Framework], comparing
- DateTime structure, arithmetic operations
- DateTimeOffset structure, arithmetic operations
ms.assetid: 87c7ddf2-f15e-48af-8602-b3642237e6d0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 01314c160fc531f5c97a1369c8444dce7f590d53
ms.sourcegitcommit: 6f28b709592503d27077b16fff2e2eacca569992
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/28/2019
ms.locfileid: "70106608"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Tarih ve saatlerle aritmetik işlemler gerçekleştirme

Hem hem de <xref:System.DateTime> <xref:System.DateTimeOffset> yapıları, değerleri üzerinde aritmetik işlemler gerçekleştiren Üyeler sağlamasına rağmen aritmetik işlemlerin sonuçları çok farklıdır. Bu konu, bu farklılıkları inceler, bunları tarih ve saat verilerinde zaman dilimi tanıma derecelerde ilişkilendirir ve Tarih ve saat verilerini kullanarak tam saat dilimi ile gerçekleştirilen işlemlerin nasıl gerçekleştirileceğini açıklar.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Tarih saat değerleri ile karşılaştırmalar ve aritmetik işlemler

Özelliği yerel saati, <xref:System.DateTimeKind> Eşgüdümlü Evrensel saati (UTC) veya belirtilmeyen bir saat dilimindeki saati temsil edip etmediğini göstermek için bir değerin tarih ve saate atanmasını sağlar. <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Ancak, değerler üzerinde <xref:System.DateTimeKind> tarih ve saat aritmetiği karşılaştırırken veya gerçekleştirilirken bu sınırlı saat dilimi bilgisi yok sayılır. Geçerli yerel saati geçerli UTC saatine göre karşılaştıran aşağıdaki örnek, bunu gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Yöntemi, yerel saatin UTC saatinden (veya ondan küçüktür) daha eski olduğunu bildiriyor ve çıkarma işlemi, ABD 'deki bir sistem için UTC ve yerel saat arasındaki farkı gösterir Pasifik standart saat dilimi yedi saattir. Ancak, bu iki değer tek bir noktaya ait farklı gösterimler sağladığından bu zaman aralığı, yerel saat diliminin UTC 'ye olan farkı ile tamamen aynı olur.

Daha genel olarak, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği karşılaştırma ve aritmetik yöntemler tarafından <xref:System.DateTime.Kind> döndürülen sonuçları etkilemez (aynı zamanda iki özdeş noktasının karşılaştırılmasının yanı sıra, bu sonuçların yorumunu etkileyebilse de). Örneğin:

- İki tarih ve saat değeri üzerinde gerçekleştirilen herhangi bir aritmetik işlemin sonucu, özelliklerinin <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> ikisi de eşit <xref:System.DateTimeKind> olan iki değer arasındaki gerçek zaman aralığını yansıtır. Benzer şekilde, iki tarih ve saat değerinin karşılaştırılması saatler arasındaki ilişkiyi doğru bir şekilde yansıtır.

- İki tarih ve saat değeri <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> üzerinde gerçekleştirilen her türlü aritmetik veya karşılaştırma işleminin sonucu, her ikisi de farklı <xref:System.DateTimeKind> <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerlerine eşit veya iki tarih ve saat değerleri, saat cinsinden farkı yansıtır iki değer arasında.

- Yerel Tarih ve saat değerlerinde aritmetik veya karşılaştırma işlemleri, belirli bir değerin belirsiz veya geçersiz olup olmadığını düşünmüyor ya da yerel saat diliminin günışığından veya tarihine kadar olan tüm ayarlama kurallarının etkisinin bir hesabını alırlar tasarruf süresi.

- UTC ve yerel bir saat arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, yerel saat diliminin, sonuçta UTC 'ye olan uzaklığa eşit bir zaman aralığı içerir.

- Belirtilmeyen bir saat ve UTC ya da yerel saat arasındaki farkı karşılaştıran veya hesaplayan tüm işlemler basit saat süresini yansıtır. Saat dilimi farklılıkları dikkate alınmamaktadır ve sonuç, saat dilimi ayarlama kurallarının uygulamasını yansıtmaz.

- İki belirtilmemiş zaman arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, iki farklı saat dilimindeki zaman arasındaki farkı yansıtan bilinmeyen bir Aralık içerebilir.

Zaman dilimi farklılıklarının tarih ve saat hesaplamalarını etkilemediği pek çok senaryo vardır (bunlardan bazılarının bir tartışması için, bkz. Tarih [saat, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md)) veya tarih ve saat verisi bağlamı karşılaştırma veya aritmetik işlemlerin anlamını tanımlar.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset değerleri ile karşılaştırmalar ve aritmetik işlemler

Bir <xref:System.DateTimeOffset> değer yalnızca bir tarih ve saat değil, bu tarih ve saati UTC 'ye göre kesin bir şekilde tanımlayan bir uzaklıktan oluşur. Bu, eşitlik ' ın <xref:System.DateTimeOffset> değerlere göre biraz farklı şekilde tanımlanması mümkün olur. Aynı tarih ve saat değerine sahip olmaları durumunda <xref:System.DateTimeOffset> Değerlereşitse,herikisideaynınoktayabaşvurduklarındadeğerlereşittir.<xref:System.DateTime> Bu, karşılaştırmalarda ve iki tarih ve saat arasındaki aralığı belirlemede en çok aritmetik işlemlerde bir değer daha doğru ve daha az bir <xref:System.DateTimeOffset> değer sağlar. Aşağıdaki örnek, <xref:System.DateTimeOffset> yerel ve UTC <xref:System.DateTimeOffset> değerlerini karşılaştırmakta olan bir önceki örneğe eşdeğerdir, bu farkı davranışa göre gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Bu örnekte, <xref:System.DateTimeOffset.CompareTo%2A> yöntemi geçerli yerel saatin ve geçerli UTC zamanının eşit olduğunu ve <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> değerlerin çıkarılması iki kez <xref:System.TimeSpan.Zero?displayProperty=nameWithType>arasındaki farkın olduğunu gösterir.

Tarih ve saat aritmetiği içindeki <xref:System.DateTimeOffset> değerlerin kullanılması, değerlerin bir saat dilimi tanıma sahip <xref:System.DateTimeOffset> olmasına rağmen, bu değerler tam zaman dilimi farkında değildir. Değerin boşluğu <xref:System.DateTimeOffset> , bir <xref:System.DateTimeOffset> değişken ilk olarak bir değere atandığında bir zaman diliminin UTC 'den sapmasını yansıtmasına karşın, bundan sonra saat diliminden bir ilişkisi olur. Artık tanınabilir bir süre ile doğrudan ilişkili olmadığından, tarih ve saat aralıklarının eklenmesi ve çıkarılması bir saat diliminin ayarlama kurallarını dikkate almaz.

Göstermek için ABD 'de yaz saati kaydetme zamanına geçiş Merkezi Standart saat dilimi 2:00 saat içinde gerçekleşir 9 Mart 2008 ' de. Bu, iki ve yarı saat aralığını 1:30 ' in orta standart saatine eklemek anlamına gelir. 9 Mart 2008 ' de, 5:00 ' de bir tarih ve saat üretilmesi gerekir 9 Mart 2008 ' de. Ancak, aşağıdaki örnekte gösterildiği gibi, eklemenin sonucu 4:00 ' dir. 9 Mart 2008 ' de. Bu işlemin sonucunun zaman içinde doğru noktayı temsil ettiğini, ancak ilgilendiğiniz saat dilimindeki zaman olmasa da (beklenen saat dilimi denketmesine sahip olmadığı) unutmayın.

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Zaman dilimlerinde zamanlarla aritmetik işlemler

Sınıfı <xref:System.TimeZoneInfo> , saatleri bir saat diliminden diğerine dönüştürtiklerinde otomatik olarak ayarlamaları uygulayan bir dizi dönüştürme yöntemi içerir. Bunlar aşağıdakileri içerir:

- İki saat <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> dilimi arasında saat dönüştüren veyöntemleri.<xref:System.TimeZoneInfo.ConvertTime%2A>

- Ve belirli <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> bir saat dilimindeki saati UTC 'ye dönüştüren veya UTC 'yi belirli bir saat dilimindeki zamana dönüştüren ve yöntemleri. <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>

Ayrıntılar için bkz. [saat dilimleri arasında süreleri dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md).

Sınıfı <xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> , tarih ve saat aritmetiği gerçekleştirirken ayarlama kurallarını otomatik olarak uygulayan herhangi bir yöntem sağlamaz. Bununla birlikte, bir saat dilimindeki saati UTC 'ye dönüştürerek, aritmetik işlemi gerçekleştirerek ve UTC 'den saat diliminizdeki zamana doğru dönüştürmeden bunu yapabilirsiniz. Ayrıntılar için bkz [. nasıl yapılır: Tarih ve Saat Aritmetiğinde](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)saat dilimlerini kullanın.

Örneğin, aşağıdaki kod, 2:00 ve 2 ' ye iki-a-yarı saat ekleyen önceki koda benzer. 9 Mart 2008 ' de. Bununla birlikte, tarih ve saat aritmetiği yapmadan önce bir merkezi standart saati UTC 'ye dönüştürdüğünden ve sonucu UTC 'den standart saate dönüştürdüğünde, sonuçta elde edilen süre, merkezi standart saat diliminin günışığından yararlanma 'a geçişini yansıtır ışınızda.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
