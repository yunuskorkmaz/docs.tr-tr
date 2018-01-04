---
title: "Tarih ve saatlerle aritmetik işlemler gerçekleştirme"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: edad8fc6643b90afc8327b574e19b178270829b3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="performing-arithmetic-operations-with-dates-and-times"></a>Tarih ve saatlerle aritmetik işlemler gerçekleştirme

Olsa da hem <xref:System.DateTime> ve <xref:System.DateTimeOffset> aritmetik işlemler sonuçlarını çok farklı olan, yapıları değerlerine aritmetik işlemler gerçekleştirme üyeleri belirtin. Bu konuda bu farklılıkları inceler, tarih ve saat verilerini saat dilimi tanıma derece ilgilidir ve tam olarak tarih ve saat verilerini kullanarak saat dilimi kullanan işlemlerini gerçekleştirmek nasıl ele alınmaktadır.

## <a name="comparisons-and-arithmetic-operations-with-datetime-values"></a>Karşılaştırmaları ve DateTime değerlerini içeren aritmetik işlemler

<xref:System.DateTime.Kind%2A?displayProperty=nameWithType> Özelliği sağlayan bir <xref:System.DateTimeKind> tarih ve saat yerel saat, Eşgüdümlü Evrensel Saat (UTC) veya belirtilmeyen bir saat dilimi süreyi temsil edip etmediğini göstermek için atanacak değer. Ancak, bu sınırlı saat dilimi bilgilerini karşılaştırma veya tarih ve saat aritmetiği üzerinde gerçekleştirme göz ardı edilir <xref:System.DateTimeKind> değerleri. Geçerli yerel saat geçerli UTC saati ile karşılaştırır, aşağıdaki örnekte bu gösterilmektedir.

[!code-csharp[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual2.cs#2)]
[!code-vb[System.DateTimeOffset.Conceptual#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual2.vb#2)]

<xref:System.DateTime.CompareTo%28System.DateTime%29> Yöntemi raporları yerel saat öncesi olduğunu (veya küçüktür) UTC saati ve çıkarma işlemi gösterir, UTC ve bir sistem için yerel saati arasındaki farkı ABD Pasifik Standart saat dilimi yedi saattir. Ancak bu iki değer zamanında tek bir noktadan farklı sunumu sağladığından, bu durumda bu zaman aralığı UTC yerel saat diliminin uzaklık tamamen önlemlerine temizleyin.

Genellikle daha <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik tarafından döndürülen sonuçlar etkilemez <xref:System.DateTime.Kind> karşılaştırma ve aritmetik yöntemleri (zaman içinde iki özdeş noktaları karşılaştırması da anlaşılacağı gibi), ancak bu sonuçlar yorumu etkileyebilir. Örneğin:

* İki tarih ve saat değerleri, tüm aritmetik işlemin sonucu olarak gerçekleştirilen <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellikleri her iki eşit <xref:System.DateTimeKind> iki değer arasındaki gerçek zaman aralığını yansıtır. Benzer şekilde, bu tür iki tarih ve saat değerleri karşılaştırma doğru şekilde zamanları arasında ilişki yansıtır.

* İki tarih ve saat değerleri, tüm aritmetik veya Karşılaştırma işleminin sonucu gerçekleştirilen <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellikleri her iki eşit <xref:System.DateTimeKind> veya farklı olan iki tarih ve saat değerleri <xref:System.DateTime.Kind%2A?displayProperty=nameWithType> özellik değerlerini saatin fark yansıtır iki değer arasında.

* Yerel tarih ve saat değerleri aritmetik veya karşılaştırma işlemleri belirli bir değeri belirsiz veya geçersiz ya da yerel saat diliminin geçiş ya da gün ışığından yararlanma neden herhangi ayarlama kuralları etkisini hesabı yararlanabilir mi olup olmadığını düşünün zaman kazandırır.

* Karşılaştırır veya UTC ve yerel saat arasındaki farkı hesaplar herhangi bir işlem sonucu UTC yerel saat diliminin uzaklık eşit bir zaman aralığı içerir.

* Karşılaştırır veya belirtilmeyen bir saat ve UTC veya yerel saat arasındaki farkı hesaplar herhangi bir işlem basit saatin yansıtır. Saat dilimi farkları değil olarak kabul edilir ve sonuç saat dilimi ayarlama kuralları uygulama yansıtmaz.

* Karşılaştırır veya iki arasındaki farkı hesaplar herhangi bir işlem süreleri, iki farklı saat diliminde saati arasındaki farkı yansıtır bilinmeyen bir aralık içerebilir belirtilmemiş.

Hangi saat diliminde farklar tarih ve saat hesaplamaları etkilemez birçok senaryo vardır (bunlardan bazıları, tartışma için bkz [DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md)) veya içine bağlamı Tarih ve saat veri karşılaştırma veya aritmetik işlemler anlamını tanımlar.

## <a name="comparisons-and-arithmetic-operations-with-datetimeoffset-values"></a>Karşılaştırmaları ve DateTimeOffset değerlerle aritmetik işlemler

A <xref:System.DateTimeOffset> değil yalnızca bir tarih ve saat, aynı zamanda bu tarih ve saat UTC'ye göre belirsizliğe tanımlayan bir uzaklık değeri içerir. Bu biraz farklı biçimde bir eşitlik için tanımlamanızı mümkün kılar <xref:System.DateTimeOffset> değerleri. Oysa <xref:System.DateTime> değerleri aynı tarih ve saat değeri varsa eşit olan <xref:System.DateTimeOffset> değerler her ikisi de aynı noktasına zamanında başvurursanız eşit. Böylece bir <xref:System.DateTimeOffset> değeri daha kesin ve küçük karşılaştırmaları ve iki tarih ve saat arasındaki aralığı belirlemek çoğu aritmetik işlemler kullanıldığında yorumlama gerekmektedir. Aşağıdaki örnek, <xref:System.DateTimeOffset> UTC ve yerel karşılaştırıldığında önceki örnek eşdeğer <xref:System.DateTimeOffset> değerlerini, davranış bu farklılık gösterir.

[!code-csharp[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual3.cs#3)]
[!code-vb[System.DateTimeOffset.Conceptual#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual3.vb#3)]

Bu örnekte, <xref:System.DateTimeOffset.CompareTo%2A> yöntemi gösterir geçerli yerel saat ve geçerli UTC saati olduğundan eşittir ve çıkarma, <xref:System.DateTimeOffset.CompareTo(System.DateTimeOffset)> değerlerini gösteren iki kez arasındaki fark olduğunu <xref:System.TimeSpan.Zero?displayProperty=nameWithType>.

Kullanmanın baş sınırlaması <xref:System.DateTimeOffset> tarih ve saat aritmetiği değerleri olduğundan, bu, ancak <xref:System.DateTimeOffset> değerlere sahip bazı saat dilimi tanıma, bunlar tam olarak saat dilimi farkında değildir. Ancak <xref:System.DateTimeOffset> değerinin uzaklığı yansıtır UTC saat diliminin uzaklığı olduğunda bir <xref:System.DateTimeOffset> değişken değeri ilk atandığı, saat dilimine bundan sonra ilişkilendirmesi haline gelir. Artık doğrudan tanımlanabilen bir saat ile ilişkili olduğundan, toplama ve çıkarma tarih ve saat aralığı dikkate almaz bir saat diliminin ayarlama kuralları.

Göstermek için gün ışığından yararlanma saati ABD geçişi Orta standart saat dilimi 2: 00'da gerçekleşir 9 Mart 2008'de. Bu, iki ve bir yarım saat aralığı 1: 30'da, Orta Standart Saati için ekleme anlamına gelir 9 Mart 2008'de bir tarih ve saat 5: 00'da, üretmesi gerekir 9 Mart 2008'de. Aşağıdaki örnekte gösterildiği gibi ancak ek 4: 00'da sonucudur 9 Mart 2008'de. Zaman içinde duyuyoruz ilgilenen saat diliminde olmasa da bu işlem bu sonucunu doğru noktası, zaman içindeki temsil Not (diğer bir deyişle, beklenen saat dilimi yok uzaklığı).

[!code-csharp[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual4.cs#4)]
[!code-vb[System.DateTimeOffset.Conceptual#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual4.vb#4)]

## <a name="arithmetic-operations-with-times-in-time-zones"></a>Saat dilimleri kez aritmetik işlemler

<xref:System.TimeZoneInfo> Sınıfı, bunlar zaman bir saat diliminden diğerine dönüştürme yükleyen ayarlamalar otomatik olarak Uygula dönüştürme yöntemleri sayısını içerir. Bunlar aşağıdakileri içerir:

* <xref:System.TimeZoneInfo.ConvertTime%2A> Ve <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A> saatleri herhangi iki saat dilimleri arasında dönüştürme yöntemleri.

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A> Ve <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A> belirli bir saat dilimi zamanında UTC'ye dönüştürmek veya belirli bir saat dilimi zamana UTC Dönüştürme yöntemleri.

Ayrıntılar için bkz [saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md).

<xref:System.TimeZoneInfo.ConvertTimeToUtc(System.DateTime)> Sınıfı, tarih ve saat aritmetiği gerçekleştirdiğinizde, otomatik olarak ayarlama kuralları geçerli herhangi bir yöntem sağlamaz. Ancak, sizin için UTC saati bir saat diliminde dönüştürülürken aritmetik işlemi gerçekleştiren ve saat dilimi zamanında dön UTC Dönüştürme bunu yapabilirsiniz. Ayrıntılar için bkz [nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md).

Örneğin, aşağıdaki kod iki-ve-a-yarım saat 2: 00'da için eklenen önceki kod benzer 9 Mart 2008'de. Ancak, tarih ve saat aritmetiği gerçekleştirir ve ardından sonucu geri Orta Standart Saati UTC dönüştürür önce UTC'ye Orta Standart Saati dönüştürmesi nedeniyle sonuçta elde edilen zaman Orta standart saat diliminin gün ışığından geçiş yansıtır süre.

[!code-csharp[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/cs/Conceptual5.cs#5)]
[!code-vb[System.DateTimeOffset.Conceptual#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.DateTimeOffset.Conceptual/vb/Conceptual5.vb#5)]

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md)
