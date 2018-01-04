---
title: "Nasıl yapılır: kullanıcıların belirsiz saatleri çözmek olanak tanır"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], ambiguous time
- ambiguous time [.NET Framework]
ms.assetid: bca874ee-5b68-4654-8bbd-3711220ef332
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d0122ca1469b32692fa9c4ef2bd37cda39622bd7
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-let-users-resolve-ambiguous-times"></a>Nasıl yapılır: kullanıcıların belirsiz saatleri çözmek olanak tanır

Belirsiz saat birden fazla Eşgüdümlü Evrensel Saat (UTC için) eşleşen bir zamandır. Saatin geçmişe, gibi standart saati bir saat diliminin gün ışığından yararlanma saati geçiş sırasında ayarlanır oluşur. Belirsiz saat işlerken, aşağıdakilerden birini yapabilirsiniz:

* Belirsiz saat öğenin kullanıcı tarafından girilen verilerin ise, karışıklığı çözmek için kullanıcıya bırakabilirsiniz.

* Saat UTC'ye nasıl eşlendiğini hakkında bir olduğu varsayımını yaparsınız. Örneğin, belirsiz bir süre içinde saat diliminin Standart Saati her zaman gösterilir varsayabilirsiniz.

Bu konuda belirsiz bir zamana çözmek bir kullanıcının olanak gösterilmektedir.

### <a name="to-let-a-user-resolve-an-ambiguous-time"></a>Belirsiz saat çözmek kullanıcı izin vermek için

1. Tarih ve saat tarafından kullanıcı girişi alın.

2. Çağrı <xref:System.TimeZoneInfo.IsAmbiguousTime%2A> zaman belirsiz olup olmadığını belirlemek için yöntem.

3. Saat belirsiz ise çağrı <xref:System.TimeZoneInfo.GetAmbiguousTimeOffsets%2A> dizisini almak için yöntemini <xref:System.TimeSpan> nesneleri. Dizideki her öğe belirsiz saat eşleyebilirsiniz UTC uzaklık içerir.

4. Kullanıcı Seç istenen uzaklık olanak tanır.

5. UTC tarihi ve saati yerel saate kullanıcı tarafından seçilen uzaklığı çıkarılmasıyla alın.

6. Çağrı `static` (`Shared` Visual Basic .NET içinde) <xref:System.DateTime.SpecifyKind%2A> UTC tarihi ve saati değer ayarlamak için yöntemin <xref:System.DateTime.Kind%2A> özelliğine <xref:System.DateTimeKind.Utc?displayProperty=nameWithType>.

## <a name="example"></a>Örnek

Aşağıdaki örnekte bir tarih ve saat girmesini ister ve belirsiz, varsa kullanıcının belirsiz saat eşlendiği UTC saati seçmesine olanak tanır.

[!code-csharp[System.TimeZone2.Concepts#11](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#11)]
[!code-vb[System.TimeZone2.Concepts#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#11)]

Bir dizi örnek kod çekirdek kullanan <xref:System.TimeSpan> belirsiz saati UTC olası uzaklıklarını belirtmek için nesneleri. Ancak, bu uzaklıkları kullanıcıya anlamlı olması olası değildir. Uzaklık anlamını açıklamak için bir uzaklık yerel saat diliminin standart saat veya kendi yaz saati temsil edip etmediğini kod ayrıca notlar. Kodu belirler hangi zaman standarttır ve hangi zamanı gün ışığından yararlanma uzaklık değeriyle karşılaştırarak <xref:System.TimeZoneInfo.BaseUtcOffset%2A> özelliği. Bu özellik, UTC saat diliminin standart saati arasındaki farkı gösterir.

Bu örnekte, yerel saat dilimine yönelik tüm başvuruları üzerinden yapılan <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özellik; bölge için bir nesne değişkeninin hiçbir zaman atanmış yerel saat. Bunun nedeni önerilen bir uygulama, bir çağrı <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi yerel saat dilimini atandığı herhangi bir nesne geçersiz kılar.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: belirsiz saatleri çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md)
