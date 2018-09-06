---
title: Yerel sistemde tanımlanan saat dilimlerini bulma
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], local
- time zones [.NET Framework], finding local system time zones
- time zone identifiers [.NET Framework]
- local time zone access
- time zones [.NET Framework], retrieving
- UTC times, finding local system time zones
- time zones [.NET Framework], UTC
ms.assetid: 3f63b1bc-9a4b-4bde-84ea-ab028a80d3e1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a65798c46b01bb7a702559d685590ecf7a6f2793
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43881908"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Yerel sistemde tanımlanan saat dilimlerini bulma

<xref:System.TimeZoneInfo> Sınıfı bir public Oluşturucu koymuyor. Sonuç olarak, `new` yeni bir anahtar sözcüğü kullanılamaz <xref:System.TimeZoneInfo> nesne. Bunun yerine, <xref:System.TimeZoneInfo> nesnelerine ait örneklerin kayıt defterinden önceden tanımlanmış saat dilimleri hakkında bilgi almak veya özel bir saat dilimi oluşturma. Bu konuda, bir saat dilimi kayıt defterinde depolanan verilerden örnekleme anlatılmaktadır. Ayrıca, `static` (`shared` Visual Basic'te) özelliklerini <xref:System.TimeZoneInfo> sınıfı yerel saat dilimi ile eşgüdümlü evrensel saat (UTC) ile erişim sağlar.

> [!NOTE]
> Kayıt defterinde tanımlanmamış saat dilimleri için özel saat dilimi aşırı yüklemelerini çağırarak oluşturabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yöntemi. Özel bir saat dilimi oluşturma ele alınmıştır [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) konuları. Ayrıca, oluşturabileceğiniz bir <xref:System.TimeZoneInfo> ile seri hale getirilmiş bir dizeden geri nesne <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi. Serileştirme ve seri durumdan çıkarılırken bir <xref:System.TimeZoneInfo> nesne ele alınmıştır [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) konuları.

## <a name="accessing-individual-time-zones"></a>Tek tek saat dilimlerini erişme

<xref:System.TimeZoneInfo> Sınıfı UTC saati ile yerel saat dilimini temsil eden iki önceden tanımlanmış saat dilimi nesneleri sağlar. Kullanılabilir olduklarından <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A> özellikleri, sırasıyla. UTC veya yerel saat dilimlerini erişme ile ilgili yönergeler için bkz: [nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md).

Ayrıca oluşturabileceğiniz bir <xref:System.TimeZoneInfo> kayıt defterinde tanımlanan tüm saat dilimini temsil eden nesne. Belirli bir saat dilimi nesnesini örnekleme ile ilgili yönergeler için bkz: [nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Saat dilimi tanımlayıcıları

Saat dilimi benzersiz olarak tanımlayan bir anahtar alan saat dilimi tanımlayıcısıdır. Saat dilimi tanımlayıcı çoğu anahtarları görece kısa olsa da, daha uzun. Çoğu durumda, karşılık gelen değeri <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> saat diliminin standart saat adını sağlamak için kullanılan özellik. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı sağlamanız emin olmak için en iyi yolu, sisteminizde mevcut saat dilimlerini numaralandırma ve bunların ilişkili tanımlayıcılar Not sağlamaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md)
- [Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md)
