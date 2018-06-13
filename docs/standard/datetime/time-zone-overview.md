---
title: Saat dilimi genel bakış
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
ms.openlocfilehash: 85483e4319b56c0df150558ce6c6a3878a6fa041
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578098"
---
# <a name="time-zone-overview"></a>Saat dilimi genel bakış

<xref:System.TimeZoneInfo> Sınıfı saat dilimi kullanabilen uygulamaların oluşturulmasını basitleştirir. <xref:System.TimeZone> Sınıfı yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) ile çalışma destekler. <xref:System.TimeZoneInfo> Sınıfı, kayıt defterinde yanı saat dilimi bilgileri hakkında önceden tanımlanmış Bu bölgeler her ikisi de destekler. Aynı zamanda <xref:System.TimeZoneInfo> sistem hakkında bilgi bulunmaz özel saat dilimlerini tanımlamak için.

## <a name="time-zone-essentials"></a>Saat dilimi temelleri

Bir saat dilimi, aynı anda kullanıldığı bir coğrafi bölgedir. Genellikle, ancak her zaman, bir saat birbirinden bitişik saat dilimleri değildir. Herhangi bir dünyanın saat dilimleri süresi uzaklık gelen Eşgüdümlü Evrensel Saat (UTC) olarak ifade edilebilir.

Yaz Saati dünyanın saat dilimlerini destekler. Yay veya erken Yaz bir saat ileri zaman ilerledikten ve normal (veya standart) saati geç yaz veya sonbaharda, döndürme tarafından gün ışığından yararlanma saati en üst düzeye çıkarmak gün ışığından yararlanma saati çalışır. Bu değişiklikler için ve Standart Saati ayarlama kuralları bilinir.

Belirli bir saat diliminde Gün ışığından yararlanma saati gelen ve giden geçiş, bir sabit veya değişken ayarlama kuralı tanımlanabilir. Bir sabit ayarlama kuralı geçişi için veya Yaz Saati her yıl oluştuğu belirli bir tarih ayarlar. Örneğin, her yıl Ekim 25 oluşuyor Standart Saati gün ışığından yararlanma saati bir geçiş sabit ayarlama kuralı izler. Daha fazla ortak kayan geçişi için belirli bir ay belirli bir haftanın belirli bir gün için veya yaz saati ayarlamak ayarlama kuralları. Örneğin, bir geçiş Standart Saati gün ışığından yararlanma saati Mart üçüncü Pazar günü oluşan bir kayan ayarlama kuralı izler.

Ayarlama kuralları destek saat dilimleri için iki tür anormal kez gün ışığından yararlanma saati gelen ve giden geçiş oluşturur: Geçersiz zamanları ve belirsiz saatleri. Geçersiz zaman standart saati gün ışığından yararlanma saati geçiş tarafından oluşturulan varolmayan bir saattir. Örneğin, belirli bir gündeki saat 2: 00'da bu geçiş oluşur ve nedenleri 3: 00'da bir değişiklik, 2: 00'da arasındaki her zaman aralığını saat ve 2:59:99 A.M. geçersiz. Belirsiz saat tek bir saat diliminde iki farklı saatler için eşlenmiş bir zamandır. Standart Saati gün ışığından yararlanma saati geçiş tarafından oluşturulur. Örneğin, belirli bir gündeki saat 2: 00'da bu geçiş oluşur ve nedenleri 1: 00'da bir değişiklik, her zaman aralığı 1: 00'da arasındaki süre ve 1:59:99 A.M. Standart saat veya gün ışığından yararlanma saati olarak yorumlanacak.

## <a name="time-zone-terminology"></a>Saat dilimi terminolojisi

Aşağıdaki tabloda saat dilimleri ve geliştirme saat dilimi ile uyumlu uygulamalar ile çalışırken sık kullanılan terimleri tanımlar.

| Terim            | Tanım |
| --------------- | ---------- |
| Ayarlama kuralı | Standart Saati gün ışığından yararlanma saati için ve geri Yaz Saati Standart Saati için geçiş oluştuğunda tanımlayan bir kural. Kural yerinde olduğunda tanımlayan bir başlangıç ve bitiş tarihi her ayarlama kuralı varsa (örneğin, ayarlama kuralı 1 Ocak 1986 konuma 31 Aralık 2006'ın yüklü olduğu eder), bir delta (Standart Saati değişiklikler sonucunda th uygulamayı süre miktarı e ayarlama kuralı), belirli bir tarih ve geçişleri ayarlama süresi boyunca gerçekleşmesi için olan zaman ilgili bilgiler. Geçişler, sabit bir kural veya kayan kural izleyebilirsiniz. |
| Belirsiz saat  | Tek bir saat diliminde iki farklı saatler için eşlenmiş bir zamanı seçin. Saatin geçmişe, gibi standart saati bir saat diliminin gün ışığından yararlanma saati geçiş sırasında ayarlanır oluşur. Örneğin, belirli bir gündeki saat 2: 00'da bu geçiş oluşur ve nedenleri 1: 00'da bir değişiklik, her zaman aralığı 1: 00'da arasındaki süre ve 1:59:99 A.M. Standart saat veya gün ışığından yararlanma saati olarak yorumlanacak. |
| Sabit kural      | Geçiş için belirli bir tarih için veya Yaz Saati ayarlar ayarlama kuralı. Örneğin, her yıl Ekim 25 oluşuyor Standart Saati gün ışığından yararlanma saati bir geçiş sabit ayarlama kuralı izler. |
| Kayan kural   | Belirli bir ay geçişi için belirli bir haftanın belirli bir gün için veya Yaz Saati ayarlar ayarlama kuralı. Örneğin, bir geçiş Standart Saati gün ışığından yararlanma saati Mart üçüncü Pazar günü oluşan bir kayan ayarlama kuralı izler. |
| Geçersiz saat    | Standart Saati gün ışığından yararlanma saati geçiş yapay varolmayan zamanı. Saatin İleri, zaman içindeki gibi bir saat diliminin standart saat, gün ışığından yararlanma saatine geçiş sırasında ayarlanır oluşur. Örneğin, belirli bir gündeki saat 2: 00'da bu geçiş oluşur ve nedenleri 3: 00'da bir değişiklik, 2: 00'da arasındaki her zaman aralığını saat ve 2:59:99 A.M. geçersiz. |
| Geçiş süresi | Belirli bir zaman hakkında bilgi değiştirin, değişikliği Yaz Saati Standart Saati (veya tersi) gibi belirli bir saat diliminde. |

## <a name="time-zones-and-the-timezoneinfo-class"></a>Saat dilimleri ve Timezoneınfo sınıfı

.NET içinde bir <xref:System.TimeZoneInfo> nesnesi, bir saat dilimi temsil eder. <xref:System.TimeZoneInfo> Sınıfı içeren bir <xref:System.TimeZoneInfo.GetAdjustmentRules%2A> bir dizi döndürür yöntemi <xref:System.TimeZoneInfo.AdjustmentRule> nesneleri. Bu dizinin her bir öğesine belirli bir süre için gün ışığından yararlanma saati gelen ve giden geçiş hakkında bilgi sağlar. (Gün ışığından yararlanma saati desteklemeyen saat dilimleri için yöntem boş bir dizi döndürür.) Her <xref:System.TimeZoneInfo.AdjustmentRule> nesnesi bir <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionStart%2A> ve <xref:System.TimeZoneInfo.AdjustmentRule.DaylightTransitionEnd%2A> belirli tarih ve saat geçişin gün ışığından yararlanma saati gelen ve giden tanımlar özelliği. <xref:System.TimeZoneInfo.TransitionTime.IsFixedDateRule%2A> Özelliği, geçiş sabit veya değişken olup olmadığını belirtir.

.NET Windows işletim sistemi tarafından sağlanan ve kayıt defterinde depolanan saat dilimi bilgilerini kullanır. Dünya saat dilimleri sayısı nedeniyle, tüm mevcut saat dilimlerini kayıt defterinde temsil edilir. Ayrıca, kayıt defteri dinamik bir yapı olduğundan, önceden tanımlanmış saat dilimleri eklenecek veya kaldırılmış. Son olarak, kayıt defteri mutlaka geçmiş saat dilimi veri içermiyor. Örneğin, Windows XP'de kayıt defteri saat dilimi ayarlamalar tek bir dizi hakkındaki verileri içerir. Windows Vista, tek bir saat dilimi için yıllık belirli aralıklarla uygulama birden çok ayarlama kuralları olduğu anlamına gelir dinamik saat dilimi veri destekler. Ancak, Windows Vista kayıt defteri ve Destek gün ışığından yararlanma saati içinde tanımlanan çoğu saat dilimlerinde yalnızca bir veya iki önceden tanımlanmış ayarlama kuralları vardır.

Bağımlılığı, <xref:System.TimeZoneInfo> kayıt defterindeki sınıfı anlamına gelir saat dilimi algılayan bir uygulama belirli bir saat dilimi kayıt defterinde tanımlanır belirli olamayacağını. Sonuç olarak, belirli bir saat dilimi (dışında yerel saat dilimini veya UTC temsil eden saat dilimi) örneği girişimi özel durum işleme kullanmanız gerekir. Gerekli olursa devam etmek için uygulama izin vererek bazı yöntemi sağlamalıdır <xref:System.TimeZoneInfo> nesne kayıt defterinden örneği olamaz.

Gerekli bir saat dilimi yokluğu işlemek için <xref:System.TimeZoneInfo> sınıfı içeren bir <xref:System.TimeZoneInfo.CreateCustomTimeZone%2A> kayıt defterinde bulunamadı özel saat dilimlerini oluşturmak için kullanabileceğiniz yöntemi. Özel bir saat dilimi oluşturma hakkında daha fazla bilgi için bkz: [nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) ve [nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md). Ayrıca, <xref:System.TimeZoneInfo.ToSerializedString%2A> yöntemi bir dizeye yeni oluşturulan bir saat dilimi ve bir veri deposu (örneğin, bir veritabanı, bir metin dosyası, kayıt defteri veya uygulama kaynağı) kaydedin. Daha sonra <xref:System.TimeZoneInfo.FromSerializedString%2A> Bu dize dönüştürmek için yöntem başa bir <xref:System.TimeZoneInfo> nesnesi. Ayrıntılar için bkz [nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) ve [nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md).

Her bir saat dilimi UTC temel uzaklığı tarafından ve aynı zamanda tüm mevcut ayarlama kuralları yansıtır UTC uzaklık tarafından belirlenir çünkü saati bir saat dilimi, bir süre içinde başka bir saat dilimi kolayca dönüştürülebilir. Bu amaçla <xref:System.TimeZoneInfo> nesnesi dahil olmak üzere, birkaç dönüştürme yöntemleri içerir:

* <xref:System.TimeZoneInfo.ConvertTimeFromUtc%2A>, belirlenmiş bir saat dilimi zamana UTC dönüştüren.

* <xref:System.TimeZoneInfo.ConvertTimeToUtc%2A>, UTC için belirlenmiş bir saat dilimi zamanında dönüştürür.

* <xref:System.TimeZoneInfo.ConvertTime%2A>, başka bir belirtilen saat dilimi zamana belirlenmiş bir saat dilimi zamanında dönüştüren.

* <xref:System.TimeZoneInfo.ConvertTimeBySystemTimeZoneId%2A>, saat dilimi tanımlayıcıları kullanır (yerine <xref:System.TimeZoneInfo> nesneler) başka bir belirtilen saat dilimi zamanında bir belirtilen saat dilimi zamanında dönüştürmek için parametre olarak.

Saatleri saat dilimleri arasında dönüştürme hakkında daha fazla bilgi için bkz: [saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md).

## <a name="see-also"></a>Ayrıca bkz.

[Tarihler, saatler ve saat dilimleri](../../../docs/standard/datetime/index.md)
