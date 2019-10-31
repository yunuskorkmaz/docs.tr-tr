---
title: Tarihler, saatler ve saat dilimleri
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
ms.openlocfilehash: d46b3cdbddeb1b4e28b7108e7925bd3f086498d0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122296"
---
# <a name="dates-times-and-time-zones"></a>Tarihler, saatler ve saat dilimleri

Temel <xref:System.DateTime> yapısına ek olarak, .NET, Saat dilimleriyle çalışmayı destekleyen aşağıdaki sınıfları sağlar:

* <xref:System.TimeZone>

  Sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölgesi ile çalışmak için bu sınıfı kullanın. <xref:System.TimeZone> sınıfının işlevselliği, büyük ölçüde <xref:System.TimeZoneInfo> sınıfının yerini almıştır.

* <xref:System.TimeZoneInfo>

  Bu sınıfı, bir sistemde önceden tanımlanmış tüm Saat dilimleriyle çalışmak, yeni saat dilimleri oluşturmak ve Tarih ve saatleri bir saat diliminden diğerine kolayca dönüştürmek için kullanın. Yeni geliştirme için <xref:System.TimeZone> sınıfı yerine <xref:System.TimeZoneInfo> sınıfını kullanın.

* <xref:System.DateTimeOffset>

  UTC 'den gelen fark (veya farkı) bilindiğinde tarih ve saatlerle çalışmak için bu yapıyı kullanın. <xref:System.DateTimeOffset> yapısı bir tarih ve saat değerini UTC 'den bu saatin bir değeriyle birleştirir. UTC ile ilişkisi nedeniyle, bağımsız bir tarih ve saat değeri kesin bir zamanda tek bir noktayı tanımlar. Bu, bir <xref:System.DateTimeOffset> değerini bir bilgisayardan <xref:System.DateTime> bir değerden diğerine daha taşınabilir hale getirir.

Belgelerinin bu bölümü, Saat dilimleriyle çalışmanız ve Tarih ve saatleri bir saat diliminden diğerine dönüştürebileceğiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.

## <a name="in-this-section"></a>Bu bölümde

[Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md) Saat dilimi kullanan uygulamalar oluşturma ile ilgili terminolojiyi, kavramları ve sorunları açıklar.

[DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md) Tarih ve saat verileriyle çalışırken <xref:System.DateTime>, <xref:System.DateTimeOffset>ve <xref:System.TimeZoneInfo> türlerinin ne zaman kullanılacağını açıklar.

[Yerel bir sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Yerel bir sistemde bulunan saat dilimlerinin nasıl numaralandırılacağını açıklar.

[Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md) Bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerinin numaralandırılacağı ve kullanıcıların bir listeden önceden tanımlanmış bir saat dilimi seçmesini sağlayan örnekler sağlar.

[Nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](../../../docs/standard/datetime/access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimine nasıl erişebileceğinizi açıklar.

[Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) Yerel sistem kayıt defterinden bir <xref:System.TimeZoneInfo> nesnesinin örneğini oluşturmayı açıklar.

[DateTimeOffset nesnesini örnekleme](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) <xref:System.DateTimeOffset> nesnenin örneklendiği ve bir <xref:System.DateTime> değerinin <xref:System.DateTimeOffset> değere dönüştürülebileceği yollar açıklanmaktadır.

[Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Gün ışığından yararlanma saatine geçişi desteklemeyen bir özel saat dilimi oluşturmayı açıklar.

[Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Gün ışığından yararlanma saatine bir veya daha fazla geçişi destekleyen bir özel saat dilimi oluşturmayı açıklar.

[Saat dilimlerini kaydetme ve geri yükleme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Saat dilimi verilerinin serileştirilmesi ve seri durumundan çıkarılması için <xref:System.TimeZoneInfo> desteğini açıklar ve bu özelliklerin kullanılabileceği bazı senaryoları gösterir.

[Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Özel saat dilimini oluşturmayı ve bu bilgilerin bir kaynak dosyasına nasıl kaydedileceğini açıklar.

[Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Katıştırılmış bir kaynak dosyasına kaydedilmiş özel saat dilimlerinin örneğini oluşturmayı açıklar.

[Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerini ekleme, çıkarma ve karşılaştırmayla ilgili sorunları ele alır.

[Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Saat diliminin ayarlama kurallarını yansıtan tarih ve saat aritmetiği yapmayı açıklar.

[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri arasında nasıl dönüştürme yapılacağını açıklar.

[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) Saatlerin bir saat diliminden diğerine nasıl dönüştürüleceğini açıklar.

[Nasıl yapılır: belirsiz zamanları çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md) Saat diliminin standart saatine eşleyerek belirsiz bir sürenin nasıl çözümleneceğini açıklar.

[Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Kullanıcının belirsiz bir yerel saat ve eşgüdümlü evrensel saat arasındaki eşlemeyi belirlemesine nasıl izin verbileceğinizi açıklar.

## <a name="reference"></a>Başvuru

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
