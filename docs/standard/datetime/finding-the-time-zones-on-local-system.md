---
title: "Yerel sistemde tanımlanan saat dilimlerini bulma"
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e61f05741c1edd86d9baad4f6ebc9f4e91318250
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/23/2017
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Yerel sistemde tanımlanan saat dilimlerini bulma

<xref:System.TimeZoneInfo> Sınıfı bir public oluşturucuya uygulamaz. Sonuç olarak, `new` anahtar sözcüğü, yeni bir oluşturmak için kullanılamaz <xref:System.TimeZoneInfo> nesnesi. Bunun yerine, <xref:System.TimeZoneInfo> nesnelerine ait örneklerin kayıt defterinden önceden tanımlanmış saat dilimleri hakkında bilgi almak veya özel bir saat dilimi oluşturarak. Bu konuda, bir saat dilimi kayıt defterinde depolanan verilerden başlatmasını anlatılmaktadır. Ayrıca, `static` (`shared` Visual Basic'te) özelliklerini <xref:System.TimeZoneInfo> sınıfı Eşgüdümlü Evrensel Saat (UTC) ve yerel saat dilimini erişim sağlar.

> [!NOTE]
> Kayıt defterinde tanımlı değil saat dilimleri için özel saat dilimlerini aşırı çağırarak oluşturabileceğiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi. Özel bir saat dilimi oluşturma ele alınmıştır [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Konular. Ayrıca, örneği bir <xref:System.TimeZoneInfo> ile seri hale getirilmiş bir dizeden geri nesne <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi. Seri hale getirme ve seri durumdan çıkarılırken bir <xref:System.TimeZoneInfo> nesne ele alınmıştır [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Konular.

## <a name="accessing-individual-time-zones"></a>Tek tek saat dilimleri erişme

<xref:System.TimeZoneInfo> Sınıfı UTC saati ve yerel saat dilimini temsil eden iki önceden tanımlanmış saat dilimi nesneleri sağlar. Kullanılabilir <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A> özellikleri, sırasıyla. UTC veya yerel saat dilimlerini erişme ile ilgili yönergeler için bkz: [nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md).

Ayrıca örneği bir <xref:System.TimeZoneInfo> kayıt defterinde tanımlanan tüm saat dilimini temsil eden nesne. Belirli saat dilimi nesnesi örneği ile ilgili yönergeler için bkz: [nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Saat dilimi tanımlayıcıları

Saat dilimi benzersiz olarak tanımlayan bir anahtar alanı saat dilimi tanımlayıcısıdır. Çoğu anahtarları görece kısa olsa da, saat dilimi tanımlayıcı daha uzun. Çoğu durumda, karşılık gelen değeri <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> saat diliminin standart saat adını sağlamak için kullanılan özellik. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı sağladığınız emin olmak için en iyi sisteminizdeki kullanılabilir saat dilimlerini numaralandırma ve bunların ilişkili tanımlayıcıları not edin yoludur.

## <a name="see-also"></a>Ayrıca bkz.

[Tarih, saat ve saat dilimleri](../../../docs/standard/datetime/index.md)
[nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md)
[nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) 
 [Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md)
