---
title: 'Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim'
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d36b5ff4912b09101694dd0e83291053260f0bf9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586423"
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim

<xref:System.TimeZoneInfo> SAX iki özellik <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A>, önceden tanımlanmış saat dilimi nesneleri, kod erişim verin. Bu konu nasıl erişileceğini açıklar <xref:System.TimeZoneInfo> bu özellik tarafından döndürülen nesne.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Eşgüdümlü Evrensel Saat (UTC) Timezoneınfo nesnesinin erişmek için

1. Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel Saat erişmeye özelliği.

2. Atama yerine <xref:System.TimeZoneInfo> nesnesi bir nesne değişkenine özelliği tarafından döndürülen Eşgüdümlü Evrensel Saat üzerinden erişmeye devam <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği.

### <a name="to-access-the-local-time-zone"></a>Yerel saat dilimi erişmek için

1. Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel sistem saat dilimi erişmek için özelliği.

2. Atama yerine <xref:System.TimeZoneInfo> nesnesi bir nesne değişkenine özelliği tarafından döndürülen yerel saat dilimi üzerinden erişmeye devam <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği.

## <a name="example"></a>Örnek

Aşağıdaki kod <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> ABD ve Kanada Doğu Standart saat diliminden dönüştürün gibi saat dilimi adını konsolda görüntülemek için özellikleri.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Her zaman yerel saat dilimi üzerinden erişmelidir <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel saat atamak yerine özellik bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni. Benzer şekilde, her zaman Eşgüdümlü Evrensel Saat üzerinden erişmelidir <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC atamak yerine özellik bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni. Bu engeller <xref:System.TimeZoneInfo> gelen bir çağrı tarafından geçersiz nesne değişkeni <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Olduğunu <xref:System> ad alanı içeri aktarılacak `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
- [Nasıl yapılır: Bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)
