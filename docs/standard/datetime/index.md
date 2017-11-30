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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="3eda6-102">Tarih, saat ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="3eda6-102">Dates, times, and time zones</span></span>

<span data-ttu-id="3eda6-103">Temel yanı sıra <xref:System.DateTime> yapısı, .NET aşağıdaki sınıflar ile saat dilimleri çalışma Bu destek sağlar:</span><span class="sxs-lookup"><span data-stu-id="3eda6-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="3eda6-104">Bu sınıf sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölge ile çalışmak için kullanın. İşlevselliğini <xref:System.TimeZone> sınıfı tarafından değiştirilen büyük ölçüde <xref:System.TimeZoneInfo> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3eda6-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="3eda6-105">Bu sınıf, bir sistemde, yeni saat dilimleri oluşturma ve kolayca tarihler ve saatler bir saat diliminden diğerine dönüştürmek için önceden tanımlanmış hiçbir saat dilimi ile çalışmak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="3eda6-105">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="3eda6-106">Yeni geliştirme için kullanmak <xref:System.TimeZoneInfo> sınıfının yerine <xref:System.TimeZone> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="3eda6-106">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="3eda6-107">Tarihler ve saatler UTC olan uzaklık (veya fark) bilinen ile çalışmak için bu yapı kullanın.</span><span class="sxs-lookup"><span data-stu-id="3eda6-107">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="3eda6-108"><xref:System.DateTimeOffset> Yapısı birleştiren bir tarih ve saat değeri ile bu süre UTC uzaklığı.</span><span class="sxs-lookup"><span data-stu-id="3eda6-108">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="3eda6-109">UTC, bir tek tek tarih ve saat ilişkisini nedeniyle değer belirsizliğe zamanında tek bir nokta tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-109">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="3eda6-110">Böylece bir <xref:System.DateTimeOffset> değeri'den başka bir bir bilgisayardan daha taşınabilir bir <xref:System.DateTime> değeri.</span><span class="sxs-lookup"><span data-stu-id="3eda6-110">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="3eda6-111">Bu bölümde belgelerin saat dilimleri ile çalışmak için ve tarih ve saati bir saat diliminden diğerine dönüştürebilirsiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-111">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3eda6-112">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="3eda6-112">In this section</span></span>

<span data-ttu-id="3eda6-113">[Saat dilimi genel bakış](../../../docs/standard/datetime/time-zone-overview.md) terminolojisi, kavramları ve konuları saat dilimi algılayan uygulamaları oluşturmaya dahil açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3eda6-113">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="3eda6-114">[DateTime, DateTimeOffset, TimeSpan ve Timezoneınfo arasında seçim](../../../docs/standard/datetime/choosing-between-datetime.md) ne zaman kullanılacağı anlatılmaktadır <xref:System.DateTime>, <xref:System.DateTimeOffset>, ve <xref:System.TimeZoneInfo> tarih ve saat verileriyle çalışırken türleri.</span><span class="sxs-lookup"><span data-stu-id="3eda6-114">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="3eda6-115">[Yerel sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) yerel sisteminizde mevcut saat dilimlerini numaralandırma açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-115">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="3eda6-116">[Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md) bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerini numaralandırma ve önceden tanımlanmış bir saat dilimi listesinden kullanıcılar izin örnekler verilmektedir.</span><span class="sxs-lookup"><span data-stu-id="3eda6-116">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="3eda6-117">[Nasıl yapılır: ön tanımlı UTC ve yerel saat dilimi nesneleri erişim](../../../docs/standard/datetime/access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimi nasıl erişileceği açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-117">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="3eda6-118">[Nasıl yapılır: bir Timezoneınfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) örneği açıklar bir <xref:System.TimeZoneInfo> yerel sistem kayıt defterinden nesnesi.</span><span class="sxs-lookup"><span data-stu-id="3eda6-118">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="3eda6-119">[Bir DateTimeOffset nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) yollarla ele bir <xref:System.DateTimeOffset> nesne oluşturulabilir ve hangi yollarla bir <xref:System.DateTime> değer dönüştürülebilir bir <xref:System.DateTimeOffset> değeri.</span><span class="sxs-lookup"><span data-stu-id="3eda6-119">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="3eda6-120">[Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) gün ışığından yararlanma saati gelen ve geçiş desteği olmayan özel bir saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-120">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="3eda6-121">[Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) gün ışığından yararlanma saati gelen ve giden bir veya daha fazla geçişleri destekler özel bir saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-121">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="3eda6-122">[Kaydetme ve saat dilimlerini geri yükleme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> seri hale getirme ve seri durumdan çıkarma saat dilimi veri için desteği ve bu özellikler kullanılabilecek senaryolardan bazıları göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="3eda6-122">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="3eda6-123">[Nasıl yapılır: saat dilimlerini katıştırılmış kaynağa kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) özel bir saat dilimi oluşturmak ve kaynak dosyası bilgilerini kaydetmek açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-123">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="3eda6-124">[Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) katıştırılmış kaynak dosyasına kaydedilen özel saat dilimlerini örneği açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-124">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="3eda6-125">[Tarih ve saatlerle aritmetik işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) ekleme, çıkarılmasıyla ve karşılaştırma ilgili sorunlar ele alınmaktadır <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.</span><span class="sxs-lookup"><span data-stu-id="3eda6-125">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="3eda6-126">[Nasıl yapılır: tarih ve saat aritmetiği saat dilimini kullanır](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) tarih ve saat diliminin ayarlama kuralları yansıtan saat aritmetiği gerçekleştirme açıklanır.</span><span class="sxs-lookup"><span data-stu-id="3eda6-126">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="3eda6-127">[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) arasında dönüştürme açıklar <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri.</span><span class="sxs-lookup"><span data-stu-id="3eda6-127">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="3eda6-128">[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) kez bir saat dilimine dönüştürülmesi açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="3eda6-128">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="3eda6-129">[Nasıl yapılır: belirsiz saatleri çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md) saat diliminin Standart Saati için eşleyerek belirsiz bir süre çözümlemeyi açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-129">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="3eda6-130">[Nasıl yapılır: kullanıcıların belirsiz saatleri çözmek izin](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) belirsiz yerel saat ve Eşgüdümlü Evrensel Saat arasında eşleme belirlemek bir kullanıcının olanak açıklar.</span><span class="sxs-lookup"><span data-stu-id="3eda6-130">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="3eda6-131">Başvuru</span><span class="sxs-lookup"><span data-stu-id="3eda6-131">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
