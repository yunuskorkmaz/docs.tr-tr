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
ms.openlocfilehash: 2e668cf3f909ed4b89f05ca63dfe69051c1d9066
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122258"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Tarih ve saatlerle aritmetik işlemler gerçekleştirme

Hem <xref:System.DateTime> hem de <xref:System.DateTimeOffset> yapıları, değerleri üzerinde aritmetik işlemler gerçekleştiren Üyeler sağlamasına rağmen aritmetik işlemlerin sonuçları çok farklıdır. Bu konu, bu farklılıkları inceler, bunları tarih ve saat verilerinde zaman dilimi tanıma derecelerde ilişkilendirir ve Tarih ve saat verilerini kullanarak tam saat dilimi ile gerçekleştirilen işlemlerin nasıl gerçekleştirileceğini açıklar.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Tarih saat değerleri ile karşılaştırmalar ve aritmetik işlemler

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği, yerel saat, Eşgüdümlü Evrensel Saat (UTC) veya belirtilmemiş bir saat dilimindeki saati temsil edip etmediğini göstermek için bir <xref:System.DateTimeKind> değerinin tarih ve saate atanmasını sağlar. Ancak, <xref:System.DateTimeKind> değerlerinde tarih ve saat aritmetiği karşılaştırırken veya gerçekleştirilirken bu sınırlı saat dilimi bilgisi yok sayılır. Geçerli yerel saati geçerli UTC saatine göre karşılaştıran aşağıdaki örnek, bunu gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> yöntemi, yerel saatin UTC zamanından daha erken olduğunu bildirir ve çıkarma işlemi, ABD Pasifik standart saat dilimindeki bir sistemin UTC ve yerel saati arasındaki farkın yedi saat olduğunu gösterir. Ancak, bu iki değer tek bir noktaya ait farklı gösterimler sağladığından bu zaman aralığı, yerel saat diliminin UTC 'ye olan farkı ile tamamen aynı olur.

Daha genel olarak, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği <xref:System.DateTime.Kind> karşılaştırma ve aritmetik yöntemler tarafından döndürülen sonuçları etkilemez, ancak bu sonuçların yorumlanmasını etkileyebilse de, aynı zamanda iki özdeş noktasının karşılaştırılması gibi. Örneğin:

- İki tarih ve saat değerlerinde gerçekleştirilen her türlü aritmetik işlemin sonucu, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliklerinin ikisi de aynı <xref:System.DateTimeKind> iki değer arasındaki gerçek zaman aralığını yansıtır. Benzer şekilde, iki tarih ve saat değerinin karşılaştırılması saatler arasındaki ilişkiyi doğru bir şekilde yansıtır.

- İki tarih ve saat değeri <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellikleri, farklı <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerleri ile eşit <xref:System.DateTimeKind> veya iki tarih ve saat değeri üzerinde gerçekleştirilen herhangi bir aritmetik veya karşılaştırma işleminin sonucu, iki deðerler.

- Yerel Tarih ve saat değerlerinde aritmetik veya karşılaştırma işlemleri, belirli bir değerin belirsiz veya geçersiz olup olmadığını düşünmüyor ya da yerel saat diliminin günışığından veya tarihine kadar olan tüm ayarlama kurallarının etkisinin bir hesabını alırlar tasarruf süresi.

- UTC ve yerel bir saat arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, yerel saat diliminin, sonuçta UTC 'ye olan uzaklığa eşit bir zaman aralığı içerir.

- Belirtilmeyen bir saat ve UTC ya da yerel saat arasındaki farkı karşılaştıran veya hesaplayan tüm işlemler basit saat süresini yansıtır. Saat dilimi farklılıkları dikkate alınmamaktadır ve sonuç, saat dilimi ayarlama kurallarının uygulamasını yansıtmaz.

- İki belirtilmemiş zaman arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, iki farklı saat dilimindeki zaman arasındaki farkı yansıtan bilinmeyen bir Aralık içerebilir.

Zaman dilimi farklılıklarının tarih ve saat hesaplamalarını etkilemediği pek çok senaryo vardır (bunlardan bazılarının bir tartışması için, bkz. Tarih [saat, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md)) veya tarih ve saat verisi bağlamı karşılaştırma veya aritmetik işlemlerin anlamını tanımlar.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset değerleri ile karşılaştırmalar ve aritmetik işlemler

Bir <xref:System.DateTimeOffset> değeri yalnızca tarih ve saati değil, bu tarih ve saati UTC 'ye göre kesin bir şekilde tanımlayan bir uzaklıktan oluşur. Bu, <xref:System.DateTimeOffset> değerlerden farklı olarak eşitlik tanımlamanızı mümkün kılar. Aynı tarih ve saat değerine sahip olmaları durumunda <xref:System.DateTime> Değerler eşitse, her ikisi de aynı noktaya başvurduklarında, <xref:System.DateTimeOffset> değerleri eşittir. Bu, karşılaştırmalarda ve iki tarih ve saat arasındaki aralığı belirlemede en çok aritmetik işlemlerde bir <xref:System.DateTimeOffset> değerini daha doğru ve daha az bir hale getirir. Aşağıdaki örnek, yerel ve UTC <xref:System.DateTimeOffset> değerlerini karşılaştırmakta olan bir önceki örneğe eşdeğer <xref:System.DateTimeOffset>, bu farkı davranışa göre gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Bu örnekte <xref:System.DateTimeOffset.CompareTo%2A> yöntemi, geçerli yerel saatin ve geçerli UTC zamanının eşit olduğunu ve <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> değerlerinin çıkarılması iki kez arasındaki farkın <xref:System.TimeSpan.Zero?displayProperty=nameWithType>olduğunu gösterir.

Tarih ve saat aritmetiğinin <xref:System.DateTimeOffset> değerlerini kullanmanın bir sınırlaması, <xref:System.DateTimeOffset> değerlerinin bir saat dilimi tanıma sahip olmasına rağmen, tam saat dilimi farkında olmamasıdır. <xref:System.DateTimeOffset> değerin boşluğu, bir zaman diliminin UTC 'den sapmasını yansıtsa da, bir <xref:System.DateTimeOffset> değişkenine bir değer atandığında, bu, bundan sonra saat diliminden önce bir ilişkisi haline gelir. Artık tanınabilir bir süre ile doğrudan ilişkili olmadığından, tarih ve saat aralıklarının eklenmesi ve çıkarılması bir saat diliminin ayarlama kurallarını dikkate almaz.

Göstermek için, ABD Orta standart saat dilimindeki gün ışığından yararlanma saatine geçiş 2:00 saat ' de gerçekleşir. 9 Mart 2008 ' de. Bu, iki ve yarı saat aralığını 1:30 ' in orta standart saatine eklemek anlamına gelir. 9 Mart 2008 ' de, 5:00 ' de bir tarih ve saat üretilmesi gerekir 9 Mart 2008 ' de. Ancak, aşağıdaki örnekte gösterildiği gibi, eklemenin sonucu 4:00 ' dir. 9 Mart 2008 ' de. Bu işlemin sonucunun zaman içinde doğru noktayı temsil ettiğini, ancak ilgilendiğiniz saat dilimindeki zaman olmasa da (beklenen saat dilimi denketmesine sahip olmadığı) unutmayın.

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Zaman dilimlerinde zamanlarla aritmetik işlemler

<xref:System.TimeZoneInfo> sınıfı, zaman dilimini bir saat diliminden diğerine dönüştürtiklerinde otomatik olarak ayarlamaları uygulayan bir dizi dönüştürme yöntemi içerir. Bunlar aşağıdakileri içerir:

- İki saat dilimi arasında saat dönüştüren <xref:System.TimeZoneInfo.ConvertTime%2A> ve <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> yöntemleri.

- Belirli bir saat dilimindeki saati UTC 'ye dönüştüren ve UTC 'yi belirli bir saat dilimindeki zamana dönüştüren <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> ve <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> yöntemleri.

Ayrıntılar için bkz. [saat dilimleri arasında süreleri dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> sınıfı, tarih ve saat aritmetiği gerçekleştirirken ayarlama kurallarını otomatik olarak uygulayan herhangi bir yöntem sağlamaz. Bununla birlikte, bir saat dilimindeki saati UTC 'ye dönüştürerek, aritmetik işlemi gerçekleştirerek ve UTC 'den saat diliminizdeki zamana doğru dönüştürmeden bunu yapabilirsiniz. Ayrıntılar için bkz. [nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Örneğin, aşağıdaki kod, 2:00 ve 2 ' ye iki-a-yarı saat ekleyen önceki koda benzer. 9 Mart 2008 ' de. Bununla birlikte, tarih ve saat aritmetiği yapmadan önce bir merkezi standart saati UTC 'ye dönüştürdüğünden ve sonucu UTC 'den standart saate dönüştürdüğünde, sonuçta elde edilen süre, merkezi standart saat diliminin günışığından yararlanma 'a geçişini yansıtır ışınızda.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
