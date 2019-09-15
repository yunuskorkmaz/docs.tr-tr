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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03a5594b689a52b641ecece0f9a92fb6cdfe5735
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991282"
---
# <a name="dates-times-and-time-zones"></a>Tarihler, saatler ve saat dilimleri

.Net, temel <xref:System.DateTime> yapıya ek olarak, Saat dilimleriyle çalışmayı destekleyen aşağıdaki sınıfları sağlar:

* <xref:System.TimeZone>

  Sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölgesi ile çalışmak için bu sınıfı kullanın. <xref:System.TimeZone> Sınıfın işlevselliği büyük ölçüde <xref:System.TimeZoneInfo> sınıfının yerini almıştır.

* <xref:System.TimeZoneInfo>

  Bu sınıfı, bir sistemde önceden tanımlanmış tüm Saat dilimleriyle çalışmak, yeni saat dilimleri oluşturmak ve Tarih ve saatleri bir saat diliminden diğerine kolayca dönüştürmek için kullanın. Yeni geliştirme için <xref:System.TimeZoneInfo> <xref:System.TimeZone> sınıfı yerine sınıfını kullanın.

* <xref:System.DateTimeOffset>

  UTC 'den gelen fark (veya farkı) bilindiğinde tarih ve saatlerle çalışmak için bu yapıyı kullanın. Yapı <xref:System.DateTimeOffset> , tarih ve saat değerini UTC 'den bu saatin bir değeriyle birleştirir. UTC ile ilişkisi nedeniyle, bağımsız bir tarih ve saat değeri kesin bir zamanda tek bir noktayı tanımlar. Bu, bir <xref:System.DateTimeOffset> değeri bir bilgisayardan <xref:System.DateTime> diğerine daha taşınabilir hale getirir.

Belgelerinin bu bölümü, Saat dilimleriyle çalışmanız ve Tarih ve saatleri bir saat diliminden diğerine dönüştürebileceğiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.

## <a name="in-this-section"></a>Bu bölümde

[Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md) Saat dilimi kullanan uygulamalar oluşturma ile ilgili terminolojiyi, kavramları ve sorunları açıklar.

[DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md) Tarih ve saat verileriyle çalışırken <xref:System.DateTime>, <xref:System.DateTimeOffset>, ve <xref:System.TimeZoneInfo> türlerinin ne zaman kullanılacağını açıklar.

[Yerel bir sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Yerel bir sistemde bulunan saat dilimlerinin nasıl numaralandırılacağını açıklar.

[Nasıl yapılır: Bir bilgisayardaki](../../../docs/standard/datetime/enumerate-time-zones.md) zaman dilimlerini listeleme, bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerini listeleme ve kullanıcıların bir listeden önceden tanımlanmış bir saat dilimi seçmesini sağlayan örnekler sağlar.

[Nasıl yapılır: Önceden tanımlanmış UTC ve yerel saat dilimi nesnelerine](../../../docs/standard/datetime/access-utc-and-local.md) erişim, Eşgüdümlü Evrensel Saat ve yerel saat dilimine nasıl erişebileceğinizi açıklar.

[Nasıl yapılır: Bir TimeZoneInfo nesnesinin](../../../docs/standard/datetime/instantiate-time-zone-info.md) örneğini oluşturma, yerel sistem kayıt <xref:System.TimeZoneInfo> defterinden bir nesnenin örneğini oluşturmayı açıklar.

[DateTimeOffset nesnesini örnekleme](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Bir <xref:System.DateTimeOffset> nesnenin örneklendiği ve <xref:System.DateTime> bir değerin bir <xref:System.DateTimeOffset> değere dönüştürülebileceği yollar açıklanmaktadır.

[Nasıl yapılır: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) olmadan saat dilimleri oluşturma, gün ışığından yararlanma saatine geçişi desteklemeyen bir özel saat dilimi oluşturmayı açıklar.

[Nasıl yapılır: Ayarlama kuralları](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) ile saat dilimleri oluşturma, gün ışığından yararlanma saatine kadar bir veya daha fazla geçişi destekleyen bir özel saat dilimi oluşturmayı açıklar.

[Saat dilimlerini kaydetme ve geri yükleme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Saat <xref:System.TimeZoneInfo> dilimi verilerinin serileştirilmesi ve serisini kaldırma desteğini açıklar ve bu özelliklerin kullanılabileceği bazı senaryoları gösterir.

[Nasıl yapılır: Zaman dilimlerini gömülü bir kaynağa](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) kaydetme, özel saat dilimi oluşturmayı ve bu bilgilerin bir kaynak dosyasına nasıl kaydedileceğini açıklar.

[Nasıl yapılır: Katıştırılmış bir kaynaktan](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) saat dilimlerini geri yükleme, gömülü bir kaynak dosyasına kaydedilmiş özel saat dilimlerini nasıl örneklendirileceğini açıklar.

[Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) Ekleme, çıkarma ve karşılaştırma <xref:System.DateTime> ve değer ile <xref:System.DateTimeOffset> ilgili sorunları ele alır.

[Nasıl yapılır: Tarih ve Saat Aritmetiğinde](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) saat dilimlerini kullanma, saat diliminin ayarlama kurallarını yansıtan tarih ve saat aritmetiği yapmayı tartışır.

[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) <xref:System.DateTime> Ve<xref:System.DateTimeOffset> değerlerini arasında dönüştürme işlemini açıklar.

[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) Saatlerin bir saat diliminden diğerine nasıl dönüştürüleceğini açıklar.

[Nasıl yapılır: Belirsiz zamanları](../../../docs/standard/datetime/resolve-ambiguous-times.md) çöz, saat diliminin standart saatine eşleyerek belirsiz bir zamanın nasıl çözümleneceğini açıklar.

[Nasıl yapılır: Kullanıcıların belirsiz zamanları](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) çözmesine izin ver, kullanıcının belirsiz bir yerel saat ve eşgüdümlü evrensel saat arasındaki eşlemeyi belirlemesine izin verir.

## <a name="reference"></a>Başvuru

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
