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
ms.openlocfilehash: c212397f99bd09195f298d7d704c879705b14f02
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281550"
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Tarih ve saatlerle aritmetik işlemler gerçekleştirme

Hem hem de <xref:System.DateTime> yapıları, <xref:System.DateTimeOffset> değerleri üzerinde aritmetik işlemler gerçekleştiren Üyeler sağlamasına rağmen aritmetik işlemlerin sonuçları çok farklıdır. Bu konu, bu farklılıkları inceler, bunları tarih ve saat verilerinde zaman dilimi tanıma derecelerde ilişkilendirir ve Tarih ve saat verilerini kullanarak tam saat dilimi ile gerçekleştirilen işlemlerin nasıl gerçekleştirileceğini açıklar.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Tarih saat değerleri ile karşılaştırmalar ve aritmetik işlemler

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType>Özelliği <xref:System.DateTimeKind> yerel saati, Eşgüdümlü Evrensel saatı (UTC) veya belirtilmeyen bir saat dilimindeki saati temsil edip etmediğini göstermek için bir değerin tarih ve saate atanmasını sağlar. Ancak, değerler üzerinde tarih ve saat aritmetiği karşılaştırırken veya gerçekleştirilirken bu sınırlı saat dilimi bilgisi yok sayılır <xref:System.DateTimeKind> . Geçerli yerel saati geçerli UTC saatine göre karşılaştıran aşağıdaki örnek, bunu gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29>Yöntemi, yerel saatın UTC zamanından daha erken olduğunu ve çıkarma işlemi, ABD Pasifik standart saat dilimindeki bir SISTEMIN UTC ve yerel saati arasındaki farkın yedi saat olduğunu bildirir. Ancak, bu iki değer tek bir noktanın farklı temsillerini sağladığından, bu durum, zaman aralığının UTC 'den yerel saat dilimine göre tam olarak ayrıştırılacağı bu durumda net bir durumdur.

Daha genel olarak, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliği <xref:System.DateTime.Kind> karşılaştırma ve aritmetik yöntemler tarafından döndürülen sonuçları etkilemez (aynı zamanda iki özdeş noktasının karşılaştırılmasının yanı sıra, bu sonuçların yorumunu etkileyebilse de). Örneğin:

- İki tarih ve saat değeri üzerinde gerçekleştirilen herhangi bir aritmetik işlemin sonucu, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özelliklerinin ikisi de eşit olan <xref:System.DateTimeKind> iki değer arasındaki gerçek zaman aralığını yansıtır. Benzer şekilde, iki tarih ve saat değerinin karşılaştırılması saatler arasındaki ilişkiyi doğru bir şekilde yansıtır.

- İki tarih ve saat değeri, özellikleri aynı ve iki tarih ve saat değeri olan iki tarih ve saat değeri üzerinde gerçekleştirilen herhangi bir aritmetik veya karşılaştırma işleminin sonucu, <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> <xref:System.DateTimeKind> <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> iki değer arasındaki saat saat farkını yansıtır.

- Yerel Tarih ve saat değerlerinde aritmetik veya karşılaştırma işlemleri, belirli bir değerin belirsiz veya geçersiz olup olmadığını düşünmüyor ya da yerel saat dilimi geçişinin yaz saati veya tarihine kadar olan geçiş kurallarından kaynaklanan ayarlama kurallarının etkisinin bir hesabını alırlar.

- UTC ve yerel bir saat arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, yerel saat diliminin, sonuçta UTC 'ye olan uzaklığa eşit bir zaman aralığı içerir.

- Belirtilmeyen bir saat ve UTC ya da yerel saat arasındaki farkı karşılaştıran veya hesaplayan tüm işlemler basit saat süresini yansıtır. Saat dilimi farklılıkları dikkate alınmamaktadır ve sonuç, saat dilimi ayarlama kurallarının uygulamasını yansıtmaz.

- İki belirtilmemiş zaman arasındaki farkı karşılaştıran veya hesaplayan herhangi bir işlem, iki farklı saat dilimindeki zaman arasındaki farkı yansıtan bilinmeyen bir Aralık içerebilir.

Zaman dilimi farklılıklarının tarih ve saat hesaplamalarını etkilemediği birçok senaryo vardır (bunlardan bazılarının bir tartışması için bkz. Tarih [saat, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](choosing-between-datetime.md)) veya tarih ve saat verilerinin içeriğinin karşılaştırma veya aritmetik işlemlerin anlamını tanımladığı.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>DateTimeOffset değerleri ile karşılaştırmalar ve aritmetik işlemler

Bir <xref:System.DateTimeOffset> değer yalnızca bir tarih ve saat değil, bu tarih ve saatı UTC 'ye göre kesin bir şekilde tanımlayan bir uzaklıktan oluşur. Bu, eşitlik ' ın değerlere göre biraz farklı şekilde tanımlanması mümkün olur <xref:System.DateTimeOffset> . <xref:System.DateTime>Aynı tarih ve saat değerine sahip olmaları durumunda Değerler eşitse, <xref:System.DateTimeOffset> her ikisi de aynı noktaya başvurduklarında değerler eşittir. Bu <xref:System.DateTimeOffset> , karşılaştırmalarda ve iki tarih ve saat arasındaki aralığı belirlemede en çok aritmetik işlemlerde bir değer daha doğru ve daha az bir değer sağlar. Aşağıdaki örnek, <xref:System.DateTimeOffset> yerel ve UTC değerlerini karşılaştırmakta olan bir önceki örneğe eşdeğerdir <xref:System.DateTimeOffset> , bu farkı davranışa göre gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Bu örnekte, <xref:System.DateTimeOffset.CompareTo%2A> yöntemi geçerli yerel saatin ve geçerlI UTC zamanının eşit olduğunu ve <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> değerlerin çıkarılması iki kez arasındaki farkın olduğunu gösterir <xref:System.TimeSpan.Zero?displayProperty=nameWithType> .

<xref:System.DateTimeOffset>Tarih ve saat aritmetiği içindeki değerlerin kullanılması, <xref:System.DateTimeOffset> değerlerin bir saat dilimi tanıma sahip olmasına rağmen, bu değerler tam zaman dilimi farkında değildir. <xref:System.DateTimeOffset>Değerin boşluğu, bir değişken ilk olarak bir değere atandığında bir zaman DILIMININ UTC 'den sapmasını yansıtmasına karşın <xref:System.DateTimeOffset> , bundan sonra saat diliminden bir ilişkisi olur. Artık tanınabilir bir süre ile doğrudan ilişkili olmadığından, tarih ve saat aralıklarının eklenmesi ve çıkarılması bir saat diliminin ayarlama kurallarını dikkate almaz.

Göstermek için, ABD Orta standart saat dilimindeki gün ışığından yararlanma saatine geçiş 2:00 saat ' de gerçekleşir. 9 Mart 2008 ' de. Bu, iki ve yarı saat aralığını 1:30 ' in orta standart saatine eklemek anlamına gelir. 9 Mart 2008 ' de, 5:00 ' de bir tarih ve saat üretilmesi gerekir 9 Mart 2008 ' de. Ancak, aşağıdaki örnekte gösterildiği gibi, eklemenin sonucu 4:00 ' dir. 9 Mart 2008 ' de. Bu işlemin sonucunun zaman içinde doğru noktayı temsil ettiğini, ancak ilgilendiğiniz saat dilimindeki zaman olmasa da (beklenen saat dilimi denketmesine sahip olmadığı) unutmayın.

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Zaman dilimlerinde zamanlarla aritmetik işlemler

<xref:System.TimeZoneInfo>Sınıfı, saatleri bir saat diliminden diğerine dönüştürtiklerinde otomatik olarak ayarlamaları uygulayan bir dizi dönüştürme yöntemi içerir. Bunlar aşağıdakileri içerir:

- <xref:System.TimeZoneInfo.ConvertTime%2A> <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> İki saat dilimi arasında saat dönüştüren ve yöntemleri.

- <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>Ve <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> belirli bir saat DILIMINDEKI saati UTC 'ye dönüştüren veya UTC 'yi belirli bir saat dilimindeki zamana dönüştüren ve yöntemleri.

Ayrıntılar için bkz. [saat dilimleri arasında süreleri dönüştürme](converting-between-time-zones.md).

<xref:System.TimeZoneInfo>Sınıfı, tarih ve saat aritmetiği gerçekleştirirken ayarlama kurallarını otomatik olarak uygulayan herhangi bir yöntem sağlamaz. Bununla birlikte, bir saat dilimindeki saati UTC 'ye dönüştürerek, aritmetik işlemi gerçekleştirerek ve UTC 'den saat diliminizdeki zamana doğru dönüştürmeden bunu yapabilirsiniz. Ayrıntılar için bkz. [nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](use-time-zones-in-arithmetic.md).

Örneğin, aşağıdaki kod, 2:00 ve 2 ' ye iki-a-yarı saat ekleyen önceki koda benzer. 9 Mart 2008 ' de. Bununla birlikte, tarih ve saat aritmetiği yapmadan önce bir merkezi standart saati UTC 'ye dönüştürdüğünden ve sonucu UTC 'den standart saate dönüştürdüğünde, sonuçta elde edilen süre, merkezi standart saat diliminin yaz saati saatine geçişini yansıtır.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma](use-time-zones-in-arithmetic.md)
