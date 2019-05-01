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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="b91ea-102">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="b91ea-102">Dates, times, and time zones</span></span>

<span data-ttu-id="b91ea-103">Temel yanı sıra <xref:System.DateTime> yapısı, .NET aşağıdaki sınıflar ile saat dilimleri çalışma Bu destek sağlar:</span><span class="sxs-lookup"><span data-stu-id="b91ea-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="b91ea-104">Bu sınıf, sistemin yerel saat dilimi (UTC) Eşgüdümlü Evrensel Saat dilimi ile çalışmak için kullanın. İşlevselliğini <xref:System.TimeZone> sınıfı tarafından değiştirilen büyük ölçüde <xref:System.TimeZoneInfo> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b91ea-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="b91ea-105">Bu sınıf, bir sistemde yeni saat dilimleri oluşturma ve kolayca tarihler ve saatler bir saat diliminden diğerine dönüştürmek için önceden tanımlanmış hiçbir saat dilimi ile çalışmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b91ea-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="b91ea-106">Yeni geliştirme için kullanmak <xref:System.TimeZoneInfo> sınıfı yerine <xref:System.TimeZone> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b91ea-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="b91ea-107">Bu yapı, tarihler ve saatler UTC olan uzaklık (veya fark) bilinen ile çalışmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="b91ea-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="b91ea-108"><xref:System.DateTimeOffset> Yapısı birleştiren bir tarih ve saat değerinin saat ile UTC ile olan uzaklığını.</span><span class="sxs-lookup"><span data-stu-id="b91ea-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="b91ea-109">UTC, tek bir tarih ve saat ilişkisini nedeniyle değer üretemez zaman tek bir nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="b91ea-110">Böylece bir <xref:System.DateTimeOffset> değeri diğerinden için bir bilgisayardan daha taşınabilir bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="b91ea-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="b91ea-111">Belgelerinin bu bölümü ile saat dilimleri çözmek ve tarihler ve saatler bir saat diliminden diğerine dönüştürebilirsiniz saat dilimiyle uyumlu uygulamalar oluşturmak için gereken bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="b91ea-112">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="b91ea-112">In this section</span></span>

<span data-ttu-id="b91ea-113">[Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md) terminoloji, kavramlar ve saat dilimiyle uyumlu uygulamalar oluşturmak için gerekli olan sorunlar ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b91ea-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="b91ea-114">[DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md) ne zaman kullanılacağı ele alınmaktadır <xref:System.DateTime>, <xref:System.DateTimeOffset>, ve <xref:System.TimeZoneInfo> türleri tarih ve saat verilerle çalışırken.</span><span class="sxs-lookup"><span data-stu-id="b91ea-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="b91ea-115">[Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) yerel bir sistemde bulunan saat dilimlerini numaralandırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="b91ea-116">[Nasıl yapılır: Bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md) kullanıcıları önceden tanımlanmış bir saat dilimi bir listeden seç sağlar ve bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerini numaralandırma örnekleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="b91ea-117">[Nasıl yapılır: Ön tanımlı UTC ve yerel saat dilimi nesnelerine erişim](../../../docs/standard/datetime/access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimi nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="b91ea-118">[Nasıl yapılır: Bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) örneğini açıklar bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesne.</span><span class="sxs-lookup"><span data-stu-id="b91ea-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="b91ea-119">[Bir DateTimeOffset nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) yöntemler anlatılır bir <xref:System.DateTimeOffset> nesne oluşturulabilir ve yöntemler bir <xref:System.DateTime> değer dönüştürülebilir bir <xref:System.DateTimeOffset> değeri.</span><span class="sxs-lookup"><span data-stu-id="b91ea-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="b91ea-120">[Nasıl yapılır: Ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Yaz Saati gelen ve geçiş desteği olmayan özel bir saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="b91ea-121">[Nasıl yapılır: Ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Yaz Saati gelen ve giden bir veya daha fazla geçişleri destekleyen özel bir saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="b91ea-122">[Saat dilimlerini geri yükleme ve kaydetme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> desteklemek için serileştirme ve seri durumundan çıkarma saat dilimi veri ve bu özellikleri kullanılabilen senaryolardan bazıları gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b91ea-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="b91ea-123">[Nasıl yapılır: Saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) özel bir saat dilimi oluşturma ve bir kaynak dosyasında bilgilerini kaydetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="b91ea-124">[Nasıl yapılır: Katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) bir gömülü kaynak dosyasına kaydedildi özel saat dilimi örneğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="b91ea-125">[Tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) ekleme, çıkarma ve karşılaştırma ilgili sorunlar ele alınmıştır <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.</span><span class="sxs-lookup"><span data-stu-id="b91ea-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="b91ea-126">[Nasıl yapılır: Tarih ve saat aritmetiğinde saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) nasıl tarih ve saat diliminin ayarlama kuralları yansıtan saat aritmetiği gerçekleştirileceği ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="b91ea-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="b91ea-127">[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) arasında nasıl dönüştürme yapılacağını açıklar <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.</span><span class="sxs-lookup"><span data-stu-id="b91ea-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="b91ea-128">[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) saatler bir saat diliminden dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="b91ea-129">[Nasıl yapılır: Belirsiz saatleri çözmelerine](../../../docs/standard/datetime/resolve-ambiguous-times.md) belirsiz bir saat, saat diliminin Standart Saati için eşleyerek çözümlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="b91ea-130">[Nasıl yapılır: Kullanıcıların belirsiz saatleri çözmelerine izin](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) bir kullanıcının bir belirsiz yerel saat ve Eşgüdümlü Evrensel Saat arasındaki eşlemeyi belirlemek olanak açıklar.</span><span class="sxs-lookup"><span data-stu-id="b91ea-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="b91ea-131">Başvuru</span><span class="sxs-lookup"><span data-stu-id="b91ea-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
