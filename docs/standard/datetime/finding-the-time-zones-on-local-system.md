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
ms.openlocfilehash: 1e7e3a7a11c1d262f7fcb63e6e12efbe5edf745f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122321"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Yerel sistemde tanımlanan saat dilimlerini bulma

<xref:System.TimeZoneInfo> sınıfı ortak bir Oluşturucu sunmaz. Sonuç olarak, yeni bir <xref:System.TimeZoneInfo> nesnesi oluşturmak için `new` anahtar sözcüğü kullanılamaz. Bunun yerine, <xref:System.TimeZoneInfo> nesneler, kayıt defterinden önceden tanımlanmış Saat dilimleriyle ilgili bilgiler alarak veya özel bir saat dilimi oluşturarak oluşturulur. Bu konuda, kayıt defterinde depolanan verilerden bir saat dilimini örnekleme ele alınmaktadır. Ayrıca, <xref:System.TimeZoneInfo> sınıfının `static` (Visual Basic`shared`) özelliklerinde Eşgüdümlü Evrensel Saat (UTC) ve yerel saat dilimine erişim sağlar.

> [!NOTE]
> Kayıt defterinde tanımlanmayan saat dilimleri için, <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> yönteminin aşırı yüklerini çağırarak özel saat dilimleri oluşturabilirsiniz. Özel saat dilimi oluşturma, [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları Ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) konularında ele alınmıştır. Ayrıca, <xref:System.TimeZoneInfo.FromSerializedString%2A> yöntemi ile seri hale getirilmiş bir dizeden geri yükleyerek bir <xref:System.TimeZoneInfo> nesnesi örneğini oluşturabilirsiniz. Bir <xref:System.TimeZoneInfo> nesnesini serileştirmek ve seri durumdan çıkarmak, [nasıl yapılır: bir katıştırılmış kaynağa zaman dilimlerini kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: gömülü bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) konularında ele alınmıştır.

## <a name="accessing-individual-time-zones"></a>Bireysel saat dilimlerine erişme

<xref:System.TimeZoneInfo> sınıfı, UTC saatini ve yerel saat dilimini temsil eden önceden tanımlanmış iki saat dilimi nesnesi sağlar. Bunlar, sırasıyla <xref:System.TimeZoneInfo.Utc%2A> ve <xref:System.TimeZoneInfo.Local%2A> özelliklerinden kullanılabilir. UTC veya yerel saat dilimlerine erişme hakkında yönergeler için bkz. [nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](../../../docs/standard/datetime/access-utc-and-local.md).

Ayrıca, kayıt defterinde tanımlı herhangi bir saat dilimini temsil eden bir <xref:System.TimeZoneInfo> nesnesi örneğini oluşturabilirsiniz. Belirli bir saat dilimi nesnesini örnekleme hakkında yönergeler için bkz. [nasıl yapılır: bir TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Saat dilimi tanımlayıcıları

Saat dilimi tanımlayıcısı, saat dilimini benzersiz bir şekilde tanımlayan bir anahtar alanıdır. Çoğu anahtar görece kısaysa, saat dilimi tanımlayıcısı oldukça uzun olur. Çoğu durumda, değeri, saat diliminin standart zamanının adını sağlamak için kullanılan <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> özelliğine karşılık gelir. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı belirttiğinizden emin olmanın en iyi yolu, sisteminizde kullanılabilir olan saat dilimlerini listelemek ve bunlarla ilişkili tanımlayıcılar olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
- [Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md)
- [Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md)
- [Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md)
