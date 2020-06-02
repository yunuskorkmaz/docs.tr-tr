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
ms.openlocfilehash: 86602cd6e662b1b1057832247babc558ef67b79f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276939"
---
# <a name="dates-times-and-time-zones"></a>Tarihler, saatler ve saat dilimleri

<xref:System.DateTime>.Net, temel yapıya ek olarak, Saat dilimleriyle çalışmayı destekleyen aşağıdaki sınıfları sağlar:

* <xref:System.TimeZone>

  Sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölgesi ile çalışmak için bu sınıfı kullanın. <xref:System.TimeZone>Sınıfın işlevselliği büyük ölçüde sınıfının yerini almıştır <xref:System.TimeZoneInfo> .

* <xref:System.TimeZoneInfo>

  Bu sınıfı, bir sistemde önceden tanımlanmış tüm Saat dilimleriyle çalışmak, yeni saat dilimleri oluşturmak ve Tarih ve saatleri bir saat diliminden diğerine kolayca dönüştürmek için kullanın. Yeni geliştirme için <xref:System.TimeZoneInfo> sınıfı yerine sınıfını kullanın <xref:System.TimeZone> .

* <xref:System.DateTimeOffset>

  UTC 'den gelen fark (veya farkı) bilindiğinde tarih ve saatlerle çalışmak için bu yapıyı kullanın. <xref:System.DateTimeOffset>Yapı, tarih ve saat DEĞERINI UTC 'den bu saatin bir değeriyle birleştirir. UTC ile ilişkisi nedeniyle, bağımsız bir tarih ve saat değeri kesin bir zamanda tek bir noktayı tanımlar. Bu, bir <xref:System.DateTimeOffset> değeri bir bilgisayardan diğerine daha taşınabilir hale getirir <xref:System.DateTime> .

Belgelerinin bu bölümü, Saat dilimleriyle çalışmanız ve Tarih ve saatleri bir saat diliminden diğerine dönüştürebileceğiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.

## <a name="in-this-section"></a>Bu bölümde

[Saat dilimine genel bakış](time-zone-overview.md) Saat dilimi kullanan uygulamalar oluşturma ile ilgili terminolojiyi, kavramları ve sorunları açıklar.

[DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](choosing-between-datetime.md) <xref:System.DateTime> <xref:System.DateTimeOffset> <xref:System.TimeZoneInfo> Tarih ve saat verileriyle çalışırken,, ve türlerinin ne zaman kullanılacağını açıklar.

[Yerel bir sistemde tanımlanan saat dilimlerini bulma](finding-the-time-zones-on-local-system.md) Yerel bir sistemde bulunan saat dilimlerinin nasıl numaralandırılacağını açıklar.

[Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](enumerate-time-zones.md) Bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerinin numaralandırılacağı ve kullanıcıların bir listeden önceden tanımlanmış bir saat dilimi seçmesini sağlayan örnekler sağlar.

[Nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimine nasıl erişebileceğinizi açıklar.

[Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma](instantiate-time-zone-info.md) <xref:System.TimeZoneInfo>Yerel sistem kayıt defterinden bir nesnenin örneğini oluşturmayı açıklar.

[DateTimeOffset nesnesini örnekleme](instantiating-a-datetimeoffset-object.md) Bir <xref:System.DateTimeOffset> nesnenin örneklendiği ve bir <xref:System.DateTime> değerin bir değere dönüştürülebileceği yollar açıklanmaktadır <xref:System.DateTimeOffset> .

[Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](create-time-zones-without-adjustment-rules.md) Gün ışığından yararlanma saatine geçişi desteklemeyen bir özel saat dilimi oluşturmayı açıklar.

[Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](create-time-zones-with-adjustment-rules.md) Gün ışığından yararlanma saatine bir veya daha fazla geçişi destekleyen bir özel saat dilimi oluşturmayı açıklar.

[Saat dilimlerini kaydetme ve geri yükleme](saving-and-restoring-time-zones.md) <xref:System.TimeZoneInfo>Saat dilimi verilerinin serileştirilmesi ve serisini kaldırma desteğini açıklar ve bu özelliklerin kullanılabileceği bazı senaryoları gösterir.

[Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](save-time-zones-to-an-embedded-resource.md) Özel saat dilimini oluşturmayı ve bu bilgilerin bir kaynak dosyasına nasıl kaydedileceğini açıklar.

[Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](restore-time-zones-from-an-embedded-resource.md) Katıştırılmış bir kaynak dosyasına kaydedilmiş özel saat dilimlerinin örneğini oluşturmayı açıklar.

[Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](performing-arithmetic-operations.md) Ekleme, çıkarma ve karşılaştırma ve değer ile ilgili sorunları ele <xref:System.DateTime> alır <xref:System.DateTimeOffset> .

[Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](use-time-zones-in-arithmetic.md) Saat diliminin ayarlama kurallarını yansıtan tarih ve saat aritmetiği yapmayı açıklar.

[DateTime ve DateTimeOffset arasında dönüştürme](converting-between-datetime-and-offset.md) Ve değerlerini arasında dönüştürme işlemini <xref:System.DateTime> açıklar <xref:System.DateTimeOffset> .

[Saatleri saat dilimleri arasında dönüştürme](converting-between-time-zones.md) Saatlerin bir saat diliminden diğerine nasıl dönüştürüleceğini açıklar.

[Nasıl yapılır: belirsiz zamanları çözme](resolve-ambiguous-times.md) Saat diliminin standart saatine eşleyerek belirsiz bir sürenin nasıl çözümleneceğini açıklar.

[Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver](let-users-resolve-ambiguous-times.md) Kullanıcının belirsiz bir yerel saat ve eşgüdümlü evrensel saat arasındaki eşlemeyi belirlemesine nasıl izin verbileceğinizi açıklar.

## <a name="reference"></a>Başvuru

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
