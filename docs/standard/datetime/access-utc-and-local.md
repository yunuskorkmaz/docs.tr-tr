---
title: "Nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim"
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
- time zones [.NET Framework], local
- predefined time zones
- UTC times, predefined
- local time zone access
- time zones [.NET Framework], retrieving
- time zones [.NET Framework], UTC
ms.assetid: 961fb70b-83f0-4dab-a042-cb5fcd817cf5
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 600dbb98264c4750db1ffb98b757ad191eaf4fe5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-access-the-predefined-utc-and-local-time-zone-objects"></a>Nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim

<xref:System.TimeZoneInfo> SAX iki özellik <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A>, önceden tanımlanmış saat dilimi nesneleri için kod erişimi verin. Bu konuda ele alınmıştır nasıl erişileceği <xref:System.TimeZoneInfo> bu özellik tarafından döndürülen nesne.

### <a name="to-access-the-coordinated-universal-time-utc-timezoneinfo-object"></a>Eşgüdümlü Evrensel Saat (UTC) Timezoneınfo nesnesinin erişmek için

1. Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> Eşgüdümlü Evrensel Saat erişmeye özelliği.

2. Atama yerine <xref:System.TimeZoneInfo> nesne bir nesne değişkeni için özellik tarafından döndürülen üzerinden Eşgüdümlü Evrensel Saat erişmeye devam <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özelliği.

### <a name="to-access-the-local-time-zone"></a>Yerel saat dilimini erişmek için

1. Kullanım `static` (`Shared` Visual Basic'te) <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel sistem saat dilimi erişmek için özellik.

2. Atama yerine <xref:System.TimeZoneInfo> nesne bir nesne değişkeni için özellik tarafından döndürülen aracılığıyla yerel saat dilimi erişmeye devam <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> özelliği.

## <a name="example"></a>Örnek

Aşağıdaki kod <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> ve <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> özellikleri ABD ve Kanada Doğu Standart Saati Bölgesi'nden bir saat dönüştürme gibi konsola saat dilimi adını görüntülemek için.

[!code-csharp[System.TimeZone2.Concepts#13](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.TimeZone2.Concepts/CS/TimeZone2Concepts.cs#13)]
[!code-vb[System.TimeZone2.Concepts#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.TimeZone2.Concepts/VB/TimeZone2Concepts.vb#13)]

Yerel saat dilimi aracılığıyla her zaman erişim <xref:System.TimeZoneInfo.Local%2A?displayProperty=nameWithType> yerel saat atama yerine özelliği bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni. Benzer şekilde, her zaman Eşgüdümlü Evrensel Saat üzerinden erişim <xref:System.TimeZoneInfo.Utc%2A?displayProperty=nameWithType> UTC atama yerine özelliği bölge için bir <xref:System.TimeZoneInfo> nesne değişkeni. Bu engeller <xref:System.TimeZoneInfo> nesne değişkeni için bir çağrı tarafından geçersiz gelen <xref:System.TimeZoneInfo.ClearCachedData%2A?displayProperty=nameWithType> yöntemi.

## <a name="compiling-the-code"></a>Kod derleme

Bu örnek gerektirir:

* Bir başvuru System.Core.dll projeye eklenmesini.

* Olduğunu <xref:System> ad alanı ile aktarılabilir `using` deyimi (C# kodunda gereklidir).

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md)
[nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)
