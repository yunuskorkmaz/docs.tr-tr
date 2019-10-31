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
# <a name="dates-times-and-time-zones"></a><span data-ttu-id="73985-102">Tarihler, saatler ve saat dilimleri</span><span class="sxs-lookup"><span data-stu-id="73985-102">Dates, times, and time zones</span></span>

<span data-ttu-id="73985-103">Temel <xref:System.DateTime> yapısına ek olarak, .NET, Saat dilimleriyle çalışmayı destekleyen aşağıdaki sınıfları sağlar:</span><span class="sxs-lookup"><span data-stu-id="73985-103">In addition to the basic <xref:System.DateTime> structure, .NET provides the following classes that support working with time zones:</span></span>

* <xref:System.TimeZone>

  <span data-ttu-id="73985-104">Sistemin yerel saat dilimi ve Eşgüdümlü Evrensel Saat (UTC) bölgesi ile çalışmak için bu sınıfı kullanın.</span><span class="sxs-lookup"><span data-stu-id="73985-104">Use this class to work with the system's local time zone and the Coordinated Universal Time (UTC) zone.</span></span> <span data-ttu-id="73985-105"><xref:System.TimeZone> sınıfının işlevselliği, büyük ölçüde <xref:System.TimeZoneInfo> sınıfının yerini almıştır.</span><span class="sxs-lookup"><span data-stu-id="73985-105">The functionality of the <xref:System.TimeZone> class is largely superseded by the <xref:System.TimeZoneInfo> class.</span></span>

* <xref:System.TimeZoneInfo>

  <span data-ttu-id="73985-106">Bu sınıfı, bir sistemde önceden tanımlanmış tüm Saat dilimleriyle çalışmak, yeni saat dilimleri oluşturmak ve Tarih ve saatleri bir saat diliminden diğerine kolayca dönüştürmek için kullanın.</span><span class="sxs-lookup"><span data-stu-id="73985-106">Use this class to work with any time zone that is predefined on a system, to create new time zones, and to easily convert dates and times from one time zone to another.</span></span> <span data-ttu-id="73985-107">Yeni geliştirme için <xref:System.TimeZone> sınıfı yerine <xref:System.TimeZoneInfo> sınıfını kullanın.</span><span class="sxs-lookup"><span data-stu-id="73985-107">For new development, use the <xref:System.TimeZoneInfo> class instead of the <xref:System.TimeZone> class.</span></span>

* <xref:System.DateTimeOffset>

  <span data-ttu-id="73985-108">UTC 'den gelen fark (veya farkı) bilindiğinde tarih ve saatlerle çalışmak için bu yapıyı kullanın.</span><span class="sxs-lookup"><span data-stu-id="73985-108">Use this structure to work with dates and times whose offset (or difference) from UTC is known.</span></span> <span data-ttu-id="73985-109"><xref:System.DateTimeOffset> yapısı bir tarih ve saat değerini UTC 'den bu saatin bir değeriyle birleştirir.</span><span class="sxs-lookup"><span data-stu-id="73985-109">The <xref:System.DateTimeOffset> structure combines a date and time value with that time's offset from UTC.</span></span> <span data-ttu-id="73985-110">UTC ile ilişkisi nedeniyle, bağımsız bir tarih ve saat değeri kesin bir zamanda tek bir noktayı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="73985-110">Because of its relationship to UTC, an individual date and time value unambiguously identifies a single point in time.</span></span> <span data-ttu-id="73985-111">Bu, bir <xref:System.DateTimeOffset> değerini bir bilgisayardan <xref:System.DateTime> bir değerden diğerine daha taşınabilir hale getirir.</span><span class="sxs-lookup"><span data-stu-id="73985-111">This makes a <xref:System.DateTimeOffset> value more portable from one computer to another than a <xref:System.DateTime> value.</span></span>

<span data-ttu-id="73985-112">Belgelerinin bu bölümü, Saat dilimleriyle çalışmanız ve Tarih ve saatleri bir saat diliminden diğerine dönüştürebileceğiniz saat dilimi kullanan uygulamalar oluşturmak için gereken bilgileri sağlar.</span><span class="sxs-lookup"><span data-stu-id="73985-112">This section of the documentation provides the information that you need to work with time zones and to create time zone-aware applications that can convert dates and times from one time zone to another.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="73985-113">Bu bölümde</span><span class="sxs-lookup"><span data-stu-id="73985-113">In this section</span></span>

<span data-ttu-id="73985-114">[Saat dilimine genel bakış](../../../docs/standard/datetime/time-zone-overview.md) Saat dilimi kullanan uygulamalar oluşturma ile ilgili terminolojiyi, kavramları ve sorunları açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-114">[Time zone overview](../../../docs/standard/datetime/time-zone-overview.md) Discusses the terminology, concepts, and issues involved in creating time zone-aware applications.</span></span>

<span data-ttu-id="73985-115">[DateTime, DateTimeOffset, TimeSpan ve TimeZoneInfo arasında seçim yapma](../../../docs/standard/datetime/choosing-between-datetime.md) Tarih ve saat verileriyle çalışırken <xref:System.DateTime>, <xref:System.DateTimeOffset>ve <xref:System.TimeZoneInfo> türlerinin ne zaman kullanılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-115">[Choosing between DateTime, DateTimeOffset, TimeSpan, and TimeZoneInfo](../../../docs/standard/datetime/choosing-between-datetime.md) Discusses when to use the <xref:System.DateTime>, <xref:System.DateTimeOffset>, and <xref:System.TimeZoneInfo> types when working with date and time data.</span></span>

<span data-ttu-id="73985-116">[Yerel bir sistemde tanımlanan saat dilimlerini bulma](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Yerel bir sistemde bulunan saat dilimlerinin nasıl numaralandırılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-116">[Finding the time zones defined on a local system](../../../docs/standard/datetime/finding-the-time-zones-on-local-system.md) Describes how to enumerate the time zones found on a local system.</span></span>

<span data-ttu-id="73985-117">[Nasıl yapılır: bir bilgisayarda mevcut saat dilimlerini numaralandırma](../../../docs/standard/datetime/enumerate-time-zones.md) Bir bilgisayarın kayıt defterinde tanımlanan saat dilimlerinin numaralandırılacağı ve kullanıcıların bir listeden önceden tanımlanmış bir saat dilimi seçmesini sağlayan örnekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="73985-117">[How to: Enumerate time zones present on a computer](../../../docs/standard/datetime/enumerate-time-zones.md) Provides examples that enumerate the time zones defined in a computer's registry and that let users select a predefined time zone from a list.</span></span>

<span data-ttu-id="73985-118">[Nasıl yapılır: önceden TANıMLANMıŞ UTC ve yerel saat dilimi nesnelerine erişme](../../../docs/standard/datetime/access-utc-and-local.md) Eşgüdümlü Evrensel Saat ve yerel saat dilimine nasıl erişebileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-118">[How to: Access the predefined UTC and local time zone objects](../../../docs/standard/datetime/access-utc-and-local.md) Describes how to access Coordinated Universal Time and the local time zone.</span></span>

<span data-ttu-id="73985-119">[Nasıl yapılır: TimeZoneInfo nesnesinin örneğini oluşturma](../../../docs/standard/datetime/instantiate-time-zone-info.md) Yerel sistem kayıt defterinden bir <xref:System.TimeZoneInfo> nesnesinin örneğini oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-119">[How to: Instantiate a TimeZoneInfo object](../../../docs/standard/datetime/instantiate-time-zone-info.md) Describes how to instantiate a <xref:System.TimeZoneInfo> object from the local system registry.</span></span>

<span data-ttu-id="73985-120">[DateTimeOffset nesnesini örnekleme](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) <xref:System.DateTimeOffset> nesnenin örneklendiği ve bir <xref:System.DateTime> değerinin <xref:System.DateTimeOffset> değere dönüştürülebileceği yollar açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="73985-120">[Instantiating a DateTimeOffset object](../../../docs/standard/datetime/instantiating-a-datetimeoffset-object.md) Discusses the ways in which a <xref:System.DateTimeOffset> object can be instantiated, and the ways in which a <xref:System.DateTime> value can be converted to a <xref:System.DateTimeOffset> value.</span></span>

<span data-ttu-id="73985-121">[Nasıl yapılır: ayarlama kuralları olmadan saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Gün ışığından yararlanma saatine geçişi desteklemeyen bir özel saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-121">[How to: Create time zones without adjustment rules](../../../docs/standard/datetime/create-time-zones-without-adjustment-rules.md) Describes how to create a custom time zone that does not support the transition to and from daylight saving time.</span></span>

<span data-ttu-id="73985-122">[Nasıl yapılır: ayarlama kuralları ile saat dilimleri oluşturma](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Gün ışığından yararlanma saatine bir veya daha fazla geçişi destekleyen bir özel saat dilimi oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-122">[How to: Create time zones with adjustment rules](../../../docs/standard/datetime/create-time-zones-with-adjustment-rules.md) Describes how to create a custom time zone that supports one or more transitions to and from daylight saving time.</span></span>

<span data-ttu-id="73985-123">[Saat dilimlerini kaydetme ve geri yükleme](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Saat dilimi verilerinin serileştirilmesi ve seri durumundan çıkarılması için <xref:System.TimeZoneInfo> desteğini açıklar ve bu özelliklerin kullanılabileceği bazı senaryoları gösterir.</span><span class="sxs-lookup"><span data-stu-id="73985-123">[Saving and restoring time zones](../../../docs/standard/datetime/saving-and-restoring-time-zones.md) Describes <xref:System.TimeZoneInfo> support for serialization and deserialization of time zone data and illustrates some of the scenarios in which these features can be used.</span></span>

<span data-ttu-id="73985-124">[Nasıl yapılır: bir katıştırılmış kaynağa saat dilimlerini kaydetme](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Özel saat dilimini oluşturmayı ve bu bilgilerin bir kaynak dosyasına nasıl kaydedileceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-124">[How to: Save time zones to an embedded resource](../../../docs/standard/datetime/save-time-zones-to-an-embedded-resource.md) Describes how to create a custom time zone and save its information in a resource file.</span></span>

<span data-ttu-id="73985-125">[Nasıl yapılır: katıştırılmış bir kaynaktan saat dilimlerini geri yükleme](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Katıştırılmış bir kaynak dosyasına kaydedilmiş özel saat dilimlerinin örneğini oluşturmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-125">[How to: Restore time zones from an embedded resource](../../../docs/standard/datetime/restore-time-zones-from-an-embedded-resource.md) Describes how to instantiate custom time zones that have been saved to an embedded resource file.</span></span>

<span data-ttu-id="73985-126">[Tarih ve saatlerle aritmetik Işlemler gerçekleştirme](../../../docs/standard/datetime/performing-arithmetic-operations.md) <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerlerini ekleme, çıkarma ve karşılaştırmayla ilgili sorunları ele alır.</span><span class="sxs-lookup"><span data-stu-id="73985-126">[Performing arithmetic operations with dates and times](../../../docs/standard/datetime/performing-arithmetic-operations.md) Discusses the issues involved in adding, subtracting, and comparing <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="73985-127">[Nasıl yapılır: Tarih ve Saat Aritmetiğinde Saat dilimlerini kullanma](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Saat diliminin ayarlama kurallarını yansıtan tarih ve saat aritmetiği yapmayı açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-127">[How to: Use time zones in date and time arithmetic](../../../docs/standard/datetime/use-time-zones-in-arithmetic.md) Discusses how to perform date and time arithmetic that reflects a time zone's adjustment rules.</span></span>

<span data-ttu-id="73985-128">[DateTime ve DateTimeOffset arasında dönüştürme](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) <xref:System.DateTime> ve <xref:System.DateTimeOffset> değerleri arasında nasıl dönüştürme yapılacağını açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-128">[Converting between DateTime and DateTimeOffset](../../../docs/standard/datetime/converting-between-datetime-and-offset.md) Describes how to convert between <xref:System.DateTime> and <xref:System.DateTimeOffset> values.</span></span>

<span data-ttu-id="73985-129">[Saatleri saat dilimleri arasında dönüştürme](../../../docs/standard/datetime/converting-between-time-zones.md) Saatlerin bir saat diliminden diğerine nasıl dönüştürüleceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-129">[Converting times between time zones](../../../docs/standard/datetime/converting-between-time-zones.md) Describes how to convert times from one time zone to another.</span></span>

<span data-ttu-id="73985-130">[Nasıl yapılır: belirsiz zamanları çözme](../../../docs/standard/datetime/resolve-ambiguous-times.md) Saat diliminin standart saatine eşleyerek belirsiz bir sürenin nasıl çözümleneceğini açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-130">[How to: Resolve ambiguous times](../../../docs/standard/datetime/resolve-ambiguous-times.md) Describes how to resolve an ambiguous time by mapping it to the time zone's standard time.</span></span>

<span data-ttu-id="73985-131">[Nasıl yapılır: kullanıcıların belirsiz zamanları çözmesine Izin ver](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Kullanıcının belirsiz bir yerel saat ve eşgüdümlü evrensel saat arasındaki eşlemeyi belirlemesine nasıl izin verbileceğinizi açıklar.</span><span class="sxs-lookup"><span data-stu-id="73985-131">[How to: Let users resolve ambiguous times](../../../docs/standard/datetime/let-users-resolve-ambiguous-times.md) Describes how to let a user determine the mapping between an ambiguous local time and Coordinated Universal Time.</span></span>

## <a name="reference"></a><span data-ttu-id="73985-132">Başvuru</span><span class="sxs-lookup"><span data-stu-id="73985-132">Reference</span></span>

<xref:System.TimeZoneInfo?displayProperty=nameWithType>
