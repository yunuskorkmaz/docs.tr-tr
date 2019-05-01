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
ms.openlocfilehash: 5355666b95d75fc18d0188c978c186690ee9ccca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61819710"
---
# <a name="dates-times-and-time-zones"></a>Tarihler, saatler ve saat dilimleri

Temel yanı sıra <xref:System.DateTime> yapısı, .NET aşağıdaki sınıflar ile saat dilimleri çalışma Bu destek sağlar:

* <xref:System.TimeZone>

  Bu sınıf, sistemin yerel saat dilimi (UTC) Eşgüdümlü Evrensel Saat dilimi ile çalışmak için kullanın. İşlevselliğini <xref:System.TimeZone> sınıfı tarafından değiştirilen büyük ölçüde <xref:System.TimeZoneInfo> sınıfı.

* <xref:System.TimeZoneInfo>

  Bu sınıf, bir sistemde yeni saat dilimleri oluşturma ve kolayca tarihler ve saatler bir saat diliminden diğerine dönüştürmek için önceden tanımlanmış hiçbir saat dilimi ile çalışmak için kullanın. Yeni geliştirme için kullanmak <xref:System.TimeZoneInfo> sınıfı yerine <xref:System.TimeZone> sınıfı.

* <xref:System.DateTimeOffset>

  Bu yapı, tarihler ve saatler UTC olan uzaklık (veya fark) bilinen ile çalışmak için kullanın. <xref:System.DateTimeOffset> Yapısı birleştiren bir tarih ve saat değerinin saat ile UTC ile olan uzaklığını. UTC, tek bir tarih ve saat ilişkisini nedeniyle değer üretemez zaman tek bir nokta tanımlar. Böylece bir <xref:System.DateTimeOffset> değeri diğerinden için bir bilgisayardan daha taşınabilir bir <xref:System.DateTime> değeri.

Belgelerinin bu bölümü ile saat dilimleri çözmek ve tarihler ve saatler bir saat diliminden diğerine dönüştürebilirsiniz saat dilimiyle uyumlu uygulamalar oluşturmak için gereken bilgileri sağlar.

## <a name="in-this-section"></a>Bu bölümde

[Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md) terminoloji, kavramlar ve saat dilimiyle uyumlu uygulamalar oluşturmak için gerekli olan sorunlar ele alınmaktadır.

[DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md) ne zaman kullanılacağı ele alınmaktadır <xref:System.DateTime>, <xref:System.DateTimeOffset>, ve <xref:System.TimeZoneInfo> türleri tarih ve saat verilerle çalışırken.

[Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) yerel bir sistemde bulunan saat dilimlerini numaralandırma açıklar.

[Nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md) kullanıcıları önceden tanımlanmış bir saat dilimi bir listeden seç sağlar ve bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerini numaralandırma örnekleri sağlar.

[Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimi nasıl açıklar.

[Nasıl yapılır: Bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) örneğini açıklar bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesne.

[Bir DateTimeOffset nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) yöntemler anlatılır bir <xref:System.DateTimeOffset> nesne oluşturulabilir ve yöntemler bir <xref:System.DateTime> değer dönüştürülebilir bir <xref:System.DateTimeOffset> değeri.

[Nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Yaz Saati gelen ve geçiş desteği olmayan özel bir saat dilimi oluşturmayı açıklar.

[Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Yaz Saati gelen ve giden bir veya daha fazla geçişleri destekleyen özel bir saat dilimi oluşturmayı açıklar.

[Saat dilimlerini geri yükleme ve kaydetme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> desteklemek için serileştirme ve seri durumundan çıkarma saat dilimi veri ve bu özellikleri kullanılabilen senaryolardan bazıları gösterilmektedir.

[Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) özel bir saat dilimi oluşturma ve bir kaynak dosyasında bilgilerini kaydetmek açıklar.

[Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) bir gömülü kaynak dosyasına kaydedildi özel saat dilimi örneğini açıklar.

[Tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) ekleme, çıkarma ve karşılaştırma ilgili sorunlar ele alınmıştır <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.

[Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) nasıl tarih ve saat diliminin ayarlama kuralları yansıtan saat aritmetiği gerçekleştirileceği ele alınmaktadır.

[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) arasında nasıl dönüştürme yapılacağını açıklar <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.

[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) saatler bir saat diliminden dönüştürüleceğini açıklar.

[Nasıl yapılır: Belirsiz saatleri çözmelerine](../../../docs/standard/datetime/resolve-ambiguous-times.md) belirsiz bir saat, saat diliminin Standart Saati için eşleyerek çözümlemeyi açıklar.

[Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) bir kullanıcının bir belirsiz yerel saat ve Eşgüdümlü Evrensel Saat arasındaki eşlemeyi belirlemek olanak açıklar.

## <a name="reference"></a>Başvuru

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
