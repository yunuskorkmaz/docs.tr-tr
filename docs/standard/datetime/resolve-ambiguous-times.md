---
title: 'Nasıl yapılır: Belirsiz saatleri çözme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
ms.openlocfilehash: ad69c0984a9d8c01ebd2198486cd0f6492a6116e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281511"
---
# <a name="how-to-resolve-ambiguous-times"></a>Nasıl yapılır: Belirsiz saatleri çözme

Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:

- Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın. Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.

- Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.

Bu konuda, saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın nasıl çözümleneceği gösterilmektedir.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Belirsiz bir süreyi saat diliminin standart saatine eşlemek için

1. <xref:System.TimeZoneInfo.IsAmbiguousTime%2A>Saatin belirsiz olup olmadığını anlamak için yöntemini çağırın.

2. Zaman belirsiz ise, saat <xref:System.TimeSpan> dilimi özelliği tarafından döndürülen nesneden saati çıkarın <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .

3. `static` `Shared` <xref:System.DateTime.SpecifyKind%2A> UTC Tarih ve saat değerinin özelliğini olarak ayarlamak için (Visual Basic .net) metodunu çağırın <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel saat diliminin standart saatini temsil ettiğini varsayarak belirsiz bir zamanın UTC 'ye nasıl dönüştürüleceğini gösterir.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Örnek, `ResolveAmbiguousTime` geçirilen değerin belirsiz olup olmadığını belirleyen adlı bir yöntemden oluşur <xref:System.DateTime> . Değer belirsiz ise, yöntemi <xref:System.DateTime> karşılık gelen UTC zamanını temsil eden bir değer döndürür. Yöntemi, yerel saat dilimi özelliğinin değerini yerel saatten çıkararak bu dönüştürmeyi işler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> .

Normalde belirsiz bir zaman, <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> <xref:System.TimeSpan> belirsiz zamanın olası UTC uzaklıklarını içeren bir nesne dizisini almak için yöntemini çağırarak işlenir. Ancak bu örnek, belirsiz bir saatin, her zaman saat diliminin standart saatine eşlenmesi gereken rastgele varsayımını yapar. <xref:System.TimeZoneInfo.BaseUtcOffset%2A>ÖZELLIĞI UTC ve saat diliminin standart saati arasındaki sapmayı döndürür.

Bu örnekte, yerel saat dilimine yapılan tüm başvurular özelliği aracılığıyla yapılır <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz. Bu önerilen bir uygulamadır çünkü yöntemine yapılan bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> , yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver](let-users-resolve-ambiguous-times.md)
