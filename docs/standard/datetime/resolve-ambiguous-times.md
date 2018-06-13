---
title: 'Nasıl yapılır: belirsiz saatleri çözme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: 2cf5fb25-492c-4875-9245-98cac8348e97
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a92081a164d15e5150c582b37c6c688cd15e619e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33571205"
---
# <a name="how-to-resolve-ambiguous-times"></a>Nasıl yapılır: belirsiz saatleri çözme

Belirsiz saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleşen bir zamandır. Saatin geçmişe, gibi standart saati bir saat diliminin gün ışığından yararlanma saati geçiş sırasında ayarlanır oluşur. Belirsiz saat işlerken, aşağıdakilerden birini yapabilirsiniz:

* Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız. Örneğin, belirsiz bir süre içinde saat diliminin Standart Saati her zaman gösterilir varsayabilirsiniz.

* Belirsiz saat öğenin kullanıcı tarafından girilen verilerin ise, karışıklığı çözmek için kullanıcıya bırakabilirsiniz.

Bu konu, saat diliminin standart saati temsil eden varsayılarak tarafından belirsiz bir süre çözmek gösterilmektedir.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Belirsiz saat saat diliminin Standart Saati için eşlemek için

1. Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntem.

2. Saat belirsiz ise zamandan çıkarma <xref:System.TimeSpan> saat diliminin tarafından döndürülen nesne <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği.

3. Çağrı `static` (`Shared` Visual Basic .NET içinde) <xref:System.DateTime.SpecifyKind%2A> UTC tarihi ve saati değer ayarlamak için yöntemin <xref:System.DateTime.Kind%2A> özelliğine <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel saat diliminin standart saati temsil eden varsayılarak belirsiz bir süre UTC tarafından nasıl dönüştürüleceği gösterilmektedir.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Adlı bir yöntemi örnek oluşur `ResolveAmbiguousTime` belirleyen olup olmadığını <xref:System.DateTime> kendisine geçirilen değerdir belirsiz. Değeri belirsiz ise, yöntem bir <xref:System.DateTime> karşılık gelen UTC saati gösteren bir değer. Yerel saat diliminin değerini çıkararak bu dönüştürme yöntemi işler <xref:System.TimeZoneInfo.BaseUtcOffset%2A> yerel saat özelliğinden.

Belirsiz saat çağırarak normalde, işlenen <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemini <xref:System.TimeSpan> belirsiz zaman olası UTC içeren nesneleri kaydırır. Ancak, bu örnek belirsiz bir saat, saat diliminin Standart Saati için her zaman eşlenmelidir rasgele varsayım yapmaz. <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Özelliği UTC ve saat diliminin standart saat uzaklığı döndürür.

Bu örnekte, yerel saat dilimine yönelik tüm başvuruları üzerinden yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özellik; bölge için bir nesne değişkeninin hiçbir zaman atanmış yerel saat. Bunun nedeni önerilen bir uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi yerel saat dilimini atandığı herhangi bir nesne geçersiz kılar.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: kullanıcıların belirsiz saatleri çözmek olanak tanır](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
