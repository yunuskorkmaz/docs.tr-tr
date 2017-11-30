---
title: Tarih, saat ve saat dilimleri
ms.custom: 
ms.date: 04/10/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- time zone objects [.NET Framework]
- date and time data [.NET Framework]
- time zones [.NET Framework]
- times [.NET Framework], time zones
- time [.NET Framework], time zones
ms.assetid: 295c16e0-641b-4771-94b3-39c1ffa98c13
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1e85fc8eac25cc6fdfb8cb3aaa77318019695c51
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="dates-times-and-time-zones"></a>Tarih, saat ve saat dilimleri

Temel yanı sıra <xref:System.DateTime> yapısı, .NET aşağıdaki sınıflar ile saat dilimleri çalışma Bu destek sağlar:

* <xref:System.TimeZone>

  Bu sınıf sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölge ile çalışmak için kullanın. İşlevselliğini <xref:System.TimeZone> sınıfı tarafından değiştirilen büyük ölçüde <xref:System.TimeZoneInfo> sınıfı.

* <xref:System.TimeZoneInfo>

  Bu sınıf, bir sistemde, yeni saat dilimleri oluşturma ve kolayca tarihler ve saatler bir saat diliminden diğerine dönüştürmek için önceden tanımlanmış hiçbir saat dilimi ile çalışmak için kullanın. Yeni geliştirme için kullanmak <xref:System.TimeZoneInfo> sınıfının yerine <xref:System.TimeZone> sınıfı.

* <xref:System.DateTimeOffset>

  Tarihler ve saatler UTC olan uzaklık (veya fark) bilinen ile çalışmak için bu yapı kullanın. <xref:System.DateTimeOffset> Yapısı birleştiren bir tarih ve saat değeri ile bu süre UTC uzaklığı. UTC, bir tek tek tarih ve saat ilişkisini nedeniyle değer belirsizliğe zamanında tek bir nokta tanımlar. Böylece bir <xref:System.DateTimeOffset> değeri'den başka bir bir bilgisayardan daha taşınabilir bir <xref:System.DateTime> değeri.

Bu bölümde belgelerin saat dilimleri ile çalışmak için ve tarih ve saati bir saat diliminden diğerine dönüştürebilirsiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.

## <a name="in-this-section"></a>Bu bölümde

[Saat dilimi genel bakış](../../../docs/standard/datetime/time-zone-overview.md) terminolojisi, kavramları ve konuları saat dilimi algılayan uygulamaları oluşturmaya dahil açıklanır.

[DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md) ne zaman kullanılacağı anlatılmaktadır <xref:System.DateTime>, <xref:System.DateTimeOffset>, ve <xref:System.TimeZoneInfo> tarih ve saat verileriyle çalışırken türleri.

[Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) yerel sisteminizde mevcut saat dilimlerini numaralandırma açıklar.

[Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md) bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerini numaralandırma ve önceden tanımlanmış bir saat dilimi listesinden kullanıcılar izin örnekler verilmektedir.

[Nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimi nasıl erişileceği açıklar.

[Nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) örneği açıklar bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesnesi.

[Bir DateTimeOffset nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) yollarla ele bir <xref:System.DateTimeOffset> nesne oluşturulabilir ve hangi yollarla bir <xref:System.DateTime> değer dönüştürülebilir bir <xref:System.DateTimeOffset> değeri.

[Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) gün ışığından yararlanma saati gelen ve geçiş desteği olmayan özel bir saat dilimi oluşturmayı açıklar.

[Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) gün ışığından yararlanma saati gelen ve giden bir veya daha fazla geçişleri destekler özel bir saat dilimi oluşturmayı açıklar.

[Kaydetme ve saat dilimlerini geri yükleme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> seri hale getirme ve seri durumdan çıkarma saat dilimi veri için desteği ve bu özellikler kullanılabilecek senaryolardan bazıları göstermektedir.

[Nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) özel bir saat dilimi oluşturmak ve kaynak dosyası bilgilerini kaydetmek açıklar.

[Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) katıştırılmış kaynak dosyasına kaydedilen özel saat dilimlerini örneği açıklar.

[Tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) ekleme, çıkarılmasıyla ve karşılaştırma ilgili sorunlar ele alınmaktadır <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.

[Nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) tarih ve saat diliminin ayarlama kuralları yansıtan saat aritmetiği gerçekleştirme açıklanır.

[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) arasında dönüştürme açıklar <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.

[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) kez bir saat dilimine dönüştürülmesi açıklanmaktadır.

[Nasıl yapılır: belirsiz saatleri çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md) saat diliminin Standart Saati için eşleyerek belirsiz bir süre çözümlemeyi açıklar.

[Nasıl yapılır: kullanıcıların belirsiz saatleri çözmek izin](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) belirsiz yerel saat ve Eşgüdümlü Evrensel Saat arasında eşleme belirlemek bir kullanıcının olanak açıklar.

## <a name="reference"></a>Başvuru

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
