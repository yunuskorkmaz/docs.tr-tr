---
title: Saat dilimine genel bakış
ms.date: 04/10/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- time zones [.NET Framework], about time zones
- transition time [.NET Framework]
- TimeZoneInfo class, about TimeZoneInfo class
- time zones [.NET Framework], creating
- invalid time [.NET Framework]
- fixed rule [.NET Framework]
- ambiguous time [.NET Framework]
- floating rule [.NET Framework]
- daylight saving time [.NET Framework]
- adjustment rule [.NET Framework]
- time zones [.NET Framework], terminology
ms.assetid: c4b7ed01-5e38-4959-a3b6-ef9765d6ccf1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0eb24c7c4f2c60a9c16d903ab1e845b058e280f7
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44342719"
---
# <a name="time-zone-overview"></a>Saat dilimine genel bakış

<xref:System.TimeZoneInfo> Sınıfı saat dilimiyle uyumlu uygulamaların oluşturulmasını basitleştirir. <xref:System.TimeZone> Sınıfı yerel saat dilimi ile eşgüdümlü evrensel saat (UTC) çalışma destekler. <xref:System.TimeZoneInfo> Sınıfı, kayıt defterinde yanı sıra tüm saat dilimi bilgileri hakkında önceden tanımlanmış Bu bölgeler her ikisini de destekler. Ayrıca <xref:System.TimeZoneInfo> hakkında hiçbir bilgi sistemi olan özel saat dilimi tanımlamak için.

## <a name="time-zone-essentials"></a>Saat dilimi temel bileşenleri

Bir saat dilimi, aynı zamanda kullanıldığı bir coğrafi bölgedir. Genellikle, ancak her zaman, bir saat uzaklıkta bitişik saat dilimlerini değildir. Herhangi bir dünyanın saat dilimlerini sürede uzaklık ile eşgüdümlü evrensel saat (UTC) olarak ifade edilebilir.

Birçok dünyanın saat dilimi gün ışığından yararlanma destekler. Yaz Saati bir saat spring veya erken yaz saati ileri ilerledikten ve geç yaz veya fall normal (veya standart) saat gün ışığından yararlanma saat en üst düzeye çıkarmak çalışır. Bu değişiklikler Standart Saati gelen ve ayarlama kuralları bilinir.

Belirli bir saat dilimindeki Yaz Saati gelen ve geçiş sabit veya bir kayan ayarlama kuralı tanımlanabilir. Bir sabit ayarlama kuralı belirli bir tarih veya gün ışığından yararlanma birinden geçmesinin her yıl oluştuğu ayarlar. Örneğin, her yıl 25 Ekim oluşan standart saati gün ışığından yararlanma bir geçiş sabit ayarlama kuralı izler. Çok yaygın kullanılan kayan ayarlama kuralları, geçiş için belirli bir ay, belirli bir haftanın belirli bir gün ışığından yararlanma saatine göre gelen veya ayarlayın. Örneğin, bir geçiş Standart Saati Mart üçüncü Pazar günü gerçekleşen ışığından kayan bir ayarlama kuralı izler.

Ayarlama kuralları destek saat dilimleri için iki tür anormal bir kez yaz saati gelen ve geçiş oluşturur: geçersiz bir kez ve belirsiz saatleri. Geçersiz bir zamandır, Standart Saati gün ışığından yararlanma saatine geçiş tarafından oluşturulan varolmayan bir zamandır. Örneğin, bu geçiş, belirli bir gündeki saat 2: 00'da gerçekleşir sebebini saati 3: 00'da değişiklik, 2: 00'da arasındaki her zaman aralığı ve 2:59:99 AM geçersiz. Belirsiz bir saat tek bir saat dilimindeki iki farklı saatler için eşlenmiş bir zamandır. Geçiş Standart Saati gün ışığından yararlanma saatine göre oluşturulur. Örneğin, bu geçiş, belirli bir gündeki saat 2: 00'da gerçekleşir sebebini saat 1: 00'da değişiklik, arasında 1: 00'da her zaman aralığı ve 1:59:99 AM Standart Saati veya bir yaz saati olarak yorumlanabilir.

## <a name="time-zone-terminology"></a>Saat dilimi terminolojisi

Aşağıdaki tabloda, saat dilimlerini ve saat dilimiyle uyumlu uygulamalar geliştirmeye çalışırken yaygın olarak kullanılan terimleri tanımlar.

| Terim            | Tanım |
| --------------- | ---------- |
| Ayarlama kuralı | Standart saatten Yaz ve yeniden yaz saati Standart Saati için geçiş oluştuğunda tanımlayan bir kural. Her ayarlama kuralı kural yerinde olduğunda tanımlayan bir başlangıç ve bitiş tarihi yok (örneğin, ayarlama kuralı 1 Ocak 1986 konuma 31 Aralık 2006 bulunduğu), bir delta (süreyi Standart Saati değişiklikleri th uygulamanın sonucu e ayarlama kuralı), belirli bir tarih ve geçişleri ayarlama aralığında olan zaman ilgili bilgiler. Geçişler sabit bir kural veya bir kayan kural takip edebilirsiniz. |
| Belirsiz saat  | Tek bir saat dilimindeki iki farklı saatler için eşlenmiş bir saat. Saatin geri sürede gibi standart saati kendi saat diliminin gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur. Örneğin, bu geçiş, belirli bir gündeki saat 2: 00'da gerçekleşir sebebini saat 1: 00'da değişiklik, arasında 1: 00'da her zaman aralığı ve 1:59:99 AM Standart Saati veya bir yaz saati olarak yorumlanabilir. |
| Sabit kural      | Geçiş için belirli bir tarih veya gün ışığından yararlanma buradan ayarlar ayarlama kuralı. Örneğin, her yıl 25 Ekim oluşan standart saati gün ışığından yararlanma bir geçiş sabit ayarlama kuralı izler. |
| Kayan kural   | Geçiş için belirli bir ay, belirli bir haftanın belirli bir gün için veya Yaz Saati ayarlar ayarlama kuralı. Örneğin, bir geçiş Standart Saati Mart üçüncü Pazar günü gerçekleşen ışığından kayan bir ayarlama kuralı izler. |
| Geçersiz zaman    | Bir yapıdır Standart Saati gün ışığından yararlanma saatine geçiş, varolmayan bir saat. Saatin ileriye doğru zamanda gibi bir saat diliminin standart saat, gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur. Örneğin, bu geçiş, belirli bir gündeki saat 2: 00'da gerçekleşir sebebini saati 3: 00'da değişiklik, 2: 00'da arasındaki her zaman aralığı ve 2:59:99 AM geçersiz. |
| Geçiş süresi | Belirli bir zaman hakkında bilgi değiştirmek Yaz Saati Standart Saati veya tam tersi değişiklik gibi belirli bir saat diliminde. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Saat dilimleri ve Timezoneınfo sınıfı

. NET'te, bir <xref:System.TimeZoneInfo> nesnesi bir saat dilimini temsil eder. <xref:System.TimeZoneInfo> Sınıfı içeren bir <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> bir dizi döndüren yöntem <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri. Bu dizinin her öğesinin belirli bir süre için Yaz Saati gelen ve geçiş hakkında bilgi sağlar. (Yaz Saati desteklemeyen saat dilimleri için yöntem boş bir dizi döndürür.) Her <xref:System.TimeZoneInfo.AdjustmentRule> nesnesinin bir <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> ve <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> Yaz Saati gelen ve belirli bir tarih ve saat geçişin tanımlayan özellik. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> Özelliği, geçiş sabit veya değişken olup olmadığını gösterir.

.NET Windows işletim sistemi tarafından sağlanan ve kayıt defterinde depolanan saat dilimi bilgilerini kullanır. Dünya saat dilimi sayısı nedeniyle, tüm mevcut saat dilimlerini kayıt defterinde temsil edilir. Ayrıca, kayıt defteri dinamik yapısı olduğundan, önceden tanımlanmış saat dilimleri için eklenen veya kaldırılmış. Son olarak, kayıt defteri mutlaka geçmiş saat dilimi veri içermiyor. Örneğin, Windows XP'de kayıt defteri saat dilimi ayarlarını yalnızca tek bir dizi ilgili verileri içerir. Windows Vista, tek bir saat dilimi için belirli aralıklarla yıllık uygulanan birden çok ayarlama kuralları olabilir yani dinamik saat dilimi veri destekler. Ancak, Windows Vista kayıt ve Destek ışığından tanımlanan çoğu saat dilimlerini yalnızca bir veya iki önceden tanımlanmış ayarlama kuralları vardır.

Bağımlılık, <xref:System.TimeZoneInfo> kayıt defterindeki sınıfı, saat dilimiyle uyumlu bir uygulama belirli bir saat dilimini kayıt defterinde tanımlanır belirli olamayacağını anlamına gelir. Sonuç olarak, belirli bir saat dilimi (veya yerel saat dilimi UTC temsil eden saat dilimi dışında) örneği girişimi, özel durum işleme kullanmanız gerekir. Uygulamayı gerekli bir devam etmesine izin vererek bazı yöntemi sağlamalıdır <xref:System.TimeZoneInfo> nesnesi kayıt defterinden örneği olamaz.

Gerekli bir saat dilimi olmaması işlemek için <xref:System.TimeZoneInfo> sınıfı içeren bir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterinde bulunamadı özel saat dilimleri oluşturma için kullanabileceğiniz yöntemi. Özel bir saat dilimi oluşturma hakkında daha fazla bilgi edinmek için bkz. [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md). Ayrıca, kullanabileceğiniz <xref:System.TimeZoneInfo.ToSerializedString%2A> yeni oluşturulan bir saat dilimi bir dizeye Dönüştür ve bir veri deposuna (örneğin, bir veritabanı, bir metin dosyası, kayıt defteri veya uygulama kaynağı) kaydetmek için yöntemi. Ardından <xref:System.TimeZoneInfo.FromSerializedString%2A> Bu dize dönüştürmek için yöntemi yeniden bir <xref:System.TimeZoneInfo> nesne. Ayrıntılar için bkz [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

Her saat dilimi UTC temel bir uzaklık yanı sıra mevcut ayarlama kurallar yansıtan utc'den uzaklık tarafından belirlenir çünkü saati bir saat dilimi, başka bir saat dilimindeki saati kolaylıkla dönüştürülebilir. Bu amaçla <xref:System.TimeZoneInfo> nesne dahil olmak üzere birkaç dönüştürme yöntemleri içerir:

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, belirli bir saat dilimindeki saati için UTC dönüştüren.

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, UTC için belirlenen bir saat dilimindeki saati dönüştürür.

* <xref:System.TimeZoneInfo.ConvertTime%2A>, başka bir belirtilen saat diliminde saate belirlenen bir saat dilimindeki saati dönüştüren.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, saat dilimi tanımlayıcıları kullanır (yerine <xref:System.TimeZoneInfo> nesneler) olarak belirlenmiş bir saat dilimindeki saati başka bir belirtilen saat dilimindeki saati dönüştürmek için parametreleri.

Saatleri saat dilimleri arasında dönüştürme hakkında daha fazla bilgi için bkz [saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md).

## <a name="see-also"></a>Ayrıca bkz.

* [Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
