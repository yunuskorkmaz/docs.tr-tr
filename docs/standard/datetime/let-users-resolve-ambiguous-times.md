---
title: 'Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver'
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
ms.openlocfilehash: ac723738d80a2f686a5fcaf279cec791b3c58619
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84281589"
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver

Belirsiz bir zaman, birden fazla Eşgüdümlü Evrensel Saat (UTC) ile eşleşen bir süredir. Saat diliminin gün ışığından yararlanma saatinden standart saate geçiş sırasında olduğu gibi saat içinde saat olarak ayarlandığında meydana gelir. Belirsiz bir süre işlenirken aşağıdakilerden birini yapabilirsiniz:

- Belirsiz saat Kullanıcı tarafından girilen bir veri öğesi ise, belirsizliği çözümlemek için bunu kullanıcıya bırakabilirsiniz.

- Saatin UTC 'ye nasıl eşlendiğini varsayımını unutmayın. Örneğin, saat diliminin standart saatinde belirsiz bir zamanın her zaman ifade edildiği varsayıladır.

Bu konu başlığı altında, kullanıcının belirsiz bir süre çözümlenme yöntemi gösterilmektedir.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Kullanıcının belirsiz bir süre çözmesine izin vermek için

1. Kullanıcı tarafından tarih ve saat girişi al.

2. <xref:System.TimeZoneInfo.IsAmbiguousTime%2A>Saatin belirsiz olup olmadığını anlamak için yöntemini çağırın.

3. Süre belirsizse, <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> nesne dizisini almak için yöntemini çağırın <xref:System.TimeSpan> . Dizideki her öğe, belirsiz saatin eşleyebileceğiniz UTC sapmasını içerir.

4. Kullanıcının istenen sapmayı seçmesini sağlayın.

5. Kullanıcı tarafından seçilen sapmayı yerel saatten çıkararak UTC Tarih ve saatini elde edin.

6. `static` `Shared` <xref:System.DateTime.SpecifyKind%2A> UTC Tarih ve saat değerinin özelliğini olarak ayarlamak için (Visual Basic .net) metodunu çağırın <xref:System.DateTime.Kind%2A> <xref:System.DateTimeKind.Utc?displayProperty=nameWithType> .

## <a name="example"></a>Örnek

Aşağıdaki örnek, kullanıcıdan bir tarih ve saat girmesini ister ve belirsiz ise kullanıcının belirsiz saatin eşlendiği UTC saatini seçmesini sağlar.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Örnek kodun çekirdeği, <xref:System.TimeSpan> UTC 'den belirsiz sürenin olası uzaklıklarını göstermek için bir nesne dizisi kullanır. Ancak, bu uzaklıklar Kullanıcı için anlamlı değildir. Kaydırmanın anlamını netleştirmek için, kod ayrıca bir uzaklığın yerel saat diliminin standart saatini mi yoksa gün ışığından yararlanma saatini mi temsil ettiğini de not eder. Kod, değeri özelliğin değeriyle karşılaştırarak hangi zamanın standart olduğunu ve ne zaman günışığından yararlanma olduğunu belirler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> . Bu özellik UTC ve saat diliminin standart saati arasındaki farkı gösterir.

Bu örnekte, yerel saat dilimine yapılan tüm başvurular özelliği aracılığıyla yapılır <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ; Yerel Saat dilimi hiçbir zaman bir nesne değişkenine atanmaz. Bu önerilen bir uygulamadır çünkü yöntemine yapılan bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> , yerel saat diliminin atandığı tüm nesneleri geçersiz kılar.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek şunları gerektirir:

- Bu <xref:System> ad alanı ifadesiyle içeri aktarılmalıdır `using` (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Nasıl yapılır: Belirsiz saatleri çözme](resolve-ambiguous-times.md)
