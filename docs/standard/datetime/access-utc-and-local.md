---
title: 'Nasıl yapılır: önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine erişme'
ms.date: 04/10/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
ms.openlocfilehash: ef22753d9934a52d955412a4493b608f265519aa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132601"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Nasıl yapılır: önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine erişme

<xref:System.TimeZoneInfo> sınıfı, kodunuzun önceden tanımlanmış saat dilimi nesnelerine erişmesini sağlayan <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A>iki özellik sağlar. Bu konu, bu özellikler tarafından döndürülen <xref:System.TimeZoneInfo> nesnelerine nasıl erişebileceğinizi açıklamaktadır.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Eşgüdümlü Evrensel Saat (UTC) TimeZoneInfo nesnesine erişmek için

1. Eşgüdümlü Evrensel saate erişmek için `static` (Visual Basic`Shared`) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliğini kullanın.

2. Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesnesini bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği aracılığıyla Eşgüdümlü Evrensel saate erişmeye devam edin.

### <a name="to-access-the-local-time-zone"></a>Yerel saat dilimine erişmek için

1. Yerel sistem saat dilimine erişmek için `static` (Visual Basic`Shared`) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliğini kullanın.

2. Özelliği tarafından döndürülen <xref:System.TimeZoneInfo> nesnesini bir nesne değişkenine atamak yerine, <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla yerel saat dilimine erişmeye devam edin.

## <a name="example"></a>Örnek

Aşağıdaki kod, bir saati ABD ve Kanada Doğu Standart saat diliminden dönüştürmek için <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliklerini kullanır, Ayrıca saat dilimi adını konsola görüntüler.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Yerel Saat dilimini bir <xref:System.TimeZoneInfo> nesne değişkenine atamak yerine <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği aracılığıyla her zaman yerel saat dilimine erişmeniz gerekir. Benzer şekilde, bir <xref:System.TimeZoneInfo> nesne değişkenine UTC bölgesi atamak yerine <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği aracılığıyla Eşgüdümlü Evrensel saate her zaman erişmeniz gerekir. Bu, <xref:System.TimeZoneInfo> nesne değişkeninin <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemine yapılan bir çağrı tarafından geçersiz kılınmasını önler.

## <a name="compiling-the-code"></a>Kodu derleme

Bu örnek şunları gerektirir:

- <xref:System> ad alanı `using` ifadesiyle içeri aktarılmalıdır ( C# kodda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)
