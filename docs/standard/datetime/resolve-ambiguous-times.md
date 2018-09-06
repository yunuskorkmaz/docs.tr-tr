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
ms.openlocfilehash: eb09b1f087e0a0f726d32d85e06cfb2a9ec741a8
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863140"
---
# <a name="how-to-resolve-ambiguous-times"></a>Nasıl yapılır: belirsiz saatleri çözme

Belirsiz bir saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleyen bir zamandır. Saatin geri sürede gibi standart saati kendi saat diliminin gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur. Belirsiz bir saat işlerken, aşağıdakilerden birini yapabilirsiniz:

* Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız. Örneğin, belirsiz bir süre içinde saat diliminin standart saat her zaman gösterilir varsayabilirsiniz.

* Bir öğenin kullanıcı tarafından girilen veriler belirsiz saat ise belirsizliği çözmek için kullanıcıya bırakabilirsiniz.

Bu konuda, saat diliminin standart saati temsil ettiği varsayarak belirsiz bir saat olarak çözmek gösterilmektedir.

### <a name="to-map-an-ambiguous-time-to-a-time-zones-standard-time"></a>Bir saat diliminin Standart Saati için belirsiz bir saat eşlemek için

1. Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntemi.

2. Belirsiz saat ise, saatten çıkar <xref:System.TimeSpan> saat diliminin tarafından döndürülen nesne <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği.

3. Çağrı `static` (`Shared` Visual Basic. NET'te) <xref:System.DateTime.SpecifyKind%2A> UTC tarih ve saat değerinin ayarlanacak yöntemi <xref:System.DateTime.Kind%2A> özelliğini <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnek, yerel saat diliminin standart saati temsil ettiği varsayarak belirsiz bir saat UTC'ye göre dönüştürmek gösterilmektedir.

[!code-csharp[System.TimeZone2.Concepts#10](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#10)]
[!code-vb[System.TimeZone2.Concepts#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#10)]

Örnek adlı bir yöntemi oluşur `ResolveAmbiguousTime` belirleyen olmadığını <xref:System.DateTime> geçirilen değer belirsiz. Değeri belirsiz ise yöntem döndürür bir <xref:System.DateTime> karşılık gelen UTC saati gösteren bir değer. Yerel saat diliminin değerini çıkararak bu dönüştürme yöntemi işleme <xref:System.TimeZoneInfo.BaseUtcOffset%2A> yerel saatinden özelliği.

Normalde, belirsiz bir saat çağrılarak gerçekleştirilir <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemi <xref:System.TimeSpan> olası belirsiz saatin UTC içeren nesneleri kaydırır. Ancak, bu örnek, belirsiz bir saat saat diliminin Standart Saati için her zaman eşlenmelidir rastgele bir varsayım yapmaz. <xref:System.TimeZoneInfo.BaseUtcOffset%2A> Özelliği, saat diliminin Standart Saati ile UTC arasındaki uzaklığı döndürür.

Bu örnekte, yerel saat dilimi için tüm başvuruları aracılığıyla yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği; yerel saati dilimi hiçbir zaman bir nesne değişkenine atanır. Bunun nedeni önerilen uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> metodu geçersiz kılar, yerel saat dilimi atandığı herhangi bir nesne.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Projeye System.Core.dll öğesine başvuru eklenmesi gerektiğini.

* Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
* [Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin verme](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md)
