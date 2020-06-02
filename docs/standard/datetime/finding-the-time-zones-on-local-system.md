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
ms.openlocfilehash: d313bbed3cc525a74b90537dd4f1742c09c62cd4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277030"
---
# <a name="finding-the-time-zones-defined-on-a-local-system"></a>Yerel sistemde tanımlanan saat dilimlerini bulma

<xref:System.TimeZoneInfo>Sınıf ortak bir Oluşturucu sunmaz. Sonuç olarak, `new` anahtar sözcük yeni bir nesne oluşturmak için kullanılamaz <xref:System.TimeZoneInfo> . Bunun yerine, <xref:System.TimeZoneInfo> nesneler, kayıt defterinden veya özel bir saat dilimi oluşturarak önceden tanımlı Saat dilimleriyle ilgili bilgiler alarak oluşturulur. Bu konuda, kayıt defterinde depolanan verilerden bir saat dilimini örnekleme ele alınmaktadır. Ayrıca, `static` ( `shared` Visual Basic) <xref:System.TimeZoneInfo> sınıfının özellikleri Eşgüdümlü Evrensel Saat (UTC) ve yerel saat dilimine erişim sağlar.

> [!NOTE]
> Kayıt defterinde tanımlanmayan saat dilimleri için, yönteminin aşırı yüklerini çağırarak özel saat dilimleri oluşturabilirsiniz <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> . Özel saat dilimi oluşturma, [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları Ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md) konularında ele alınmıştır. Ayrıca, <xref:System.TimeZoneInfo> yöntemiyle bir seri hale getirilmiş dizeden geri yükleyerek bir nesnesi örneğini oluşturabilirsiniz <xref:System.TimeZoneInfo.FromSerializedString%2A> . Bir nesneyi seri hale getirme ve serisini kaldırma <xref:System.TimeZoneInfo> , [nasıl yapılır: bir katıştırılmış kaynağa zaman dilimlerini kaydetme](save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: bir katıştırılmış kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md) konularında ele alınmıştır.

## <a name="accessing-individual-time-zones"></a>Bireysel saat dilimlerine erişme

<xref:System.TimeZoneInfo>Sınıfı, UTC saatini ve yerel saat dilimini temsil eden önceden tanımlanmış iki saat dilimi nesnesi sağlar. Bunlar <xref:System.TimeZoneInfo.Utc%2A> <xref:System.TimeZoneInfo.Local%2A> , sırasıyla ve özelliklerinden kullanılabilir. UTC veya yerel saat dilimlerine erişme hakkında yönergeler için bkz. [nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](access-utc-and-local.md).

Ayrıca <xref:System.TimeZoneInfo> , kayıt defterinde tanımlı herhangi bir saat dilimini temsil eden bir nesne örneği oluşturabilirsiniz. Belirli bir saat dilimi nesnesini örnekleme hakkında yönergeler için bkz. [nasıl yapılır: bir TimeZoneInfo nesnesinin örneğini oluşturma](instantiate-time-zone-info.md).

## <a name="time-zone-identifiers"></a>Saat dilimi tanımlayıcıları

Saat dilimi tanımlayıcısı, saat dilimini benzersiz bir şekilde tanımlayan bir anahtar alanıdır. Çoğu anahtar görece kısaysa, saat dilimi tanımlayıcısı oldukça uzun olur. Çoğu durumda, değeri, <xref:System.TimeZoneInfo.StandardName%2A?displayProperty=nameWithType> saat diliminin standart zamanının adını sağlamak için kullanılan özelliğine karşılık gelir. Ancak, özel durumlar vardır. Geçerli bir tanımlayıcı belirttiğinizden emin olmanın en iyi yolu, sisteminizde kullanılabilir olan saat dilimlerini listelemek ve bunlarla ilişkili tanımlayıcılar olduğunu unutmayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Tarihler, saatler ve saat dilimleri](index.md)
- [Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](access-utc-and-local.md)
- [Nasıl yapılır: Bir TimeZoneInfo nesnesinin örneğini oluşturma](instantiate-time-zone-info.md)
- [Saatleri saat dilimleri arasında dönüştürme](converting-between-time-zones.md)
